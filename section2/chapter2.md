## 第二章：入门




|   |  |
| ---------- | ----------: |
| ![Alert](https://raw.githubusercontent.com/xiaojike/minecraft-pi-book-zh/master/section1/alert.png)     |  **注意**：本书假设你已经知道如何在树莓派上安装RespBian操作系统，你能够登陆，打开桌面环境（使用 startx），并且能使用基本的命令行命令。如果你不知道如何做这些事情，有大量的在线指南可以参看。     |

你需要做的的第一件事情是在树莓派上安装Minecraft Pi版。更多的指导可以在这里发现：[http://pi.minecraft.net/](http://pi.minecraft.net/)

现在你需要打开一个终端（terminal），使用 cd mcpi 命令进入mcpi目录。然后用 ./minecraft-pi 命令运行Minecraft Pi版。

一旦你在Minecraft里创建了一个新游戏，你得熟悉以下的操作：

**w** 让玩家向前移动

**a** 让玩家向左移动

**s** 让玩家向后移动

**d** 让玩家向右移动

**鼠标** 改变玩家的方向/视角

**tab** 释放鼠标

**鼠标右键点击** 放置块

**鼠标左键点击** 打碎块

**滚动鼠标滑轮** 选择块类型

**空格** 跳跃（飞行时，会飞的更高）

**双击空格键** 飞行（再次双击空格键时停止飞行）

**shift** 蹲下（飞行时，会飞的更低）

**e** 块选择菜单

**1-8** 从库存选择块

**esc** 打开选项菜单（也可以释放鼠标）

在Minecraft里玩耍。建造点什么东西。看看这种块都有什么不同，比如水的块，把它周围的块敲碎，看看会发生什么。

在树莓派上运行Minecraft Pi，必须是在桌面环境下，Respbian默认的命令行环境是无法运行Minecraft的。

### 2.1  用Python编程

Python是一门非常适合初学者的编程语言。它很容易阅读和编写。

Python现在有两个主要版本2.7和3。在这本书里，我们将使用2.7版。两个版本之间有些细微的差别。你可以找到更多的在线资源，或者用Ninja-IDE（下面将会提到）的功能，来检查你代码的兼容性。

#### 2.1.1	Minecraft Pi 版 API

Minecraft Pi 版API为程序员提供了一组游戏接口。也就是说，你不需要改变游戏本身，就可以通过调用API来和游戏交互。

这些API存在mcpi目录的子目录里。你需要把它们拷贝到你的python代码所在的目录下，以便使用这些API。进入你的代码目录，在终端里执行以下命令：

	cp -r ~/mcpi/api/python/* .
	
别忘了句号。

#### 2.1.2	编写和运行代码

在树莓派上编写Python代码有很多应用可以选择。我们将梳理一遍这些选项。你可以根据自己的偏好选择一项编写和运行代码的应用。你可以尝试不同的选项，看看哪一个是你最喜欢的。无论你选择哪个应用来编写代码，请确保它可以在Minecraft中运行。

##### 终端(terminal) + nano

终端是一种用文本与树莓派交互的方式。它使用命令行来代替图形化的人机交互。你也许习惯使用图形化的桌面系统或文件管理系统。终端也可以做同样的事情，只不过是用文本代替了鼠标的点击。

在终端里，我们使用一种叫做Nano的文本编辑器，来创建和修改Python源文件。用终端进入你Python代码存放的目录，然后执行一下命令：

	nano filename.py
	
可以改成你想要的任何文件名

Nano编辑器使用光标定位文本的位置。使用鼠标无法改变光标的位置，只能通过方向键移动光标。而且不能使用ctrl+c 加ctrl+v来拷贝粘贴文本。

保存文件使用ctrl+o，再接入输入你想要保存的文件名。退出Nano编辑器使用ctrl+x。当退出时，Nano会提醒你保存文件。

对熟悉使用图形化系统的人来说，适应Nano这种命令行的操作方式，可能是很困难的。

在创建完文件后，你可以用以下命令在终端里运行它：

	python filename.py
	
如果python命令后不跟文件名，python将打开交互式控制台，可以直接编写运行代码，这是一种完美的快速测试代码的方式：

	python

使用ctrl+z退出交互式控制台。

##### IDLE

IDLE是Python默认的集成开发环境(IDE)。一个集成开发环境(IDE)不但能够写代码，还提供了其他有用的功能，例如调试，语法高亮等。树莓派上的IDLE有两个版本，我们将使用IDLE，而不是IDLE3。

IDLE 是一个非常基本的 IDE。默认情况下，打开它会进入到交互式控制台，这里可以快速测试代码且无需保存。若要创建一个新的文件，请单击文件 > 新窗口或按 ctrl + n。

保存文件使用“文件”菜单。确保你保存的文件和mcpi API同目录。

在文本编辑窗口运行你写的程序，可以点击运行菜单，或是使用快捷键F5。也可以在终端里运行程序。

##### Geany

Geany是另一种比IDLE更健壮的IDE。它支持多种语言编程，而且有比IDLE更多的功能，我建议你了解一下它都能做什么。

Geany没有被预装在Raspbian系统上。安装它需要联网，可以在终端里执行以下命令来安装：

	sudo apt-get update && sudo apt-get upgrade
	sudo apt-get install geany
	
Geany现在在代码区下面提供了任务栏。一旦保存了程序，就可以通过Geany内置的终端或是通用终端来执行程序。

##### Ninja-IDE

Ninja-IDE相对其他IDE知名度要小一些。它是一款专为Python设计的，制作极为精良的IDE。因此，它为Python开发者设计了大量非常有用的功能，例如Python 2.7 和 Python 3兼容性高亮显示的功能。

目前Ninja-IDE在树莓派上的安装有点复杂。你可以在我的网站上找到安装帮助：[https://arghbox.wordpress.com/2013/06/09/ninja-ide-on-the-raspberry-pi/](https://arghbox.wordpress.com/2013/06/09/ninja-ide-on-the-raspberry-pi/ )

在侧栏上有一个运行按钮，可以运行你的程序。

你可以把一个目录当成一个项目来进行管理。而且它还有很多有用的插件，可以自定义颜色，这些功能都可以在菜单中找到。





		


	





 





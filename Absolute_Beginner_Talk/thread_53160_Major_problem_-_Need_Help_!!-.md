---
title: "Major problem - Need Help !!-"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by ChristophorusX on 2005-07-30
Hi, before I start talking about my problem please keep in mind that I am a total Linux newbie, Ubuntu is the first distro I use and I have been using it for 2 days now   :) 

I have downloaded some programs, but I can't seem to figure out how to install them.
I am used to Windows where there is an installer or an .exe file that you run but on Linux it's very weird for me.

For example I have downloaded  Beep Media Player, after I extract all I see is a bunch of files and so, I lauched the readme file to see how to install , for the basic installation for example they tell me :

[b]cd bmp-0.9.7
./configure
make
make install[/b]

Do I type this in the terminal or what ? I'm lost !

Another thing ; sometimes they mention compiling the whole thing, my question is does Ubuntu have a compiler for most programming languages or something ?
Or I have to download one ?

---

### Post by jasmuz on 2005-07-30
Those commands are to be executed in a terminal.
If you get any error messages saying that you dont have compilers installed.

Do a sudo apt-get install build-essential

---

### Post by ChristophorusX on 2005-07-30
Ah OK , but do I have to put these files somewhere ? Do they have to be in a specific directory ?

---

### Post by black hole sun on 2005-07-30
[QUOTE=ChristophorusX]Ah OK , but do I have to put these files somewhere ? Do they have to be in a specific directory ?[/QUOTE]
 No. Building it can be done in any directory. "make install" installs the program, puts files in the right places.

On a side note; why aren't you using synaptic to install it for you? It has beep media player, as well a newer version than the one you're trying to use.

---

### Post by ChristophorusX on 2005-07-30
Before I get to the **synaptic** part , when I type the previous command lines that I have posted in my first post I get the follwing :

[b]chris@Chris:~$ cd bmp-0.9.7
bash: cd: bmp-0.9.7: No such file or directory
chris@Chris:~$ ./configure
bash: ./configure: No such file or directory
chris@Chris:~$ make
make: *** No targets specified and no makefile found.  Stop.
chris@Chris:~$ make install[/b]

What is **synaptic** and what does it do ?

---

### Post by cwaldbieser on 2005-07-30
Synaptic is a GUI program for another program you will hear a lot of talk about called "apt-get".  It gets a list (from the Internet) of the thousands of different programs you might want to install.  You pick the programs you want off the list, click a button, and it installs them for you.  It is like InstallShield on steroids.

The way it works is that your computer comes with a list of different sites (called repositories) that the program can look up info on what programs are available and where to get them from.  You can add extra repositories to your initial list.  It is covered in the Guide: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by smoon on 2005-07-30
Why don't you just install the Beep Media Player with synaptic? The package is called "beep-media-player". Alternatively you can type the following in a terminal:
```
sudo apt-get install beep-media-player
```
There's a package "bmp-skins" with some themes as well. The packages are in universe, see [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) on howto enable extra repositories. I suggest you read through the [Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/) to find out how common things like installing software work under Ubuntu.

---

### Post by sophtpaw on 2005-07-30
[QUOTE=black hole sun]No. Building it can be done in any directory. "make install" installs the program, puts files in the right places.

On a side note; why aren't you using synaptic to install it for you? It has beep media player, as well a newer version than the one you're trying to use.[/QUOTE]

HI,

and welcome to the land Ubuntu in the world of Linux. Relax and enjoy and very soon you will be glad that you left the arrid planet of micro$lash winblows.

I am also a total newbie and i've managed to get going; so if i can, anyone can - trust me.
Now a word of advice: make your life easy! Use Synaptic. After all it is practically the killer application in ubuntu (and Debian and Debian-based distros) It has never been easier. Point and click and its installed (Bill Gates eat your heart out!)  You'd be silly not to use it. Of course in time you will begin to learn and do more and more from a terminal in command line. But all in good time. 
I also advise to go and check out [www.ubuntuguide.com](www.ubuntuguide.com) which i found very useful in getting up to speed on most everything.

sophtpaw

--------------------------

easy does it!

---

### Post by az on 2005-07-30
[QUOTE=ChristophorusX]Before I get to the **synaptic** part , when I type the previous command lines that I have posted in my first post I get the follwing :

[b]chris@Chris:~$ cd bmp-0.9.7
bash: cd: bmp-0.9.7: No such file or directory
chris@Chris:~$ ./configure
bash: ./configure: No such file or directory
chris@Chris:~$ make
make: *** No targets specified and no makefile found.  Stop.
chris@Chris:~$ make install[/b]

What is **synaptic** and what does it do ?[/QUOTE]


In Windows, you use installers because nobody has any choice.  Things are premade and you have no say in how they are built.  In linux (or any other open source system) not everyting is the same.  To use a metaphor, if the operating system was a house, you may need to use different cement to glue different kinds of bricks together when you build your house.

So, the fact that there is not only one way to do things adds a lot of power.  You can take applicaitons that are written by somebody and compile them to run on your system.

Yes, it is more complicated.

The solution is that there are about 14000 applications already built for you.  Everything within one distribution is pretty much made the same way.  So you can install a precompiled binary package from the repositories.

Synaptic is the tool for accessing and installing packages from the repositories.  Beep media player is in the Universe repository.

If you want  amore recent version of beep media player, you have the freedom to do what you attempted: compile it from source.

If you want to just instlal the binary package from Synaptic, you can stop reading this post now.



What the readme of the tarball you have says is the general instructions for compiling something.  This is done from the command line.  You probably uncompressed the tar.gz file and read the readme with the Gedit text editor.  That means that you never extracted the source from the package and that is why you are getting the errors "No such file or directory" and so forth.

What you would do is open a terminal

find where the tarball is:  for example

ls
cd Desktop
ls
(ls is the command to show a list of the items in the current directory.  cd means Change Directory.  Take this opportunity to use things like tab completion and the up arrow to simplify your comman line experience.  For example, instead of typing "cd Desktop", you can do "cd D" and then hit tab.  You should get the word Desktop to write itself for you.  Also, if you mistype something, you can hit up arrow and have the last line repeat istelf.  Keep hitting it for a history of your typed commands.  But I digress.)

To extract the source from the bmp tarball do
tzr xvzf bmp*
then
cd bmp*
./configure
etc...

---

### Post by ChristophorusX on 2005-07-30
Well I have found the Synaptic Package Manager, now all I have to do is select the packages of the applications that I have downloaded and it will install them for me ?

---

### Post by poofyhairguy on 2005-07-30
[QUOTE=ChristophorusX]Well I have found the Synaptic Package Manager, now all I have to do is select the packages of the applications that I have downloaded and it will install them for me ?[/QUOTE]


And hit apply.

---

### Post by aysiu on 2005-07-30
Click "Reload."
Search for packages you want.
Double-click them to mark them for installation.
Then, click "Apply."

---

### Post by sophtpaw on 2005-07-30
[QUOTE=ChristophorusX]Well I have found the Synaptic Package Manager, now all I have to do is select the packages of the applications that I have downloaded and it will install them for me ?[/QUOTE]

Couldn't be easier. If you see it in Synaptic click on it. Right click and mark for installation (same applies should you want to uninstall something) and then click the tab at the top 'Apply'

and Bob is your uncle,

sophtpaw

-------

easy does it!

---

### Post by ChristophorusX on 2005-07-30
OK , but for example I have downloaded an application, how can I add it to the synaptic database ? And does synaptic install it for me ? And which file should I add to the database among the various files in the program ?

---

### Post by az on 2005-07-30
Anything is the repositories is guranteed to not bork your system.  (mostly, anyway, everything in main...)

Anything you compile yourself is not.  So you are on your own.

Betcha can't find an application that is not already in the package repositories, though.

---

### Post by smoon on 2005-07-30
[QUOTE=ChristophorusX]OK , but for example I have downloaded an application, how can I add it to the synaptic database ? And does synaptic install it for me ? And which file should I add to the database among the various files in the program ?[/QUOTE]

You don't need to download anything on your own, Synaptic takes care of that as well. The only things you've to do in order to install a program are: Open Synaptic; Find the program you want to install; Mark it for installation; Click "Apply"
That's it, everything else is taken care of by synaptic. For example, if you  want to install Beep Media Player, you would do this:
[list]
[*]Open Synaptic
[*]Click "Search"
[*]Search for "beep media" (without the "") in Name and Description
[*]Click on the entry that says "beep-media-player" and select it for installation
[*]Click on "Apply" in the toolbar
[*]Wait for Synaptic to finish the installation
[*]Close Synaptic
[/list]

Note: You need to enable the "Universe" repository for beep-media-player, see [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) for how to do that.

---

### Post by ChristophorusX on 2005-07-31
I read the [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and followed the tutorial, but now when I open the Sysnaptic Package Manager I get a message stating that the follwing problems were found :

[b]W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/b]

I hit OK and continue, now when I search for beep media it doesn't find anyhing  :-? 

Help people !

---

### Post by smoon on 2005-07-31
[QUOTE=ChristophorusX]I read the [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and followed the tutorial, but now when I open the Sysnaptic Package Manager I get a message stating that the follwing problems were found :

[b]W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/b]

I hit OK and continue, now when I search for beep media it doesn't find anyhing  :-? 

Help people ![/QUOTE]

Maybe you forgot to run ```
sudo apt-get update
``` after editing your sources.list?

---

### Post by ChristophorusX on 2005-07-31
Oh yeah ! Sorry I feel like an idiot.

---

### Post by ChristophorusX on 2005-07-31
I'm beginning to understand and see how this works but I still have questions (I hope I'm not beeing such a pain in the a**)

The Synaptic Manager can't find everything, for example I have downloaded a game this morning, and still have no idea on how to install it ??:

The game is called Jake2 I believe it's a first person shooter based on the Quake2 Engine from id Software , anyways there is a file called Jake2-0.9.4-install.jar
and another file called Jake2src-0.9.4.tar.gz now I think that the first one is the installation files and the second one is source ? (Correct me if I'm wrong)

I have trouble installing the game, I will share the readme of Jake2-0.9.4-install.jar :

README :

Installation
------------

from binary distribution:
- run the installer with "java -jar Jake2-0.9.4-install.jar"
- follow the instructions
- change to the installation directory
- run the game with Jake2.sh or Jake2.bat
- to run Jake2 with the lwjgl OpenGL/OpenAL driver use Jake2_lwjgl.sh
or Jake2_lwjgl.bat

build from source:
- unpack jake2src-version.tar.gz or jake2-version.zip
- set JAVA_HOME environment variable to Your J2SDK1.4 installation
- run "build.sh installer" or "build.bat installer" to build the installer

Can someone tell me what should I do ? Because I'm lost.
Thanks again guys.

---

### Post by Brother_Marquis on 2005-08-30
[QUOTE=ChristophorusX]I'm beginning to understand and see how this works but I still have questions (I hope I'm not beeing such a pain in the a**)

The Synaptic Manager can't find everything, for example I have downloaded a game this morning, and still have no idea on how to install it ??:

The game is called Jake2 I believe it's a first person shooter based on the Quake2 Engine from id Software , anyways there is a file called Jake2-0.9.4-install.jar
and another file called Jake2src-0.9.4.tar.gz now I think that the first one is the installation files and the second one is source ? (Correct me if I'm wrong)

I have trouble installing the game, I will share the readme of Jake2-0.9.4-install.jar :

README :

Installation
------------

from binary distribution:
- run the installer with "java -jar Jake2-0.9.4-install.jar"
- follow the instructions
- change to the installation directory
- run the game with Jake2.sh or Jake2.bat
- to run Jake2 with the lwjgl OpenGL/OpenAL driver use Jake2_lwjgl.sh
or Jake2_lwjgl.bat

build from source:
- unpack jake2src-version.tar.gz or jake2-version.zip
- set JAVA_HOME environment variable to Your J2SDK1.4 installation
- run "build.sh installer" or "build.bat installer" to build the installer

Can someone tell me what should I do ? Because I'm lost.
Thanks again guys.[/QUOTE]


Hi everyone,
I was just wondering if there was ever a reply to this last question from ChristophorusX.  I just installed Ubuntu and understand Synaptic but have difficulty understanding how to install something not there (i.e. Team Speak).  ChristophorusX's last post summarizes my ignorance nicely!

---

### Post by aysiu on 2005-08-30
[QUOTE=Brother_Marquis]Hi everyone,
I was just wondering if there was ever a reply to this last question from ChristophorusX.  I just installed Ubuntu and understand Synaptic but have difficulty understanding how to install something not there (i.e. Team Speak).  ChristophorusX's last post summarizes my ignorance nicely![/QUOTE]

Download the file.

[http://i22.photobucket.com/albums/b337/psychocats/5c2542db.png](http://i22.photobucket.com/albums/b337/psychocats/5c2542db.png)

Double-click what you download, and click Extract.

[http://i22.photobucket.com/albums/b337/psychocats/7d58cd26.png](http://i22.photobucket.com/albums/b337/psychocats/7d58cd26.png)

Select the directory to extract it to:

[http://i22.photobucket.com/albums/b337/psychocats/b679e950.png](http://i22.photobucket.com/albums/b337/psychocats/b679e950.png)

Wait for it to extract:

[http://i22.photobucket.com/albums/b337/psychocats/f25914ca.png](http://i22.photobucket.com/albums/b337/psychocats/f25914ca.png)

Click on the extracted folder and then click on setup.sh

[http://i22.photobucket.com/albums/b337/psychocats/d4536432.png](http://i22.photobucket.com/albums/b337/psychocats/d4536432.png)

Choose run.

Then, you get a wizard.

[http://i22.photobucket.com/albums/b337/psychocats/0ddc1111.png](http://i22.photobucket.com/albums/b337/psychocats/0ddc1111.png)

Just go through the wizard.

[http://i22.photobucket.com/albums/b337/psychocats/b3c62acb.png](http://i22.photobucket.com/albums/b337/psychocats/b3c62acb.png)

---

### Post by Brother_Marquis on 2005-08-30
I knew it must be something that easy...thanks.

---

### Post by graigsmith on 2005-08-30
[QUOTE=ChristophorusX]I'm beginning to understand and see how this works but I still have questions (I hope I'm not beeing such a pain in the a**)

The Synaptic Manager can't find everything, for example I have downloaded a game this morning, and still have no idea on how to install it ??:

The game is called Jake2 I believe it's a first person shooter based on the Quake2 Engine from id Software , anyways there is a file called Jake2-0.9.4-install.jar
and another file called Jake2src-0.9.4.tar.gz now I think that the first one is the installation files and the second one is source ? (Correct me if I'm wrong)

I have trouble installing the game, I will share the readme of Jake2-0.9.4-install.jar :

README :

Installation
------------

from binary distribution:
- run the installer with "java -jar Jake2-0.9.4-install.jar"
- follow the instructions
- change to the installation directory
- run the game with Jake2.sh or Jake2.bat
- to run Jake2 with the lwjgl OpenGL/OpenAL driver use Jake2_lwjgl.sh
or Jake2_lwjgl.bat

build from source:
- unpack jake2src-version.tar.gz or jake2-version.zip
- set JAVA_HOME environment variable to Your J2SDK1.4 installation
- run "build.sh installer" or "build.bat installer" to build the installer

Can someone tell me what should I do ? Because I'm lost.
Thanks again guys.[/QUOTE]
 ok, it looks like this file Jake2-0.9.4-install.jar  is a java file. and this file Jake2src-0.9.4.tar.gz is the source. if you wanna run the .jar file you'll need java.

i have installed stuff from source before.  you extract the source files to a directory, open up a terminal and type this from within that directory.  
./configure
make
then you type either this
make install
or 
sudo make install    < beware though, this one will try to install it to your system. if your not sure where it's installing it or anything i would not run this command because you might not be able to figure out how to remove it.

sometimes you can type make uninstall to get rid of it. but that doesn't always work.

---


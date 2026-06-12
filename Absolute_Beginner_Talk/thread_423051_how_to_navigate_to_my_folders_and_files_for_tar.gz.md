---
title: "how to navigate to my folders and files for tar.gz programs"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by kystorms on 2007-04-25
I am trying really hard to find the info here about how to navigate to my folder where i extracted a program (gtwitter) i know where it is, but i dont know how to navigate to it in the terminal. where can i find the commands to do so?

i have found some howtos but the three i have used do not seem to get me anywhere, for instance, i know that my home directory has a folder called downloaded programs etc, which is where i extracted gtwitter to, yet i can not cd to the folder called "downloaded programs etc"

what am i doing incorrectly?

:confused:

---

### Post by taurus on 2007-04-25
Assuming the name of the file is program.tar.gz, open a terminal and do

```
cd ~/Desktop
tar xvzf program.tar.gz
cd program
```
Then, have a look at either INSTALL or README for instruction on how to install it.

```
more INSTALL
```
Hit the space bar for the next 24 lines.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by kystorms on 2007-04-25
thanks for the info, however none of what i have been told so far is working??? i guess this is harder than i thought it would be, i just wish there was a way to learn how to download and open programs and find directories and files.
in case anyone is reading this - the program i downloaded was gtwitter, it went to my desktop and then i extracted into my home folder into a folder called downloaded programs.

is there a step by step on how to download and use files here on the site? i dont mean to sound so slow, usually i take to new programs pretty easily.
:-(

---

### Post by taurus on 2007-04-25
What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

p.s.  Did you look at the link in my previous post?

---

### Post by annda on 2007-04-25
read this for how to move around in the terminal:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

remember, linux is case sensitive, so /home/kystorms/desktop is a directory that does not exist. /home/kystorms/Desktop is you desktop. beware of spaces too.

the best way is to use the TAB key to complete tha path for you in the terminal.

suppose you open the terminal and want to get to 'downloaded programs' folder that is sitting on your desktop.

type:

cd De<hit TAB>down<hit TAB>

and so on.

when you are in the directory, you can get to the ./configure commands.

---

### Post by kystorms on 2007-04-25
this is the code i get when i typed that in:
lisac@lisac-desktop:~$ ls -la ~/Desktop
total 100
drwxr-xr-x  2 lisac lisac  4096 2007-04-25 16:37 .
drwxr-xr-x 58 lisac lisac  4096 2007-04-25 15:16 ..
-rw-r--r--  1 lisac lisac 88730 2007-04-25 15:08 gtwitter-0.2.4.tar.gz
lisac@lisac-desktop:~$

---

### Post by taurus on 2007-04-25
Try

```
cd ~/Desktop
tar xvzf gtwitter-0.2.4.tar.gz
cd gtwitter-0.2.4
ls -la
```
and post the output of the last command here.

---

### Post by kystorms on 2007-04-25
lisac@lisac-desktop:~$ cd ~/Desktop
lisac@lisac-desktop:~/Desktop$ tar xvzf gtwitter-0.2.4.tar.gz
gtwitter-0.2.4/
gtwitter-0.2.4/configure.ac
gtwitter-0.2.4/Makefile.include
gtwitter-0.2.4/Makefile.am
gtwitter-0.2.4/aclocal.m4
gtwitter-0.2.4/COPYING
gtwitter-0.2.4/README
gtwitter-0.2.4/Makefile.in
gtwitter-0.2.4/missing
gtwitter-0.2.4/INSTALL
gtwitter-0.2.4/install-sh
gtwitter-0.2.4/configure
gtwitter-0.2.4/gtwitter/
gtwitter-0.2.4/gtwitter/CompositeInterface.cs
gtwitter-0.2.4/gtwitter/PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtwitter.gtwitter.pc.in
gtwitter-0.2.4/gtwitter/Main.cs
gtwitter-0.2.4/gtwitter/Makefile.am
gtwitter-0.2.4/gtwitter/ChangeLog
gtwitter-0.2.4/gtwitter/PostToTwitter.cs
gtwitter-0.2.4/gtwitter/MainWindow.cs
gtwitter-0.2.4/gtwitter/Makefile.in
gtwitter-0.2.4/gtwitter/gtk-gui/
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.MainWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/gui.stetic
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/generated.cs
gtwitter-0.2.4/gtwitter/GetTwitterData.cs
gtwitter-0.2.4/gtwitter/AboutDialog.cs
gtwitter-0.2.4/gtwitter/ReadInfo.cs
gtwitter-0.2.4/gtwitter/AssemblyInfo.cs
gtwitter-0.2.4/gtwitter/gtwitter.in
gtwitter-0.2.4/data/
gtwitter-0.2.4/data/gtwitter-64.png
gtwitter-0.2.4/data/gtwitter-22.png
lisac@lisac-desktop:~/Desktop$ cd gtwitter-0.2.4
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ ls -la

---

### Post by taurus on 2007-04-25
Now run

```
cd ~/Desktop/gtwitter-0.2.4
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure 
make
sudo make checkinstall
```

---

### Post by aktiwers on 2007-04-25
If you are currios I will explain what those commands do for you:
>  cd ~/Desktop/gtwitter-0.2.4
Goes to the folder that you extracted from the tar.gz (wich is like a zip or a rar.. a way to compress files)

>  sudo aptitude update
Updates your source.list
>  sudo aptitude install build-essential checkinstall
Installs tools you need to compile programs


>  ./configure 
>  make
>  sudo make checkinstall
This are the 3 commands you use to compile programs, when you download the source code.

Hope that helps. Please Correct me if im wrong.

---

### Post by kystorms on 2007-04-25
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:6 [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper/e17 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper/e17 Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 194B in 16s (12B/s)
Reading package lists... Done
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$

---

### Post by aktiwers on 2007-04-25
All fine..  now do the rest of the commands! :)

---

### Post by kystorms on 2007-04-25
I just do not see what the next command should be?
I am sorry to be so dumb about this, i really want to learn this 
but thankyou so VERY much for all the help you have given so far, you have been just wonderful.

---

### Post by aktiwers on 2007-04-25
This is the next commands! :)

>  sudo aptitude install build-essential checkinstallInstalls tools you need to compile programs


>  ./configure >  make>  sudo make checkinstallThis are the 3 commands you use to compile programs, when you download the source code.

---

### Post by kystorms on 2007-04-25
ok, did all the steps -
this is what i got:
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... no
configure: error: mcs Not found
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ make
make: *** No targets specified and no makefile found.  Stop.
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ sudo make checkinstall
make: *** No rule to make target `checkinstall'.  Stop.
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$

---

### Post by aktiwers on 2007-04-25
What about:
```
sudo make install
```

---

### Post by kystorms on 2007-04-25
I am very sorry to post this much code -
this is what i get start to finish :

lisac@lisac-desktop:~$ cd ~/Desktop
lisac@lisac-desktop:~/Desktop$ tar xvzf gtwitter-0.2.4.tar.gz
gtwitter-0.2.4/
gtwitter-0.2.4/configure.ac
gtwitter-0.2.4/Makefile.include
gtwitter-0.2.4/Makefile.am
gtwitter-0.2.4/aclocal.m4
gtwitter-0.2.4/COPYING
gtwitter-0.2.4/README
gtwitter-0.2.4/Makefile.in
gtwitter-0.2.4/missing
gtwitter-0.2.4/INSTALL
gtwitter-0.2.4/install-sh
gtwitter-0.2.4/configure
gtwitter-0.2.4/gtwitter/
gtwitter-0.2.4/gtwitter/CompositeInterface.cs
gtwitter-0.2.4/gtwitter/PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtwitter.gtwitter.pc.in
gtwitter-0.2.4/gtwitter/Main.cs
gtwitter-0.2.4/gtwitter/Makefile.am
gtwitter-0.2.4/gtwitter/ChangeLog
gtwitter-0.2.4/gtwitter/PostToTwitter.cs
gtwitter-0.2.4/gtwitter/MainWindow.cs
gtwitter-0.2.4/gtwitter/Makefile.in
gtwitter-0.2.4/gtwitter/gtk-gui/
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.MainWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/gui.stetic
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/generated.cs
gtwitter-0.2.4/gtwitter/GetTwitterData.cs
gtwitter-0.2.4/gtwitter/AboutDialog.cs
gtwitter-0.2.4/gtwitter/ReadInfo.cs
gtwitter-0.2.4/gtwitter/AssemblyInfo.cs
gtwitter-0.2.4/gtwitter/gtwitter.in
gtwitter-0.2.4/data/
gtwitter-0.2.4/data/gtwitter-64.png
gtwitter-0.2.4/data/gtwitter-22.png
lisac@lisac-desktop:~/Desktop$ cd gtwitter
bash: cd: gtwitter: No such file or directory
lisac@lisac-desktop:~/Desktop$ more INSTALL
INSTALL: No such file or directory
lisac@lisac-desktop:~/Desktop$ tar xvzf gtwitter-0.2.4.tar.gz
gtwitter-0.2.4/
gtwitter-0.2.4/configure.ac
gtwitter-0.2.4/Makefile.include
gtwitter-0.2.4/Makefile.am
gtwitter-0.2.4/aclocal.m4
gtwitter-0.2.4/COPYING
gtwitter-0.2.4/README
gtwitter-0.2.4/Makefile.in
gtwitter-0.2.4/missing
gtwitter-0.2.4/INSTALL
gtwitter-0.2.4/install-sh
gtwitter-0.2.4/configure
gtwitter-0.2.4/gtwitter/
gtwitter-0.2.4/gtwitter/CompositeInterface.cs
gtwitter-0.2.4/gtwitter/PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtwitter.gtwitter.pc.in
gtwitter-0.2.4/gtwitter/Main.cs
gtwitter-0.2.4/gtwitter/Makefile.am
gtwitter-0.2.4/gtwitter/ChangeLog
gtwitter-0.2.4/gtwitter/PostToTwitter.cs
gtwitter-0.2.4/gtwitter/MainWindow.cs
gtwitter-0.2.4/gtwitter/Makefile.in
gtwitter-0.2.4/gtwitter/gtk-gui/
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.MainWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/gui.stetic
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/generated.cs
gtwitter-0.2.4/gtwitter/GetTwitterData.cs
gtwitter-0.2.4/gtwitter/AboutDialog.cs
gtwitter-0.2.4/gtwitter/ReadInfo.cs
gtwitter-0.2.4/gtwitter/AssemblyInfo.cs
gtwitter-0.2.4/gtwitter/gtwitter.in
gtwitter-0.2.4/data/
gtwitter-0.2.4/data/gtwitter-64.png
gtwitter-0.2.4/data/gtwitter-22.png
lisac@lisac-desktop:~/Desktop$ INSTALL
bash: INSTALL: command not found
lisac@lisac-desktop:~/Desktop$ tar xvzf gtwitter-0.2.4.tar.gz
gtwitter-0.2.4/
gtwitter-0.2.4/configure.ac
gtwitter-0.2.4/Makefile.include
gtwitter-0.2.4/Makefile.am
gtwitter-0.2.4/aclocal.m4
gtwitter-0.2.4/COPYING
gtwitter-0.2.4/README
gtwitter-0.2.4/Makefile.in
gtwitter-0.2.4/missing
gtwitter-0.2.4/INSTALL
gtwitter-0.2.4/install-sh
gtwitter-0.2.4/configure
gtwitter-0.2.4/gtwitter/
gtwitter-0.2.4/gtwitter/CompositeInterface.cs
gtwitter-0.2.4/gtwitter/PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtwitter.gtwitter.pc.in
gtwitter-0.2.4/gtwitter/Main.cs
gtwitter-0.2.4/gtwitter/Makefile.am
gtwitter-0.2.4/gtwitter/ChangeLog
gtwitter-0.2.4/gtwitter/PostToTwitter.cs
gtwitter-0.2.4/gtwitter/MainWindow.cs
gtwitter-0.2.4/gtwitter/Makefile.in
gtwitter-0.2.4/gtwitter/gtk-gui/
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.MainWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/gui.stetic
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/generated.cs
gtwitter-0.2.4/gtwitter/GetTwitterData.cs
gtwitter-0.2.4/gtwitter/AboutDialog.cs
gtwitter-0.2.4/gtwitter/ReadInfo.cs
gtwitter-0.2.4/gtwitter/AssemblyInfo.cs
gtwitter-0.2.4/gtwitter/gtwitter.in
gtwitter-0.2.4/data/
gtwitter-0.2.4/data/gtwitter-64.png
gtwitter-0.2.4/data/gtwitter-22.png
lisac@lisac-desktop:~/Desktop$ cd ~/Desktop
lisac@lisac-desktop:~/Desktop$ tar xvzf gtwitter-0.2.4.tar.gz
gtwitter-0.2.4/
gtwitter-0.2.4/configure.ac
gtwitter-0.2.4/Makefile.include
gtwitter-0.2.4/Makefile.am
gtwitter-0.2.4/aclocal.m4
gtwitter-0.2.4/COPYING
gtwitter-0.2.4/README
gtwitter-0.2.4/Makefile.in
gtwitter-0.2.4/missing
gtwitter-0.2.4/INSTALL
gtwitter-0.2.4/install-sh
gtwitter-0.2.4/configure
gtwitter-0.2.4/gtwitter/
gtwitter-0.2.4/gtwitter/CompositeInterface.cs
gtwitter-0.2.4/gtwitter/PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtwitter.gtwitter.pc.in
gtwitter-0.2.4/gtwitter/Main.cs
gtwitter-0.2.4/gtwitter/Makefile.am
gtwitter-0.2.4/gtwitter/ChangeLog
gtwitter-0.2.4/gtwitter/PostToTwitter.cs
gtwitter-0.2.4/gtwitter/MainWindow.cs
gtwitter-0.2.4/gtwitter/Makefile.in
gtwitter-0.2.4/gtwitter/gtk-gui/
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.MainWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/gui.stetic
gtwitter-0.2.4/gtwitter/gtk-gui/gtwitter.PreferencesWindow.cs
gtwitter-0.2.4/gtwitter/gtk-gui/generated.cs
gtwitter-0.2.4/gtwitter/GetTwitterData.cs
gtwitter-0.2.4/gtwitter/AboutDialog.cs
gtwitter-0.2.4/gtwitter/ReadInfo.cs
gtwitter-0.2.4/gtwitter/AssemblyInfo.cs
gtwitter-0.2.4/gtwitter/gtwitter.in
gtwitter-0.2.4/data/
gtwitter-0.2.4/data/gtwitter-64.png
gtwitter-0.2.4/data/gtwitter-22.png
lisac@lisac-desktop:~/Desktop$ cd gtwitter-0.2.4
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ ls -lacd ~/Desktop/gtwitter-0.2.4
drwxr-xr-x 4 lisac lisac 4096 2007-04-25 19:51 /home/lisac/Desktop/gtwitter-0.2.4
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper/e17 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://e17.dunnewind.net](http://e17.dunnewind.net) dapper/e17 Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 194B in 16s (12B/s)
Reading package lists... Done
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ sudo aptitude install build-essential checkinstall
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--19:52:15--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--19:52:25--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--19:52:35--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--19:52:45--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--19:52:55--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--19:53:06--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--19:53:19--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--19:53:29--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--19:53:39--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--19:53:49--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--19:53:59--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--19:54:09--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... no
configure: error: mcs Not found
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... no
configure: error: mcs Not found
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ make
make: *** No targets specified and no makefile found.  Stop.
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$ sudo make checkinstall
make: *** No rule to make target `checkinstall'.  Stop.
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$  sudo make install
make: *** No rule to make target `install'.  Stop.
lisac@lisac-desktop:~/Desktop/gtwitter-0.2.4$

i just know i am doing something wrong, here but i can say i am learning now!

---

### Post by aktiwers on 2007-04-25
Gotta say im not a big compiler my self.. but that looks ok actually.
Only it says it has 1 errors in the compilation..

Try run the program now. 
```
gtwitter
```i dont know the run command for that program, so if that dont works try
hitting the "tab" button on your keyboard (right above "caps lock".)
And see if it types the rest for you.

Lets see what happens.

EDIT: The tab button thing is offcause after you typed the above command.. if it doesnt work.

---

### Post by kystorms on 2007-04-25
when i type and use the tab key, i get a huge list of programs, of which none are twitter. i guess maybe i can go to the google forum for the program and see what if any fix there is for this.

thanks so much again for everyones help!
:-)

---

### Post by aktiwers on 2007-04-25
Yeah sorry I couldnt be of more help. I dont know that much about compiling.. maybe someone else can help you out here.
Good luck and if you find a solution, please post it :)

---

### Post by boob11 on 2007-10-24
tnx man

---


---
title: "Basic questions"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Sanix on 2005-12-15
Hello :)
I have some (for you) simple questions:
I'm using windows for a long time. If I install something, I know where it will be placed (more or less). If I install something on linux, I don't know where it is. I can use a new command, but I don't know the filesystem.
For example:
Windows                                    linux
software c:\program files\  -------- ?
documents and settings ------- /home/....
How can I uninstall something? I don't want to do it with synaptics.
How can I get a list with all installed programms?
Does make this installed programms my pc slower?
Startup config file is /etc/modules, correct?
When I'm starting up my system, it takes a long time to set up my wireless connection, but at home I don't need it. How can I disable it, that it isn't automatically load a startup?
When I use the make command for compiling and installing something. I get a list with compiled and installed files directly into the console. Shall I put this in a file for later use? Or exists a file with this information already?

---

### Post by manicka on 2005-12-15
[QUOTE=Sanix]Hello :)
How can I uninstall something? I don't want to do it with synaptics.
How can I get a list with all installed programms?
[/QUOTE]

Synaptic is the best way to install a program if your new to Linux. It's simple and uses a GUI. To see what is installed, open Synaptic, click on the 'Status' button at the bottom left, then choose 'Installed from the menu. This will list every package that you have installed.

An even more graphical way to add and remove programs is to use the 'Add Applications' tool. You'll find it somewhat similar the way windows does it. I prefer the Synaptic/Apt way though

go to:
System-->Adminstartion->Add Applications

---

### Post by Sanix on 2005-12-15
But I want to do it using cli.

---

### Post by Knomefan on 2005-12-15
[QUOTE=Sanix]But I want to do it using cli.[/QUOTE]
Synaptic is just a graphical frontend to apt-get, so you can simply use apt-get to install and remove programs in the cli.

Btw., I recently found an introduction to apt that should help you out:
[http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)
(Don't get confused by it mentioning Debian, Ubuntu is based on Debian.)

Hope this helps.

---

### Post by alamba on 2005-12-15
then read up on apt-get

Akshay

---

### Post by xmastree on 2005-12-15
[QUOTE=Sanix]I'm using windows for a long time. If I install something, I know where it will be placed (more or less). If I install something on linux, I don't know where it is.[/quote]Most applications spread themselves around the system. The executable will be in /usr/bin but the other files will be elsewhere, such as /usr/share/name_of_application and other palces.

You can use synaptic to help you understand this. Open it, select an installed package, go to properties and look at Installed files.



> How can I uninstall something? I don't want to do it with synaptics.
dpkg in the command to use.```
man dpkg
```will explain how to use it.

---

### Post by jegerjensen on 2005-12-15
>For example:
>Windows                                    linux
>software c:\program files\  -------- ?
>documents and settings ------- /home/....

When you install a program in linux files are put into many places, the spesific program files are often put inside the /usr folder, system
configuration in /etc, user configuration in /home/user and so on.  Use "dpkg -l package" to list all files belonging to one program (package)

>Does make this installed programms my pc slower?
basically no.  Not unless you run all your new programs at the same time.

>Startup config file is /etc/modules, correct?
nope.  /etc/modules is one of the startup files.  many of the files in /etc are used at the startup.  /etc/init.d/  contains the different scripts being run.  As you can see the system boot is quite complicated.  Many of the scripts in /etc/init.d have configuration files in /etc/default/

>When I'm starting up my system, it takes a long time to set up my wireless connection, but at home I don't need it. How can I disable it, that it isn't automatically load a startup?

in /etc/network/interfaces there is a setting "auto CardNo"  (Card = eth or wlan, No=0 or 1)  Try commenting out  that line.  e.g.
replace 
auto eth0
with  
#auto eth0
(assuming eth0 is your wireless card)

>When I use the make command for compiling and installing something. I get a list with compiled and installed files directly into the console. Shall I put this in a file for later use? Or exists a file with this information already?

optimally use apt-get to install packages.  If you have to install from source have a look at checkinstall.   ($apt-cache show checkinstall)

hope this answered your questions, welcome to the world of Linux;)

---

### Post by Sanix on 2005-12-15
ok, thank you for your answers especially jegerjensen.

---

### Post by Van_Gogh on 2005-12-15
If jegerjensens answer doesn't work, a workaround(with quirks) is to press <ctrl>-c when you are waiting for the network interface. That will cancel the network configuration. You'll have to do it every time you don't have an connection, which is annoying.

---

### Post by bscbrit on 2005-12-15
Once you have installed a program, you can always find it by using the 'which' command:

which program_to_find

It will usually return the full path to the executable e.g.

/usr/bin/program_to_find

which is often all you need to type to make the program run.  I hope this answers one of your original questions.

---

### Post by bscbrit on 2005-12-15
You might find this link useful

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

It explains the linux filesystem and tells you where the various files are stored.

---


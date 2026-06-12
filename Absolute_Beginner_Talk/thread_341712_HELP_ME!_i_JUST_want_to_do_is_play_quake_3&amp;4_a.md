---
title: "HELP ME! i JUST want to do is play quake 3&amp;4 and play my mp3s/videos!"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by jared234 on 2007-01-19
i installed ubuntu and the instructions to install q4 and q3 say i need to create a file (not on the desktop) and i dont have permission! i can not understand why?? also i need to find a program that will let me play mp3's and videos:(   The problem is that i do not have permission to create folders.  When i go to the users and groups i see my user name AND root. upon installing the os in question i chose a password under the impression it was for the root, however it only works under my user name and i can not login as root, is there something that went wrong on the install? i really need some help, PLEASE!!

---

### Post by frolle on 2007-01-19
How do you try to install quake?

To play videos use mplayer.

Mp3 you can use xmms

Remember to have w32codecs.

---

### Post by jared234 on 2007-01-19
what is a w32code?? i can not run a file with .run extenstion either. the instructions ask me to create a file under /user/local/games but i "do not have that permission".  This OS will not recognize a .run or .exe extension. btw thatnks for the mplayer and xmms info ;)

---

### Post by Hendrixski on 2007-01-19
:) welcome to the exciting world of a secure operating system.   Regular users do not have permissions to install programs, and therefor cannot install viruses.  There is one super-user account, called root, which can install programs.

When you installed Linux you created two passwords, one for your user account, one for your root account.  if you want to access the privileges of your root account while working as a regular user you can use SUDO on the command line, or just type in your password when using Synaptic to install software.

For MP3's I recommend Amarok, it's pretty cool, you can just select it from the list in Synaptic and bang it installs.  For video games, I suggest you not waste your time and read a book instead.

BTW, all of this is in the instruction manuals, and help files that come with Ubuntu, that many people have spent countless hours to make.  I suggest you look at those before posting questions here, they are more thorough than any answer I or anyone else in the forums can give.

Hope that helps.

---

### Post by Hendrixski on 2007-01-19
> **jared234 said:**
> what is a w32code?? i can not run a file with .run extenstion either. the instructions ask me to create a file under /user/local/games but i "do not have that permission".  This OS will not recognize a .run or .exe extension. btw thatnks for the mplayer and xmms info ;)

Oh yeah, and .exe is just Microsofts crappy way of installing programs.  It doesn't work on any other operating systems.  Not on Mac, not on Linux, not on UNIX.  Nowhere but Windows.

Remember, if you want to get permission to usr/local/games you may need to type sudo before your command and enter your root password.

---

### Post by jared234 on 2007-01-19
so you're saying that if i reinstall in OS i will be able to log in with "sudo" as the username and be able to change the files?

---

### Post by riven0 on 2007-01-19
> **jared234 said:**
> so you're saying that if i reinstall in OS i will be able to log in with "sudo" as the username and be able to change the files?

No, no! :) When you want to install something you either go through Synaptic Package Manager (System >> Administration >> Synaptic Package Manager). 

Or you install through the terminal: Applications >> Accessories >> Terminal. So for example, in the terminal, to install firefox you would do: [B]sudo apt-get install firefox
[/B]
To browse and change files with administrative abilities, open the terminal and copy and paste: **gksudo nautilus**

---

### Post by jared234 on 2007-01-19
this is the command im trying to use: mkdir -p /usr/local/games/quake4/q4base

are you saying i should use: sudo mkdir -p /usr/local/games/quake4/q4base   ?

ive been with windows since 96 and im REALLY used to the GUI style, is there any way i can just point and click this problem and not have to worry about terminal instructions??  I tried to run the point release file (.run file and i just 2xclicked it) and the OS is telling me its a no go.  i think the stems back to my permissions as was explained as: "Welcome to the exciting world of a secure operating system. Regular users do not have permissions to install programs, and therefor cannot install viruses. There is one super-user account, called root, which can install programs." do i just login as root to solve these issues??? because i can't

---

### Post by jared234 on 2007-01-19
listen, i know it's not your job to help me. so i think im going to try mandrake, and then with that linux venture fails for me im going to go pay 3 months worth of ramen noodle for windows :P

---

### Post by Delkster on 2007-01-19
Just in case you're still reading:

Practically every music and video player in Ubuntu can play mp3 files but the ones included in the default installation need additional codec plugins for that.

I assume that you use the latest Ubuntu 6.10 "Edgy Eft" (with the Gnome desktop), not Kubuntu (with the KDE desktop). If you use Kubuntu or the older Ubuntu 6.06 LTS release ("Dapper Drake"), there are [instructions](https://wiki.ubuntu.com/RestrictedFormats) for those releases in the Ubuntu wiki. By the way, it's generally a good idea to let us know which one you're using so that we can provide instructions for the correct desktop.

The following applies to Ubuntu 6.10 ("Edgy Eft"):
In order to allow e.g. Rhythmbox (included by default) play mp3 audio, do the following:
1. Open System > Administration > Software Sources. Enable the community maintained (universe) software. If, at some point, you also want to have mp3 encoding and not just playback, select legally restricted (multiverse) as well. Close the window. 
1. Open Applications > Add/Remove
2. If you have Ubuntu 6.10, select to display all available applications, not only the officially supported ones. In Ubuntu 6.06 select to display unsupported and proprietary/commercial applications.
3. Enter "codec" in the search box. You should find a couple of packs of extra codecs for GStreamer (which is what Rhythmbox et al use for audio/video playback) as well as a package of Xine extra plugins. Install both GStreamer plugin packs and the Xine extra plugins. Select "Ok".

After the installation has finished, Rhythmbox should be able to play mp3 files.


The wiki also has more information on [administrative privileges](https://wiki.ubuntu.com/RootSudo). By default logins to the root account are disabled in Ubuntu and sudo is used instead. Basically, your normal user account usually doesn't have the permission to modify things outside of your home folder and personal settings, but sudo allows you to gain root privileges on demand, and for example when using the system administration tools in System > Administration. The password for sudo is your own -- the root account itself doesn't even have a valid password by default. Read the wiki page for more information.

If you want to do file management as root, there's a plugin for the file manager called nautilus-gksu. It allows you to open a file (or folder) with root privileges in the Nautilus file manager via the right-click context menu.


For Quake 3/4 and other games with an installer that has a .run or .sh filename ending (these instructions also assume that you're running Ubuntu 6.10 with Gnome -- let us know if you aren't):
Another useful plugin for Nautilus is nautilus-open-terminal. You can find it in Synaptic Package Manager (under System > Administration) once you've enabled the "universe" software repository as instructed above. Mark it for installation, apply the changes in Synaptic and close it. After that, open Applications > Accessories > Terminal and enter the command "killall nautilus". That'll cause the file manager to be terminated and automatically restarted, and the plugin should now be usable.

Now browse to the folder where you have the Q3/Q4 installer. Once in the folder, open File > Open in terminal (or something along those lines). You should now have a terminal command line whose "working directory" is conveniently the one where your game installer is. You can view the contents of the folder with the "ls" command (that's a lowercase L, not an upper-case i) and verify that you're in the right place. From the listing you can also copy the name of the installer file so you can paste it in the following command:
```
gksudo sh installer-file-name-here
```
That way you can run the installer with administrative privileges.

Note that the installer may or may not succesfully place icons for the games in the menus, and the icons may or may not become visible until the next time you log in. You can, however, run the games from the terminal if needed. The automatic completion of commands with the tab button is useful here.

After the game has been installed, open a terminal. I don't know the exact names of the Quake 3/4 executables but they're probably something like q3a, quake4, or something. In the terminal, just hit q to start the command (don't press enter) and then hit tab twice. You'll get a list of all commands and programs that start with a q. You can probably figure out from the list which one is the game you just installed. Just enter the command and the game should start. Once you know the command, you can also add a launcher for the game in the menus or the panels yourself.


Good luck.

---

### Post by Janusz11 on 2007-01-19
Take it easy, mate! :-)

First, I also suggest, that if you're new to Linux, go and have a look around the net, grab some informations and try things out to get a feel for your new system- because [Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm). ;-)

Ubuntu is a good choice if you're used to get things done in a GUI, because with Ubuntu most thing can be done right there. However, that doesn't save you from making use of a terminal or console from time to time and edit files manually or call programs from there. And I suggest that you try to get a feel for the console because its so much more powerful than a GUI- if you got used to it you don't want to miss it anymore! 

Of course you can go,  trash Ubuntu and install Mandriva instead. But remember, no matter what its called, its still Linux under the hood! ;-)

If you want to play games in Linux than this [FAQ](http://www.icculus.org/lgfaq/) might be helpful to you.

Have fun!

---

### Post by jared234 on 2007-01-22
i have learned so much in the last 2 days.  thank you all so much for your help!

---

### Post by irish_flu on 2007-01-22
> **jared234 said:**
> i have learned so much in the last 2 days.  thank you all so much for your help!

I think that if you stick with Ubuntu for a bit, you'll find that if it has something going for it over and above the other Linux flavors, it's this community.

---


---
title: "Matlab 2007a install"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Remy001 on 2007-08-19
A quick history. I am completely new to linux, installed yesterday. Always wanted to use it but I am not programing savvy. So forgive my ignorance
     I am trying to install MatLab 2007a from DVD
when I try and install how Matlab says I get, Matlab74 is the directory 
             /Matlab74$ /media/cdrom1/ install &
             [1] 15266
              bash: /media/cdrom1/: is a directory

            remy@Tatianna:~/Matlab74$ 
 
 So I tried ls -l... and get
           ~/Matlab74$ ls -l /media/cdrom1
           total 1753
           -r-xr-xr-x 1 root root  37482 2007-01-11 17:05 install
           dr-xr-xr-x 3 root root   2048 2007-02-09 00:32 InstallForMacOSX.app
           -r--r--r-- 1 root root 850228 2007-02-01 02:36 inst_doc.pdf
           -r--r--r-- 1 root root  75605 2007-02-01 02:24 license.txt
           -r--r--r-- 1 root root 817557 2007-02-01 02:36 mac_install_guide.pdf
           -r--r--r-- 1 root root   6460 2007-02-01 02:24 readme.txt
           dr-xr-xr-x 6 root root   2048 2007-02-09 01:11 update
          dr-xr-xr-x 3 root root   2048 2007-02-09 00:32 utils

If I understand this correctly I should be able to run executable files from drive

Any help would be greatly appreciated

---

### Post by kidcharles on 2007-08-19
I think you have a very simple problem here. I notice there is a space between '/media/cdrom1' and 'install'. The way you have it typed now, the shell will try to execute the command '/media/cdrom1' and will think anything that comes after it is an option. What you really want to do is execute the command '/media/cdrom1/install'. The & is optional but is fine. You can also go into the directory /media/cdrom1 and execute the install script by typing './install'. the ./ is necessary to indicate that you want to execute the 'install' script that is in the current directory, which is indicated by a single period.

Incidentally, I just installed Matlab 2007a myself the other day on my Ubuntu distro and it's pretty impressive, it has all the functionality of the Windows version.

---

### Post by Remy001 on 2007-08-19
Thanks for the reply.
 When I took the space out I get
                   ~/Matlab74$ /media/cdrom1/install
                   bash: /media/cdrom1/install: /bin/sh: bad interpreter: Permission denied

When I try ./install   from the cd drive I get a message saying it couldn't find "/install"
   I can see a file named install so I am confused

---

### Post by kidcharles on 2007-08-20
To install you will have to have root privileges. In Ubuntu this is typically done by preceding the command with 'sudo' which will prompt for your user password. Try using the command

```

$ sudo /media/cdrom1/install

```

or

```

$ sudo ./install

```

from the cdrom1 directory. You can also try:

```

$ sudo sh install

```

which will run the install script with a different 'shell'.

---

### Post by Remy001 on 2007-08-20
All I get now is 
            ~/Matlab$ sudo /media/cdrom1/install
             sudo: unable to execute /media/cdrom1/install: Permission denied

I appreciate your help. This is why I waited so long to try linux, I'm just not up with command line stuff

---

### Post by Remy001 on 2007-08-20
KidCharles, Thanks for your help I think I have it now,
 I copied files to temp folder then went into Bin and Install and had to check the box under permissions to allow executing

Thanks again
 Remy001

---

### Post by VTphilipv on 2007-08-20
i have a similar problem - even logged in as root i keep getting "permission denied" error after accepting the first license agreement. I have tried sh install* -t as well, as ubuntu suggests. ./install does not work at all.
I have also checked the box in under properties/permission to allow files to be executed....

oh, if i just type /media/cdrom/install it tells me the directory does not exist. but if i go:

cd /media
cd /cdrom

it finds the directory just fine.

any ideas?

---

### Post by kidcharles on 2007-08-20
> **Remy001 said:**
> I copied files to temp folder then went into Bin and Install and had to check the box under permissions to allow executing

That was going to be my next suggestion. Normally I would have said the problem was that the file was not executable, but based on your 'ls -l' output, you'll notice that the line for the install script was

```

-r-xr-xr-x 1 root root 37482 2007-01-11 17:05 install

```

Notice those x's? Those stand for 'executable'. Here's a nice little tutorial I just found to give you an idea of what all that information means.

[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

---

### Post by kidcharles on 2007-08-20
> **VTphilipv said:**
> 
oh, if i just type /media/cdrom/install it tells me the directory does not exist. but if i go:

cd /media
cd /cdrom

it finds the directory just fine.

any ideas?

The slash (/) is the difference VTphilipv. That stands for the root directory of the system, the upper most point in the directory tree. If you wanted to dig down into the /media directory you would use:

```

cd /media
cd cdrom

```

(Note the lack of the slash in front of cdrom). Otherwise if you type 'cd /cdrom' you are actually accessing the symbolic link 'cdrom' in the root directory /, not the directory or symbolic link in the /media directory. I think the reason it says the /media/cdrom directory doesn't exist is that you may have a directory called '/media/cdrom0' instead, but /cdrom works because you have a symbolic link (similar to the Windows shortcut) in your root directory that points to /media/cdrom0.

If you have trouble installing off the cdrom I'd say copy the files over to a temporary directory and install from there. I did an install off a network drive and had no problems. It really should not be necessary to do this, I'm not sure why there is a problem.

---

### Post by dave-5B on 2007-08-20
hey when u guys installed matlab did it put a link in your apps menu that doesnt work

i have to run it from command line

---

### Post by Remy001 on 2007-08-20
I wish I could let you know but I am getting a license error that my license dat file I made, like they told me, the error says my decimal format is incorrect

---

### Post by kidcharles on 2007-08-20
> **dave-5B said:**
> hey when u guys installed matlab did it put a link in your apps menu that doesnt work

i have to run it from command line

Very easy fix for this dave-5B. If you add the option '-desktop' to the 'matlab' command it should work fine. Matlab has had this annoying problem as long as I've been running it on linux. To get that link to work hopefully you can right-click on it and change its properties to change the command from 'matlab' to 'matlab -desktop'. Otherwise you can make your own custom application launcher.

---

### Post by Chris S. on 2007-08-20
To change the launcher in the apps menu, you'll have to right click on the menu bar in the panel and select edit menu, then find the launcher, right click it, and select properties.  That'll get you to where you can change the command.  (Edit: oh, you can also have the launcher run matlab as a terminal application, which is another work-around for this problem.  It's more annoying having that terminal there, but on some machines the "-desktop" option causes problems ... or it used to).

As for the install, VTphilipv, I read when I installed MATLAB that the CD (or DVD maybe) doesn't mount with the right permissions.  You can either try and mount it with the right permissions, which means hunting down how to do this, or just copy the contents of all install CDs to your hard drive and just run the install from there using the same procedure (different path names of course).

---

### Post by Cerny on 2007-08-22
Is it possible to get matlab through sudo apt-get  or do you have to have the cd/dvd for it?

---

### Post by kidcharles on 2007-08-22
> **Cerny said:**
> Is it possible to get matlab through sudo apt-get  or do you have to have the cd/dvd for it?
Matlab is a closed-source commercial program and is not on the repositories. There are a couple of open source and free alternatives. One is 'octave' which I know for sure is highly compatible with the matlab scripting language, and another is 'scilab' which I haven't tried yet.

---

### Post by Cerny on 2007-08-22
Sweet, that's what I was looking for. If not matlab then something equivalent to it. Thanks.

---

### Post by doojsdad on 2007-08-29
This thread will be a great help when my wife gets her MATLAB discs.  I recently bought her a 1420N and I want her transition to be as smooth as possible.  I'll be bookmarking this thread for when it's time to install MATLAB on it!  She'll also need IDL, which I haven't looked into installing yet.

---

### Post by hmjbarbosa on 2007-11-29
Dear all,

Have you managed to get matlab working correctly?

I have installed Matlab 2007a on my HP 32bits latop and I can't
see the main menubar. I mean, the menus are there and do work
if I click them, but they are not visible (check the screen 
shot below).

[IMG]http://www.geocities.com/hbarbosa/matprob.png[/IMG]

My OS is Ubuntu 7.10 with all updates installed. And the laptop
is a duo core with 2Gb ram. Any ideas what might be wrong?
java version is "1.6.0_03" and I do have the video card working
correctly (eg google earth works perfectly and other opengl 
applications as well).

By the way, I installed the same on an old P4 machine running
old suse10 and I can see the menus. Hence, its is not a problem
with the installation source.

Any help is welcome.

---

### Post by ptn107 on 2007-11-29
I've been running both matlab 07 and must say that if you can spare the flashy features give Octave a try.  It's in the universe repository.

```
sudo apt-get install octave octave-forge -y
```

It does the job fairly well.

---

### Post by hmjbarbosa on 2007-11-29
Answering my own post: the problem with the menubar is java related.

Although Ubuntu comes with an installed java virtual machine, Matlab uses its own. The problem is that some versions of jre will clash with compiz and hence the windows will not be rendered correctly.

To solve this, you must tell Matlab to stop using its own jre:

```
>> version -java

ans =

Java 1.5.0 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode, sharing
```

and start using the one you got with Ubuntu:

```

$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

```

To accomplish this just set the environment variable MATLAB_JAVA to the jre you want to use. You may want to read this [[COLOR="Blue"]_matlab article_[/COLOR]]("http://www.mathworks.com/support/solutions/data/1-1812J.html?solution=1-1812J") before doing this.

In my case I added the following to my ".profile"
```

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
```

And now the Matlab uses jre 1.6 and all menus work. From matlab I now get: 

> >> version -java

ans =

Java 1.6.0_03 with Sun Microsystems Inc. Java HotSpot(TM) Client VM mixed mode, sharing

---

### Post by atentik on 2007-12-23
I encounter similar problem here. I simply cannot determine how to access the ".profile" to make the necessary changes.

---

### Post by spaznrq on 2008-02-01
When you guys installed Matlab (I have R2007a), in the matlab install directory, does your "etc" folder have anything else besides a license.dat?  That's all I see, but from reading installation instructions, it sounds like there should be other things in there as well.

I've posted my problem here...
[http://ubuntuforums.org/showthread.php?t=338656](http://ubuntuforums.org/showthread.php?t=338656)
... but I want to find people who have this version (R2007a) successfully installed to compare to.  Basically, I can't create symbolic links to the matlab executable to be able to run it in a terminal by typing "matlab" because I simply can't find where that executable is installed to, or if it was ever even installed.

---

### Post by kidcharles on 2008-02-02
To spaznrq:

There is nothing in my /usr/local/matlab/etc directory besides 'license.dat' either.

In my setup, which was the default setup using the Matlab installer, the executable binary is /usr/local/matlab/bin/matlab. There is a symbolic link to this (and to 'mex' in the same directory) in /usr/local/bin.

---

### Post by syxbit on 2008-02-02
are you guys able to print?
i can't if i have compiz enabled, and do the java runaround for it to work :(

---

### Post by mc87 on 2008-02-02
I had the same problem with the matlab toolbar not showing up when compiz-fusion is running. Mathworks recommended setting a shell variable 

setenv AWT_TOOLKIT 3DMToolkit = 3DMToolkit

and the toolbar was up and running.  The only problem is you have to launch matlab from the terminal every time.

---

### Post by syxbit on 2008-02-03
so just typing 'setenv AWT_TOOLKIT 3DMToolkit = 3DMToolkit' in the terminal and then running matlab each time?
i'll try it when i get home

---

### Post by kbless7 on 2008-02-03
I had the same problem too. I did come up with a great work around for it though.

Open the text editor and create a shell script with the following code:

```
#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
.matlab/bin/matlab -desktop
```

Note that the .matlab part is the location of the startup file for matlab. Yours is probably different, so change that part. Then just create a launcher and for the command do:

```
sh /path/to/script
```

The "-desktop" part of the command creates a shell for matlab to run in so it doesn't have to be ran from the terminal. 

-Matt

---

### Post by mc87 on 2008-02-03
> **syxbit said:**
> so just typing 'setenv AWT_TOOLKIT 3DMToolkit = 3DMToolkit' in the terminal and then running matlab each time?
i'll try it when i get home

Actually, it's more convenient to just put that in your .tcshrc file then it gets executed each time you start the terminal

---

### Post by syxbit on 2008-02-04
i get a command not found when typing 'setenv....' in the terminal

---

### Post by mc87 on 2008-02-04
> **syxbit said:**
> i get a command not found when typing 'setenv....' in the terminal

You're probably using bash, so you would need to use export instead of setenv

---

### Post by kbless7 on 2008-02-04
> **mc87 said:**
> You're probably using bash, so you would need to use export instead of setenv

Use the export command I posted above. setenv is for other linux systems.

---

### Post by g_l_rey on 2008-02-09
I am also having some issues installing MatLab.  I have created an installation directory but when I run the Matlab installer and get to the point where I need to verify the directory it says that the directory is not writable.  The directory is /usr/local/matlab75.   My guess is that I need to have superuser privilages, but since the Matlab installer is a GUI I can't use sudo.  Your help is greatly appreciated.

---

### Post by mc87 on 2008-02-09
I had the exact same problem on my first try.  I ended up just installing matlab in my home directory

---

### Post by pr4wn on 2008-02-23
i have the same problem of the toolbar or help window not showing. when i type: 

 export AWT_TOOLKIT 3DMToolkit = 3DMToolkit

i get the following errors:

bash: export: `3DMToolkit': not a valid identifier
bash: export: `=': not a valid identifier
bash: export: `3DMToolkit': not a valid identifier

any tips greatly appreciated.

---

### Post by pr4wn on 2008-02-23
> **mc87 said:**
> You're probably using bash, so you would need to use export instead of setenv

i have the same problem of the toolbar or help window not showing. when i type: 

 export AWT_TOOLKIT 3DMToolkit = 3DMToolkit

i get the following errors:

bash: export: `3DMToolkit': not a valid identifier
bash: export: `=': not a valid identifier
bash: export: `3DMToolkit': not a valid identifier

any tips greatly appreciated.

---

### Post by kbless7 on 2008-02-23
> **pr4wn said:**
> i have the same problem of the toolbar or help window not showing. when i type: 

 export AWT_TOOLKIT 3DMToolkit = 3DMToolkit

i get the following errors:

bash: export: `3DMToolkit': not a valid identifier
bash: export: `=': not a valid identifier
bash: export: `3DMToolkit': not a valid identifier

any tips greatly appreciated.

What do you get when you type ```
version -java
``` in matlab? Also what do you get when you type ```
java -version
``` in the terminal?

-Matt

---

### Post by thinkgeek on 2008-03-26
When type commands that kbless7 suggested I find:

In Matlab
[PHP]>> version -java

ans =

Java 1.6.0 with Sun Microsystems Inc. Java HotSpot(TM) 64-Bit Server VM mixed mode
[/PHP]

In the terminal
[PHP][root@host-15153 ~]# java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea 64-Bit Server VM (build 1.7.0-b21, mixed mode)
[/PHP]

I am not running Ubuntu, rather Fedora 8. I can't see how that would make a huge difference.

Normally when I install matlab I add
[PHP]export AWT_TOOLKIT=3DMToolkit [/PHP]
to the matlab launcher script. However, this time that doesn't work, and I get the following error.
[PHP][root@host-15153 ~]# /opt/matlab/bin/matlab
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /opt/matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.load0(Unknown Source)
        at java.lang.System.load(Unknown Source)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at javax.swing.ImageIcon.<clinit>(Unknown Source)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class
[/PHP]

The only difference between this installation of matlab and any other installation I've done in the past is that this is 64-bit matlab instead of 32-bit. I'm sure this makes a difference, but I'm unsure of what the fix might be.

Any help is much appreciated.

---

### Post by thinkgeek on 2008-03-28
After doing a little bit of searching, I found a solution to the problem of matlab not working correctly while running Compiz Fusion. 

First I installed Sun's Java Runtime Environment (JRE) 6 Update 5 from Sun's website. I downloaded the rpm.bin and followed the installation instructions located on Sun's website.

Next I located where it had been installed so that I could tell matlab to use it. It was located in "/usr/java/". So I added the following line of code to the beginning of the matlab launcher script located in "/bin" of the matlab installation directory.

```
 export MATLAB_JAVA=/usr/java/jre1.6.0_05/ 
```

When I launch matlab now while running Compiz Fusion, it works. I also don't need to have the line
```
 export AWT_TOOLKIT=3DMToolkit  
```
in the matlab launcher script.

---


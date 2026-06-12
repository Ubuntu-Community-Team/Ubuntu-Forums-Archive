---
title: "stereotypical n00bz0r questions"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Chasehead on 2006-05-15
hey im totally new to linux, managed to do install ubuntu 5.10 gnome on my computer along with windows me...now some questions.

1)in windows, you download an exe, open it, follow installation instructions, choose a directory to install, add to program files, and bam youre done....so why in linux must you get "packages"? i have used the add applications program before and it seems to work with some stuff, but it seems really complicated to just get a program and have it added to a location of your specification for a lot of programs.

2)why is linux so command line heavy? in modern day computing, most people never even need to use a keyboard for anything other than naming directories and stuff. i know it gives you unlimited control, but still, why would people go out of their way to learn an entirely knew language just to open a few files?

3)whats the difference between linux itself and things like window managers, GNOME, KDE, x window system, etc? my understanding is that linux itself is like DOS in that it is the actual operating system, while windows was like a colourful blanket put over top of DOS to make it easier to use. So is ubuntu like windows in that way? or is Gnome and KDE like windows in that way? 

basically i want to say ARRRGGGHHHHH!!!!!!!!!

i have searched quite a bit on these subjects and still do not understand exactly what is going on. i will gladly except links to guides which are written for even monkeys to understand.

w00t.

---

### Post by confused57 on 2006-05-15
Check out this website:

[http://www.psychocats.net/essays/linuxforwindows.php](http://www.psychocats.net/essays/linuxforwindows.php)

This is aysiu's(a well-respected member of this forum) website.  Be sure to read some of his other "essays" or "howto's" listed on his site.  He has a way of explaining things that are easy to understand and quite insightful...

---

### Post by Sef on 2006-05-15
> 1)in windows, you download an exe, open it, follow installation instructions, choose a directory to install, add to program files, and bam youre done....so why in linux must you get "packages"? i have used the add applications program before and it seems to work with some stuff, but it seems really complicated to just get a program and have it added to a location of your specification for a lot of programs.

Synaptic Package Manager is a front-end GUI (Graphical User Interface.)  It is easy to install packages from it.

2)why is linux so command line heavy? in modern day computing, most people never even need to use a keyboard for anything other than naming directories and stuff. i know it gives you unlimited control, but still, why would people go out of their way to learn an entirely knew language just to open a few files?

With Ubuntu, you have a choice of using the command line (terminal) or a GUI (Synaptic) for downloading packages.

> 3)whats the difference between linux itself and things like window managers, GNOME, KDE, x window system, etc? my understanding is that linux itself is like DOS in that it is the actual operating system, while windows was like a colourful blanket put over top of DOS to make it easier to use. So is ubuntu like windows in that way? or is Gnome and KDE like windows in that way?


Technically, Ubuntu and other distros are GNU/LInux.  Linux is the kernel and GNU is everything else.   Think of Linux as the heart and GNU as the rest of the body.  

Think of a Window Managers as the skin.  There's a lot going on underneath that you don't worry about.   They mostly are GUI-based today.  

GNU/Linux may seem similar to Windows, but they function very differently.  GNU/Linux is modular: you can take out an application and it won't affect the system.  Windows is monolithic: Almost all applications are part of the system; hence, if you take out an application that is a part of the system, you can cause the computer to become unstable.

---

### Post by joshrobinson on 2006-05-15
the term linux gets thrown around all the time as different things

linux can be the kernel (which is the heart of the operating system that everythign communicates with, hardware communicates with the kernel, and so on)

linux can be called the entire operating system
linux can also be called a distrobution/distro.. such as suse, redhat, or ubuntu

command line is so heavy because thats what the operating system came from, and you would be suprised how far its come.. alot of things now can be done with GUI that were much harder to do in the past.. and honestly for us linux guru's command's are alot faster then working with the gui

and installing packages is easier then exe files for me.. double click it.. put in the password.. and its installed.. all you have to do is execute it

---

### Post by joshrobinson on 2006-05-15
[QUOTE=Sef]Syn...[/QUOTE]

great minds think alike 8)

---

### Post by skippy81 on 2006-05-15
[QUOTE=Chasehead]1)in windows, you download an exe, open it, follow installation instructions, choose a directory to install, add to program files, and bam youre done....so why in linux must you get "packages"?[/QUOTE]

Linux is surely easier than windows in this respect.  Use synaptic package manager.  You download and install a program in one click.  You can uninstall and delete a program in one click.  Useful programs to complement the one you choose are downloaded and configured automatically.  Packages definately give linux the edge over windows when it comes to quickly obtaining a new program.

[QUOTE=Chasehead]2)why is linux so command line heavy? in modern day computing, most people never even need to use a keyboard for anything other than naming directories and stuff. i know it gives you unlimited control, but still, why would people go out of their way to learn an entirely knew language just to open a few files?[/QUOTE]

Linux is command line heavy because it is a 'real' operating system.  Windows is actually very limited in its capabilities.  Find a hacking guide on the internet - step 1 is always install linux.  Find a guide to running a webserver - step 1 install linux.  :p The command line allows you to operate your linux box from anywhere in the world with a simple telnet session.  You can reboot a linux box from hawai.  The most common 'home and office' tasks can all be done without the command line, but knowing the commands gives you more power.  Don't forget that windows command line is used all the time by IT pros, I have never seen anyone with any skill fiddle with the gui to refresh an IP, they use 'ipconfig'.  Likewise with massive deletes and copy operations.  Learning the commands in linux really isnt hard - if you were totally new to computers and had never used windows I doubt you would find it any easier to learn than linux.  

[QUOTE=Chasehead]3)whats the difference between linux itself and things like window managers, GNOME, KDE, x window system, etc? [/QUOTE]  In the old days windows was a program which ran within MSDOS - now the gui IS windows, no matter what you do you always have the gui sitting there using resources.  With linux the gui programs are seperate.  The x window system is basically a framework - like the windows API is.  Gnome and KDE are GUIs which run within this framework.  Linux is usable without a GUI.  Thus you can telnet in from ANY computer, anywhere in the world and do anything you want on your linux box.

---

### Post by mostwanted on 2006-05-15
1) Take a look at this site: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

2) You don't really *need* to use the temrinal that much. It's just the easiest way to make uniform instructions for all distros.

3) DOS (I suspect you mean MS-DOS) is Microsoft's old operating system. The interface was command-line based, but later versions had a graphical interface as well (Windows 1.0 through 95 to ME). The newer versions of Windows don't have a real command-line, but instead come with an emulator for some of the old DOS commands.

I'm not sure what you mean about Linux being like DOS; try to not see the operating systems as just the interfaces they present, that's a very small part of an operating system.

The equivalent to the graphical shell in Windows is the X Windowing system (low level graphics) + the window manager (draws the windows you can move around) + the desktop enviroment (Gnome or KDE: a set of common widgets and default programs).

[QUOTE=Chasehead]i will gladly except links to guides which are written for even monkeys to understand.[/QUOTE]

Well, I linked you to *"The Monkey Blog"* earlier on :)

---

### Post by brentoboy on 2006-05-15
When windows 95 made it so that you boot strait to windows (instead of a dos prompt, where you would type "win" to get a gui), I got really ticked off, because the prompt is where the real work gets done.  Since then, I have grown acustomed to gui instead, and prefer it.  I like ubuntu becuase unlike slackware and gentoo, a lot of things can be done from the gui.

The only thing that can be hard in Ubuntu to do from the gui is edit an arbitrary file that is owned by root.  if you edit your applications menu (right click the ubuntu symbol, and edit menu) you can find a root file browser, enable that link,  and then you can browse the file system and open files (or edit their permissions) as root.

The examples posted on most websites and howto's use the command line becuase it is easier to explain how to type this:.....  rather than explain where to find button X, and what menu to open....  for example it is so much easier to say:

sudo apt-get build-essential

then it is to say:

goto the "System" menu, under "Administration", click "Synaptic Package Manager"  then find "build-essential" in the list of packages, click it, and verify the dependancy packages, ...  

a picture is worth a thousand words, and sometimes, it takes a thousand words to explain how to navigate a picture (gui), but in a terminal window, the relationship is one word for one word.  so, from a technical howto writer's standpoint, the terminal is just cleaner, and there is less room for accidental misunderstanding.

---

### Post by aysiu on 2006-05-15
[QUOTE=brentoboy]
The only thing that can be hard in Ubuntu to do from the gui is edit an arbitrary file that is owned by root.  if you edit your applications menu (right click the ubuntu symbol, and edit menu) you can find a root file browser, enable that link,  and then you can browse the file system and open files (or edit their permissions) as root.[/QUOTE] I usually advise that people create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` in Gnome or ```
kdesu konqueror
``` in KDE. That way, they can just click, type in a password, and be able to browse graphically to change root-owned files.

Once they close the window, they're out of temporarily being root.

---

### Post by joshrobinson on 2006-05-15
[QUOTE=aysiu]```
gksudo nautilus
``` in Gnome or[/QUOTE]

ive always used sudo nautilus, which works fine also.. but i just wanted to add, that if you make a desktop launcher to run a root file browser then you have to use gksudo.. you know why that is aysiu?

---

### Post by aysiu on 2006-05-15
[QUOTE=joshrobinson]ive always used sudo nautilus, which works fine also.. but i just wanted to add, that if you make a desktop launcher to run a root file browser then you have to use gksudo.. you know why that is aysiu?[/QUOTE] While *sudo nautilus* does work, *sudo* is really for only terminal commands. *gksudo* is what you should use for graphical applications.

In the case of *sudo nautilus*, there's probably no harm done (for whatever reason), but I know *sudo kate* does not work and sometimes screws up user permissions.

It's always a good idea to use *sudo* with terminal commands and *gksudo* or *kdesu* with graphical applications.

---

### Post by joshrobinson on 2006-05-15
[QUOTE=aysiu]While *sudo nautilus* does work, *sudo* is really for only terminal commands. *gksudo* is what you should use for graphical applications.

In the case of *sudo nautilus*, there's probably no harm done (for whatever reason), but I know *sudo kate* does not work and sometimes screws up user permissions.

It's always a good idea to use *sudo* with terminal commands and *gksudo* or *kdesu* with graphical applications.[/QUOTE]

yeah ive mainly just used sudo nautilus in a terminal, i guess that gk is there for like you said being in the GUI

thanks aysui

---

### Post by mcduck on 2006-05-15
[QUOTE=joshrobinson]ive always used sudo nautilus, which works fine also.. but i just wanted to add, that if you make a desktop launcher to run a root file browser then you have to use gksudo.. you know why that is aysiu?[/QUOTE]
Both sudo and gksudo need your password, but sudo has no way to ask you for it unless run in terminal. So if you make a launcher for 'sudo nautilus' and click it, nothing happens.. (unless you set the launcher to 'run in terminal')

Gksudo instead gives you a window where you can enter your password, so it doesn't need the terminal window. And that's why it suits better for launchers :)

---

### Post by Chasehead on 2006-05-15
hey thanks for all the help! much appreciated and this has helped me to understand more of what exactly is going on.

> Linux is surely easier than windows in this respect. Use synaptic package manager. You download and install a program in one click. You can uninstall and delete a program in one click. Useful programs to complement the one you choose are downloaded and configured automatically. Packages definately give linux the edge over windows when it comes to quickly obtaining a new program.


when i use the synaptic package manager, some of the stuff intalls no problem and shows up in the applications menu...but a lot of stuff shows up somewhere in the file system in one of the many folders in there, and doesnt show up in the applications menu at all. like for instance, I downloaded doomlegacy and 3ddesktop, and i don't know what file is the actual program (windows programs all end in .exe, and when you click on it, it opens up no problem...unless you get a missing .dll error!;) ).


> a picture is worth a thousand words, and sometimes, it takes a thousand words to explain how to navigate a picture (gui)

That is an awesome quote!

---

### Post by joshrobinson on 2006-05-15
[QUOTE=Chasehead]hey thanks for all the help! much appreciated and this has helped me to understand more of what exactly is going on.




when i use the synaptic package manager, some of the stuff intalls no problem and shows up in the applications menu...but a lot of stuff shows up somewhere in the file system in one of the many folders in there, and doesnt show up in the applications menu at all. like for instance, I downloaded doomlegacy and 3ddesktop, and i don't know what file is the actual program (windows programs all end in .exe, and when you click on it, it opens up no problem...unless you get a missing .dll error!;) ).




That is an awesome quote![/QUOTE]

well i know 3ddesktop you type 3ddesk to run, im not sure about doomlegacy
you can type 3ddesk into a terminal, or add beagle to your top panel, by right clicking it and going to add to panel and clicking "deskbar"

when it shows up you can run commands in there instead of a terminal

---

### Post by aysiu on 2006-05-15
[QUOTE=Chasehead]
when i use the synaptic package manager, some of the stuff intalls no problem and shows up in the applications menu...but a lot of stuff shows up somewhere in the file system in one of the many folders in there, and doesnt show up in the applications menu at all. like for instance, I downloaded doomlegacy and 3ddesktop, and i don't know what file is the actual program (windows programs all end in .exe, and when you click on it, it opens up no problem...unless you get a missing .dll error!;) ).[/QUOTE] Read [I installed it, but where did my program go?](http://monkeyblog.org/ubuntu/installing.html#where_did_it_go).

---

### Post by nudnik on 2006-05-15
1)in windows, you download an exe, open it, follow installation instructions, choose a directory to install, add to program files, and bam youre done....so why in linux must you get "packages"? i have used the add applications program before and it seems to work with some stuff, but it seems really complicated to just get a program and have it added to a location of your specification for a lot of programs.

Linux is not standardized as Windows is. There are dozens of different distributions using several variants of the same kernel. If a program is not customised for that particular distro, it will often not work at all, or perform oddly. Therefore, many distributions have there own customised set of programs available for download from their servers. 

The only way around this is to compile your own programs from source, something I have to do occassionally since I am using the 2.6.16.16 kernel. 


2)why is linux so command line heavy? in modern day computing, most people never even need to use a keyboard for anything other than naming directories and stuff. i know it gives you unlimited control, but still, why would people go out of their way to learn an entirely knew language just to open a few files?


 Generally speaking, Linux is not designed for broad appeal and thus retains some of the industrial interface qualities of its UNIX parent. This can be very useful for certain specialised tasks, but does get a bit old when used for day to day desktop tasks. This will change in the future as distributions arise which have all of the interface friendly features of Windows, but with Linux's more resiliant underlying architecture. 

3)whats the difference between linux itself and things like window managers, GNOME, KDE, x window system, etc? my understanding is that linux itself is like DOS in that it is the actual operating system, while windows was like a colourful blanket put over top of DOS to make it easier to use. So is ubuntu like windows in that way? or is Gnome and KDE like windows in that way?

Linux is like DOS in the sense you refer to it. Gnome and KDE are the GUIs (like Windows) Ubuntu is merely a name for the Ubuntu developers particular build of the Gnome desktop enviroment. 

There is the important difference of course as a previous poster pointed out that Linux based systems are modular.

---

### Post by steve.horsley on 2006-05-15
[QUOTE=Chasehead]hey im totally new to linux, managed to do install ubuntu 5.10 gnome on my computer along with windows me...now some questions.

1)in windows, you download an exe, open it, follow installation instructions, choose a directory to install, add to program files, and bam youre done....so why in linux must you get "packages"? i have used the add applications program before and it seems to work with some stuff, but it seems really complicated to just get a program and have it added to a location of your specification for a lot of programs.
[/QUOTE]
I don't know if others have pointed this out, but pacakages are the way software is delivered. But unlike random .exe files from dodgy web sites, packages normally come from Ubuntu repos so you can trust them, and packages know about other packages - they know what other packages are needed for the thing you are installing to work, and they know which other packages must **not** be installed (conflicts). Windows has no such concept, and many problems have been caused by conflicts or missing dependencies.
> 
3)whats the difference between linux itself and things like window managers, GNOME, KDE, x window system, etc? my understanding is that linux itself is like DOS in that it is the actual operating system, while windows was like a colourful blanket put over top of DOS to make it easier to use. So is ubuntu like windows in that way? or is Gnome and KDE like windows in that way? 

I would go further than others have said. The Linux kernel doesn't even have a command line. The kernel provides services for programs to call upon - the real core. The command interpreter, bash, is a program that runs atop of the kernel, interprets commands and sends the appropriate requests to the kernel.

Xwindows is another layer again - it is normally launched from a bash script, and creates the GUI. As you have figured out, there are different styles of GUI (window managers) that run on top of X, of which KDE, Gnome and XFCE are the best known these days (fvwm was my first - quite basic by today's standards). 
> 
basically i want to say ARRRGGGHHHHH!!!!!!!!!

It's having to **un**-learn stuff that is rather harder than the new stuff you have to learn. It is worth it though.

---

### Post by aysiu on 2006-05-15
**Package Management**
I compare here (with screenshots) installing software through Synaptic and through a setup.exe:

[http://www.psychocats.net/essays/winuxinstall](http://www.psychocats.net/essays/winuxinstall)

Synaptic is particularly handy if you want to install about five or six programs at once. Clicking through five setup.exes is a pain.

Now, if you want stuff *outside* the repositories, that's when Linux application installation is a pain...

Luckily for me, I don't need stuff outside the repos.

**Command-line**
I can understand where you might get the impression that Linux is heavily reliant on the command-line, seeing as how most people will offer instructions via the command-line. 

The truth is that Linux is not reliant on the command-line, for the most part, especially if you use distros like SuSE, Mepis, PCLinuxOS, or Linspire. Almost everything can be configured via point-and-click. 

A little less so in Ubuntu, but I can't think of any task that I do on a day-to-day basis in Ubuntu that *cannot* be done graphically. I choose to use the command-line because it's often faster, but that's my choice.

For more info, read [Why I think the command-line is user-friendly...](http://www.ubuntuforums.org/showthread.php?t=59334)

---


---
title: "Problem installing Avast Antivirus"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Orline on 2007-06-29
Hi,

I'm a "newbie^10" on Linux and Ubuntu 7.04, that I installed yesterday.
So far, so good ! First thing I thought of was to install anti virus program.
Looked on internet - they say best of all is Avast!
Downloaded "avast4workstation_1.0.6-2_i386.deb" on the desktop.
Used command "sudo dpkg -i avast4workstation_1.0.6-2_i386.deb" and it worked (anazing ! ;-) ) Went to site to apply for license key, got it, entered it and scanned, then upgdated program.
The only problem : I cannot get the icon in Aplication/Accessories list.
Went in the directory window by window in : /usr/lib/avast4workstation/share/avast/desktop
(otherwise how to do cd/usr/lib/avast4workstation/share/avast/desktop ???? ) HAve not a RUN window as in Windows ...
Used command as shown here : sudo ./install-desktop-entries.sh instal 
Nothing in the list.
Used OPEN by other application, then USE a custom Command and inserted "sudo ./install-desktop-entries.sh install"
Rebooted.
Nothing in the Application/Accessories list.

What is wrong, please ??????

Thanks, Orline

---

### Post by @trophy on 2007-06-29
> **Orline said:**
> Hi,

I'm a "newbie^10" on Linux and Ubuntu 7.04, that I installed yesterday.
So far, so good ! First thing I thought of was to install anti virus program.
Looked on internet - they say best of all is Avast!
Downloaded "avast4workstation_1.0.6-2_i386.deb" on the desktop.
Used command "sudo dpkg -i avast4workstation_1.0.6-2_i386.deb" and it worked (anazing ! ;-) ) Went to site to apply for license key, got it, entered it and scanned, then upgdated program.
The only problem : I cannot get the icon in Aplication/Accessories list.
Went in the directory window by window in : /usr/lib/avast4workstation/share/avast/desktop
(otherwise how to do cd/usr/lib/avast4workstation/share/avast/desktop ???? ) HAve not a RUN window as in Windows ...
Used command as shown here : sudo ./install-desktop-entries.sh instal 
Nothing in the list.
Used OPEN by other application, then USE a custom Command and inserted "sudo ./install-desktop-entries.sh install"
Rebooted.
Nothing in the Application/Accessories list.

What is wrong, please ??????

Thanks, Orline

Hey first of all welcome to Ubuntu.

And second, here's what you need to do:

1: Click on Applications, then Accessories, then Terminal

2: That will open up a terminal window (looks like DOS) and that's where you put in those commands.

3: First command is "cd /usr/lib/avast4workstation/share/avast/desktop" (without the quotes)  "cd" means "Change Directory" same as in DOS, and "/usr/lib/avast4workstation/share/avast/desktop" is the directory you're trying to switch to.

4: Second command is "sudo ./install-desktop-entries.sh" (without the quotes)  "sudo" needs to be put in front of everything which modifies system files, "./" means the current directory, and "install-desktop-entries.sh" is a shell script which installs stuff to your menu (like a .bat file in windows).

Hope that helps!  Let us know if you are having any more trouble.

Oh, and by the way... you don't really need an antivirus program for linux anyway.  There are no linux viruses in the wild.  None.  Zip.  Zilch.  Nada.

---

### Post by Mr Greencastle on 2007-06-29
You needn't worry about viruses in Linux, as there are none.

The only benefit I see of using an AV program is to scan your Windows partition (If you have one) without having to boot into Windows.

Hope that enlightened you!

Mr Green

---

### Post by speaker219 on 2007-06-29
> **Mr Greencastle said:**
> You needn't worry about viruses in Linux, as there are none.

The only benefit I see of using an AV program is to scan your Windows partition (If you have one) without having to boot into Windows.

Hope that enlightened you!

Mr Green
Ditto. There is no need for this, there are almost no viruses for linux. Anti-virus tools for Linux are designed to get rid of viruses on a Windows partiton or if you share files or anything like that.

---

### Post by mytwobears on 2007-06-30
> **Orline said:**
> Hi,

I'm a "newbie^10" on Linux and Ubuntu 7.04, that I installed yesterday.
So far, so good ! First thing I thought of was to install anti virus program.
Looked on internet - they say best of all is Avast!
Downloaded "avast4workstation_1.0.6-2_i386.deb" on the desktop.
Used command "sudo dpkg -i avast4workstation_1.0.6-2_i386.deb" and it worked (anazing ! ;-) ) Went to site to apply for license key, got it, entered it and scanned, then upgdated program.
The only problem : I cannot get the icon in Aplication/Accessories list.
Went in the directory window by window in : /usr/lib/avast4workstation/share/avast/desktop
(otherwise how to do cd/usr/lib/avast4workstation/share/avast/desktop ???? ) HAve not a RUN window as in Windows ...
Used command as shown here : sudo ./install-desktop-entries.sh instal 
Nothing in the list.
Used OPEN by other application, then USE a custom Command and inserted "sudo ./install-desktop-entries.sh install"
Rebooted.
Nothing in the Application/Accessories list.

What is wrong, please ??????

Thanks, Orline


If you hit Alt F2 you will get a Run program window, then just type in "avastgui" (without the quotes) and hit enter.  The avast antivirus program will start up.

Hope this helps.

---

### Post by fallsoff on 2008-02-28
ok ok ok_same deal__avast in Gutsy. I did the DL and install. Cant find the app. Finally found the container in temp. searched and searched.

Came here, saw the post, ran the cmds and sh exactly as recommended, No icon__nada on the desktop. Then did the alt-f2=run command and same thing Nothing. Any idea why I cant find Avast or get an icon ior anything after all that work.
Bill is looking better and better to me these days!
thanks
fallsoff

---

### Post by hyper_ch on 2008-02-28
Leave your virus troubles with windows... on linux you normally don't need antivirus.

---

### Post by fallsoff on 2008-02-28
thanks! i get different opinions going back and forth gates to free.l
fallsoff

---

### Post by fallsoff on 2008-02-28
The deeper question was how do i find a downloaded and installed app and get it to run? I searched all over Hell and never did get this one located so that it could be used if needed. Is it a sudo command? if so what is syntax please. Or is there a central location where apps are stored that I can get a shortcut to copy to the desktop from? Am i making sense? I am still grappling with basic concepts in Linux. I am doing lots of reading and dont mind blowing it ujp and reinstalling a few times, I just need to learn the basics of running apps, cmd syntax, GUI and so forth.
Thanks for responding. This is a good forum!
Best,
fallsoffmotorcycle
ps
130 AM here....yawn!

---

### Post by hyper_ch on 2008-02-28
Use Add/Remove Software to download and install applications.

---

### Post by fallsoff on 2008-02-28
sorry miscommunication here. how to RUN an app that was installed and cant be found [by me]. i looked all over. where oh where do they go and how do you get them to run when you do find the? i hate desktop icon clutter but sometimes it is necessary to easily run an app.
best.
fallsoff

---

### Post by Joeb454 on 2008-02-28
it could be in **/usr/bin** or **/usr/sbin** or **/usr/share/apps**

It varies...I don't know why...and yes it bugs me too.

Aside from that, are you aware that you only really need a virus scanner on Linux to check for Windows Viruses that could be passed on through a network

---

### Post by lswest on 2008-02-28
well, if you download a .deb you can generally install it by double-clicking or using this command in a terminal: ```
sudo dpkg -i [packagename].deb
```  after installing the program can be (or should be able to be) run using the packagename (without version numbers and such) in either a terminal or in the application launcher (reached through alt + f2).  So that if it was amsn-1.2.5.6.deb you would run it with ```
 amsn 
```  If you're not sure if the program will run, running it in the terminal will tell you if the command/program exists or not.  Hope it helps clear things up, but i agree with the others, virus scanners are obsolete in Linux, unless you mean to scan a windows disk with it.

*EDIT* the avast software package is called avast4workstation_1.0.8-2_i386.deb, but i believe the command to start it is ```
avast4
``` (not 100% sure,  but i think so)

---

### Post by fallsoff on 2008-02-28
Hi again,
in one of the usr/?? folders i found a partially opened box file icon for avast. Was that the stored DL or the actual app itself? I could not get it to run, so i assume it was the unzipped download preinstall. Again I am confused.  i just wanted to press a button and run avast on some folders in the windows share i access through Ubuntu.

scuse the hasty scribbling and thanks again,
fallsoff

---

### Post by Oldsoldier2003 on 2008-02-28
> **fallsoff said:**
> The deeper question was how do i find a downloaded and installed app and get it to run? I searched all over Hell and never did get this one located so that it could be used if needed. Is it a sudo command? if so what is syntax please. Or is there a central location where apps are stored that I can get a shortcut to copy to the desktop from? Am i making sense? I am still grappling with basic concepts in Linux. I am doing lots of reading and dont mind blowing it ujp and reinstalling a few times, I just need to learn the basics of running apps, cmd syntax, GUI and so forth.
Thanks for responding. This is a good forum!
Best,
fallsoffmotorcycle
ps
130 AM here....yawn! 
if you downloaded the taball and can't find it try (in a terminal):
```
 locate <filename>
``` 

if you get an error about the database being over 8 days old:
```
sudo slocate -u
```

will redo your default locate database. of if you just want to index a specific path:

```
sudo slocate -U /path_goes_here
```

---

### Post by Oldsoldier2003 on 2008-02-28
> **fallsoff said:**
> Hi again,
in one of the usr/?? folders i found a partially opened box file icon for avast. Was that the stored DL or the actual app itself? I could not get it to run, so i assume it was the unzipped download preinstall. Again I am confused.  i just wanted to press a button and run avast on some folders in the windows share i access through Ubuntu.

scuse the hasty scribbling and thanks again,
fallsoff

whats the name of the file? or rather extension. if its .deb its a package file and you can right click it to install it.

---

### Post by fallsoff on 2008-02-28
will look and see this afternoon and THANKS!
fallsoff

---


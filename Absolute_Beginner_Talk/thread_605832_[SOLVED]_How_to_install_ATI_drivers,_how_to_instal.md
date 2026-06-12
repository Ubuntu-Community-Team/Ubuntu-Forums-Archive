---
title: "[SOLVED] How to install ATI drivers, how to install anything."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by DawnDisciple on 2007-11-07
I am not happy with the ATI drivers Linux downloaded for me and want to install the ones I downloaded from AMD site.  Thing is its not like windows it won't let me run it, my head hurts.

---

### Post by oilchangeguy on 2007-11-07
read this:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by carlosjuero on 2007-11-07
To install the drivers you downloaded, first make sure that you uninstall the previous drivers (there should be an uninstall script in /usr/share/ati).

If there is an /usr/share/ati folder open up the Terminal and do this:
```

cd /usr/share/ati
sudo ./fglrx-uninstall.sh

```
The uninstall script will run and remove the fglrx drivers from the system.

Next, change to the place you downloaded the ATI drivers (lets say on your Desktop) and run the routine as follows (from terminal):
```

cd ~/Desktop
sudo ./ati-driver-installer-8.42.3-x86-x86_64.run

```
(Note: this assumes that you downloaded the latest ATI driver to your Desktop)

This will uncompress the installer and then open the GUI installation screen - choose an automatic install. When the install is done, do the following command from the terminal:
```

sudo aticonfig --initial

```
and then reboot the computer.

---

### Post by stchman on 2007-11-07
> **DawnDisciple said:**
> I am not happy with the ATI drivers Linux downloaded for me and want to install the ones I downloaded from AMD site.  Thing is its not like windows it won't let me run it, my head hurts.

The ATI restricted driver will be all you need, just enable it.

---

### Post by DawnDisciple on 2007-11-07
I just get command not found, I don't think I have sudo, and I haven't a clue how to get it, this is so hard, none of it makes sense. All I want to do in install a driver, this is rocket science.

---

### Post by carlosjuero on 2007-11-07
> **DawnDisciple said:**
> I just get command not found, I don't think I have sudo, and I haven't a clue how to get it, this is so hard, none of it makes sense. All I want to do in install a driver, this is rocket science.
sudo is part of the operating system, it is a command to elevate you to root level so you can install drivers and system software. You have to ensure that 1) You are spelling the name of the file exactly how it appears (Lower case & upper case letters the way they show up), 2) You are in the folder that the script is, or specify the full path.

---

### Post by Maestro23 on 2007-11-07
> **DawnDisciple said:**
> I just get command not found, I don't think I have sudo, and I haven't a clue how to get it, this is so hard, none of it makes sense. All I want to do in install a driver, this is rocket science.

This is NOT Windows. Soon as you get that out your head, and realize that things are done differently in a Linux OS, things will get better. :smile:

You need to use the **sudo **command for admin/root access when installing certain files or dealing with directories owned by root /.

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

*Great 1st post in this thread by carlos.

---

### Post by DawnDisciple on 2007-11-07
LoL, everyone just says do this or do that, type this pull that push the other but nobody ever tells you how to do,push and pull.:)

---

### Post by NightCrawler03X on 2007-11-07
> **carlosjuero said:**
> To install the drivers you downloaded, first make sure that you uninstall the previous drivers (there should be an uninstall script in /usr/share/ati).

If there is an /usr/share/ati folder open up the Terminal and do this:
```

cd /usr/share/ati
sudo ./fglrx-uninstall.sh

```
The uninstall script will run and remove the fglrx drivers from the system.

Next, change to the place you downloaded the ATI drivers (lets say on your Desktop) and run the routine as follows (from terminal):
```

cd ~/Desktop
sudo ./ati-driver-installer-8.42.3-x86-x86_64.run

```
(Note: this assumes that you downloaded the latest ATI driver to your Desktop)

This will uncompress the installer and then open the GUI installation screen - choose an automatic install. When the install is done, do the following command from the terminal:
```

sudo aticonfig --initial

```
**[size=4]and then reboot the computer[/size]**.

Actually, all you need to do is restart your X Server. For most distros, it's quite simple: Ctrl+Alt+Backspace
That will bring you back to your login screen, log back in and you have ATI 3d support.


Alternative to downloading the driver from AMD's site, the driver is available in Ubuntu's restricted drivers section:
Go to "System > Adminstration > Restriced Drivers", and there should be a box called something like "ATI 3d". Tick the box, click apply, it will download and install the drivers, then all you need to do at your shell emulator is type 
```
aticonfig --initial
``` then press Crtl+Alt+Backspace. Log back in once it prompts you with a login, and you have 3D support.
The advantage to this is that everything is put in the right place, and it is more certain that everything will work *correctly*.

---

### Post by DawnDisciple on 2007-11-07
You see.

(you need to use the sudo command for admin/root access when installing certain files or dealing with directories owned by root /.)

For all I know you have just insulted my mother.
I'm of down the pub](*,)

---

### Post by gn2 on 2007-11-07
Have you tried using Envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by oilchangeguy on 2007-11-07
> **DawnDisciple said:**
> LoL, everyone just says do this or do that, type this pull that push the other but nobody ever tells you how to do,push and pull.:)

did you read post #2? and some one telling you type this, push that. is telling you what you need to know. the forum is not here to hold your hand. it can only do so much. it's up to you to help yourself. since no one from the forum is sitting with you.

---

### Post by Cannaregio on 2007-11-07
> **DawnDisciple said:**
> You see.

(you need to use the sudo command for admin/root access when installing certain files or dealing with directories owned by root /.)

For all I know you have just insulted my mother.
I'm of down the pub](*,)


Well, you had a lot of help, a lot of people using you the courtesy to explain things calmly. 
And you have reacted, really, and more than once, just as a nasty little troll.
Have phun at the pub. When you come back, reinstall windows and  leave this stuff, it is waay over your head. 
Since you don't seem even capable to read the answers you asked for, I doubt it is worth to help you further.

---

### Post by DawnDisciple on 2007-11-07
> **oilchangeguy said:**
> did you read post #2? and some one telling you type this, push that. is telling you what you need to know. the forum is not here to hold your hand. it can only do so much. it's up to you to help yourself. since no one from the forum is sitting with you.

I am very grateful for everyones time, you have all been great, it's me I think its all a bit over my head. I never thought for a minute there would be so much messing about to execute a simple task.

---

### Post by DawnDisciple on 2007-11-07
nasty little troll, lol, no, the going down the pub bit was a joke.  If I have come over as not being grateful, I'm sorry, but as I am reading the posts I am trying the stuff out and trying to reply at the same time, so my answers are not getting my full attention ie: short and to the point.

---

### Post by DawnDisciple on 2007-11-07
After finding where the directory's are I found the user/share but no ati folder, so that was why the command was dropping. So I don't know where it stored the driver, I have also found the restricted driver manger which says I have a ATI accelerated driver in use but dosen't give me the path to it.
Not bad hu, only took me a hour to work that out.

---

### Post by DawnDisciple on 2007-11-07
> **gn2 said:**
> Have you tried using Envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Gave up with trying to do it manually and downloaded envy ran it where it uninstalled the old driver and installed the new from the web site, thanks

RESOLVED

---


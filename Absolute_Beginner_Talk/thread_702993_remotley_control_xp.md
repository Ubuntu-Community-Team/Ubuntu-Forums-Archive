---
title: "remotley control xp?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by DasLegionnaire on 2008-02-20
Ok so...

I really suck at networking on any OS, it's kind of the part of PC's I didn't ever pay attention to, and now it seems like it may behoove me to remotely control my xp PC from my ubuntu notebook...

i have no idea how to go about doing this. i read something about a program called freenx, would that allow you to do this? the only reason i ask about that specific software is because i am worried about responsiveness. it would be really cool to be able to access my pc through a browser. any help appreciated.

---

### Post by amingv on 2008-02-20
You can use LogMeIn ([www.logmein.com](www.logmein.com)). I guess the beer-free version will do. You can access your Windows PC from any browser.
You will need to download the java plugin to access it from Linux.

---

### Post by tyggna1 on 2008-02-20
If you're new to Linux, you're in for a treat--networking is easy!

As for controlling windows--vnc is probably your best bet.
Once you have it set up (and secured, but all the online install guides will tell you how to do that), all you have to do is type in your ip:vncport.
e.g.:
```
localhost:5900
```
login, and bam! you'll have control of the desktop.  VNC ports for both Linux and windows--pretty handy.  Just take care when installing it--read through the manuals and setup guides first--you don't want to inadvertently give control of your computer to someone else.

If you're looking for the vice-verse effect (controlling a Linux station remotely), then you'll want to look into something called openssh.  This is a command-line only utility, but it's how I spend most my time configuring my server (rarely do I ever actually sit in front of it).  Openssh also ports for both windows and Linux--but it's more difficult to setup in windows.

Hope that is helpful.

---

### Post by Origin415 on 2008-02-20
You can find a VNC server for windows here: [http://www.realvnc.com/](http://www.realvnc.com/)

Once you configure it, type Alt+F2 on your Linux box and vncviewer
Put in the ip address and password and your in!

---

### Post by Dissident85 on 2008-02-20
you can use "terminal services" under applications -> internet 

i think, correct me if i am wrong please :) 

oh and you will need to have remote desktop enabled on xp... 

right click "My Computer" -> "Remote" tab 
then make sure "enable Remote Desktop on this computer" is ticked... 

also add users by clicking on "Select Remote users"

Thats what i use when i connect to my work computers... i find it faster than VNC and you have more control... more options.

---

### Post by bodhi.zazen on 2008-02-20
Two steps:

1. Configure Windows : [http://www.helpwithwindows.com/WindowsXP/howto-14.html](http://www.helpwithwindows.com/WindowsXP/howto-14.html)

2. Connect from Ubuntu : [http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html](http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html)

---

### Post by freddyp on 2008-02-20
I also recommend LogMeIn Free ([www.logmein.com](www.logmein.com)).  You can access your Windows PC from any browser from any PC, either inside or outside of a home network.  There is no LogMeIn Linux client that provides a way to control a Linux box, but your question was controlling a Windows box from Linux box, right?  Hey, there's a free version of LogMeIn and it does not require any network changes like port forwarding or other items like that!
__________________

---

### Post by DasLegionnaire on 2008-02-21
i'm very excited to try logmein.com i've looked at the website and it seems extremely useful. i do not yet have a wireless adapter for my windows pc, but i will get one this weekend, and i will explain how it goes.


as an electronic musician the thought of being able to control my main studio computer from my laptop (and in ubuntu!) sounds amazing.

---

### Post by daflame on 2008-02-22
> **DasLegionnaire said:**
> Ok so...

I really suck at networking on any OS, it's kind of the part of PC's I didn't ever pay attention to, and now it seems like it may behoove me to remotely control my xp PC from my ubuntu notebook...

i have no idea how to go about doing this. i read something about a program called freenx, would that allow you to do this? the only reason i ask about that specific software is because i am worried about responsiveness. it would be really cool to be able to access my pc through a browser. any help appreciated.

FreeNX can access windows PCs, but the server needs a linux host.

I have a forum on FreeNX here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---


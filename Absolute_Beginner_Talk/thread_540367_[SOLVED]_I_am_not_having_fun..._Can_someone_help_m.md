---
title: "[SOLVED] I am not having fun... Can someone help me with my X Server?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by SarahRox on 2007-09-01
Hello!

Today I've been tasked with building a print server, setting up my home network AND putting my boyfriend's PC in it's shiny new case. I've been working on the Ubuntu server for round about 3 hours now - everytime I solve 1 problem it comes up with shiny new ones! I've been assured this will be worth it in the end....

I've managed to convince the nice server to accept my monitor but now it's choking on my graphics card. I'm ASSUMING (up until about 3 hours ago I was a pure Windows girl) that it would like drivers, but I've no idea how to get these from a command line or if it would be quicker to grab em on a CD but again I'm new to this whole command line thing.

I had brought up a screen earlier that allowed me to look at my devices, which is how I fixed my monitor but I can't remember how to do this so can't give you much more info. My graphics card is an ATI9600XT.

Please assume no knowledge when replying and include instructions of how to get any further info. 

Thank you already!! :)

---

### Post by rich.bradshaw on 2007-09-01
Try envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by SarahRox on 2007-09-01
I did look at that but I've no idea how to install and run from the command line. Do I need to put it onto CD then pop it in the drive? I tried typing in some of the commands in his FAQ but it just didn't do anything. No error messages nothing, just seemed to expect me to type more.... :S

I'm sorry I'm a total n00b at this! :)

---

### Post by banewman on 2007-09-01
Lots of first time folk have a graaphics card issue. This site should get you on your way
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). lots of luck.:lolflag:

---

### Post by w4ett on 2007-09-01
Well, if this installation is on a server, at the very most all you will need is the open source driver...(I assume you will not be using this machine for anything other than a server)

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "ati" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop if you have already installed gnome-desktop.  If you haven't and want a gui desktop from the command line:

```
sudo apt-get install gnome-desktop
```

---

### Post by SarahRox on 2007-09-01
Not a single one of those solutions worked, but a random mashup of all 3 has resulted in me having a shiny GUI!

THANK YOU!!!! :popcorn::popcorn::popcorn::popcorn::popcorn:

---


---
title: "[HELP] what is going on"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by FlamingGooch on 2007-10-18
10/19/07 EDIT: Is it because my graphics card is not compatible that it won't finish installing Gibbon?


Ok. I need someone to give me a detailed, easy to follow instrucion on how to do important stuff in 7.10. As of right now, my 7.10 will not install because I get the error mentioned below.

I need to know:
1. How to install things
2. How to install Pidgin
3. How to get Compiz working (for my friend's comp not mine)
4. What does the error 
```
bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```
5. Is there anything different i have to do to get compiz working on my graphics card which is an ATI X1400?

Please for the love of god someone help me im going insane trying to figure this out on my own.
](*,) ](*,) ](*,) ](*,)

---

### Post by steveneddy on 2007-10-18
OK - you need to tell us a little about your hardware.

You have two posts with the same issue.

Almost everyone is updating to the new Gutsy release, so no one is really reading the forums tonight.

You must be patient. These are all volunteer forums and I don't think that you will get good help talking like that.

Is this error from a Broadcom wireless device?

And have you actually searched the forums before posting these threads? 

Be patient.

---

### Post by steveneddy on 2007-10-18
1. You install things through Synaptic or apt-get in terminal.

System --> Administration --> Synaptic Package Manager

2. Same answer - go to Synaptic and find Pidgen. Right click, choose install. At the top is an apply button. Hit the button when you are ready to install.

3. As long as the hardware can handle 3D graphics, you go to 

System --> Preferences --> Appearance

Choose the Visual Effects tab.

4. I don't know - see my previous post.

5. Install nVidia and be happy.

---

### Post by FlamingGooch on 2007-10-18
I've been searching a lot and havn't found too much. I'm currently on a Dell 9400 notebook with Intel Core 2 Duo at 2 GHz. The wireless card that came with the computer is Broadcom I believe. I'm trying to run a dual boot environment with vista and 7.10 .

The 7.10 install just stops when I get to that error message. My graphics card is an ATI X1400. Does that cause any problems?

I'm sorry about not being patient, it's just that this is frustrating because I'm pretty much new to linux. The only experience I have is with my GentooX distro on my regular Xbox.

---

### Post by steveneddy on 2007-10-18
[Look here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

I know it's Feisty, but it will get you started. Most of it will be the same.

[Look here, also]("https://help.ubuntu.com/7.04/add-applications/C/index.html").

[Look here.]("http://ubuntuforums.org/forumdisplay.php?f=73")

Good luck.

---

### Post by steveneddy on 2007-10-18
Search for broadcom 43xx support.

[Here's one now]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx").

Searching in Networking and Wireless may give you a few answers.

---

### Post by HermanAB on 2007-10-18
...and when all else fails, go to the ndiswrapper web site on Sourceforge and start reading.

Cheers,

H.

---

### Post by FlamingGooch on 2007-10-19
> **steveneddy said:**
> Search for broadcom 43xx support.

[Here's one now]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx").

Searching in Networking and Wireless may give you a few answers.

This solution is fine and dandy. However, for my particular problem, it is of no use. The error I'm getting just halts the installation and it goes no further, so I can get to no terminal.

All of the workarounds for the bcm43xx problem all involve me having access to a terminal window, which I don't. During the install, the text on screen says: "Starting GNOME desktop manager..."

After that my monitor just flickers and I get the bcm43xx error. Is my graphics card not allowing the install to continue?

---

### Post by conehead77 on 2007-10-19
For Compiz and ATI look here: [http://forlong.blogage.de/](http://forlong.blogage.de/)

---

### Post by DRAGONPOWER on 2007-10-19
anybody with hp laptop having audio issues? my sound is not working , alsa , oss , no device works? do i need a driver? im running gutsy 64-bit on em64t, sound card i believe is intel hd ich8? 

help!

---

### Post by unisol on 2007-10-19
FlamingGooch why dont you try the alternate-install cd? you might get it to install.

---

### Post by FlamingGooch on 2007-10-19
What exactly are the differences between the regular old Live CD and the Alternate install CD?

---

### Post by unisol on 2007-10-20
the alternate install installs in text-mode , and doesnt require the resources it takes to boot the livecd.

---


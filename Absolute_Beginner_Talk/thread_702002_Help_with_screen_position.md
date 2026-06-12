---
title: "Help with screen position"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-19
I have had Ubuntu 7.10 for a couple days now. About an hour ago I installed windows, and when I relaunched back to LiveCD to install Grub I noticed my screens positions was about an inch to the left. I thought it was just the LiveCD for a second. So I quit that and launched into the Ubuntu that has been working fine for me. And noticed it is the same 1 inch to the left. This all happened after installing Windows on the unpartioned piece of harddrive I was saving for windows. Messing with the monitor controls on the front of the monitor kind of help, but not much. I would hate to have to do this each I time I switch from windows to Ubuntu. 

If anyone knows the problem please let me know. I might not have given much info, but just let me know if you need more.

---

### Post by ImThatNerd on 2008-02-19
I cannot seem to find any help on this issue. Also it looks like someone else had the same problem but no help with resolving: [http://www.experts-exchange.com/OS/Linux/Q_22766337.html?eeSearch=true](http://www.experts-exchange.com/OS/Linux/Q_22766337.html?eeSearch=true)

---

### Post by RxRated on 2008-02-19
I'm thinking it's a problem with your xorg.conf file.  Try running this from terminal and select the correct video driver and screen resolutions.
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ImThatNerd on 2008-02-19
> **RxRated said:**
> I'm thinking it's a problem with your xorg.conf file.  Try running this from terminal and select the correct video driver and screen resolutions.
sudo dpkg-reconfigure -phigh xserver-xorg

Alright I selected my Screen resolution that it use to be on windows. I hit space to put an asteric in the space and hit enter. Nothing happened. What should I do next?

I got the drivers (.exe) for windows, but doubt that would do anything.

---

### Post by stevescripts on 2008-02-19
For what its worth, I have to use the on-screen-display adjustments every time I
must boot the alternative OS (XP)

It works for me .. but a bit of a pain.

Steve

---

### Post by RxRated on 2008-02-19
Reboot Ubuntu and see if it adjusted your screen.  (I'm no expert, but I had a similar problem on my laptop which this fixed)

---

### Post by ImThatNerd on 2008-02-19
Alright I did the resolution I thought it was. Fixed one side. But made the others worse. I suppose I just need to experiment with the others.

---

### Post by RxRated on 2008-02-19
I'm thinking it could be the driver you choose.  What video does it have?

---

### Post by ImThatNerd on 2008-02-19
What do you mean? I have an old Dell monitor. Haven't installed any drivers in windows yet since I wanted to fix this problem first.

---

### Post by RxRated on 2008-02-19
When you ran code I gave you, it asks you for a video driver.  What video board are you running? 
nvidia, ati, s3 etc.  Choose the correct one from the list, and then choose your resolution.  Probably 800x600 or 1024x768.

---

### Post by ImThatNerd on 2008-02-19
> **RxRated said:**
> When you ran code I gave you, it asks you for a video driver.  What video board are you running? 
nvidia, ati, s3 etc.  Choose the correct one from the list, and then choose your resolution.  Probably 800x600 or 1024x768.

It didn't ask me for any video driver.

It went straight to the list to select resolution size...

---

### Post by RxRated on 2008-02-19
That's odd.  It does on my machine.  Well I tried!  I have no other ideas on how to fix it.
Maybe someone else can help.  Good luck!

---

### Post by ImThatNerd on 2008-02-19
[IMG]http://i29.tinypic.com/2805rab.jpg[/IMG]

Alright now it is messed up more than it was before. Before I tried the command you gave me. Is there a way I can restore defaults? or should I try reinstalling Ubuntu?

---


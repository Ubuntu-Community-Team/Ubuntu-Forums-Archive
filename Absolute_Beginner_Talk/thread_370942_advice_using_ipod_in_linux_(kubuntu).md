---
title: "advice?? using ipod in linux (kubuntu)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by TruthBridge on 2007-02-26
hi. absolute beginner here. im trying to get my ipod to work through linux since itunes encrypts all the files. i got gtkpod already but have no idea what it is even :P. can anyone give me a step by step beginners guide to getting my ipod to work with amarok on kubuntu? thank you.

---

### Post by Luk0r on 2007-02-26
You could try using Wine:

[http://www.winehq.com/](http://www.winehq.com/)

Follow the instructions on their Ubuntu download page to get the very latest release.

Alternatively, you could just use GTKPod: [http://gtkpod.sourceforge.net/](http://gtkpod.sourceforge.net/)

---

### Post by TonKi on 2007-02-26
Should work out of the box by default and I use amarok for iPod management.
```
sudo apt-get install amarok
```
[https://wiki.ubuntu.com/KubuntuIpod]("https://wiki.ubuntu.com/KubuntuIpod")

---

### Post by markupstart on 2007-02-26
Here is how I got my Ipod to work in Amarok.  First, plug in the Ipod, it should automount. Take note of where it mounted it to.  mine is:

 /media/MARK IPOD I

Load up Amarok, go to settings>configure Amarok>Media Devices

Click on Add Device>Select Plugin>"Apple Ipod Device"

Enter Name for Device

Enterr the Mount point for Ipod, mine was

 /media/MARK IPOD I

of course yours will be different.

Click ok

Click ok

Go to Devices tab

Click on Connect

It should connect to the Ipod and show you the contents in the window.

---

### Post by amber on 2007-02-26
I am in the same boat as you. I am highly new to linux and am in the process of setting up my ipod as well. I just plugged my ipod right in and it noticed it right away and brought up the music player Rythmbox. I haven't done a whole lot with it yet, but so far so good.

---


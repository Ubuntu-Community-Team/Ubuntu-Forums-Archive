---
title: "Xubuntu on iMac G3 problem"
date: 2007-01-21
forum: Apple PPC Users
---

### Post by newbie builder on 2007-01-21
I've had an old G3, 400mhz, 12gb hard drive that I don't use anymore..so I thought I'd make I'd use that for my first foray into Linux before installing anything on my macbook and because the thign is fairly slow with OSX. Everything appears to be loading, then when I get the black screen and hit CTRL+ALT+F1 the screen just says "Authentication token is no lonver valid; new one required. You are required to change your password immediately (root enforced)"
What should I do?
Thanks--

---

### Post by Salpiche on 2007-01-22
> **newbie builder said:**
> I've had an old G3, 400mhz, 12gb hard drive that I don't use anymore..so I thought I'd make I'd use that for my first foray into Linux before installing anything on my macbook and because the thign is fairly slow with OSX. Everything appears to be loading, then when I get the black screen and hit CTRL+ALT+F1 the screen just says "Authentication token is no lonver valid; new one required. You are required to change your password immediately (root enforced)"
What should I do?
Thanks--

Is this during boot? 
I'm using an old G3, 400mhz, 256 meg, 80gb hd and the only time I see a black screen like that is during boot time while xorg sets. , and I just let it be.

---

### Post by newbie builder on 2007-01-22
This is after it shows a screen with a blue ubuntu symbol that is loading, then it becomes black, then what I described above happens..so yes during the boot I guess.

---

### Post by Salpiche on 2007-01-23
Have you try waiting for a while? I get the same thing and I just wait not touching anything 'till it's done, though you might want to try installing ububntu instead of xubuntu just to see what happend. To me it sounds like a xorg configuration issue, it might be having issues loading the video device.

---

### Post by bodycoach2 on 2007-01-23
What version are you trying to load? For me, the 6.06, and 6.10 versions would never install on my older iMacs. Try the 6.06.1 version of Xubuntu, and only use the alternate install CD. The liveCD just won't boot.

Let us know if it works.

> **newbie builder said:**
> I've had an old G3, 400mhz, 12gb hard drive that I don't use anymore..so I thought I'd make I'd use that for my first foray into Linux before installing anything on my macbook and because the thign is fairly slow with OSX. Everything appears to be loading, then when I get the black screen and hit CTRL+ALT+F1 the screen just says "Authentication token is no lonver valid; new one required. You are required to change your password immediately (root enforced)"
What should I do?
Thanks--

---

### Post by Salpiche on 2007-01-23
> **bodycoach2 said:**
> What version are you trying to load? For me, the 6.06, and 6.10 versions would never install on my older iMacs. Try the 6.06.1 version of Xubuntu, and only use the alternate install CD. The liveCD just won't boot.

Let us know if it works.

I second that since I had to use the Ubuntu 6.10 alternate install cd in order to install Ubuntu at all.

---

### Post by humboldthead on 2007-01-23
Hi, I am also having a problem with a g3 mac, 350mhz, I think its a problem. I installed 6.06.1 from the alternate cd, everything seemed fine throughout the install, however it did mention a "low memory mode", now after loading the drivers during the boot-up, it says "cannot access the hardware clock via any known method",  then it starts the logs, run boot scripts, then gives me a login prompt, i log in, then get another prompt, with~and a dollar sign, what do i do here? I expected to see a gui around this time, can someone help, I was so excited to finally install linux, now I would love to see it, thanks ahead of time if you can assist me!

---

### Post by 3rdalbum on 2007-01-24
Humboldthead, what happens if you type:

```
startx
```

after you have logged in?

And, er, you didn't by any chance tell it to install the server edition?

---

### Post by humboldthead on 2007-01-24
Thanks 3rd,

It  said that it had to restart to start my new system after install, I logged in,

I tried "startx" at the prompt (~$), and it says "command not found"

I thought that the "cannot access the hardware clock via any known method", or the "low memory mode" may have been the prob....
Huh, any other commands that you suggest that may bring up the desktop?
oh yea, I didn't install the server, but typed "install-powerpc" after inserting the cd and at the prompt...hope that was right....
Thanks again!

---

### Post by newbie builder on 2007-01-24
> **bodycoach2 said:**
> What version are you trying to load? For me, the 6.06, and 6.10 versions would never install on my older iMacs. Try the 6.06.1 version of Xubuntu, and only use the alternate install CD. The liveCD just won't boot.

Let us know if it works.

I'm using the 6.1 alternate install cd of Xubuntu...I spend yesterday downloading the Ubuntu 6.1 alternate install and I'll give that a chance later today hoping for better luck.
Thanks!

---

### Post by 3rdalbum on 2007-01-25
> **humboldthead said:**
> Thanks 3rd,

It  said that it had to restart to start my new system after install, I logged in,

I tried "startx" at the prompt (~$), and it says "command not found"

I thought that the "cannot access the hardware clock via any known method", or the "low memory mode" may have been the prob....
Huh, any other commands that you suggest that may bring up the desktop?
oh yea, I didn't install the server, but typed "install-powerpc" after inserting the cd and at the prompt...hope that was right....
Thanks again!

The desktop should have been installed, but it really looks like it hasn't been.

Try typing:

```
sudo apt-get install ubuntu-desktop
```

at the same command prompt that you typed "startx" at.

---

### Post by gurnemanz on 2007-01-25
> **3rdalbum said:**
> 

And, er, you didn't by any chance tell it to install the server edition?

Now I'm puzzled - I thought installing the server version and then Gnome or another DE was supposed to be a good way of getting Xubuntu to install on older and slower Macs.

No?

---

### Post by bodycoach2 on 2007-01-25
Be sure to burn the disk at the slowest speed possible. With the older iMacs, disks burned at high speeds didn't work. Burn slow.


> **newbie builder said:**
> I'm using the 6.1 alternate install cd of Xubuntu...I spend yesterday downloading the Ubuntu 6.1 alternate install and I'll give that a chance later today hoping for better luck.
Thanks!

---

### Post by humboldthead on 2007-01-25
> **3rdalbum said:**
> The desktop should have been installed, but it really looks like it hasn't been.

Try typing:

```
sudo apt-get install ubuntu-desktop
```

at the same command prompt that you typed "startx" at.

-----------

Ok, did that, it asked me to re-enter my cd, then it seems to be installing a ton of files, t now seems it needs more disk space, i choose yes, then after a few min, back to the ~$ prompt, i do "sudo apt-get upgrade" it upgrades more files, it says working in bottom left corner of screen and pauses for awhile, now it is saying "Sub-process /usr/bin/dpkg returned an error code (1) and then back to the ~$ prompt.....huh...I know I am close...and Im learning some command lines already!
Thanks, hopefully something will breakthrough to that GUI Ive been anxious to see....

---

### Post by xphelanx on 2007-01-25
Just figured that I would spawn a brand new issue in this thread. I have an iMac G3 233mhz w/96mb ram up and running with Xubuntu 6.06 and all original peripherals (mouse & keyboard) but for some reason, I have big problems with my keyboard. Caps lock tends to be weird showing the light when caps lock is not on and vice versa. Also, it can make the caps lock key look like it's working, but when I type, everything is IN CAPS. Mostly, I am able to put caps on once, and then it's stuck on until it fixes itself when I log out. In my xorg.conf file, it calls it a pc104 keyboard, but it's more like 96. What can I do to make this work? I have tried pc105, macintosh, and imac in place of pc104 ](*,)  I have tried using a different standard keyboard, but I keep having the same problem :(

---

### Post by bodycoach2 on 2007-01-27
If you have a different USB keyboard, try that and see if you still get the error. The keyboard itself may have a problem.

> **xphelanx said:**
> Just figured that I would spawn a brand new issue in this thread. I have an iMac G3 233mhz w/96mb ram up and running with Xubuntu 6.06 and all original peripherals (mouse & keyboard) but for some reason, I have big problems with my keyboard. Caps lock tends to be weird showing the light when caps lock is not on and vice versa. Also, it can make the caps lock key look like it's working, but when I type, everything is IN CAPS. Mostly, I am able to put caps on once, and then it's stuck on until it fixes itself when I log out. In my xorg.conf file, it calls it a pc104 keyboard, but it's more like 96. What can I do to make this work? I have tried pc105, macintosh, and imac in place of pc104 ](*,)  I have tried using a different standard keyboard, but I keep having the same problem :(

---

### Post by xphelanx on 2007-01-28
> **bodycoach2 said:**
> If you have a different USB keyboard, try that and see if you still get the error. The keyboard itself may have a problem.
Yeah, I've already tried that and it still seems to have the issue :(

---

### Post by samden on 2007-01-29
Just a little point, you may be well beyond this by now but I will mention it anyway. Although the Ubuntu live cd is unlikely to work on an iMac G3, the Xubuntu live cd appears to have lower RAM requirements and may work. I had endless problems with alternative install cds for some reasons, and ended up installing 6.06 on my 500Mhz iMac G3 slot loader with 192Mb RAM with the live Xubuntu cd. 

I am pushing the limits of this cd - sometimes it will and sometimes it won't work, but when it worked it was much better than the alternate install cd for some reason.

---

### Post by nhylo on 2007-01-30
excuse me this gay ask about XUBUNTU and some how you are talking about UBUNTU .
Iam new also and I have had no result except using parallels in my mini  but my Imac g3 "nada" and Iam afraid of doing my lombard wich is the one I want to use.
Truly never seen a bunch of people with so many diferent answer in aany amc forun in 6 years 

Iam frustraired big time

nhylo

---

### Post by samden on 2007-01-31
Xubuntu and Ubuntu: Short explanation by a newbie:

Ubuntu and Xubuntu are basically the same thing. The guts of them are the same. The pretty pictures on the screen are a little different.

Ubuntu uses Gnome as its GUI (Graphical User Interface), this is a good, well-featured GUI. As I understand, the GUI is basically the thing that makes the pretty pictures come up on the screen rather than just having a string of text.

Xubuntu uses XFCE instead - this is a bit more lightweight and doesn't take as much RAM to run. May run better on older computers. Probably less fully-featured in some ways but you seem to be able to install bits of Gnome and run pretty much anything inside it. Some people prefer it to Gnome anyway - comes down to personal preference a lot.

You can even do one Ubuntu install but install both Gnome and XFCE, in effect having both Ubuntu and Xubuntu on the same computer, you just log in to the one you want to use at the time. So there is really little difference. And most advice people give for Ubuntu also applies for Xubuntu as well.

I hope that provides a basic explanation. Any computer geek would cringe at the terminology I am sure but I hope it makes sense for a non-geek!

---


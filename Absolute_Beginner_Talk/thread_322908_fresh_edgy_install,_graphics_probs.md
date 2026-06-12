---
title: "fresh edgy install, graphics probs"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by ziggyx2003 on 2006-12-21
Greetings All,

recently installed ubuntu edgy on my older intel computer, had no problems all went very well.

Now am trying to install on my other pc , and I think the problem is my graphics card. Nvidia Geforce 6600, i have swapped my Flatron L1717S for a crt monitor without any change, so i dont think my monitor is the base problem.

I install and following the post install reboot, i first get ubuntu loading screen in black and white, and then just a screen with coloured vertical lines. I can not get any kind of graphical interface of any kind.

I can get to the ?command line using control, alt, F1, I have reconfigured the xorg config manually, it has saved the graphics card info put in. but still no working screen.

I cant download the nvidia drivers because i cant open the universe and multiverse repositories because i cant load synaptic, have tried to load synaptic via the command line and get

GtK-WARNING **: cannot open display.

I have spent hours reading every thread with a possible solution but nothing has worked.

So my question is "is there a way to open the multiverse, universe repositories via the command line, and then install nvidia drivers" in the hope of getting the graphics into some kind of order. at least enough to be able to access the gui so i can continue to figure out any problems.

I am new to linux so please provide step by step instructions where needed.

Thank you for your time and trouble.

---

### Post by taurus on 2006-12-21
Did you boot into recovery mode from GRUB menu and try these commands?

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by ziggyx2003 on 2006-12-22
yes, i did that, but without any change in the outcome.

This is my pc set up.

Motherboard: MSI MS6702
CPU: Amd Athlon (tm) 64, 3000+
Video Adaptor: Nvidia GeForce 6600 LE (256mg ram)
Monitor: LG Flatron L1717S
RAM: 1G
Harddrives x 2

After a very frustrating evening last night, today i reinstalled windows xp, with the intent of having windows on one harddrive and linux on the other, so i still have some pc funtionality while trying to figure out my ubuntu problems.

When i install the live cd, i need to change the screen resolution (F4) to 1024 x 768 , 32 bit in order to get it to to work, if i dont do that, then i get the thick lines with no gui in sight. 

If i do a full install i cant change those settings, i have changed them in the xserver-xorg but that doesnt seem to help.

Also my monitor (lcd), in windows it says the refresh rate is 60 but when i go to the live cd without altering any settings , the monitor menu says refresh 75 and and resolution a little above 600x400, and i have no way of changing it there.

Not sure what to do.

Regardless of the outcome, it has been a learning experience which can only be a good thing.

Any advice greatly appreciated.

---

### Post by taurus on 2006-12-22
If X is running fine from the LiveCD but you are still experiencing problems after installing it, then you can always boot from the LiveCD, mount your harddrive where / is located, and copy /etc/X11/xorg.conf from the LiveCD over to your harddrive.  Make sure you use "nv" for the "Driver" of your nVidia card...

---

### Post by ziggyx2003 on 2006-12-23
First I am pleased to say I actually managed to do all that.

Second I am sad to say, it made no difference.

Back to square one.

I will just keep reading and trying stuff. I am gonna get it done, just gonna take time obviously.

Thank you for your help.

8) :D 8)

---

### Post by azkehmm on 2006-12-23
> **ziggyx2003 said:**
> "is there a way to open the multiverse, universe repositories via the command line, and then install nvidia drivers" in the hope of getting the graphics into some kind of order. at least enough to be able to access the gui so i can continue to figure out any problems.

AS far as I know, yes there is. Boot into recovery mode

Edit the /etc/apt/sources.list using the text-editor "Nano:

```

sudo nano /etc/apt/sources.list

```

now, uncomment (remove the ## in front of the urls) the repositories you need.

Now, update you package lists using aptitude

```

sudo aptitude update

```

and now, you should be able to find the nvidia driver using aptitude

```

sudo aptitude

```


Please note, that I'm not superexperienced with linux, so there is possibly an easier way of doing this, but I'll leave someone more experienced than me to post that :)

---

### Post by ziggyx2003 on 2006-12-25
Thank you very much for that info, it works.

However (you knew that however was coming)

When i go to download/install the driver I think i need, i get this.

[http://archive.ubuntu.com](http://archive.ubuntu.com) edgy restricted nvidia-glx 1.0.8774+2.6.17.5-11 [ERROR] 
Temporary failure resolving 'archive.ubuntu.com'.

downloaded 0b in 0s
some files were not downloaded successfully.

When i use ifconfig command the output gives me the impression my internet connection is working.

I have uncommented every url in my apt/sources.list


Thank you

---

### Post by Azakus on 2006-12-25
That link should by [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Post your sources.list file with```
cat /etc/apt/sources.list
```

---

### Post by spockrock on 2006-12-25
try this, sudo apt-get update, and see if it errors, then sudo apt-get install nvidia-glx.

once you have the drivers installed, you should be able to have a working x session.

---


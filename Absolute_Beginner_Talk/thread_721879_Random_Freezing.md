---
title: "Random Freezing"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by ProgenitorVirus on 2008-03-11
Computer:

eMachines T3104
AMD Sempron Processor 3100+
80 gig HDD, 1/2 for XP, half for Ubuntu
768 MB RAM
nVidia GeForce 5500 FX

I've been getting random crashes.  The system locks up, and can only be restarted.  It doesn't seem to be caused by any program, though firefox is a loose connection (8/10 times it was open, probably by coincidence).

I have no idea why its doing this, and it doesn't leave a log.

Any help/ideas?

Thanks for your Help!!

---

### Post by ejb331 on 2008-03-11
I would try to narrow down what is causing the problem. For example, does it happen during a certain time during the day? Or does it freeze after running for a certain amount of time? Is it random? If you can try to exit all programs (if possible) and see if it still freezes. If it doesn't then one by one open your normal programs/processes and see if you can figure out what triggers it.

Another thing to check is your Nvidia driver install. It would not be a bad idea to uninstall and reinstall with the newest Nvidia driver. If you are not sure how to do this or you want an easy way to install Nvidia drivers, I recommend using [Envy]("http://albertomilone.com/nvidia_scripts1.html"). 

Also, when your comp freezes, are you doing a hard reset (holding down the power button till it turns off)? If so, this can be really bad for your computer. If you are using a hard reset you should try using this [http://wlmtips.com/2008/03/11/what-to-do-if-your-computer-freezes-in-linux/]("http://wlmtips.com/2008/03/11/what-to-do-if-your-computer-freezes-in-linux/")

---

### Post by 1scorpio on 2008-03-11
I am a new user so I wont post any code but I had the same problem. mine would freeze when screen saver came on or when i tried to change the screen saver also froze in some graphics.  I solved (god only knows how)by messing around in the synaptic mgrs openGL stuff. I just thought that was the prob any how it worked maybe some of the older guys can tell us more specifically what??

---

### Post by ProgenitorVirus on 2008-03-11
It happens completely randomly.  I HAVE to hard reset, NOTHING is operable at the point when it freezes. It doesn't seem to be related to programs, HOWEVER, on startup, I get this error sometimes:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

If thats at all relevant

---

### Post by ProgenitorVirus on 2008-03-11
Also, I'm noticing some pretty high CPU spikes with my computer,

I'm a migrating Windows user, and used to seeing CPU around 3%, and 20% means somethings bad usually.  As we speak, my CPU is ranging around 90 to 99%.  Moments ago, it was around 10%, which still seems high.

I'm also holding off on installing the 198 updates available (This was a clean install, not even graphics driver is installed)

Does the CPU rate mean anything?  Or is this normal for Ubuntu?

---

### Post by ProgenitorVirus on 2008-03-11
Just had another freeze, without updates or graphics driver

I was running FireFox.  I'm not convinced that FireFox is the cause though, its happened when it isn't up.

---

### Post by Bob Unitt on 2008-03-12
I see this as well. I have a dual-boot machine - Windows 2000 & Ubuntu 7.10, both of which are used about equally.  I don't think it's the hardware, as I only ever see this problem with the Ubuntu boot. I have an Nvidia GeForce 7800 GS on this machine. I vaguely suspect the Nvidia driver (1.0-9639) as the problem seems to manifest itself when the video card has some work to do (e.g. running a game or displaying some kind of moving picture), but I can't prove it. Incidentally, I run two screens side-by-side with different resolutions, which may or may not be relevant.

---

### Post by JacksonDane on 2008-03-17
Everything you're describing is happening to me too. Like you said Firefox is usually open, but I think that's just because I use it so much. I get the same error on start up quite often. I've tried different nvidia drivers (now that I got an 8800 though I can't, not that it solved the problem anyways). I've upgraded most of my computer hardware over the past 6 months and it didn't seem change anything, still occasional freezes. 

I reformatted and that solved the problem temporarily, but it did come back after a few weeks. I've racked my brain trying to find the solution and have been coming up blank. I'm just crossing my fingers for next months release.

---

### Post by nick_h on 2008-03-17
Have you tried disabling "Visual Effects" - it can sometimes cause "random" crashes.

---


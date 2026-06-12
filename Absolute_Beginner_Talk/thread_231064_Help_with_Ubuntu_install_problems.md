---
title: "Help with Ubuntu install problems"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by piddubutt on 2006-08-06
I've been trying to install Dapper Drake on my machine for the past few days but I haven't been able to get it to work. At first I tried using the desktop installation disk, and the live cd worked fine under low graphics mode. When I tried installing it, however, the ubuntu screen loaded up the drivers and everything fine, but for some reason kept giving me a blank screen after the cursor in the top left corner went solid. (Ctrl-Alt-F1 didn't do anything.)

So I downloaded the alternate install disc and tried installing it in OEM mode, but it gave me an error with the default linux-386 kernel. So I installed the kernel-image-2.6.15-23-386 instead. But when i created an account and rebooted, it gave me an error, something like DLLError, cant open display. Now when I boot into Ubuntu through Grub, it gives me a command line, which I dont know how to do much with. I'm running an Athlon 2800 with   an Radeon 9500 Pro. Any suggestions?

(Sorry about the repeat post)

---

### Post by az on 2006-08-06
How much ram do you have?

Ubuntu does not work with a 2.4 kernel, but your original kernel error is probably due to a bad disk or some other hardware problem.

---

### Post by piddubutt on 2006-08-07
I dont think RAM should be a problem, I have a gig of it in the system. And sorry about the mistake, the kernel is actually kernel-image-2.6.15-23-386.

---

### Post by pdub on 2006-08-07
Can you post the display error?

---

### Post by piddubutt on 2006-08-07
I've gotten it to work using the following commands from another thread:

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

I have a couple of questions though. The way I'm getting it to work now is by logging into the root account and then using 'startx'. I made another account as well, but for some reason it doesn't start up when i use that one, probably because I haven't configured the administrator priveliges or whatever correctly on that one. What's the way to fix that? Also, how can you set it to load directly into the graphical interface every time it boots?

---

### Post by pdub on 2006-08-07
Check your /etc/inittab file and make sure the runlevel is set to 2 as shown below.

# The default runlevel.
id:**2**:initdefault:

---


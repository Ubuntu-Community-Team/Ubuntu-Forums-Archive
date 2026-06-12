---
title: "HELP HELP!, Low Screen Resolution"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by williambrodie on 2007-05-29
_

---

### Post by blackened on 2007-05-29
You might try reconfiguring the X server:

In terminal
```
sudo dpkg-reconfigure xserver-xorg
```

Make sure you select the resolutions you want using the spacebar. When you're finished reconfiguring
```
sudo /etc/init.d/gdm restart
```

---

### Post by joe.turion64x2 on 2007-05-29
> **williambrodie said:**
> I just restarted by Kubuntu and the screen resolution is 640x480, and in 'Monitor & Dispaly' settings it is the highest option, i have actually just rebooted 'cus last time i booted i had this problem... I was in 640x480 and in 'Monitor & Display' settings that time and when i increased the resolution the size of everything increased but it no longer fit the screen, all i could see is the top left corner of  the screen...
I checked in The hardware options and my video card is recognised
Are your graphics card drivers installed? Has your system ever had a higher resolution before?

---

### Post by williambrodie on 2007-05-29
_

---

### Post by joe.turion64x2 on 2007-05-29
Then you should have to reconfigure the X server as suggested above.

---

### Post by williambrodie on 2007-05-29
Thanks a lot, but one more thing, im new to linux, how do u type commands in the terminaL as root?

---

### Post by Brightbelt on 2007-05-29
Pardon me for elbowing my way in, but I posted on this 15 minutes ago and have gotten no responses.
I'm on an ATI Radeon X1650 and my maximum choice goes only to 1024 x 768. Here are the strange facts:
- My Synaptic Package Manager shows the accelerated graphics driver to be installed
- The Resricted Drivers manager shows the accelerated driver as disabled.

The thing is: I've tried enabling the accelerated graphics driver in the Restricted Drivers Manager several times, and I always reboot to a blank screen. I welcome any ideas...or should I follow the advice given here?

Many Thanks, Frank Bright

---

### Post by alienexplorers on 2007-05-29
Sudo Command

---

### Post by FerhatBingol on 2007-05-29
but you don't tell us much about your computer. 

Maybe it is something with Video BIOS? 

Even it is not the case, can you pls post your hardware, just to learn...

---

### Post by Brightbelt on 2007-05-29
Now I'm yelling HELP!!!!

I tried the reconfiguration and I got a crash upon rebooting. It says X server is unable to load and it gives an Error: Microcode bcm43xx

Here is more system info:
I have an HP Media PC, with an AMD X2 64 2.71 Ghz 4600+ Processor, 2 GB of DDR (new) ram, an ATI Radeon X1650Graphics Card with 512 Mb memory. I have 2 internal hard drives, but Ubuntu is set partitioned on C:\ that I share a dual boot with Vista.

HELP!! I do need to know what I can type when my system won't boot and/or how to get to a command prompt and what to do from there.

I've reinstalled so many times, I'd hate to have to do it again. Thanks for any help, Frank

---

### Post by williambrodie on 2007-05-29
_

---

### Post by Outrunner on 2007-05-29
```
sudo /etc/init.d/gdm stop
```
and then
```
sudo /etc/init.d/gdm start
```

---

### Post by williambrodie on 2007-05-29
_

---

### Post by Outrunner on 2007-05-29
Just a thought, are you using Kubuntu? If so just substitute kdm for gdm. If it still doesn't work try
```

startx
```

---

### Post by blackened on 2007-05-29
startx won't work if the xserver is already up and running. Try ctrl+alt+backspace to kill the xserver, it should restart on its own. If it doesn't, then type startx.

---


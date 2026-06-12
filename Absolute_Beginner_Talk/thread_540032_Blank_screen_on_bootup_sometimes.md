---
title: "Blank screen on bootup sometimes"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Reljoy on 2007-09-01
I have installed Ubuntu 7.04 onto an Acer Veriton 3500 Standard V2 with an Intel graphics card. 

Sometimes when I boot up, it does the graphical loading "line" of brown squares across the screen and then displays a little whiteish/grey circle which I can move with the mouse. Then the circle freezes up and wont move and in the centre of the screen I get a square about 4cm square (at a guess) which is made up of random squiggles (which for some reason remind me of something I used to see sometimes on a Mac Classic or Performa 580 running O/S 7.5). The screen then goes blank - totally. And that is how it stays.
To "fix" it I turn it off and unplug things such as the keyboard and monitor and power cable. Then replug and restart. On restart I make sure the keyboard is working and if it is I go in to the grub menu and choose an "older" command line bootup. When this boots up ok (it always has) I then shutdown and restart. Sometimes the restart then works fine and sometimes it doesn't. Today I had to choose an older graphical "version" and boot. Then I read about CTRL + ALT +F1 and did that and couldn't get back to the GUI and so had to restart. Assuming that it automatically selected the "latest" version in Grub, it booted up fine.

Since I have an Intel graphics card and not ATI, I don't think my problem can be the same as what other people are experiencing.

Can anyone give me an idea of what is causing my problem? I'm wondering if Ubuntu has an "issue".  How can you tell what "version" in Grub you have booted into?

Thanks,

---

### Post by southernman on 2007-09-01
To find out which kernel version your running type "uname -a" in a terminal.

For a temporary fix just edit your /boot/grub/menu.lst and put a "#" in front of the kernel lines that are giving you problems. Be sure to also comment out the "rescue mode" kernel line for the offending kernel.

Running "lspci" will show you what components are running from your motherboard. Here you can tell what video chip your using. From this you can maybe fix the problem. However, it's a little over my head for the actual fix. Hence the reason I suggested a temporary fix for the time being.

Running "lsmod" will show you what modules the kernel is loading.

HTH's some at least.

---

### Post by Reljoy on 2007-09-01
Thanks for the reply. What do you mean by 
"HTH's some at least"?

---

### Post by Reljoy on 2007-09-01
The kernal that it booted up successfully into at the moment is the latest one on my system
ubuntu 2.6.20-16-generic
Just goes to show that sometimes it will boot up nicely and sometimes it wont!

---

### Post by southernman on 2007-09-01
> **Reljoy said:**
> Thanks for the reply. What do you mean by 
"HTH's some at least"?
HTH's = Hope That Help's

It may not be a software issue at all, since it only does it sometime. It sounds like it's a hardware issue to me.

---

### Post by Reljoy on 2007-09-01
Thanks for your replys.

---

### Post by alienexplorers on 2007-09-01
I was having a simular problem a while back and it ended up being the graphic card drivers.  I updated to the most recent using ENVY and all my blank screen problems went away.  The odd thing is that when the kernel is updated I have to unload my video drivers and reload them or I end up with the intermittent blank screen problems again.

---


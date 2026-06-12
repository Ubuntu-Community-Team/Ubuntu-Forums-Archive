---
title: "Another noob's woes..."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by DapperDave42 on 2007-02-02
Hi there folks. After a long time of pondering, I have finally decided to try to ween myself off of m$ products...however I've been having many difficulties trying to install ubuntu on my system. Here are the details:
AMD64 3000+
Chaintec mobo with a nVidia nForce3 250 chipset
1.5gig DDR400 memory
ATI Radeon 9600pro
ATI TVwonder (tv-tuner only)
200 gig SATA HD (already split with a 160 gig winXP partition on it)
80 gig SATA HD (unformatted).

The following are the install methods of 6.10 I have tried with corresponding results (edit: I am installing on the 2nd partition of the 200gig HD):

64bit - system hangs on ubuntu splash screen (grey bouncing progress bar) - does when just booting from the cd

64bit /alternative - using the text only install method ubuntu seemed to install ok, but when I rebooted the machine the system hung after the screen flashed to black (my guess would be when it's initializing the video drivers?)

32-bit - this time the system booted from the cd fine (the splash screen was in color this time)...until it loaded the desktop, it then froze after about 10 seconds (though they were glorious seconds...)

32-bit /alternative - again, i went back to the text only install, which again completed, but the machine freezes a few seconds after I log in.

All of these installs had clean wipes and re-formats between them (yes, including the xp partition).  And yes, I have checked the checksums of all the iso's.  My friends at work suggested it may be a problem with my chipset, and suggested I try red hat (which i'm downloading now) - but I'd really rather get ubuntu working.  Thank you in advance for any advice.

---

### Post by quirks on 2007-02-02
I don't know much about drivers, but to me that sounds like there is a problem when switching to graphical mode, which may be related to your video card. Have you tried to switch to the command line (by pressing Ctrl-Alt-F1)? Or does the machine freeze completely? I'm not sure whether these terminals are available when booting from the live CD, so try to boot from your installation.

quirks

---

### Post by DapperDave42 on 2007-02-02
it freezes solid (even the cd drive won't respond to its own eject button) >.<

---

### Post by quirks on 2007-02-02
What you could try to do is boot in recovery mode. Press Esc when GRUB gives you the option to enter the boot menu. Then choose "recovery mode". This should not boot into graphical mode and you should have the possibility to investigate the problem. Unfortunately, I am certainly not advanced enough to tell you how to fix this, but being able to run a terminal should be a great progress. You should give that a try. Maybe some other gurus in the forums can give you more advice then.

quirks

---

### Post by toolazy2work on 2007-02-02
try 6.06, Its the long term support version anyway

---

### Post by DapperDave42 on 2007-02-02
Thanks, I'll give that a try, but I'd have no idea what to do even if I did get a terminal - curse my years of dependency on gui's!

---

### Post by toolazy2work on 2007-02-02
If you get a terminal, just type in "startx" without the quotes.  If that freezes the machine, go back into the terminal and type "sudo dpkg-reconfigure xserver-xorg" without the quotes and try to reconfigure the xserver.

---

### Post by Brunellus on 2007-02-02
> **toolazy2work said:**
> If you get a terminal, just type in "startx" without the quotes.  If that freezes the machine, go back into the terminal and type "sudo dpkg-reconfigure xserver-xorg" without the quotes and try to reconfigure the xserver.
you won't get X in a recovery console.

---

### Post by daniel of sarnia on 2007-02-02
> **Brunellus said:**
> you won't get X in a recovery console.

What do you mean, I have started x in the recovery console a number of times.

---

### Post by Brunellus on 2007-02-02
> **daniel of sarnia said:**
> What do you mean, I have started x in the recovery console a number of times.
I might be mistaken.  but then, the only time I *really* needed the recovery console was when I was facing down some really nasty filesystem corruption. . .

---

### Post by daniel of sarnia on 2007-02-02
Go into your recovery console buy pressing esc at boot.

then type this:

```
 apt-get update 
```

then

```
 apt-get install xorg-driver-fglrx 
```

then

```
 dpkg-reconfigure xserver-xorg 
```

A menu will come up select the fglrx driver, not the ati one. The rest of the questions you are prompted with the defaults should be fine. 

then when that's done and you're at your console type:

```
 nano /etc/X11/xorg.conf
```

that will open a config file which you need to add this to then end:
```

Section "Extensions"
        Option      "Composite" "0"
EndSection

```
press "ctrl x" and hit y then then enter key to over write the file.

Then reboot your computer and everything should would. For more into on ati video drivers in ubuntu look here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

EDIT: Almost forgot to say, you need to install ubuntu with the alternat cd first than reboot into the recovery console to do this. good luck!

---

### Post by daniel of sarnia on 2007-02-02
> **Brunellus said:**
> I might be mistaken.  but then, the only time I *really* needed the recovery console was when I was facing down some really nasty filesystem corruption. . .

I've had to deal with this a number of times now. Because I'm crazy and keep buying ati cards. To get the ones that don't have drivers built into xorg working I always have to do this and I have started x from recovery console to test it all most each time.

But this is strange because I though his card hard at lest 2 d support from dri built into xorg. Oh well installing the binary driver from the repos should do it.

---

### Post by DapperDave42 on 2007-02-02
Thanks so much for the instructions - I had checked the compatibility guide and thought my card wouldn't be an issue (though i had planned on installing the binaries anyway) - I can't wait to try this out (still waiting on a DVD image of Fedora to finish d/ling just to be safe).
Thanks again, I'll let you know if this fixes the problem.
~Dave

---


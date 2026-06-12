---
title: "Can't install"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Cap'n Murph on 2007-12-07
I just downloaded the Iso for the 64-bit version and burned it to a CD twice, once at maximum speed, once at 4x, and in both cases when I try to install the screen goes blank and my monitors "no signal" message appears. I get to the initial menu, but I've tried both install and checking the disc, and both times the screen went blank.

---

### Post by taurus on 2007-12-07
What's the spec of your machine especially the graphic card?  You can always try using the alternate CD since it's a text based installer.  No need to boot into Live first before you can install it.

---

### Post by Cap'n Murph on 2007-12-07
I'm using an NVidia GeForce 8600 GT with 2 gigs of ram and an Athlon X2 3 ghz dual core. I'll give the text one a shot real quick.

---

### Post by Dr Small on 2007-12-07
I had the same problem for Gutsy 32bit.
Try pressing CTRL + ALT + F7 when the screen says No Signal and goes blank, and then typing in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You may have to choose the Vesa drivers, and also, set the screen resolution to what your monitor can handle. When finished go back to Display:0 by pressing CTRL + ALT + F7 and then press CTRL + ALT + SHIFT + BACKSPACE and that will restart X.


That may help, as it did for me.

Dr Small

---

### Post by Cap'n Murph on 2007-12-07
Nothing happens when I hit ctrl+alt+F7, and the text install says it can't detect the cd in the drive (and I'm booting from the cd, so I don't know what the hell that's about).

---

### Post by Dr Small on 2007-12-07
I am sorry. I made a mistak :(
I ment CTRL + ALT + F1.

---

### Post by Cap'n Murph on 2007-12-07
I'm still not getting anything

---

### Post by awthomp on 2007-12-07
I had the same problem trying to install the x64 version with a decent NVidia graphics card.  I don't know too much about these things, but a friend told me it has something to do with the frame buffer in the kernel.

My fix:

Download and install the x32 version.  You won't see any performance differences anyways.

---

### Post by nikoPSK on 2007-12-07
if you are in windows try magic iso or something. In linux try K3b or disable window resize in compiz. Worked for me.

---

### Post by Cap'n Murph on 2007-12-07
Well I tried the 32 but version and it got to the loading screen before giving me several error messages:

[###.######] Buffer I/O error on device Fd0

it spits that out about 20 times with different numbers before going to a built in shell of some kind

---

### Post by Duck2006 on 2007-12-07
Have you tryed safe graphic mode?

---

### Post by kle on 2007-12-07
With an  nVidia geforce card, I would think you have to tell the live CD you are installing from (or else the grub menu, if you have a dual boot)

noapic irqpoll

From the CD I believe you can add those two words to the command line. There is supposed to be an option where you can alter how the CD launches. 

Once in, you alter the   file  /boot/grub/menu.lst
adding the two   words to the two lines almost at the bottom of the file that start with "kernel"

---

### Post by Cap'n Murph on 2007-12-07
safe graphic mode was no different. I got what I think was the command line by hitting F6 over the option to install, but when I added noapic irqpoll on the end, it didn't change anything. If you can't tell already, though, I'm fairly new at this (I just converted less then a week ago), so I could very easily have done it wrong.

---

### Post by kle on 2007-12-08
Ok

Maybe you  have to start all over again. 
If you are trying to install a dual boot, I would urgently suggest you follow the guide on 
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
It may look a bit daunting, but Herman walks you through every single step.Once you get used to his layout, his directions are extremely clear. 
Except for the noapic irqpoll part (he eveidently does not have a nVidia geforce card)

Regardless of whether you are trying dual boot, I suggest you go through the installation steps again, again adding the string (and I add a word to it)
"noapic irqpoll noirqdebug"
without the quotes, at the end of the string in F6 mode (on the installation disk)

I am sorry that I have not saved the URLS about installation to the pages that got me on my feet.

---

### Post by Cap'n Murph on 2007-12-08
Perhaps it was just not meant to be...So far I've tried:

64-bit Unbuntu
32-bit Unbuntu
64-bit Unbuntu text install
64-bit Kunbuntu

I've burned them all several times, and tried them with and without the commands you've given me, and none have even gotten through to the actually formatting/installation. I give up:(.

---


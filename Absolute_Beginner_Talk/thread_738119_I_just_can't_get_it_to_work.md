---
title: "I just can't get it to work"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by cabjnico on 2008-03-28
Ok, I've tried reading all of the information i find on the internet to make ubuntu boot after install, but i think i just plain don't understand what to do.. I did the noapic etc etc to boot from the live cd (i'm using a dv6000 btw, 6449us to be specific [amd turion64 x2]).
I used windows to create a partition of about 10-11 gigabytes of unallocated space and asked ubuntu to install on the biggest continuous free space.
this is a screen of the final settings
[http://i3.photobucket.com/albums/y75/thenico/Screenshot.png](http://i3.photobucket.com/albums/y75/thenico/Screenshot.png)
thank you in advance, and sorry for another thread like this one

---

### Post by cisforcojo on 2008-03-28
When you say an unallocated "partition" of free space. Is it a new partition or is it just 10-11 free?
Because if you install on the biggest allocation of continuous free space, that's using space on your Windows drive.

Btw, no need to apologize. :)

---

### Post by Hospadar on 2008-03-28
are you getting any error messages? is it just booting windows with no sign of grub?

---

### Post by tango_ninja on 2008-03-28
what is the problem that you are having?

it seems that everything is in order...if (in this screenshot) you advance, you will create a main partition (5) and a swap partition (6) with boot loader. then you will be able to install ubuntu on partition 5.

---

### Post by cabjnico on 2008-03-28
i made an unallocated space of 10 gigs, and it installs on it. and separates about 500 megabytes for swap

grub does launch, but when i boot ubuntu it goes to the third line of the loading bar and stops there (like a ninth of the way)

---

### Post by LowSky on 2008-03-28
> **cabjnico said:**
> I did the noapic etc etc to boot from the live cd (i'm using a dv6000 btw, 6449us to be specific [amd turion64 x2]).
      

Noapic is for computer that are from 2000 or older, a new machine doesnt need you to enter those commands

---

### Post by cisforcojo on 2008-03-28
Sorry for the post before, I'm on a slow connection and was waiting for your screenshot to finish loading. I'm sure someone has told you what to do by now ;)

Anyway, the problem seems to be that your main drive is 'sda' but you're instructing hte boot loader to install onto hd0. Thus, there will be no boot loader when you boot up. I believe hd0 should be sda0. Anyone? Anyone?

---

### Post by cisforcojo on 2008-03-28
> Noapic is for computer that are from 2000 or older, a new machine doesnt need you to enter those commands

That's not 100% true. I'm using a Chinese Lenovo (IBM) computer that I bought 2 years ago and 2 years ago I needed to use that to get Ubuntu to install. Just my experience (I don't need it anymore though. No idea what it was about).

---

### Post by cabjnico on 2008-03-28
> **cisforcojo said:**
> That's not 100% true. I'm using a Chinese Lenovo (IBM) computer that I bought 2 years ago and 2 years ago I needed to use that to get Ubuntu to install. Just my experience (I don't need it anymore though. No idea what it was about).

haha yeah, the live cd wouldn't boot so i researched and added those commands.
how do i change hd0 to sda0 (hopefully without erasing anything from windows vista partition) thanks for your help

---

### Post by cabjnico on 2008-03-28
nevermind, i just had to look at my screen haha what a dummy

so i'll try changing (hda0) to (sda0) and if i'll tell you if it worked
thanks for the help, again

---

### Post by cisforcojo on 2008-03-28
Alright well your bootloader is installing fine then. Try loading with the command 'nosplash' (this takes away the graphical loader and will tell you exactly what's going on. You'll be able to see where it's halting.

---

### Post by cabjnico on 2008-03-28
fatal error...

execute grub-install (sda0) failed :S

---

### Post by cisforcojo on 2008-03-28
Yeah it looks like your bootloader is loading fine actually. Try loading your system with the option (in GRUB) 'nosplash'

That'll let you see exactly where your system is stopping.

---


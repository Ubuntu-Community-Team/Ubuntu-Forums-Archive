---
title: "i refuse to share the MBR"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by wolfen69 on 2007-07-20
the way i "dual and triple boot". 
every OS has its own drive.
when you're installing one OS, pull the plug on every other drive.
when you're done installing, hit f12 or something similar to pick boot order.
why make it hard? having multiple partitions on 1 drive only leads to heartache.
does anyone else feel the same way?

---

### Post by Motoxrdude on 2007-07-20
Not really. I am triple booting without a problem. I just hate how windows doesn't play nice with ubuntu when i have to reinstall it.

---

### Post by felicity on 2007-07-20
Haha, I agree! Except grub is nice once you get all the drives installed so you don't have to go to BIOS each time to do the boot order.

---

### Post by wolfen69 on 2007-07-20
> **Motoxrdude said:**
> Not really. I am triple booting without a problem. I just hate how windows doesn't play nice with ubuntu when i have to reinstall it.

THAT'S why i dont do it that way. if i have to reinstall windows or whatever, it's no problem. just unplug everything else.

---

### Post by wolfen69 on 2007-07-20
you can always pick boot order via bios

---

### Post by eentonig on 2007-07-20
It's a viable solution. If you have fast access to disable/enable the drives. For 99% of the users, that won't be the case, as there HD are built in to the PC.

On my worklaptop, I have my personal OS running like you said. 

WinXP Pro installed on the internal HD (work)
Ubuntu installed on an USB attached HD. And my bios bootorder is set to (CDrom), USB, HD.

This way, if I do'nt attach my usb, win loads up. If I do attach my usb, Ubunto loads.

---

### Post by wolfen69 on 2007-07-20
i dont understand why people make things harder than they should be.

---

### Post by Motoxrdude on 2007-07-20
There's microsoft for you ;)

---

### Post by wolfen69 on 2007-07-20
cool, im sure your stuff runs just fine.

---

### Post by wolfen69 on 2007-07-20
i gave it up a while ago.(windows)

---

### Post by wolfen69 on 2007-07-20
i try to present a different way of thinking about dual booting, that's all.

---

### Post by thedivvyman on 2007-07-20
I  agree - I  have  a  drive  with  dual  boot  xp & ubuntu,  but  also  have  a  second  drive  with  xp  only  and  a  third  with  only  ubuntu.  The  last  drive  is  used  90%  of  the  time. The  dual boot drive is  hardly  ever  used  and  xp  is  used  to  check  printer  maintainence  etc.

---

### Post by Frak on 2007-07-20
Nothing a little editing of the Grub config file won't fix. Or just use the GrubED script.

---

### Post by eentonig on 2007-07-20
> **wolfen69 said:**
> i gave it up a while ago.(windows)

for personal use, me too. But my company forces me to use it and prohibits altering the partitions. So this way, I can give some proper use to the laptop when I'm at home. And still comply with our companies policy.

---

### Post by rillip on 2007-07-20
This is fine if you have multiple drives, and can easily select from your bios which hard drive boot order to choose. My bios gives rather generic hdd0, hdd1, so it'd be quite a bother to figure out which was which.

---

### Post by evieP on 2007-07-20
I never realised how **_easy_** it was to edit a GRUB menu until somebody showed me. ```
 sudo gedit  /boot/grub/menu.lst 
```

All you do is count the lines in menu.lst (11,12 or so) and change the number (usually default 0) to whatever OS you have listed in the initial Grub screen lines (Count them from 0 to the end, spaces too if you have them)

On this triple-boot system, Feisty is 0, Edgy is 6, WinXP is 11, so if you want a permanent boot to WinXP, you simply change the 0 to (in my case) 11.  Oh, and about 4 lines further on the timeout default is set to 10 (seconds), so if you want to create a secret Ubuntu system for yourself (Dads please note!) just make Grub flash by so that only you can catch it--well, that's one way of doing it, I guess!..........ooops!  (PS don't forget to save menu.lst as well)

---

### Post by Benbow on 2007-07-20
After amending the drive numbers, how do you activate the whole thing? I don't quite understand. Sad, isn't it!

---

### Post by rojer on 2007-07-20
Ok exaclty what I have tried to do.

BUT how?

I had Win XP on sata dirve (disconnected), I installed Ubuntu on IDE, reconnected SATA.

I can only boot form XP.  Tried changing Bios but can only select Hard drive not specific hd.

---

### Post by Tomosaur on 2007-07-20
Every OS **needs** a bootloader to run. Windows uses one, but it is invisible and doesn't present you with any options unless you go out of your way to force it to.

Ubuntu uses Grub, which is far more friendly. The EASIEST way to have multiple OSs is to share the MBR. This is usually no trouble at all, unless you run Windows, which uses a destructive MBR, so if you ever need to reinstall it, it can cause problems.

I would say that switching physical drives is more difficult than simply choosing which OS to boot in Grub, however.

---

### Post by rillip on 2007-07-23
> **rojer said:**
> Ok exaclty what I have tried to do.

BUT how?

I had Win XP on sata dirve (disconnected), I installed Ubuntu on IDE, reconnected SATA.

I can only boot form XP.  Tried changing Bios but can only select Hard drive not specific hd.

Exactly,  With your bios, you'll have to actually physically unplug the Windows drive to boot the other.  With mine I have to guess which disk is which, with yours, it just goes in order without asking you.

---

### Post by evieP on 2007-07-23
Benbow,....to activate your new choice of OS after changing the default number, as outlined in #16, you just save the file, thats all.!........Your choice becomes the new default on your next boot.  You have 10 seconds to highlight a different OS if you change your mind, that's why GRUB is (IMHO) such a powerful and flexible tool even for us beginners!

---


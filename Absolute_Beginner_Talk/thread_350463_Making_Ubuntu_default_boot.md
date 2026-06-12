---
title: "Making Ubuntu default boot"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Elliot.strumlauf on 2007-01-31
First off, I am rather new to Ubuntu. Sorry, and thank you for your patience. 

My problem: I am dual booting Ubuntu 6.10 and Suse 10.2, and Suse keeps booting up by default. As I dislike Suse, I have tried uninstalling it, but then i keep getting a GRUB error 22. I am trying to make Ubuntu 6.10 my default boot, so that when I turn my computer on it will load it automatically, instead of suse 10.2. 

I have read many forums telling me to edit boot/grub/menu.lst, but nothing actually helped, the only thing they did was copy what it said =P.

Thank you!

---

### Post by rsambuca on 2007-01-31
Which system did you install first?

---

### Post by Elliot.strumlauf on 2007-01-31
Thank for the expediency! I installed 6.10 first. After I installed 6.10, I tried Dream2.2, and it did the same auto load as suse, so i replaced it with Suse in hopes that i could now autoload ubuntu yet try a new OS!

---

### Post by old_geekster on 2007-01-31
Here is a link that you will probably find helpful:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

You can find anything that your heart desires; including, how to change the default OS in GRUB.

I normally copy and paste most of the commands, since I am a newbie, also.

If you haven't installed "Automatix2, I highly recommend it.  It will save you some heartburn.:)

---

### Post by mikemn84 on 2007-01-31
I would suggest this [http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed") 
It can edit your grub list through a pretty graphical interface.  Just follow the instructions on the first page to install.  Its pretty slick

---

### Post by Elliot.strumlauf on 2007-01-31
Thanks guys! Yeah i have Automatix2, what an amazing program......I'll checks these sites out and get back to ya =)

---

### Post by rsambuca on 2007-01-31
OK, error 22 means that the grub instructions from the MBR are pointing to a place that it can't find (since you deleted them!)

You'll need to boot from the ubuntu liveCD

open a terminal, and enter the command```
 sudo grub
```

you will see a prompt that says grub>

enter ```
find /boot/grub/stage1
```

you will now see where the grub instructions are located (or perhaps more than one)  eg. (hd1,1)

enter ```
root (hd1,1)
``` This tells the grub loader where the stage1 instructions are.  You will replace (hd1,1) with your correct location from the "find" command

Now, enter ```
setup (hd0)
``` to write the instructions to the MBR

type "quit" to exit grub.  Reboot and hopefully you are good to go.

---

### Post by Elliot.strumlauf on 2007-01-31
As for ubuntuguide.org, it didn't work at all....there were no instructions whatsoever =P

As for GrubED....no installation file..

And thank you rsambuca, but the grub did something weird. When i did find /boot/grub/stage1, it gave me:

 (hd0,0)
 (hd0,2)

I used (hd0,2) first, I followed your directions, and it gave me the same old auto-Suse. Note, though, that it was giving me the Error 22 when I deleted Dream (then autoloading) and only had the non default loading ubuntu. This dissappeared upon Suse10.2, but Suse took it's place!!!

I then used (hdo,0) hoping that it must be my desired ubuntu boot, but it gave me: 
grub> root (hdo,0)

Error 23: Error while parsing number

ARGH!

---

### Post by rsambuca on 2007-01-31
did you enter root (hd[COLOR="Red"]0[/COLOR],0) ?

it is a zero, not a small letter o.

---

### Post by mikemn84 on 2007-01-31
If the problem is more complex as rsambuca has suggested, grubED wont fix that... however, the instructions for installation are:

From the terminal, cd to the directory you unpacked the zip to and type
```

sudo ./install

```
Installation from then on it is automatic.

To run:
```

gksudo GrubEd

```

---

### Post by Elliot.strumlauf on 2007-01-31
Finally got it running!!! Rsambuca, you were right, i hit o, whoops!

Thank you so much for every one who helped me, for every one who uses this, follow rsambuca's advice! Thanks!

---

### Post by Elliot.strumlauf on 2007-02-08
Follow up: Ubuntu loads by default, hurray! But, Suse cannot be accessed through grub, and no where can I find a way to boot to it.....any help? I want to now install foresightlinux and the fact that It will most likely ruin Ubuntu again is dissappointing.

---

### Post by rsambuca on 2007-02-08
I believe Suse uses Grub as its bootloader as well.  There should be no problem loading all of these OS's and having grub manage them all.

---


---
title: "grub problem"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by zambotti on 2006-06-08
I installed Dapper on a second hd--primary hd was win98.  When the grub loader comes on, if I choose win98, the floppy drive runs, then it says "Starting Win 98", then "Type the name of the Command Interpreter" and gives me an A prompt.  Nothing seems to work after that.
If I choose Ubuntu from the grub menu, it boots just fine.  What's the problem?  Thanks.

---

### Post by Dragonfire on 2006-06-09
Have you first checked to make sure that it's not set to check floppy drive first in your bios, and have you also checked to make sure that the HD is listed in the bios as an existing hd?

That's really the two main problems i can think of. Anything beyond that, and message/e-mail me, or email my friend Wes(Vash is his nickname)

My email:Linuxconversionteam@gmail.com
Wes' email:vash5556@gmail.com

(also, you can reach us on our site. the link is posted in my signature below.)

---

### Post by cotcot on 2006-06-09
I am not sure this is the solution of your problem. But give it a try.
When the boatloader looks for the floppy (is there a floppy in this drive ?) i would think that the path for win98 in the menu.lst is not correct.
You may check this. Boot ubuntu and do ```
gedit /boot/grub/menu.lst
```

Go down in this file and look for the section with the windows entry. It is normally at the end of the file. I give you mine as an example. I have ubuntu, gentoo and windows XP in triple boot :

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

My XP is on my first hard disk on the first partition (same as your windows) : that is why (hd0,0). Check this in yours. Make sure that you have (hd0,0) after root.

---

### Post by nanotube on 2006-06-09
[QUOTE=Dragonfire]Have you first checked to make sure that it's not set to check floppy drive first in your bios, and have you also checked to make sure that the HD is listed in the bios as an existing hd?

That's really the two main problems i can think of. Anything beyond that, and message/e-mail me, or email my friend Wes(Vash is his nickname)

My email:Linuxconversionteam@gmail.com
Wes' email:vash5556@gmail.com

(also, you can reach us on our site. the link is posted in my signature below.)[/QUOTE]

what's with the luring people to email you? i've seen you do this in several posts now.

posting problems and solutions on this forum means these solutions are available to future people that may be having these problems. when you unnecessarily promote your email, you remove this potential benefit to future forum readers.

i understand you are just trying to promote your linuxconversionteam project, but come on, be reasonable about it. :)

---

### Post by gbw69 on 2006-06-09
hi
i had a similar problem.
thought i'd be clever and undo grub with fdisk /mbr, then fix the win98 problem just so i can get internet access.
how would i get grub or linux back without repartitioning or reloading ubuntu?

---

### Post by anaconda on 2006-06-09
It sounds, that you have BIOS booting order 
1. boot from hard-disk
2. boot from floppy
And when grub fails it tries the second option.. which is floppy...

I think that your grub has remapped the hard-drives, so that ubuntu is hd0 and win98 is hd1 (or that ubuntu actually is in the primary hd0 hard-disk)

And win98 must be on the primary hd. (as you said it is)
otherwise it just wont/cant boot.

try adding 
          map (hd0) (hd1)
          map (hd1) (hd0)
to your menu.lst to the win98 boot thing. just before the makeactive line...      

(The example exchanges the order between the first hard disk and the second hard disk. See also DOS/Windows. )

---

### Post by gbw69 on 2006-06-09
[QUOTE=anaconda]It sounds, that you have BIOS booting order 
1. boot from hard-disk
2. boot from floppy
And when grub fails it tries the second option.. which is floppy...

I think that your grub has remapped the hard-drives, so that ubuntu is hd0 and win98 is hd1 (or that ubuntu actually is in the primary hd0 hard-disk)

And win98 must be on the primary hd. (as you said it is)
otherwise it just wont/cant boot.

try adding 
          map (hd0) (hd1)
          map (hd1) (hd0)
to your menu.lst to the win98 boot thing. just before the makeactive line...      

(The example exchanges the order between the first hard disk and the second hard disk. See also DOS/Windows. )[/QUOTE]

Thanks for your prompt reply.
can you edit the menu.lst from win98?

---

### Post by anaconda on 2006-06-09
No you can't. (if you didn't install ubuntu to fat32-partition.)

Boot to ubuntu, or use a liveCD to edit it.

---

### Post by zambotti on 2006-06-09
cotcot
Thank you.  I tried what you asked and here's what I got:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Looks the same as yours.  My bios is set to load hd0 first, by the way.  So my only problem is that it looks at floppy drive first anyway and hangs there.

---

### Post by drtvasudevan on 2006-06-09
disable the floppy seek from bios!

tv

---

### Post by zambotti on 2006-06-09
drtvasudevan
there is no way to disable floppy from bios.  i have it listed as last, but grub still looks there.  
When I choose win98, I get this:
root (hd0,0,)
Filesystem type unknown, partition type 0x44
Save default

I think thats the problem.  Thanks

---

### Post by cotcot on 2006-06-09
[QUOTE=drtvasudevan]disable the floppy seek from bios!

tv[/QUOTE]

or put the bootloader on the floppy (i have this on both pc : floppy is grub menu; floppy out is XP or win 98 : so i do not have to bother my family with linux before i get them familiar to it).

---


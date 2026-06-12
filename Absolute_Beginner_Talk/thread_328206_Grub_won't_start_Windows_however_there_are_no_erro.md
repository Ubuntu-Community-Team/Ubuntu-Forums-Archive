---
title: "Grub won't start Windows however there are no errors"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by szantaii on 2006-12-30
Hi!
I'm new to ubuntu, I recently installed it.
I have 3 hard drives:
[LIST=1][*]120GB sata with two partitions, Windoxs XP on the first (ntfs), and some data on the other (ntfs)[*]200GB sata (ntfs), just for my stuff :D[*]and a 160GB IDE drive with ubuntu[/LIST]

I set in the BIOS to boot from the IDE drive first, not the onboard sata. GRUB comes in, everything is cool, but when I want to boot to XP GRUB says Starting up... and thats it. It doesn't do anything from this point. No error msgs, no nothing...
I can boot into my windows if I set the boot priority to boot from the onboard sata first, but I'd like to use GRUB instead of setting the BIOS all the time I want to load windows.
Please help me. :(

```
cat /boot/grub/device.map

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```

```
sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6397    51383871   83  Linux
/dev/hda2            6398       19457   104904450    b  W95 FAT32

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6553    52636941    7  HPFS/NTFS
/dev/sda2            6554       14593    64581300    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cilinderek of 16065 * 512 = 8225280 bytes

  Eszköz Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24320   195350368+   7  HPFS/NTFS
```

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by diepruis on 2006-12-30
Hvae you tried putting the root directive after the map directives?

---

### Post by szantaii on 2006-12-30
You mean:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd1,0)
chainloader	+1
```

Thanks for your reply, I've tried it. Nothing happened, the same thing happens... actually nothing happens.

---

### Post by diepruis on 2006-12-30
Mmmm... you could try commenting the map statements and changing the root one to hd(0,0). Not sure if that will work though.

---

### Post by szantaii on 2006-12-30
Commented out, changed the root to (hd0,0), but the only result was:
> Error 13: Invalid or unsupported executable format

---

### Post by diepruis on 2006-12-30
Oh silly me, the original conf was correct, but you neet to add boot at the end of it.
[http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading](http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading)

---

### Post by szantaii on 2006-12-30
So you mean:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
boot
```

will solve my problem?

---

### Post by Frak on 2006-12-30
Should and if not, take of the map markers.

---

### Post by diepruis on 2006-12-30
It might. I'm no GRUB expert, but that's what the documentation says, so you should try at least ;)

---

### Post by szantaii on 2006-12-30
I did it. Guess what... it didn't help. :D
I tried both:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
boot
```
and
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1
boot
```

---

### Post by Frak on 2006-12-30
Did you try the Windows XP it has in the GRUB menu.lst? Thats what I used and it worked perfectly.

---

### Post by diepruis on 2006-12-30
Okay, could you try the one **with** the map directives again? This time try substituting root(1,0) with root(0,0). If that doesn't work, could you try rootnoverify(0,0)?

---

### Post by szantaii on 2006-12-30
Frak, please rephrase your last post cause I didn't understand what you wanted to say. :D

---

### Post by szantaii on 2006-12-30
> **diepruis said:**
> Okay, could you try the one **with** the map directives again? This time try substituting root(1,0) with root(0,0). If that doesn't work, could you try rootnoverify(0,0)?

Just to be precise, and I am getting a little confused:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd0,0)
chainloader	+1
boot
```

and if that does not work:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd0,0)
chainloader	+1
boot
```

However I want to thank you all for the help, I appreciate it.

---

### Post by Frak on 2006-12-30
in the menu.lst there is a part with an example of how an XP boot phrase should look, when I boot back into Kubuntu later I'll post what it says, but If you found it it'd be easier, but I remember it was something simple.

---

### Post by diepruis on 2006-12-30
> **szantaii said:**
> Just to be precise, and I am getting a little confused

Looks good.

No problem ;)

---

### Post by szantaii on 2006-12-30
Now I see:

```
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
```

So you say, I should try that. Okay I will, but I have to go, because my girlfriend is getting angry... In a half an hour I'm gonna be back, and I'll try your and diepruis' advices.

---

### Post by Frak on 2006-12-30
Thats it.

---

### Post by szantaii on 2006-12-30
diepruis: I got > Error 13: Invalid or unsupported executable format
Frak: I used the exmaple like that:
```
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
makeactive
chainloader	+1
```
and the same thing happened... nothing. It said Starting up... then nothing.
I don't know what to try...

---

### Post by Frak on 2006-12-30
did you put **boot** at the bottom?

---

### Post by szantaii on 2006-12-30
First I forgot about it, and second I did, but nothing.

---

### Post by Duck2006 on 2006-12-30
You could try it this way

Code
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
makeactive
savedefault
chainloader	+1
boot

---

### Post by Frak on 2006-12-30
Did you take out the # signs?  That might sound n00bish, but we have to rule out every possible mistake, of mine or yours, no offense to anybody.

---

### Post by Duck2006 on 2006-12-30
Also you could try a # mark in front of savedefault

---

### Post by szantaii on 2006-12-30
Frak: I checked it, I took them out, didn't take that as an offense. :)
Duck2006: tried both. none of them helped.

---

### Post by confused57 on 2006-12-30
You could try rootnoverify, as someone suggested:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		    Microsoft Windows XP Professional - magyar
rootnoverify  (hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by diepruis on 2006-12-30
Are you absolutely sure that your Windows isn't pooched?

---

### Post by Frak on 2006-12-30
You try using super GRUB?

---

### Post by szantaii on 2006-12-30
> **confused57 said:**
> You could try rootnoverify, as someone suggested
Didn't help.

diepruis: If you mean that my windows is fscked up, than no. I can see my windows drive from ubuntu. And I can boot windows if I change the boot device priority in BIOS, but in that case Grub doesn't come up because it is on the IDE drive...

Frak: You mean Super GRUB disk?

pfff... This is getting like a cabaret. (I mean, thanks for all the help, but I am getting a little desperate.)

---

### Post by Frak on 2006-12-30
[http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

Auto GRUB Editor, with a graphical approach, it can reduce errors.

---

### Post by szantaii on 2006-12-30
I installed that script. And?

---

### Post by confused57 on 2006-12-30
Here's an excellent link about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This site is maintained & developed by herman, a forum member.

---

### Post by gn2 on 2006-12-30
Which drive did you install Grub to?

Were the two Sata drives connected when you installed Ubuntu?

Do you have a Windows CD?

Do you have a Super Grub disc?

---


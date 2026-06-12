---
title: "cdrom wont mount"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-05-31
Hi, a few days ago I set up, with help of course, auto mount for my 2nd disc. Everythings going just fine with that. Today I used my cd for the first time since then and it wont mount. Really weird!
I'm sure I never touched that part of fstab.
anyway here's my current fstab;
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
/dev/sdb1 /media/seagate ext3 defaults 0 0
[COLOR="Red"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]
and my backup fstab;
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
[COLOR="Red"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]
relevant parts look identical to me.
the error message;
[COLOR="Red"]mount: special device /dev/scd0 doesn't exist[/COLOR]
in /media there are 4 entries ; [COLOR="Red"]cdrom[/COLOR] (link)[COLOR="Red"] cdrom0[/COLOR], [COLOR="Red"]seagate[/COLOR](2nd disc) and the actual [COLOR="Red"]dvd[/COLOR] (playing on totem)
Also the icon on the desktop is now called CD-ROM1
I even tried changing fstab just now to cdrom1 and then the desktop icon changed itself to CD-ROM2. Oh, and I checked /dev/scd0 and yeah there isn't one, plenty of sda's and sdb's but nary a scd to be seen

Is it a ghost in the machine?
Spooooooky.
Any clues? I prefer to use VLC than Totem (no offence to totem-guys)
Thanks.

---

### Post by Inxsible on 2007-05-31
> **carloslosgrande said:**
> Hi, a few days ago I set up, with help of course, auto mount for my 2nd disc. Everythings going just fine with that. Today I used my cd for the first time since then and it wont mount. Really weird!
I'm sure I never touched that part of fstab.
anyway here's my current fstab;
 
and my backup fstab;
 
relevant parts look identical to me.
the error message;
[COLOR=red]mount: special device /dev/scd0 doesn't exist[/COLOR]
in /media there are 4 entries ; [COLOR=red]cdrom[/COLOR] (link)[COLOR=red] cdrom0[/COLOR], [COLOR=red]seagate[/COLOR](2nd disc) and the actual [COLOR=red]dvd[/COLOR] (playing on totem)
Also the icon on the desktop is now called CD-ROM1
I even tried changing fstab just now to cdrom1 and then the desktop icon changed itself to CD-ROM2.
Is it a ghost in the machine?
Spooooooky.
Any clues? I prefer to use VLC than Totem (no offence to totem-guys)
Thanks.
 
This is because you upgraded your linux kernel from -15 to -16. I have the same problem. 
Do you have only 1 CD/DVD drive on your machine?
 
It seems that the kernel update creates a phantom icon for the CD-ROM 1.

---

### Post by carloslosgrande on 2007-05-31
Yes I upgraded. Yes I have only 1 cd/dvd drive.
So....we wait for the fix?

---

### Post by Inxsible on 2007-05-31
> **carloslosgrande said:**
> Yes I upgraded. Yes I have only 1 cd/dvd drive.
So....we wait for the fix?
 
pretty much ...yeah :(

---

### Post by Inxsible on 2007-05-31
I am assuming that your other drive icon for CD/DVD works the way it should without problems.

---

### Post by carloslosgrande on 2007-05-31
yeah, well I've only tried a dvd so far and it'll work with totem but not vlc. haven't tried mplayer.
totem seems to bypass the icon thing altogether.
Anyway, thanks for telling me.
It wasn't something I broke for a change.

---

### Post by Inxsible on 2007-05-31
> **carloslosgrande said:**
> yeah, well I've only tried a dvd so far and it'll work with totem but not vlc. haven't tried mplayer.
totem seems to bypass the icon thing altogether.
Anyway, thanks for telling me.
It wasn't something I broke for a change.
 
What happens when you try to play a DVD with VLC ?

---

### Post by carloslosgrande on 2007-05-31
Nothing, it just won't play. I select cdrom from the menu, and then nothing. thats when I checked the icon and saw it wasn't mounted.......and the rest.

I just tried to eject the dvd and got a whole lot of errors
the > device system:/media/hda (/dev/hda) named SIN_CITY currently mounted at /media/SIN_CITY
> can't be unmounted because a problem in mtab, ie > cannot create a link to /etc/mtab~
and other programs are attempting to use said device. 
> cannot stat /media/SIN_CITY : no such file or directory
Well, all I wanted to do was try something else. Such a fuss.

Its actually really late here, so I'll have to check back in the morning

---

### Post by JohnPhys on 2007-05-31
I'm having the same issue.

It appears that Feisty uses scsi emulation for the ide drives, and maps the cd drive to /dev/scd0 in 2.6.20-15-generic, and this is what was put in the fstab.

When I look in dmesg when .20-16-generic boots, the cd drive device point is created at /dev/hda, and there is no symlink from /dev/scd0 -> /dev/hda.  This is why the drives won't work.

As a work around, you can either: boot the -15-generic kernel (works for me), or change the fstab to have /dev/hda rather than /dev/scd0 for the cd drive (should work, haven't tried it).

---

### Post by carloslosgrande on 2007-05-31
Hi JohnPhys, Just tried the fstab change but no joy there.
Also in an excess of clicking I deleted kernel version 12 and 15 yesterday morning. oops.

---

### Post by JohnPhys on 2007-05-31
You might still be able to install 2.6.20-15-generic from the repositories

---

### Post by alex_anthony on 2007-06-01
I found a fix for this! (or at least for this problem on my laptop)
In nautilus look at /dev and you will probably see files called cdrom, cdrw, dvd, dvdrw and anything else like that which refers to cd or dvd
Find in fstab this line:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```
and change it to have /dev/cdrom at the start and copy this, changing it each time so you have a line for each of those files you found in /dev 
thus at the end of mine I have this
```
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/cdrw /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/dvd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/dvdrw /media/cdrom0 udf,iso9660 user,noauto 0 0
```
This tells it to find your cds in the place they are in the new kernel, and still mounts them in the same place (although I'm not sure if this would have to be changed if you had 2 disk drives)

---

### Post by carloslosgrande on 2007-06-02
[I]Hi Alex Anthony, I tried your idea and yes it works, both totem and vlc play.
The panel dvd disc icon has disappeared, but the desktop icon remains.
It seems a good temporary fix. Thanks man.
Carlos.[/I]

---


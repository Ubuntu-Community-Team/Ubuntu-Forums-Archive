---
title: "Extra CD-ROM drive"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-05-29
Hello all

I just upgraded to the new generic kernel version just a couple hours ago and now I've got this extra CD drive on my comp...does anyone know how to get rid of it? I've got a laptop with a single DVD-RW drive...

I've included a pic to better demonstrate...see how i've got a audio disc in there...

EDIT: If it can't be remove why did the upgrade suddenly give me an extra drive...what's its purpose?? Thanks!

---

### Post by SoulinEther on 2007-05-29
I have the same thing myself. Or at least I had it. I didn't really try to fix it. A solution wouldn't be bad.

I have two floppy drives for sure. But I only physically see one on my computer.

Hey, whatever, maybe I have a second floppy drive in an alternate dimension. :D

---

### Post by Inxsible on 2007-05-29
Did this happen to you recently ?

I updated my machine today... some 4 updates for linux-kernels and I see an extra CD Rom-1 too.


I thought maybe i should just restart and see if it still hangs around !

---

### Post by isaacj87 on 2007-05-29
haha, perhaps! but unfortunately I can't utilize this cdrom drive from the alternate dimension...

---

### Post by isaacj87 on 2007-05-29
Yeah...it happened within the past hour...I tried restarting but it didn't help..:(

---

### Post by gimfred on 2007-05-29
You could consider it a feature... the writer part separated from the reader part. However, just to be sure, do you have a blank disk in the drive? any disk at all?

---

### Post by forestpixie on 2007-05-29
I had same thing - there was a ghostly phantom creaking cd rom pitched up in fstab - i commented it out and all was once more as it was before the invasion of the phantom cd roms

Not sure if that was right but it worked

:)

---

### Post by Inxsible on 2007-05-29
The problem is that I do not have an extra entry for it in the fstab. I just have one entry which I had ever since I installed Ubuntu.

---

### Post by rufus05 on 2007-05-29
I have the same issue.  When I upgraded my kernel I got the new cdrom drives.

I tried just deleting them, but I got an error message when I did.  When I checked, neither has been mounted the icons are just there.

The new drives are not functional, but just seem to be annoying icons.  I don't think they are creating any serious issues, but I haven't had a chance to really check it out.

Any help on removing them would be greatly appreciated.

Thanks.

---

### Post by isaacj87 on 2007-05-29
My situation is the same with rufus...my new found drive isn't functional.

---

### Post by Inxsible on 2007-05-29
> **isaacj87 said:**
> My situation is the same with rufus...my new found drive isn't functional.

Ditto !

---

### Post by isaacj87 on 2007-05-29
When you revert back to a previous kernel (through the GRUB menu) it doesn't appear but I don't want to go through the trouble of removing the new kernel upgrade. I'm just a linux noobie...so I have no idea how any of this stuff works, just the basics to get me by.

---

### Post by phidia on 2007-05-29
The devs don't read these forums so perhaps this should be reported at launchpad  [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) as a bug? 
I saw the available upgrades but opted not to.

---

### Post by Bakerman on 2007-05-29
I had the same thing when I upgraded from Edgy to Feisty. I had four non-functioning CD/DVD drives listed instead of two. I couldn't find a way round the problem so I scrubbed it and re-installed Edgy again. No Problems since I'm pleased to say.

I thought it was just something weird happening because of my set-up, or me being new to Linux...

---

### Post by man[BEAR] on 2007-06-04
I also suffer from this, I have one wroking drive and two extras so when I try to play Battlefield 1942 it tries to go to the fake drives instead of the real disk

---

### Post by isaacj87 on 2007-06-06
Is there really no solution to this? I've tried umount and all that...The only solution I can think of is downgrading kernels..but I don't really want to do that!

---

### Post by Inxsible on 2007-06-06
found a solution :
1) Go to the /dev folder and look for all the cd related icons /files there. I had cdrw cdrom dvdrw and dvdrom
```
ls -l | grep dvdrw
```
The output will be somthing like this```
lrwxrwxrwx 1 root root           3 2007-06-06 17:44 dvdrw -> hda

```
2)Replace dvdrw with the ones that you found in /dev. Most likely they will all map to the same device name. For me all of them had an alias of hda

3) Then I changed the /etc/fstab entry from```
 /dev/sda /media/cdrom0 udf,iso9660 user,noauto 0 0
```
to ```
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Now I have only one drive in the new kernel.

Note the change from /dev/sda to /dev/hda ...guess -16 recognizes devices in some other way.

---

### Post by isaacj87 on 2007-06-07
hmmm..it worked...but i had /dev/hdb....what would happen if you just deleted the line?

---

### Post by isaacj87 on 2007-06-09
it seems the latest kernel update corrected my problem. :)

---


---
title: "unable to mount selected volume (my cd drive won't mount)"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by AndyParka on 2007-06-11
I've searched ALOT for a solution but none have helped me.

When i insert a disc into my drive nothing happens... it spins... but nothing is seen by ubuntu. i used to be able to see stuff but somthing changed for some reason. now i dont know much about the ubuntu file system so i dont know wat files to put here. the message i get from the browser when i try to open the cd is this:

unable to mount selected volume

more details

mount: special device /dev/hdc does not exist


some of the other posts i read ether had a really confusing solution that didn't make sence to me or they just had a reply saying they had solved it. so a VERY detaild tutorial or somthing would be nice.

i had a problem with my xorg.conf file not long ago when i installed ubuntu and i fixed it by running mint off the cd and copying its xorg.conf and paisting it over ubuntu's. could i do somthing similar to solve this problem? if not dont worry about it.

thanx in advance.

Andy Parka

---

### Post by klytu on 2007-06-11
I'll try to help. 

Please first post the output of the following commands: ```
dmesg | grep CD
```and ```
cat /etc/fstab
```You could just cut and paste the output into your reply post. Checking first  to make sure your CD drive is found by the kernel and that your fstab is set up properly to mount CD's automatically.

---

### Post by ricardisimo on 2007-06-12
I'm having the same problem, and it appears to be a discrepancy between the logical name for the hardware in /etc/fstab on the one hand and, say, sudo lshw on the other. Our fstab is telling the system to look for hardware that doesn't exist. Here's the pertinent section of my hardware list:
```
*-cdrom:0
                description: DVD reader
                product: RW/DVD GCC-4520B
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd0
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD-RAM GSA-H22L
                vendor: HL-DT-ST
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H22L1.0006/08/05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
```
And here's /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5cbae883-1ea5-4909-a0f7-25dd778ffc45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1cfc19bb-b5dc-4199-8498-7bb897ec58f6 none            swap    sw              0       0
/dev/sdb1 /media/storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
What I need to know, but don't, is which of the several logical names listed is the appropriate one for my two CD/DVD drives. Is it /dev/cdrom, /dev/dvd, /dev/scd1, or maybe /dev/sr1, or something else. The options are out of hand, and yet with all of these possibilities the Feisty upgrade still managed to pick the wrong one. Bizarre.

Any help is appreciated.

---

### Post by ricardisimo on 2007-06-12
Well, I've tried inputing every possible line for the CDROM and DVDRW in fstab. Nothing. And, based on what I've read elsewhere, CD and DVD drives don't need any fstab line at all, which raises all sorts of questions, none of which I'll bring up now. Apparently this might be yet another kernel issue, and I guess we're sitting tight until it's fixed.

Just in case, though, here's my info:
```
~$ dmesg | grep cd
[   18.228114]   PREFETCH window: cdd00000-ddcfffff
[   22.556955] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.592360] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   23.592948] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   23.592984] ohci_hcd 0000:00:03.0: irq 17, io mem 0xdfffd000
[   23.626276] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.640608] sr1: scsi3-mmc drive: 125x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.757754] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   23.757811] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   23.757842] ohci_hcd 0000:00:03.1: irq 18, io mem 0xdfffe000
[   23.940916] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   23.940986] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   23.941052] ehci_hcd 0000:00:03.3: irq 20, io mem 0xdffff000
[   23.941063] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  446.697063] cdrom: sr0: mrw address space DMA selected
[  446.922944] cdrom: sr0: mrw address space DMA selected
[ 1090.177522] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 4 in
[ 1188.252799] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 6034 in
```
Thanks in advance for any help.

---

### Post by klytu on 2007-06-12
> **ricardisimo said:**
> Well, I've tried inputing every possible line for the CDROM and DVDRW in fstab. Nothing. And, based on what I've read elsewhere, CD and DVD drives don't need any fstab line at all, which raises all sorts of questions, none of which I'll bring up now. Apparently this might be yet another kernel issue, and I guess we're sitting tight until it's fixed.

Just in case, though, here's my info:
```
~$ dmesg | grep cd
[   18.228114]   PREFETCH window: cdd00000-ddcfffff
[   22.556955] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.592360] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   23.592948] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   23.592984] ohci_hcd 0000:00:03.0: irq 17, io mem 0xdfffd000
[   23.626276] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.640608] sr1: scsi3-mmc drive: 125x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.757754] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   23.757811] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   23.757842] ohci_hcd 0000:00:03.1: irq 18, io mem 0xdfffe000
[   23.940916] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   23.940986] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   23.941052] ehci_hcd 0000:00:03.3: irq 20, io mem 0xdffff000
[   23.941063] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  446.697063] cdrom: sr0: mrw address space DMA selected
[  446.922944] cdrom: sr0: mrw address space DMA selected
[ 1090.177522] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 4 in
[ 1188.252799] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x43 data 6034 in
```
Thanks in advance for any help.

Yes, it is bizarre that none of the choices worked. From what I understand, though, a proper fstab entry is needed in order for disc to be auto-mounted when inserted into an optical drive. Also, please post the output using capital CD: ```
dmesg | grep CD
``` The caps were on purpose in my post above. :-) Humor me, I believe the output will show which variation to use in your fstab. Then we can try to decipher why it´s not working. 

I suspect, as you hinted, that it´s a kernel issue. For one thing, I don´t know why your CD and DVD drives appear to be mapped to multiple /dev logical entries when you do lshw. This may be why you can´t get any of the listings to work. For example, on my working Feisty installation - both my optical drives each have a single, unique logical mapping which corresponds to what is in my fstab.

---

### Post by ricardisimo on 2007-06-13
Oops! Uh, I was just checking to see if you were paying attention... I'll be at my work machine shortly, and will do it correctly this time around. While I'm here, though, I should mention that I made a backup copy of /etc/fstab in case nothing worked or got worse. It did get worse, of course, and now nothing is working, DVD-wise, not even individual apps that used to be able to read DVDs just fine like VLC. Just yesterday morning I started watching a movie in between chores, then got wrapped up in all of this. Now no DVDs mount (however, Serpentine can read CDs in either drive... bizarre, huh?).

Anyhow, I repasted the old fstab back in but it failed to revert to its previous behavior, which was at least tolerable, if not optimal. The system is now blind to empty removables and DVDs. CDs do appear and have at least some functionality if not all. Really, really bizarre. Thanks again.

---

### Post by ricardisimo on 2007-06-13
Here we go:
```
:~$ dmesg | grep CD
[   23.012953] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4520B 1.00 PQ: 0 ANSI: 5
[   23.015190] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22L 1.00 PQ: 0 ANSI: 5
[   23.166006] Uniform CD-ROM driver Revision: 3.20
[   23.166419] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.183493] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   23.272436] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 03 00 0c 00
[   50.495217] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 02 00 00 00 00 02 00 0c 00
[   50.523564] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 02 00 00 00 00 02 00 0c 00
```

---

### Post by Inxsible on 2007-06-13
You could either
 
1) Remove the entry of the cd rom from the fstab ( or rather comment it out by putting a # in front of the line)
 
OR 
 
2) ```
ls -a dev | grep cd
```
it will probably map to a name. If you change cd to dvd or dvdrw or cdrom, it will give you the name of the device. For me they all mapped to "hda"
 
So I changed my fstab to match the device name obtained.
 
I hope thats understandable.

---

### Post by ricardisimo on 2007-06-13
```
~$ ls -a dev | grep cd
ls: dev: No such file or directory
```
I tried changing "cd" to any and all of the usual suspects. Nothing.

---

### Post by anaconda on 2007-06-13
EDIT: sorry just noticed that you already have /dev/hdc in your fstab, so ignore the rest! or maybe the scd0 would work better for you!

I solved my CD problems (not automounting and sometimes not even manual mounting) by editing the fstab file to be like it was in edgy (ubuntu6.10)

eg. to be mounted as an IDE drive , which it is!

Feisty handles IDE drives (CD and hard-disks) with scsi drivers, because they are supposed to work as well.. Not so in every case.

(my CD/DVD drive was /dev/hda in edgy, but in feisty it had changed to /dev/scd0 )

so I just edited the line in fstab and changed
/dev/scd0  ->  /dev/hda
so that it will be mounted with the IDE drivers..
and after that it has been working perfectly.!!

Your CD propably isnt hda.. but it is one of these: hda ,hdb , hdc or hdd.

---

### Post by ricardisimo on 2007-06-13
They're already listed there as hdc and hdd, so perhaps I should do the opposite of what you did, and get rid of the "hds". Any opinions?

---

### Post by ricardisimo on 2007-06-13
What am I saying? That's exactly what I already did. Never mind. Anyone else know what's going on?

Based on other threads it appears that Feisty generally (and specifically since the latest kernel image) is having quite a bit of difficulty with mounting drives. Could this just be something we have to wait out? I have no problem with that, but I'd like to be able to play my DVDs again. Thanks.

---

### Post by danny_kay1710 on 2007-06-13
i am relatively new at this so it probably wont work but i think from the looks of things your cd rom drivers are mapped as sr0 and sr1 which i have never seen before

you could try:

```
mount /dev/sr0 /mnt/cdrom0
mount /dev/sr1 /mnt/cdrom1
```

see if that does anything
danny_kay1710

[EDIT]
I just noticed they also appear to be mounting as scd0 and scd1 so you could also try

```
mount /dev/scd0 /mnt/cdrom0
mount /dev/scd1 /mnt/cdrom1
```

---

### Post by ricardisimo on 2007-06-13
/mnt? Do you mean /media? There's nothing in my /mnt folder, so I doubt this would have an effect.

---

### Post by klytu on 2007-06-13
> **ricardisimo said:**
> Here we go:
```
:~$ dmesg | grep CD
[   23.012953] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4520B 1.00 PQ: 0 ANSI: 5
[   23.015190] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22L 1.00 PQ: 0 ANSI: 5
[   23.166006] Uniform CD-ROM driver Revision: 3.20
[   23.166419] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.183493] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   23.272436] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 03 00 0c 00
[   50.495217] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 02 00 00 00 00 02 00 0c 00
[   50.523564] sr1: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 02 00 00 00 00 02 00 0c 00
```

This is strange - you're getting read errors on one of your drives. How are the drives physically connected? Are they connected via an IDE cable? Looks like they are both connected to the same cable according to what you have posted so far ... 

Have your DVD drives worked at all since you started using Feisty? If not, try booting with kernel option all_generic_ide,  then examine dmesg again as in my first post to see how the drives are mapped and compare with you fstab. If the drives did work before in Feisty, can you recall when they first stopped working?

---

### Post by ricardisimo on 2007-06-13
I've got more problems than just drive mounting. If I go directly to /media/cdrom1 (my DVDRW) I find there, reasonably, a folder called "audio_ts" and a file (shouldn't it be a folder as well?) called "video_ts". I cannot get anything to open it; not totem, not vlc, nothing. Attached is a screenshot. I attempted to add "vlc" as a command in the launcher to open it and got the response "Could not add application to the application database".

What is going on? Why do I get the impression that we are forever doomed to tremendous difficulty with all things DVD (encrypted, at least). By the way, yes I installed totem-xine, libdvdreader3, libdvdcss2, etc., executed the script, blah, blah, blah... I don't mind doing work to understand my system and get it up and running, but taking backwards steps is frustrating.

---

### Post by Inxsible on 2007-06-13
So do you see an icon of the CD/DVD-RW in nautilus ?

I fail to understand where you are at now?

do you still have issues recognizing the drive..or the contents within the drive ?

---

### Post by ricardisimo on 2007-06-13
Both. Now I can't even eject the drive to pull the DVD out. It just gets worse and worse...

---

### Post by Inxsible on 2007-06-13
The CD ROM 1 and CD-ROM 2 are, i think phantom icons. and you just mounted them i guess.

Your Audio Disc is the one that is the true drive. Try ejecting that !

---

### Post by Inxsible on 2007-06-13
try this command
```
ls -l /dev | grep cd
```See what it maps to.

Your output will be of this format
```
lrwxrwxrwx 1 root root           4 2007-06-12 23:36 cdrom -> scd0
lrwxrwxrwx 1 root root           4 2007-06-12 23:36 cdrw -> scd0
lrwxrwxrwx 1 root root           4 2007-06-12 23:36 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-06-12 23:36 dvdrw -> scd0
```

As you can see, for me all the cd/dvd maps to scd0 - which is the device name. Thats the name you need in fstab

---

### Post by ricardisimo on 2007-06-13
The audio disk is an actual audio disk in the CDRW. Here's this:
```
~$ ls -l /dev | grep cd
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 cdrom -> scd0
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 cdrw -> scd0
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 dvdrw -> scd1
crw-rw-rw- 1 root tty       2, 221 2007-06-13 13:50 ptycd
brw-rw---- 1 root cdrom    11,   0 2007-06-13 13:50 scd0
brw-rw---- 1 root cdrom    11,   1 2007-06-13 13:50 scd1
crw-rw---- 1 root cdrom    21,   2 2007-06-13 13:50 sg2
crw-rw---- 1 root cdrom    21,   3 2007-06-13 13:50 sg3
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 sr0 -> scd0
lrwxrwxrwx 1 root root           4 2007-06-13 13:50 sr1 -> scd1
crw-rw-rw- 1 root tty       3, 221 2007-06-13 13:50 ttycd
```
Thanks for your help.

---

### Post by Inxsible on 2007-06-13
So do you have 2 physical drives ?

one is CD RW/ DVD Combo and the other DVDRW ?

They map to scd0 and scd1 resp.
You will have to change your fstab. Could you post your fstab here.
```
gksudo gedit /etc/fstab
```

---

### Post by klytu on 2007-06-13
> **Inxsible said:**
> So do you have 2 physical drives ?

one is CD RW/ DVD Combo and the other DVDRW ?

They map to scd0 and scd1 resp.
You will have to change your fstab. Could you post your fstab here.
```
gksudo gedit /etc/fstab
```

Ricardisimo posted his fstab earlier and indicated that he tried various combinations of changes for the /dev entries in it, but none worked. Another of his earlier posts shows he has a DVD (read-only?) drive and a DVD-RW drive. 

It seems to me that you are probably right that the drives are mapped to scd0 and scd1. But the question is why didn´t that work when he updated his fstab earlier and why is his dmesg showing read errors in one of the drives?

---

### Post by ricardisimo on 2007-06-14
> **klytu said:**
> Ricardisimo posted his fstab earlier and indicated that he tried various combinations of changes for the /dev entries in it, but none worked. Another of his earlier posts shows he has a DVD (read-only?) drive and a DVD-RW drive. 

It seems to me that you are probably right that the drives are mapped to scd0 and scd1. But the question is why didn´t that work when he updated his fstab earlier and why is his dmesg showing read errors in one of the drives?

Maybe I'm dylsexic... sidlexyc... how do you spell dyslexic again? Could one of you take an educated guess at how those two lines SHOULD read, based on the information above. I'll try it again based on your suggestion. Otherwise I'm at a loss. Thanks.

---

### Post by urizel on 2007-06-14
Try the following:

ls -a/dev/ | grep cd 

this should yield something like:
cdrom             ptyd0  ptysa  ptyy4       tty22  ttyc9  ttyS1  ttyx9
cdrw              ptyd1  ptysb  ptyy5       tty23  ttyca  ttys2  ttyxa

Then, review /etc/fstab by typing:

cat /etc/fstab, where hopefully, you'll find something like this:

/dev/cdrom /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
you might also see how the first cdrom (cdrom0) is aliased in /media
something like this: 0 lrwxrwxrwx 1 root    6 2007-03-22 17:29 cdrom -> cdrom0

So...install a CD, then ...

sudo mount -t iso9660 /dev/cdrom /media/cdrom

cd /media/cdrom
there's your files!

hope this helps.

---

### Post by klytu on 2007-06-14
> **ricardisimo said:**
> Maybe I'm dylsexic... sidlexyc... how do you spell dyslexic again? Could one of you take an educated guess at how those two lines SHOULD read, based on the information above. I'll try it again based on your suggestion. Otherwise I'm at a loss. Thanks.

OK. (Eject any DVDs/CDs in your drives first ...) I'm thinking your corrected fstab should probably look like this (I commented the old lines that related to your DVD drives):

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5cbae883-1ea5-4909-a0f7-25dd778ffc45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1cfc19bb-b5dc-4199-8498-7bb897ec58f6 none            swap    sw              0       0
/dev/sdb1 /media/storage ext3 defaults 0 0
# /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/scd0         /media/cdrom0   udf,iso9660 user,noauto     0       0**
# /dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
**/dev/scd1         /media/cdrom1   udf,iso9660 user,noauto     0       0**
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Make sure /media/cdrom0 and /media/cdrom1 actually exist in your filesystem,  insert a disk in one of your drives, and hopefully it will automatically mount. I noticed in a screenshot in one of your posts that there also seems to be a /meda/cdrom2 directory - what all is in your /media directory?

---

### Post by ricardisimo on 2007-06-14
So here's the latest. I went back to scd0 and scd1, as per your recommendation. With fstab edited thusly, DVDs are invisible in the DVDRW, while Audio CDs in the DVDRW are only usable by Sound Juicer. Everything else (Nautilus, k3b, Grip, etc.) accepts that something is present, but can't read it.

Meanwhile, in the CDRW, DVDs are usable and readable by - at least - VLC and k3b, which is enough for now. CDs are very nearly invisible except for, once again, Sound Juicer.

I'm at a loss.

---

### Post by Inxsible on 2007-06-14
> **ricardisimo said:**
> So here's the latest. I went back to scd0 and scd1, as per your recommendation. With fstab edited thusly, DVDs are invisible in the DVDRW, while Audio CDs in the DVDRW are only usable by Sound Juicer. Everything else (Nautilus, k3b, Grip, etc.) accepts that something is present, but can't read it.

Meanwhile, in the CDRW, DVDs are usable and readable by - at least - VLC and k3b, which is enough for now. CDs are very nearly invisible except for, once again, Sound Juicer.

I'm at a loss.

Audio CD's will be only accesible by Sound-juicer. They are tracks on the cd. not files. Unlike Windows Ubuntu will not show you the tracks in nautilus.

As to why your DVD's arent visible in the DVDRW...i am not really sure.

---

### Post by ricardisimo on 2007-06-14
> **Inxsible said:**
> Audio CD's will be only accesible by Sound-juicer. They are tracks on the cd. not files. Unlike Windows Ubuntu will not show you the tracks in nautilus.
Really? I could swear that this is not the case on my home comp. I distinctly remember seeing content on CDs in Nautilus. Besides, certainly k3b or Grip should be able to scan audio discs, wouldn't you think?

---

### Post by Inxsible on 2007-06-14
> **ricardisimo said:**
> Really? I could swear that this is not the case on my home comp. I distinctly remember seeing content on CDs in Nautilus. Besides, certainly k3b or Grip should be able to scan audio discs, wouldn't you think?

Well..Nautilus has never shown me the content of audio cd's. But K3B does allow me to see them and rip them if i want.

---

### Post by themis on 2007-06-15
Hi to you all!
I can't either play dvd's and i'm really confused with what I've been reading.
here is what I get with commands previously asked.I would really like some help!

```

embryo@xotiko:~$ dmesg | grep CD
[    5.232000] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R6012 1331 PQ: 0 ANSI: 5
[    5.380000] Uniform CD-ROM driver Revision: 3.20
[    5.380000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  303.872000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  303.872000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  305.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  307.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  309.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  311.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  313.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  315.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  317.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  319.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  321.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  323.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  325.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  327.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  329.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  331.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  333.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  335.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  337.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  339.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  341.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  343.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  345.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  347.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  349.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  351.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  353.900000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  355.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  357.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  359.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  361.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  363.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  365.900000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  367.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  369.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  371.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  373.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  375.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  377.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  379.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  381.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  383.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  385.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1174.560000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 1174.560000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1174.564000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1176.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1178.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1180.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1182.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1184.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1186.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1188.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1190.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1192.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1194.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1196.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1198.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1200.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1202.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1204.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1206.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1208.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1210.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1212.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1214.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1216.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1218.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1220.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1222.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1224.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1226.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1228.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1230.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1232.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1234.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1236.600000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1238.608000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1240.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1242.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1244.584000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1246.592000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1248.600000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1250.608000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1252.616000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1254.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
embryo@xotiko:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=fff71f61-0ac1-41b1-8594-a10993d238a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a0606d8b-24d7-4f77-a627-9de8c08ee524 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0embryo@xotiko:~$ 

```

:(

---

### Post by klytu on 2007-06-15
> **themis said:**
> Hi to you all!
I can't either play dvd's and i'm really confused with what I've been reading.
here is what I get with commands previously asked.I would really like some help!

```

embryo@xotiko:~$ dmesg | grep CD
[    5.232000] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R6012 1331 PQ: 0 ANSI: 5
[    5.380000] Uniform CD-ROM driver Revision: 3.20
[    5.380000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  303.872000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  303.872000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  305.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  307.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  309.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  311.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  313.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  315.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  317.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  319.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  321.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  323.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  325.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  327.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  329.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  331.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  333.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  335.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  337.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  339.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  341.896000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  343.904000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  345.912000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  347.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  349.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  351.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  353.900000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  355.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  357.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  359.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  361.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  363.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  365.900000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  367.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  369.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  371.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  373.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  375.892000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  377.920000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  379.908000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  381.916000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  383.924000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[  385.888000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1174.560000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 1174.560000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1174.564000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1176.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1178.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1180.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1182.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1184.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1186.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1188.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1190.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1192.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1194.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1196.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1198.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1200.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1202.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1204.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1206.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1208.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1210.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1212.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1214.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1216.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1218.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1220.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1222.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1224.596000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1226.604000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1228.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1230.576000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1232.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1234.588000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1236.600000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1238.608000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1240.612000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1242.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1244.584000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1246.592000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1248.600000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1250.608000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1252.616000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1254.580000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
embryo@xotiko:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=fff71f61-0ac1-41b1-8594-a10993d238a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a0606d8b-24d7-4f77-a627-9de8c08ee524 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0embryo@xotiko:~$ 

```

:(

You're getting the same kind of read errors that Ricardisimo got. My guess is that the 2.6.20.16 kernel in Feisty is what is causing both of you trouble; it chokes on certain combinations of drives, controllers, and motherboards. What is the output of ```
ls -l /dev | grep cd 
```for you? Also, you could try booting with the all_generic_ide kernel option, then posting the new output of ```
dmesg | grep CD
```to see if that at least removes the read errors. I don't remember whether Ricardisimo tried that or posted back with the results in his situation ....

---

### Post by themis on 2007-06-15
Klytu,thanks for the reply.Here is what I get:

```
embryo@xotiko:~$ ls -l /dev | grep cd
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 cdrom -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 cdrw -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 dvdrw -> scd0
crw-rw-rw- 1 root tty       2, 221 2007-06-15 17:53 ptycd
brw-rw---- 1 root cdrom    11,   0 2007-06-15 17:53 scd0
crw-rw---- 1 root cdrom    21,   1 2007-06-15 17:53 sg1
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 sr0 -> scd0
crw-rw-rw- 1 root tty       3, 221 2007-06-15 17:53 ttycd

```

How can I boot with the all_generic_ide kernel option?

---

### Post by klytu on 2007-06-15
> **themis said:**
> Klytu,thanks for the reply.Here is what I get:

```
embryo@xotiko:~$ ls -l /dev | grep cd
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 cdrom -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 cdrw -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 dvd -> scd0
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 dvdrw -> scd0
crw-rw-rw- 1 root tty       2, 221 2007-06-15 17:53 ptycd
brw-rw---- 1 root cdrom    11,   0 2007-06-15 17:53 scd0
crw-rw---- 1 root cdrom    21,   1 2007-06-15 17:53 sg1
lrwxrwxrwx 1 root root           4 2007-06-15 17:54 sr0 -> scd0
crw-rw-rw- 1 root tty       3, 221 2007-06-15 17:53 ttycd

```

How can I boot with the all_generic_ide kernel option?

If you boot into Ubuntu using GRUB,  hit e to edit the boot options for Feisty before GRUB boots your kernel. Then use your arrow keys on your keyboard to highlight a line that should look something like this (your UUID will probably be different): > kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=28d7a250-3276-42d3-bbbb-a26bf02ab513 ro quiet splash Hit e again to edit this line and insert all_generic_ide like this: > kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=28d7a250-3276-42d3-bbbb-a26bf02ab513 ro **all_generic_ide** quiet splash Press enter after making the change, then hit b to boot. (The option will affect only this boot-up, the change won't be permanent). Post the output of ```
dmesg | grep CD
``` after booting, then  see if you can now mount DVDs and CDs in your drive. If this works, post back and I'll tell you how to make the change permanent.

---

### Post by themis on 2007-06-15
KLytu,it worked!!!!
Oh,I am so excited!!!
here is what you asked me for:

```
embryo@xotiko:~$ dmesg | grep CD
[  326.465110] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R6012 1331 PQ: 0 ANSI: 5
[    7.176000] Uniform CD-ROM driver Revision: 3.20
[    7.176000] sr 0:0:1:0: Attached scsi CD-ROM sr0

```


so,what's next??:D

---

### Post by themis on 2007-06-15
OH!!!!I changed a dvd,just to see what I have stored, and it's not recognisable!

and I get again:
```

embryo@xotiko:~$ dmesg | grep CD
[  326.465110] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-R6012 1331 PQ: 0 ANSI: 5
[    7.176000] Uniform CD-ROM driver Revision: 3.20
[    7.176000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[ 1457.172000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1457.204000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1459.232000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1461.192000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1463.200000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1465.208000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1467.216000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1469.224000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1471.244000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1473.196000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1475.200000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1477.280000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1479.216000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1481.224000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1483.228000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1485.192000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1487.200000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1489.208000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1491.216000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1493.224000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1495.228000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1497.196000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1499.204000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1501.212000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1503.228000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1505.228000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1507.192000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1509.196000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1511.204000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1513.212000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1515.220000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1517.228000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1519.232000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1521.196000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1523.216000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1525.216000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1527.236000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1529.232000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1531.288000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1533.252000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1535.256000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1537.264000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1539.272000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1541.280000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1543.288000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1545.252000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1547.256000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1549.264000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 1551.276000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
```

Is it because it is not permanent??hope so!

---

### Post by klytu on 2007-06-15
So when you re-booted with all_generic_ide your CD/DVD drive could mount and read discs but then you re-booted and got the errors again? Or do you mean the drive worked for the first disc, but not for another one but you didn´t re-boot in between?

---

### Post by themis on 2007-06-15
I didn't reboot in between!!
I just changed a dvd and got all the usual error messages.
Should I try to boot again with the way you told me to??

---

### Post by ricardisimo on 2007-06-16
```
:~$ uname -r
2.6.20-16-generic
```
Doesn't this mean I'm already running generic?

P.S. - AndyParka and Themis - I filed a bug report with Launchpad, Bug #120663. Please add your name to it, or modify it as you see fit. Thanks.

---

### Post by themis on 2007-06-16
> **ricardisimo said:**
> ```
:~$ uname -r
2.6.20-16-generic
```
Doesn't this mean I'm already running generic?

P.S. - AndyParka and Themis - I filed a bug report with Launchpad, Bug #120663. Please add your name to it, or modify it as you see fit. Thanks.

ricardisimo "uname" prints system information and the "-r" option stands for kernel release, so you're correct
Take a look at this:  [http://en.wikipedia.org/wiki/Uname](http://en.wikipedia.org/wiki/Uname) and your man page.

---

### Post by klytu on 2007-06-16
> **themis said:**
> I didn't reboot in between!!
I just changed a dvd and got all the usual error messages.
Should I try to boot again with the way you told me to??

Were you able to read or mount any discs before you changed the DVD? If not, then unfortunately the boot option you tried made no difference and did not solve your issue.

---

### Post by klytu on 2007-06-16
> **ricardisimo said:**
> ```
:~$ uname -r
2.6.20-16-generic
```
Doesn't this mean I'm already running generic?

P.S. - AndyParka and Themis - I filed a bug report with Launchpad, Bug #120663. Please add your name to it, or modify it as you see fit. Thanks.

You are correct that you are running the generic kernel. The all_generic_ide option forces loading of module ata_generic that can force an IDE card to work and sometimes clears up problems with IDE drives that don´t function properly with this kernel. The option does not mean that you are forcing the generic kernel to load.

---

### Post by themis on 2007-06-16
> **klytu said:**
> Were you able to read or mount any discs before you changed the DVD? If not, then unfortunately the boot option you tried made no difference and did not solve your issue.

I wasn't able to read or mount any dvd'd at anytime before I changed the dvd.BUT:

I booted again with all_generic_ide, just to check better what Have I done.
Neither of the dvd's are playing.
The first is not recognised at all.
As for the second, a desktop iccon appears,totem player starts,and some initial stuff from the film are shown(not the film), but when I ask it to play the movie,it says:
```
Please install the necessary plugins and restart Totem to be able to play this media. 
```
But I have installed every plugin I have read I need to play a dvd.

I was too excited when totem started and didn't check at first,sorry for that.
Any ideas?
thank you for your patience

---

### Post by klytu on 2007-06-16
> **themis said:**
> I wasn't able to read or mount any dvd'd at anytime before I changed the dvd.BUT:

I booted again with all_generic_ide, just to check better what Have I done.
Neither of the dvd's are playing.
The first is not recognised at all.
As for the second, a desktop iccon appears,totem player starts,and some initial stuff from the film are shown(not the film), but when I ask it to play the movie,it says:
```
Please install the necessary plugins and restart Totem to be able to play this media. 
```
But I have installed every plugin I have read I need to play a dvd.

I was too excited when totem started and didn't check at first,sorry for that.
Any ideas?
thank you for your patience

OK. Let´s see what your fstab looks like. What is the output of ```
cat /etc/fstab
``` I have a sinking feeling that you and Ricardisimo are going to have the same unsolved situation, but we can take a shot ...

---

### Post by aludlum on 2007-06-17
I think I am having the same problems as the other user you are helping.

One CD Rom give this error message: mount: special device /dev/hdc does not exist

The other gives this: mount: special device /dev/hdd does not exist

I don't seem to get a response from your first suggested command, I'm probably doing something wrong:

aludlum@aludlum-desktop:~$ dmesg | grep CD
aludlum@aludlum-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6f641667-5fdf-4ef6-997c-b6d21fba0e7a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=29a550ad-24c6-46f0-8323-fd332700b72e /media/hda3     ext3    defaults        0       2
# /dev/hda5
UUID=af76221a-1efb-4831-87b4-1540ede4ea23 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
aludlum@aludlum-desktop:~$ 

Thanks for any help, I'm certainly finding this all confusing.







> **klytu said:**
> I'll try to help. 

Please first post the output of the following commands: ```
dmesg | grep CD
```and ```
cat /etc/fstab
```You could just cut and paste the output into your reply post. Checking first  to make sure your CD drive is found by the kernel and that your fstab is set up properly to mount CD's automatically.

---

### Post by themis on 2007-06-19
> **klytu said:**
> OK. Let´s see what your fstab looks like. What is the output of ```
cat /etc/fstab
``` I have a sinking feeling that you and Ricardisimo are going to have the same unsolved situation, but we can take a shot ...

```
embryo@xotiko:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=fff71f61-0ac1-41b1-8594-a10993d238a6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a0606d8b-24d7-4f77-a627-9de8c08ee524 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by EricWiz on 2007-06-19
Hi,

So I am having the same sort of issues. I cannot get my CDROM to mount even though I used it to install Ubuntu. I put in a CD and I cannot eject it.  I get a messagebox saying cannot eject volume.

Here is my cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ae690d30-1cd5-46d3-adf8-c82f9575d88d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9e395d5b-a0a1-4f31-a111-ea1b605770d9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

If, however, I run
```
sudo mount -t iso9660 /dev/cdrom /media/cdrom0

```
I can get to the data but  
I still cannot get the cd ejected.

Lastly, 
dmesg | grep CD produces nothing.

Any help would be hugely appreciated. Sorry to have hijacked the thread. If I should start a new one instead, please let me know.

Thanks,
Eric

EDIT:
I changed my /etc/fstab from dev/hdc to dev/cdrom for the cdrom line and all is fat,dumb and happy now!! I don't know if this will help anyone else but I hope so!

---

### Post by klytu on 2007-06-20
> **themis said:**
> ```
embryo@xotiko:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=fff71f61-0ac1-41b1-8594-a10993d238a6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=a0606d8b-24d7-4f77-a627-9de8c08ee524 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
```

You could try changing this line:> /dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0 to this > /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0 and see if that helps. But honestly, from what you posted earlier, I don´t see anything wrong with your original fstab. In the unlikely event that this works, I wouldn´t be able to explain why!

---

### Post by klytu on 2007-06-20
> **aludlum said:**
> I think I am having the same problems as the other user you are helping.

One CD Rom give this error message: mount: special device /dev/hdc does not exist

The other gives this: mount: special device /dev/hdd does not exist

I don't seem to get a response from your first suggested command, I'm probably doing something wrong:

aludlum@aludlum-desktop:~$ dmesg | grep CD
aludlum@aludlum-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6f641667-5fdf-4ef6-997c-b6d21fba0e7a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=29a550ad-24c6-46f0-8323-fd332700b72e /media/hda3     ext3    defaults        0       2
# /dev/hda5
UUID=af76221a-1efb-4831-87b4-1540ede4ea23 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
aludlum@aludlum-desktop:~$ 

Thanks for any help, I'm certainly finding this all confusing.

What is the output of ```
sudo lshw
``` for you?

---

### Post by themis on 2007-06-21
> **klytu said:**
> You could try changing this line: to this  and see if that helps. But honestly, from what you posted earlier, I don´t see anything wrong with your original fstab. In the unlikely event that this works, I wouldn´t be able to explain why!

No!it tries too hard but the disk is still not mounted.
Should I switch the line back to what it was before,or not?
Is there something else I could try?
Thanks,anyway!!!!

---

### Post by klytu on 2007-06-21
> **themis said:**
> No!it tries too hard but the disk is still not mounted.
Should I switch the line back to what it was before,or not?
Is there something else I could try?
Thanks,anyway!!!!

Yes, you can just change it back. 

Unfortunately, I don´t have any other ideas you could try. Sorry, I couldn´t help you. I think the difficulties you, Ricardisimo and a lot of other people are experiencing with this is because of a bug that needs to be fixed. You might want to follow the link to the bug report filed earlier in this thread to see if a fix is ever found.

---

### Post by themis on 2007-06-21
> **klytu said:**
> Yes, you can just change it back. 

Unfortunately, I don´t have any other ideas you could try. Sorry, I couldn´t help you. I think the difficulties you, Ricardisimo and a lot of other people are experiencing with this is because of a bug that needs to be fixed. You might want to follow the link to the bug report filed earlier in this thread to see if a fix is ever found.

Thanks for the help, you've been very kind ! !
I will wait for the fix!

---

### Post by aludlum on 2007-06-22
> **klytu said:**
> What is the output of ```
sudo lshw
``` for you?

Thanks for trying to help me.  Here's what I got.  No sign of two cdrom drives.

aludlum@aludlum-desktop:~$ sudo lshw
Password:
aludlum-desktop           
    description: Desktop Computer
    product: K7SOM+
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: K7SOM+
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Slot-1
          size: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 256KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 495MB
     *-pci
          description: Host bridge
          product: 740 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: d0000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:d0000000-d3ffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
                resources: iomemory:c0000000-c7ffffff iomemory:cfee0000-cfefffff ioport:ac00-ac7f
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: ioport:c00-c1f
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE latency=128
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ff00-ff0f
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6Y060L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YAR41BW0
                   serial: Y22L7P4E
                   size: 57GB
                   capacity: 57GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 28GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 2196MB
                      capacity: 2196MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1098MB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 1098MB
                         capabilities: nofs
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 4071MB
                      capabilities: primary
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
             resources: ioport:d400-d4ff ioport:d000-d07f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: ioport:dc00-dcff ioport:d800-d87f irq:10
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffa000-cfffafff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 21.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfff9000-cfff9fff irq:12
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Storage Device
                   vendor: Generic
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi0
                   version: 1.00
                   serial: 20020509145305401
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: USB Storage-CFC
                      vendor: IC
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                 *-disk:1
                      description: SCSI Disk
                      product: USB Storage-SMC
                      vendor: IC
                      physical id: 0.0.1
                      bus info: scsi@0:0.0.1
                      logical name: /dev/sdb
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:2
                      description: SCSI Disk
                      product: USB Storage-MMC
                      vendor: IC
                      physical id: 0.0.2
                      bus info: scsi@0:0.0.2
                      logical name: /dev/sdc
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:3
                      description: SCSI Disk
                      product: USB Storage-MSC
                      vendor: IC
                      physical id: 0.0.3
                      bus info: scsi@0:0.0.3
                      logical name: /dev/sdd
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffb000-cfffbfff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth1
             version: 90
             serial: 00:0d:87:46:cc:e5
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: ioport:cc00-ccff iomemory:cfff8000-cfff8fff irq:10
aludlum@aludlum-desktop:~$

---

### Post by klytu on 2007-06-23
> Thanks for trying to help me.  Here's what I got.  No sign of two cdrom drives.

```
aludlum-desktop           
    description: Desktop Computer
    product: K7SOM+
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: K7SOM+
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Slot-1
          size: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 256KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 495MB
     *-pci
          description: Host bridge
          product: 740 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: d0000000
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:d0000000-d3ffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
                resources: iomemory:c0000000-c7ffffff iomemory:cfee0000-cfefffff ioport:ac00-ac7f
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: ioport:c00-c1f
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE latency=128
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ff00-ff0f
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6Y060L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YAR41BW0
                   serial: Y22L7P4E
                   size: 57GB
                   capacity: 57GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 28GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 2196MB
                      capacity: 2196MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1098MB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/hda6
                         capacity: 1098MB
                         capabilities: nofs
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 4071MB
                      capabilities: primary
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
             resources: ioport:d400-d4ff ioport:d000-d07f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: ioport:dc00-dcff ioport:d800-d87f irq:10
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffa000-cfffafff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 21.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfff9000-cfff9fff irq:12
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Storage Device
                   vendor: Generic
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi0
                   version: 1.00
                   serial: 20020509145305401
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: USB Storage-CFC
                      vendor: IC
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                 *-disk:1
                      description: SCSI Disk
                      product: USB Storage-SMC
                      vendor: IC
                      physical id: 0.0.1
                      bus info: scsi@0:0.0.1
                      logical name: /dev/sdb
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:2
                      description: SCSI Disk
                      product: USB Storage-MMC
                      vendor: IC
                      physical id: 0.0.2
                      bus info: scsi@0:0.0.2
                      logical name: /dev/sdc
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:3
                      description: SCSI Disk
                      product: USB Storage-MSC
                      vendor: IC
                      physical id: 0.0.3
                      bus info: scsi@0:0.0.3
                      logical name: /dev/sdd
                      version: 301b
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffb000-cfffbfff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth1
             version: 90
             serial: 00:0d:87:46:cc:e5
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: ioport:cc00-ccff iomemory:cfff8000-cfff8fff irq:10
```
That's bizarre ... but of course it makes sense that if the kernel isn't finding your CD drives, you won't be able to mount CDs. :-) How are the drives physically connected? Are they connected via USB?  Are they connected via an IDE ribbon(s)? Have they worked before and have you confirmed they still do? (with another operating system, for example)  If you recently installed the drives make sure the jumper settings on the drives are correct.  For example,  if they are both on the same IDE ribbon only one can be set to master or they could both be set for "cable select".

---

### Post by minhtrietle on 2007-08-02
I've tried so hard to work on this problem but this is what I end up with.

:confused::confused:

:mad::mad::mad:

I understand that I'm using FREE software, but I still hope that Ubuntu will do something about this supposed-to-work-out-of-the-box bug soon.

---

### Post by Arjent on 2007-08-05
I had the same problem with mounting errors, albeit not as many other problems with seeing some things and not others. I'm not sure if this solution will fix all your errors, but it fixed my cdrom mounting issues.
Try going into your boot sequence and altering the order so your cdrom boots after your hard drive.  It worked for me and a few others.

Good luck

---

### Post by Gotou on 2007-08-11
This is discouraging.

I dumped Feisty and reloaded Dapper just so I could have my cd drive back.

I need this particular computer to work and not be fubared by upgrades.

OK, I've vented.

---

### Post by ricardisimo on 2007-09-27
Is there any way to, perhaps, eavesdrop on developers' conversations to see if this is on anyone's radar? I'd love to know that Gutsy is going to resolve this issue. Thanks.

---


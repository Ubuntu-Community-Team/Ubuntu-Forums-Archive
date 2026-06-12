---
title: "Mounting: Lacie 250gb Usb2.0"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by skatedawe on 2005-08-27
Hi. The only big problem now who remain is my external hdd.

 I don't know for 100% how to mount it at the right way. It is formatted as FAT32.

 I tried to search all the threads, couldn't get it in a easy way. I have to get it to write & read.
 
 I just have to put this smilie for my last time  ](*,)

---

### Post by aysiu on 2005-08-27
I use a Lacie 160 GB USB 2.0 external hard drive, and when I turn it on, it automounts and appears as an icon on the desktop. I know that doesn't help, but at least you know something's wrong--whatever's happening to you, that's no the way it should be.

---

### Post by skatedawe on 2005-08-27
[QUOTE=aysiu]I use a Lacie 160 GB USB 2.0 external hard drive, and when I turn it on, it automounts and appears as an icon on the desktop. I know that doesn't help, but at least you know something's wrong--whatever's happening to you, that's no the way it should be.[/QUOTE]

 I know, i used gnome and it happend. When i clicked on it nautilus it frozed. Not even "killall nautilus" did work :/. Im using KDE now, don't know if it's better or worse.

 When I turn off / on the drive nothing happen.

---

### Post by skatedawe on 2005-08-27
My fstab;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hdb1       /home           reiserfs defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

 Something with  /dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0 ?   O:)

 I found this too;

 ```
root@ubuntu-main:/home/main # sudo fdisk -l

Disk /dev/hda: 82,3 GB, 82348277760 byte
255 huvuden, 63 sektorer/spår, 10011 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1   *           1        9823    78903216   83  Linux
/dev/hda2            9824       10011     1510110   82  Linux växling / Solaris

Disk /dev/hdb: 164,6 GB, 164696555520 byte
255 huvuden, 63 sektorer/spår, 20023 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdb1               1       20023   160834716   83  Linux

Disk /dev/sda: 251,0 GB, 251000193024 byte
255 huvuden, 63 sektorer/spår, 30515 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       30515   245111706    c  W95 FAT32 (LBA)
```

 How do I mount this?, it is that one. 250gb FAT32t ? 

 Disk /dev/sda

---

### Post by skatedawe on 2005-08-28
I can see it with KDE ( media:/ ) , when i click on it i'm getting in. When I click on a folder or try to open a file everything freeze. 

 Is there anything i could do?

 Anything with permissions, I dont have a clue. Plz post similar problems with forums threads.

---

### Post by skatedawe on 2005-08-29
I haven't found out any solution yet, i will try to format it again or for the first time. Because of the "pre-formation" that the company did.  :roll:  Maybe they did a less good formatoperation. See if it works after that.

---

### Post by skatedawe on 2005-08-31
I don't think i could take anymore right now. I've worked on this hdd almost a week now. I formated it to ext2, Fat32 ( i only could format it up too 200gb strange ? ), And now reiserFS.

 I can't mount it, i've tried automounting with Kde, when the pop up comes up it totaly freeze with 0%. I've tried to mount it manually but nothing happens.

 Any idéas? plz, help. This is WEARD!

---

### Post by Nequeo on 2005-08-31
This probably isn't want you want to hear... But I was never able to get any LaCie drives working with Linux at all.

Maxtor drives, on the other hand, appear almost instantly as soon as you plug them in.

One last thing that may shed some light on the situation is to type 'dmesg' about 30 seconds after you plug in your drive, and then post the result here.

Cheers,

---

### Post by Jussi Kukkonen on 2005-09-01
[QUOTE=Nequeo]This probably isn't want you want to hear... But I was never able to get any LaCie drives working with Linux at all.
[/QUOTE]

Don't get disappointed yet -- I have exactly opposite experience... I had my 160Gig LaCie working fine as NTFS, and now it's fine as EXT3. 

Here's my (pretty standard) fstab line in case you're interested:
```
/dev/sda        /media/usb     auto    rw,user,noauto  0       0
```
Unfortunately I don't have the line for NTFS mount anymore..

---

### Post by skatedawe on 2005-09-02
[QUOTE=Jussi Kukkonen]Don't get disappointed yet -- I have exactly opposite experience... I had my 160Gig LaCie working fine as NTFS, and now it's fine as EXT3. 

Here's my (pretty standard) fstab line in case you're interested:
```
/dev/sda        /media/usb     auto    rw,user,noauto  0       0
```
Unfortunately I don't have the line for NTFS mount anymore..[/QUOTE]

 thx, but i will try to sell it. 

 When you said that it worked as NTFS i realized it, I think it's to late now anyway. I've tried to format it to ReiserFS and Fat32 3 times, again and again. I looked for some kernel things who perhaps could solve my problems. I found a bug or a thing that was 1.5 year old, it have been fixed already. 

 I'm going to try to sell it to a friend of mine, if he don't want it im gonna use it as a backup hdd. Have it in my bookcase or something  :-|

 Nvm, Im giving up and will buy a new HDD internal this time. Maxtor 300gb Sata2.

 I think I feel some peace about it anyways.  :roll:

---

### Post by Vidar on 2005-09-05
I have the same identical Drive, the 250gb Lacie external USB 2.0. As far as I know, it's actually a maxtor hdd inside the casing. 

I have no problems auto-mounting, but it always mounts as Read-only, which is kind of annoying. Haven't really had time to look into this, but if someone has a clue I'd be more than thankful.

---

### Post by ubuntme on 2005-09-05
Umm, have you tried putting a line into fstab for it? or mounting it manually?

Also if the enclosure doesn't work you can always take the HD out and use it as internal.

---

### Post by Vidar on 2005-09-24
[QUOTE=ubuntme]Umm, have you tried putting a line into fstab for it? or mounting it manually?

Also if the enclosure doesn't work you can always take the HD out and use it as internal.[/QUOTE]
 Yup, solved my problem... strange thing is that initially it was automounted but it somehow broke after a couple of days of fiddling with my installation (nothing serious though, mostly just updating and configuring packages).

Here's my fstab in case somebody has a use for it (the lacie is /dev/sdb1 here):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,user_xattr,errors=remount-ro 0$/dev/hda5       none            swap    sw                      0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0
/dev/sda1       /media/sata     ext3    defaults,user_xattr     0       2
/dev/sdb1       /media/USB      ntfs    umask=0222              0       0

```

---

### Post by Jussi Kukkonen on 2005-09-24
[QUOTE=Vidar]Yup, solved my problem... strange thing is that initially it was automounted but it somehow broke after a couple of days of fiddling with my installation (nothing serious though, mostly just updating and configuring packages).

Here's my fstab in case somebody has a use for it (the lacie is /dev/sdb1 here):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,user_xattr,errors=remount-ro 0$/dev/hda5       none            swap    sw                      0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto      0       0
/dev/sda1       /media/sata     ext3    defaults,user_xattr     0       2
/dev/sdb1       /media/USB      ntfs    umask=0222              0       0

```[/QUOTE]
 It mounts as read only because it's NTFS -- you can't write to NTFS from linux.

You'll need to format it (to FAT or EXT probably) before you can write to it.

---

### Post by Vidar on 2005-09-24
[QUOTE=Jussi Kukkonen]It mounts as read only because it's NTFS -- you can't write to NTFS from linux.

You'll need to format it (to FAT or EXT probably) before you can write to it.[/QUOTE]
 Yeah, that I know. :)

Will probarbly format it as ext3 as soon as I've migrated my laptop to linux as well, then it wont need to be ntfs any longer. Also considering FAT in order to retain compatiblity if moving it to my computer at work.

---


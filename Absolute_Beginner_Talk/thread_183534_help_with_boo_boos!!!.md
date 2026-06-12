---
title: "help with boo boos!!!"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Iron_550 on 2006-05-28
ok i fianaly got my hd prob fixed after 6-8 hours of working on it but now in the mittle of ubuntu comming on theres this:
*checking all files....
fsck.ext3: NO such file or directory while trying to open /dev/hda1/dev/hda1:


the superblock could not be read or does not describe a corect ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and notswap or ufs or somthingelse), then superblock is corrupt, and you might try running e2fsck with an alternate superblock:  e2fsck:   -d 8198<device>


fsck failed plz repair manually.


any help?? thx

only had 3 houres of sleep

---

### Post by ifokkema on 2006-05-28
[QUOTE=Iron_550]*checking all files....
fsck.ext3: NO such file or directory while trying to open /dev/hda1/dev/hda1:


the superblock could not be read or does not describe a corect ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and notswap or ufs or somthingelse), then superblock is corrupt, and you might try running e2fsck with an alternate superblock:  e2fsck:   -d 8198<device>[/QUOTE]

Hi,

What command did you use? /dev/hda1/dev/hda1 is ofcourse not a valid disk. I think you made a typo.
Try:
```
sudo fsck /dev/hda1
```

Ivo

---

### Post by Iron_550 on 2006-05-28
no it really said that I am looking at it now

---

### Post by Iron_550 on 2006-05-28
for that comand -----

un able to lookup (none)via gethostbyname() 



i do not have internet on that computer yet i have dial up how do i put it on thereand fix this prob?

---

### Post by catlett on 2006-05-28
Are you in ubuntu or does this happen when you try to boot to ubuntu? Is Ubuntu on /dev/hda1? Do you have any other OSs on the drive?

---

### Post by Iron_550 on 2006-05-28
i am not in ubuntu yet it happens before i get in there wile i am booting up and not i do not have any other OSs on my drive i formated it on the install

---

### Post by ifokkema on 2006-05-28
[QUOTE=Iron_550]i am not in ubuntu yet it happens before i get in there wile i am booting up and not i do not have any other OSs on my drive i formated it on the install[/QUOTE]

OK, could you get us the output of this:
```
cat /etc/fstab
```

That may have a typo somehow.

---

### Post by Iron_550 on 2006-05-28
its mombojumbo it says somthing like: 

/etc/fstab:static file system information.

---

### Post by Iron_550 on 2006-05-28
<filesystem> <mount point>    <type>   <opions>      <dump     <pass>
     proc           proc                proc      defaulst           0         0


dev/mapper/ubuntu-root /    ext3 defaults, errors=remount-ro0
    1
/dev/hda1          /boot           ext      defaults     0     2
dev/mapper/ubuntu-swap_1 none       swap     sw             0       0
/dev/hdd          media/crom0    udf , iso960user , noauto        0     0
/dev/fd0         /media/floppy0     auto    rw, user, noato 0     0
\root@(none):`#\


thats what is says

---

### Post by ifokkema on 2006-05-28
[QUOTE=Iron_550]dev/mapper/ubuntu-root /    ext3 defaults, errors=remount-ro0
    1
/dev/hda1          /boot           ext      defaults     0     2
dev/mapper/ubuntu-swap_1 none       swap     sw             0       0
/dev/hdd          media/crom0    udf , iso960user , noauto        0     0
/dev/fd0         /media/floppy0     auto    rw, user, noato 0     0[/QUOTE]

There are some things that I've never seen in there... such as the /dev/mapper disks, but that shouldn't create your problem... 

The line starting with /dev/hda1, I assume the third column says 'ext3' or 'ext2'?

If you type in
```
mount
```
does it show a line starting with /dev/hda?

If it doesn't show such a line, what happens when you type:
```
fsck /dev/hda1
```

or
```
init 5
```

The last command should try and get the system booted up further.

---

### Post by catlett on 2006-05-28
```
/dev/hda1 /boot ext defaults 0 2
```
That is not right. The file system is not listed. It will be ext2 or ext3. It should look more like this.
```
/dev/hda1 /boot  ext2 defaults 0   2
```

---

### Post by Iron_550 on 2006-05-28
yes it showed for  cat /etc/fstab

/dev/hda1 /boot ext3 defaults 0 2



and for 

mount

/dev/mapper/ubuntu-root on / type ext3 (rw,errors=remount-or)
proc on /proc type proc (rw)
sysfs on /sys type sysfs(rw)
devpts on / dev/pts type devpts (wr, gid=5, mode=620)
tmtmpfs on /dev/shm shm type tmfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/voltile type tmpfs (rw, mode=07550)
root...

then fsck /dev/hda1

fsck 1.38 (jun 2005)
e2fsck 1.38 (jun 2005)
fsck..ext3 no such file file or directory wile trying to open /dev/hda1

the superblock could not be read or does not describe a corect ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and notswap or ufs or somthingelse), then superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck: -d 8198<device>

---

### Post by Iron_550 on 2006-05-28
it is now in a all black window where the mouse is orb and it has a little black thingys going around it and it gos back and forth to a screen that says stuff i know the last thing it says is about checking battery life? whats goin on? i can read it, it blinks too fast.

---

### Post by Iron_550 on 2006-05-28
the fsck file is not here i quess so what do i do ?

---

### Post by catlett on 2006-05-28
Do you have anything important on this drive? If not it is easier to do a fresh install than chase errors.
Do you have access to an install disk? Is it Breezy 5.10 or Dapper 6.06 If you don't have dapper but you have access to the internet with another computer, download dapper it is being released as stable on June 1st.
Hopefully another formatting of the drive during install will take care of any errors in the drive.
If you don't want to reinstall, do you have a live cd? You can run the live cd and then mout the drive or partition in question and see what happens. If it mounts open it up in a folder and see if youre ubuntu file system is there. Check your /etc/fstab to make sure you have all the partitions you want mounting correctly

---

### Post by Iron_550 on 2006-05-28
thank you so much *hugs* your now my best friend!

---

### Post by catlett on 2006-05-28
Post an update when you reinstall. Hopefully a claen install did it for you. See you in the forums.

---

### Post by Iron_550 on 2006-05-28
i am fixed i am fixed now it is saying i do not have a modem what do i do?

---

### Post by catlett on 2006-05-29
Just noticed your reply. I don't know much about modem issues because I never had any. Start by making a new thread. List as much info about your modem as you can.  Also state how you access the internet. The more info the better. I'l try and find what I can but post a new thread so people can see it's about something else and hopefully you'll get the attention of someone with modem experience.

---


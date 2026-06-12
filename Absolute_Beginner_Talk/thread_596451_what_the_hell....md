---
title: "what the hell..."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by shleyman on 2007-10-29
ok so i ahev a sony ericcson w550i and i want to be able to get music too and from my phone but when i plug it in it just says that it cannon 'mount' the phone whenever i click it.
the details say
mount_point cannont contain the following characters: newline, G_DIR_SEPERATOR (usually /)
please can you help me as im trying to get some pictures of my granmas funeral off my phone 
thanks in advance

---

### Post by shleyman on 2007-10-29
somebody please help me

---

### Post by jingo811 on 2007-10-29
Don't worry Michael Jackson to the rescue :)

What does it output when you do these 2 commands in CLI mode?  With the device plugged into the PC.
_Applications> Accessories> **Terminal**_

```
$sudo fdisk -l
```

```
$sudo df -h
```

---

### Post by shleyman on 2007-10-29
the first one gives 
```
ash@the-matrix:~$ $sudo fdisk -l

Disk /dev/sdb: 236 MB, 236781568 bytes
3 heads, 19 sectors/track, 8113 cylinders
Units = cylinders of 57 * 512 = 29184 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8112      231188+   4  FAT16 <32M
ash@the-matrix:~$
```

and the second one gives: 
```
ash@the-matrix:~$ $sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G   14G  125G  10% /
varrun                220M   92K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   72K  220M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   34M  186M  16% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             146G   14G  125G  10% /media/sda1
/dev/scd0             4.4G  4.4G     0 100% /media/NEW
ash@the-matrix:~$ 
```

---

### Post by jingo811 on 2007-10-29
That's odd and confusing :confused: did you copy and paste all output information from this command or did you censor away output info?
```
$sudo fdisk -l
```

How is your operating system and partition setup?

---

### Post by shleyman on 2007-10-29
i put everthing that i got from those commands
and about a month ago i converted form windows to feisty, completely formatting the drives and starting a fresg and it wouldnt work then and when i upgraded to gutsy i was hoping for some luck but none arrived

---

### Post by jingo811 on 2007-10-29
I'm thinking that you didn't partition things right from your Windows / Feisty stage.  Then when you upgraded from Feisty to Gutsy I'm suspecting that it made your problems twice as complicated.

I I were you I would:

[COLOR="Red"]FORGET WHAT I SUGGESTED HERE, it's not neccessary.  I re-read your posts![/COLOR]

The **fdisk** and **df** command doesn't make sense to me.  I will need a second doctors opinion before doing surgery on you.
By the way do you know how many MegaBytes your phone capacity is?

---

### Post by shleyman on 2007-10-29
256 i think 
its has an internal memory.
am i really going to have to kill my computer again?

---

### Post by shleyman on 2007-10-29
infact i got it to work once but i dont know how?
i messed with fstab once i think too

---

### Post by jingo811 on 2007-10-29
Just wait for a second opinion from somebody else on this forum before taking action!
But I must say again your outputs doesn't make sense to me :confused: You must have missed a section when you copy and pasted the fdisk command.
```
$sudo fdisk -l
```

Press **Ctrl+F10** to maximize the Terminal window and scroll it in order to make sure you got everything.

---

### Post by alienexplorers on 2007-10-29
> ash@the-matrix:~$ $sudo fdisk -l
ash@the-matrix:~$ $sudo df -h
The extra dollar sign should not be there.  Try leaving it off.

---

### Post by shleyman on 2007-10-29
yep i guarantee thats all that came up
i even screenied it. ( the reso is a bit low because i put t on my myspace...
[img]http://a905.ac-images.myspacecdn.com/images01/105/l_8e549f2a6ededd989d7f20cde03d6a48.png[/img]edit: aha
this is what i got without the extra dolla sign  

```
ash@the-matrix:~$ sudo fdisk -l
[sudo] password for ash:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19293   154970991   83  Linux
/dev/sda2           19294       19457     1317330    5  Extended
/dev/sda5           19294       19457     1317298+  82  Linux swap / Solaris

Disk /dev/sdb: 236 MB, 236781568 bytes
3 heads, 19 sectors/track, 8113 cylinders
Units = cylinders of 57 * 512 = 29184 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8112      231188+   4  FAT16 <32M
ash@the-matrix:~$ 

```

---

### Post by jingo811 on 2007-10-29
You are not supposed to insert $ :) the $ sign signifies that you're typing in CLI mode.
**WRONG**
```
$ $sudo fdisk -l
```
**CORRECT**
```
$sudo fdisk -l
```




**SHOT in the DARK**
This is a shot in the dark but try it and see if something happens.
```

$ls /media
$sudo mkdir /media/phone1
$ls /media
```

```
$sudo mount /dev/sdb1 /media/phone1
$cd /media/phone1
$ls -lh

```

[COLOR="Red"]Important[/COLOR]
When you unplug your device from Linux it's important to unmount it first on software level before doing it physically.  If you don't then you could damage the data on your phone or other external memory devices.
```
$[COLOR="Red"]sudo umount /dev/sdb1[/COLOR]
```

---

### Post by shleyman on 2007-10-29
yay i think all that worked because im onto my phone but when i try put files on it just says i dont have the permissions....

---

### Post by jingo811 on 2007-10-29
I'm not sure if I should advise this method but I'll do it anyways :KS

[B]Alt+F2
gksudo nautilus[/B]

browse to your phone1 by navigating to it GUI style.
**Filesystem > media > phone1**

You are now navigating through your Linux filesystem as ROOT which is a bad thing if you're a newbie.  Since that's the way you break things unintentionally.

---

### Post by shleyman on 2007-10-29
hell naw im not a noobie 
ive already gone through the noobie stage on my windows which is why i decided to switch for a bit of a challenge but i went in abit too head first 
so im going to unplug my phone now see if it worked...
wish me luck

---

### Post by jingo811 on 2007-10-29
Veteran Windows users are usually Newbie Linux users when they do the switch.  They are built upon 2 completely different philosophies thus no matter how much you know in Windows it won't really apply in Linux.

---

### Post by shleyman on 2007-10-29
it worked.
you guys are legends in my book.
i owe you a drink. thanks you soo much

---

### Post by jingo811 on 2007-10-29
This calls for a [victory dance]("http://youtube.com/watch?v=TtJRNyPK-lc") 	\\:D/

---

### Post by shleyman on 2007-10-29
i actually rofl

---

### Post by Crafty Kisses on 2007-10-29
> **jingo811 said:**
> Don't worry Michael Jackson to the rescue :)

That's just freaky.

---


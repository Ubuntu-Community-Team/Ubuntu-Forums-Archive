---
title: "everything was working fine and then............"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by uubuuntuu rox on 2007-07-17
hello ppl
i installed ubuntu day before yesterday with xp
n it was working fine
then i had to reinstall xp on c: from then onwards when i select ubuntu in grub it says" unable to mount partition"
when i run sudo fsck on my linux partition it says 
clean ,98942/2403744 files,584151/4801419 blocks

what should i do
 please help

---

### Post by uubuuntuu rox on 2007-07-17
hello ppl
i installed ubuntu day before yesterday with xp
n it was working fine
then i had to reinstall xp on c: from then onwards when i select ubuntu in grub it says" unable to mount partition"
when i run sudo fsck on my linux partition it says 
clean ,98942/2403744 files,584151/4801419 blocks
on all the other partitions it says 
fsck 1.40-wtp 
fsck:  fsck.ntfs/swap:not found
error 2 while executing fsck.ntfs /swap for /dev/sdax

what should i do
 please help

---

### Post by rjfioravanti on 2007-07-17
People always have problems when they install windows after ubuntu, because it clobbers stuff. Just search the forums for reinstalling grub or something

---

### Post by oilchangeguy on 2007-07-17
> **rjfioravanti said:**
> People always have problems when they install windows after ubuntu, because it clobbers stuff. Just search the forums for reinstalling grub or something

windows doesn't clobber anything. it simply overwrites grub. this is no big deal, use the live cd and you can reinstall grub.

---

### Post by uubuuntuu rox on 2007-07-17
thanx i have sarched a lot 
tried to mount that partition but to 
no avail
i am completlty new 
n dont no much about editing files n all
shold i reinstall it 
or thr is some way 
pls help
thanx again

---

### Post by rjfioravanti on 2007-07-17
> **oilchangeguy said:**
> windows doesn't clobber anything. it simply overwrites grub. this is no big deal, use the live cd and you can reinstall grub.

aren't you saying.. windows doesn't clobber anything.. it just clobbers grub?

---

### Post by uubuuntuu rox on 2007-07-17
i have installed grub using a live 
cd on mbr 
it loads properly 
but when i select ubuntu 
it says unable to mount partition
i have treid mounting my linux partiotn on /media/ubuntu
but no good

thanx for posting ppl
i was getting deprresed

---

### Post by oilchangeguy on 2007-07-17
> **rjfioravanti said:**
> aren't you saying.. windows doesn't clobber anything.. it just clobbers grub?

so windows is not designed to dual boot. big deal. this is not a major issue. certainly not cause to slam an os. this forum is not a windows bashing forum, or any other os. if you can offer advice to a new ubuntu user, great. but don't slam another os. there's no reason for it.

---

### Post by rjfioravanti on 2007-07-17
Put in live CD and start the GParted partition editor to see what your partitions look like now

It should be in System -> Administration

---

### Post by rjfioravanti on 2007-07-17
> **oilchangeguy said:**
> so windows is not designed to dual boot. big deal. this is not a major issue. certainly not cause to slam an os. this forum is not a windows bashing forum, or any other os. if you can offer advice to a new ubuntu user, great. but don't slam another os. there's no reason for it.

im not slamming it. I pointed out the fact that when you install it second it clobbers grub. Sorry i said stuff instead of grub, I didn't think someone was going to jump all over me

---

### Post by pebo on 2007-07-17
Yeah well I think the guy was asking for help, so here's [a link]("http://ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+grub"). Once you are back in ubuntu you will need to add an entry for windows - but one thing at a time! HTH

---

### Post by uubuuntuu rox on 2007-07-17
thanx 
it says
partiton     filesysytem                                       size                used           unused        flags
/dev/sda1   ntfs                                              39.o6 gb       4.95gb       34.47 gb      boot
    /dev/sda2   extended with a lock sign on it      109.98gb        ---             ---                lba
   /dev/sda5 ntfs            ................................................................................                                        
  /dev/sda6  ntfs         ...................................................................................
  /dev/sda7  ext3                                                 18.32gb           65.50mb          31.08gb   boot
  /dev/sda8   linux-swap   ...............................................................................
/dev/sda9   ntfs      ........................................................................................
dots indicated just general information

---

### Post by dptxp on 2007-07-17
Windows is installed first.
Reinstall Ubuntu in 40 minutes and save time.

---

### Post by rjfioravanti on 2007-07-17
is it a problem that he has 8 partitions?

---

### Post by ajgreeny on 2007-07-17
> is it a problem that he has 8 partitions?
Could be because you can only have 4 primary partitions on a disk, though you can have logical partitions in an extended partition, rather like ubuntu always puts the swap partition in an extended partition.  Having so many just makes things more difficult but not impossible if they are organised properly.

---

### Post by Rui Pais on 2007-07-17
> **uubuuntuu rox said:**
> thanx 
it says
partiton     filesysytem                                       size                used           unused        flags
/dev/sda1   ntfs                                              39.o6 gb       4.95gb       34.47 gb      boot
    /dev/sda2   extended with a lock sign on it      109.98gb        ---             ---                lba
   /dev/sda5 ntfs            ................................................................................                                        
  /dev/sda6  ntfs         ...................................................................................
  /dev/sda7  ext3                                                 18.32gb           65.50mb          31.08gb   boot
  /dev/sda8   linux-swap   ...............................................................................
/dev/sda9   ntfs      ........................................................................................
dots indicated just general information
Hi,
using your liveCD, if you do:
```
mkdir sda7
sudo mount /dev/sda7 sda7

```
whats the output?
If it mounts ok, post the output of:
```
cat sda7/etc/fstab
```
and 
```
blkid 
```
please.

---


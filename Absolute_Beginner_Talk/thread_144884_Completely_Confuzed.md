---
title: "Completely Confuzed"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by -=Raven=- on 2006-03-15
Hi all,

Im a complete beginner to linux and ubuntu and im seeking some help regarding NTFS + Linux. Ive got a 120 gb HDD, partitioned into 3 drives. I have windows on one, My shares on the other and ubuntu on the third. The only problem im having at the minute is getting my music off my shares HDD. Is it possible to just copy the music over using ubuntu? Please dont tell me that ive got to copy all 70 gig to cds.

Cheers all

-=Raven=-

---

### Post by Darkriser on 2006-03-15
suppose you have your ntfs partition on /dev/hda1:

umount /dev/hda1

mkdir /media/win (use WHATEVER instead of "win")

sudo mount /dev/hda1 /media/win -t ntfs -o nls=utf8,umask=0222

enter your password

cd /media/win

dir

welcome to your ntfs partition \\:D/

---

### Post by Darkriser on 2006-03-15
[QUOTE=Darkriser]
umount /dev/hda1

mkdir /media/win (use WHATEVER instead of "win")
[/QUOTE]

hmmm...edit:
sudo umount /dev/hda1
enter your password

sudo mkdir /media/win (use WHATEVER instead of "win")
enter your password

---

### Post by -=Raven=- on 2006-03-15
ok thats cool, now can you explain it in english please lol

Please remember i know virtually nothing about linux

---

### Post by chimera on 2006-03-15
[QUOTE=-=Raven=-]ok thats cool, now can you explain it in english please lol

Please remember i know virtually nothing about linux[/QUOTE]

you write those commands in the terminal, which you can access in the applications->accesories menu

---

### Post by -=Raven=- on 2006-03-15
Do i have to type that in the terminal? if so i keeps shouting at me and telling me i cant do stuff. Permission Denied

---

### Post by chimera on 2006-03-15
[QUOTE=-=Raven=-]Do i have to type that in the terminal? if so i keeps shouting at me and telling me i cant do stuff. Permission Denied[/QUOTE]

than add "sudo " in front of the command. You will be prompted for your user password (the one you entered during the installation), which you must then write and press enter.

---

### Post by -=Raven=- on 2006-03-15
Ok done that, now its saying /dev/hda1 not found

---

### Post by Darkriser on 2006-03-15
like chimera said...:mrgreen: 

once you are in your ntfs partition, you can use "cp" command to copy files from ntfs to your linux partition. i recommend creating a directory in "~" directory, which means your HOME directory (very similar to "My Documents" under Windows), e.g. mkdir ~/music (note: "~" is a shortcut for /home/<your_username> directory).

aaah...if having problem with any command in linux, use "<command> --help" or "man <command>" in console. you'll get some help about the <command>.

---

### Post by -=Raven=- on 2006-03-15
[QUOTE=-=Raven=-]Ok done that, now its saying /dev/hda1 not found[/QUOTE]
it wont find it

---

### Post by Darkriser on 2006-03-15
[QUOTE=-=Raven=-]Ok done that, now its saying /dev/hda1 not found[/QUOTE]

you have 1 physical hard drive?
if so, try using /dev/hds1, instead of /dev/hda1

oh....and where is your share partition located? if not first on the disk, modify the command above (e.g. /dev/hds2, etc.)

---

### Post by Darkriser on 2006-03-15
sorry, i'm idiot :oops: 

for IDE drives use :
/dev/hda1 (disk 1, partition 1)
/dev/hda2 (disk 1, partition 2)
/dev/hdb1 (disk 2, partition 1)
etc.

for SCSI drives use:
/dev/sda1 (disk 1, partition 1)
/dev/sda2 (disk 1, partition 2)
/dev/sdb1 (disk 2, partition 1)

sorry again....

---

### Post by -=Raven=- on 2006-03-15
It wont let me do anything, it keeps saying that /dev/hda1 is not found. Please help, im pulling my hair out and going crazy trying to get my music

---

### Post by -=Raven=- on 2006-03-15
lol dont worry about it darkriser. Still though, its not working. Is there remote assistance or something in ubuntu because im going put a hammer through my monitor soon. Ive been at this since 8am this morning. its now 2pm lol........ crazy.
Im typing in:

sudo umount /dev/hda1 (ive tryed hda2 and got the same)

it then says:

umount /dev/hda1 not found etc..

---

### Post by Darkriser on 2006-03-15
do you have any icons (like hard drives) on your desktop (upper left area) ?

---

### Post by -=Raven=- on 2006-03-15
ok im a step futher lol.

Now it says /dev/hdb2 not mounted.

When i tryed the mkdir /media/win it says permission denied.

---

### Post by -=Raven=- on 2006-03-15
[QUOTE=Darkriser]do you have any icons (like hard drives) on your desktop (upper left area) ?[/QUOTE]

only a Audio cd icon and a screenshot i took.

---

### Post by Darkriser on 2006-03-15
first:
use "sudo mkdir /media/win", instead of "mkdir /media/win" only

second:
do you have ide or scsi hard drive?
what partitions do you have on it? what is on partition 1, 2 and 3?

---

### Post by -=Raven=- on 2006-03-15
[QUOTE=Darkriser]first:
use "sudo mkdir /media/win", instead of "mkdir /media/win" only

second:
do you have ide or scsi hard drive?
what partitions do you have on it? what is on partition 1, 2 and 3?[/QUOTE]


First one is done. That worked.

Second, there is 3 partitions, i think my music is on the 2nd. in windows i had C with windows on it, D with my music + shares + stuff and E i formatted and used it for ubuntu.

---

### Post by meborc on 2006-03-15
for ubuntu dual-boot/mounting issues check:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

&

[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

those are a good read even if you already got things going...
good luck

---

### Post by Darkriser on 2006-03-15
ok, if you have IDE disk, try
sudo mount /dev/hda2 /media/win -t ntfs -o nls=utf8,umask=0222

and if you have SCSI disk, try
sudo mount /dev/sda2 /media/win -t ntfs -o nls=utf8,umask=0222

you can eventually try both of them, if unsure....nevermind, you just get some errors, post them, pls.

---

### Post by mozetti on 2006-03-15
Ok, so now you need to type
```
sudo mount /dev/hdb2 /media/win -t ntfs -o nls=utf8,umask=0222
```

What that does it tell Ubuntu that you want your 2nd partition to be mounted in your /media/win directory.

****NOTE** - Linux cannot write to NTFS successfully. Attempting to do this could corrupt your partiton. Don't try to save/modify/create files on any NTFS partitoins. Linux can read NTFS fine, but not write.**

---

### Post by Darkriser on 2006-03-15
[QUOTE=mozetti]Ok, so now you need to type
```
sudo mount /dev/hdb2 /media/win -t ntfs -o nls=utf8,umask=0222
```

What that does it tell Ubuntu that you want your 2nd partition to be mounted in your /media/win directory.

****NOTE** - Linux cannot write to NTFS successfully. Attempting to do this could corrupt your partiton. Don't try to save/modify/create files on any NTFS partitoins. Linux can read NTFS fine, but not write.**[/QUOTE]


WHY /dev/hdb2??? this points to SECOND hard drive....but he has only ONE....therefore should use /dev/hda2 od /dev/sda2!!!

---

### Post by -=Raven=- on 2006-03-15
Ok, i did that and got this:

raven@viper:~$ sudo mount /dev/hdb2 /media/win -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by -=Raven=- on 2006-03-15
[QUOTE=Darkriser]WHY /dev/hdb2??? this points to SECOND hard drive....but he has only ONE....therefore should use /dev/hda2 od /dev/sda2!!![/QUOTE]


Oh god im so sorry, i feel like such a fool now ive realized..... my hdd is set as a slave, i ment to change it months ago :cry: :cry: :cry:  god i feel like such a ejit lol

---

### Post by Darkriser on 2006-03-15
nobody's perfect....don't worry [-( 

ok...did you happen to advance ?

---

### Post by -=Raven=- on 2006-03-15
no, it says this now

raven@viper:~$ sudo mount /dev/hdb2 /media/win -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by meborc on 2006-03-15
still suggest you take a look at those links i posted in the previous page ;)

---

### Post by Darkriser on 2006-03-15
are you sure the filesystem on that partition was NTFS? wasn't there FAT32 used, instead?

in such case try:
sudo mount /dev/hda1 /media/partitionname -t vfat -o iocharset=utf8,umask=000

---

### Post by Darkriser on 2006-03-15
[QUOTE=meborc]still suggest you take a look at those links i posted in the previous page ;)[/QUOTE]

=D>

---

### Post by -=Raven=- on 2006-03-15
Ok, im sure its NTFS. I tryed that tho darkriser and got this...


raven@viper:~$ sudo mount /dev/hdb1 /media/win -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by mozetti on 2006-03-15
[QUOTE=Darkriser]WHY /dev/hdb2??? this points to SECOND hard drive....but he has only ONE....therefore should use /dev/hda2 od /dev/sda2!!![/QUOTE]

Yeah, i was just going off the info he provided. He said he had success unmounting hdb2 -- so, that's the one I used.

---

### Post by -=Raven=- on 2006-03-15
Cant i do this like, without typing it into the terminal? like in the file system or something?

---

### Post by Darkriser on 2006-03-15
[QUOTE=-=Raven=-]Cant i do this like, without typing it into the terminal? like in the file system or something?[/QUOTE]

well, some drives are mounted on start-up automatically (defined in /etc/fsstab file), but external partitions (like windows, etc) are accessible only for root, not for ordinary users (and you ARE an ordinary user).

---

### Post by -=Raven=- on 2006-03-15
feel like such a dumbass....... all i want is my music

---

### Post by Darkriser on 2006-03-15
try reading those links posted by meborc, maybe it helps. i don't have ubuntu here at work, so can't do much investigation :cry:

---

### Post by -=Raven=- on 2006-03-15
ok mate, thank you for your help :KS . i would be bald with out it :)

---

### Post by -=Raven=- on 2006-03-15
Ok, after looking at one of those sites i think i might have messed up during the installation. I deleted the empty partition and created a new one, i cant remember what file system it used. Does this matter?

---

### Post by -=Raven=- on 2006-03-15
Its all ok!!!! !its done now, i went into the ubuntu setup and found out that my shares hdd was hdb5!!!! its done now anyway lol thanks for the help everyone:mrgreen:

---

### Post by chimera on 2006-03-15
Well that took a long time, glad you got it working now\\:D/

---


---
title: "adding ubuntu to osx/windows dual boot, to make triple boot"
date: 2007-07-06
forum: Apple Intel Users
---

### Post by ryan86corolla on 2007-07-06
i am thinking i can just resize my windows partition and add ubuntu as a third boot option. i have right now os x and a 32gb windows xp partition, set up using bootcamp. will i still be able to boot windows when i resize that partition and install ubuntu? i'm on a first gen black macbook.
thanks in advance.

---

### Post by gahau on 2007-07-06
man i had the same question has you! read my post should be a couple one dawn, the one that mention a lost noob

---

### Post by thefockinfury on 2007-07-06
i, too, am sort of a noob so my answer will probably be half-baked. i'll leave it to the heavyweights around here to provide the nitty gritty.

windows needs to be the last partition on your drive otherwise it gets confused when it boots. so resizing your windows partition wont work because you would need to resize the front of your partition upwards instead of the back of your partition downwards... and i'm pretty sure you can't do that (if there's a utility out there that can do that, let me know about it too! :p). what you could do instead is resize your OSX partition downwards to create a linux partition at the end of it, between OSX and windows. you would use the diskutil resizeVolume command. it's so secret that its not even in the man pages for diskutil, but if you type 'diskutil resizeVolume' in the terminal you'll get info on its syntax and usage. it would be something like:

sudo diskutil resizeVolume disk0s2 [new OSX size] [linux partition format] [linux partition name] [linux partition size]

hope that helps

edit: one thing to look into would be whether resizing your OSX partition would mess up the partitions that come after it on the drive. hopefully someone else will know more about that than me!

---

### Post by gahau on 2007-07-06
ok here is what i found out
use refit
found here
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
and here is a post from another forum that was pretty usefull... havent tested yet
[http://forum.onmac.net/showthread.php?t=2705](http://forum.onmac.net/showthread.php?t=2705)

---

### Post by thefockinfury on 2007-07-06
bah, i didn't mention rEFIt. yeah, you may or may not need to download and install rEFIt depending on what version of ubuntu you're installing and how nifty you want your bootup process to look (rEFIt is a cool little interface)

here's the source i used the most when setting up my triple boot:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

this one is also REALLY helpful as supplementary information and for more information specific to feisty:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) 

notice that according to that second link you don't need to install rEFIt if you're installing feisty. GRUB handles the booting instead. i kind of glossed over this section because i already had rEFIt installed from a previous attempt at setting up a triple boot, and it still worked fine. selecting OSX on the rEFIt screen takes you straight to OSX while selecting windows or linux takes you to the GRUB bootloader where you select windows or linux from there. a minor annoyance but hey whatever. 

sorry i didn't give the whole story earlier!

---

### Post by gahau on 2007-07-06
okok here is what i am planning to do
i am considering the option with refit...
i have mac osx with bootcamp i think it like 60gb and 10gb
i was woundering in i lunch refit right now will it just create another partition with the primary one (60, where i run mac osx) or i will have to reformat everything and therefore have to back up all my data etc etc (i really dont wanna do)

---

### Post by grim1234 on 2007-07-06
> **gahau said:**
> okok here is what i am planning to do
i am considering the option with refit...
i have mac osx with bootcamp i think it like 60gb and 10gb
i was woundering in i lunch refit right now will it just create another partition with the primary one (60, where i run mac osx) or i will have to reformat everything and therefore have to back up all my data etc etc (i really dont wanna do)

If you have 60gb osx hfs and 10gb ntfs with bootcamp I would resize the osx hfs drive to give you space for linux, use the info in the link above to do this.

Then boot from the ubuntu cd and create a ext3 filesystem in the free space using manual partitioning (don't choose automatic partitioning  :p  ). Don't create a swap partition (it will complain about performance), because if you do you will have more than 4 partitions, which can cause problems for refit. 

After you have installed ubuntu download and install refit using the refit mpkg on their website. 

You should have 4 partitions, 

1.EFI ~200mb
2. HFS+ - OSX
3. ext3 linux
4. ntfs xp

The refit bootloader will let you choose between the three all going well.

---

### Post by ryan86corolla on 2007-07-06
i decided to resize my os x partition to make room for ubuntu. here's what i did in terminal.app:

```
sudo diskutil resizeVolume disk0s2 55G
```

disk0s2 was the os x partition of my internal hd, and i resized it from it's previous size of about 62gb. i haven't tried to boot windows (now the last partition on that drive, apparently still 32gb) yet, but disk utility now says i have an os x partition of 55gb, some free space, and last the 32gb windows partition created previously with boot camp. i plan to format and use the free space with the feisty live cd. i'll report back once i see how it goes.

also, i don't plan to use refit - holding down option during bootup gives you an option of all bootable things the computer sees - external hard drives, cds, etc. i plan to use this built in feature rather than refit. to each his own.

---

### Post by gahau on 2007-07-06
humm ok
i have read the articles...
is there someone that would be generous enought to explain me in a noob understandable maneer so i can finaly do this?

how to rezise my drive! that have allready osx on it and also xp from bootcamp

---

### Post by cyberdork33 on 2007-07-06
> **gahau said:**
> humm ok
i have read the articles...
is there someone that would be generous enought to explain me in a noob understandable maneer so i can finaly do this?

how to rezise my drive! that have allready osx on it and also xp from bootcamp

He gives the answer to this exactly in the post before yours

---

### Post by gahau on 2007-07-06
this is the anwser???

i decided to resize my os x partition to make room for ubuntu. here's what i did in terminal.app:

Code:

sudo diskutil resizeVolume disk0s2 55G

disk0s2 was the os x partition of my internal hd, and i resized it from it's previous size of about 62gb. i haven't tried to boot windows (now the last partition on that drive, apparently still 32gb) yet, but disk utility now says i have an os x partition of 55gb, some free space, and last the 32gb windows partition created previously with boot camp. i plan to format and use the free space with the feisty live cd. i'll report back once i see how it goes.

also, i don't plan to use refit - holding down option during bootup gives you an option of all bootable things the computer sees - external hard drives, cds, etc. i plan to use this built in feature rather than refit. to each his own.

i mean its that easy? trying to find the terminal type in the cmd... and that is it?

when does refit and ubuntu come in play?

sorry still noob

---

### Post by cyberdork33 on 2007-07-06
OK, I know you really want to get it right, but you are going a little overboard. The How to triple boot thread exists for a reason. It shows you what you HAVE to do to get a triple boot system. Please follow the guide as there is no reason to post the same information over and over.
[http://ubuntuforums.org/showthread.php?t=384449](http://ubuntuforums.org/showthread.php?t=384449)

The command you quoted (and gave no indication that it was a quote, which made it kind of difficult to read), is one you can use to make the OSX partition smaller. The exact command posted will resize the second partition on your main disk to 55 GB (as is noted by the 55G at the end). If you want to make it something different than that, then change that number (and possibly the disk. I have already told you how to check the disk and partition that you want to resize using 'diskutil list').

After you resize your OSX partittion, you can boot from the Ubuntu CD and install it in the free space you created.

I don't mean to sound rude, but this is really not that difficult, and if this is too difficult for you then you may not want to install Ubuntu at all. If you want to try it out, you could also just run Ubuntu in a Virtual Machine. VMware or parallels both will run Ubuntu.

rEFIt is not a must. It just gives you a nice interface to choose which OS to boot. See the rEFIt website:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by gahau on 2007-07-06
not at all not offense taken!
i am actualy glad that u replied =)
but hey i might not know a whole lot now but i am willing to learn and try :p

---

### Post by gahau on 2007-07-06
ok i have actualy tried the cmd
sudo diskutil resizeVolume disk0s2 54G
with my journal enable or disable
i get this error message
Resizing encountered error The underlying task reported failure on exist (-9972) on disk disk0s2 Macintosh HD...

Stuck

---

### Post by cyberdork33 on 2007-07-06
I found this:
> The resizeVolume command occasionally fails. If it encounters any disk problems, it will stop, and you&#8217;ll need to run Disk Utility or another disk-maintenance program. If you have any system or special metadata files&#8212;which can&#8217;t be moved&#8212;in the section of your partition that you wish to reallocate, the command will also fail. Unfortunately, the error messages won&#8217;t go into any detail.
[http://www.macworld.com/2007/02/secrets/marchgeekfactor/index.php](http://www.macworld.com/2007/02/secrets/marchgeekfactor/index.php)

Also on that page it states that you need to have a journaled filesystem. I would read through that entire page just to make sure you are doing everything correctly.

---

### Post by gahau on 2007-07-07
arggg dang it what am i doing wrong?!
i have finaly got rid of that error msg (minor repairs was needed)
but now i get this

Gahau-Liang:~ Gahau$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *74.5 GB  disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       64.0 GB   disk0s2
   3:   Microsoft Basic Data Untitled           10.2 GB   disk0s3
Gahau-Liang:~ Gahau$ diskutil resizeVolume /dev/disk0s2 55G Linux Linux 9GStarted resizing on disk disk0s2 Macintosh HD
Verifying
Resizing Volume

Resizing encountered error No space left on device (28) on disk disk0s2 Macintosh HD
Gahau-Liang:~ Gahau$ 

...help

and i try several other cmd!
the sudo diskutil resizeVolume and other ones similar...

arg

---

### Post by gahau on 2007-07-07
Resizing encountered error No space left on device (28 ) on disk disk0s2 Macintosh HD
Gahau-Liang:~ Gahau$

---

### Post by cyberdork33 on 2007-07-07
just try shrinking the hfs partition without creating the linux partition.

---

### Post by gahau on 2007-07-07
witch cmd was that again?
because i have tried 
sudo diskutil resizeVolume disk0s2 <enter here new size>
it gave me somekind of error msg no space available...

---

### Post by ryan86corolla on 2007-07-07
i successfully shrunk my os x partition with diskutil to make room for an ubuntu partitoin, which i created with the livecd and installed. however, though os x and ubuntu boot fine, somehow the ubuntu partition, though physically created in the free space between my os x and windows partition, shows up after the windows partition in disk utility now...and windows won't boot now. do you think it's because windows doesn't see itself as the last partition? when i try to boot it says it can't find hal.dll, reinstall windows. i am pretty sure if i get rid of the ubuntu partition using the livecd, even with the free space still there i'll be able to boot both windows and os x fine again, since there will be only two partitions (besides the efi partition) like the standard boot camp setup; i don't think it cares about free space betweent hem, i'll just have a few wasted gbs of hd space.

---

### Post by cyberdork33 on 2007-07-07
> **ryan86corolla said:**
>  do you think it's because windows doesn't see itself as the last partition?

yep, idk why it sees itself that way, but that is likely the issue

---

### Post by ryan86corolla on 2007-07-08
ok, i removed the ubuntu partition, but grub is still there. when i pick windows when booting up, a grub command line comes up, and i'm not sure how to get into windows from there. can i get rid of grub and restore mbr to the way boot camp had it without reformatting?

---

### Post by ryan86corolla on 2007-07-08
ok, i got rid of grub using the xp install cd. i booted into windows via the install cd, pressed 'r' for recovery mode, logged into my windows install, and typed 'fixmbr' at the cmd prompt. i now have windows booting natively and in parallels just fine, as well as os x still working normally. so lesson learned: since disk0s1, disk0s2, and disk0s3 are taken, another partition will be disk0s4 which makes windows angry (unbootable). so unless i can somehow change partition numbers, no matter where the partition lies on the disk, it will always be "after" the windows partition since it was created later. so this disk will stay dual boot. thanks for the help everyone.

---


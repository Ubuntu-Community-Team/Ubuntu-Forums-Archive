---
title: "Dual Boot - menu.lst not found"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-10-29
Hi guys,

i am unable to do dual booting of Win XP & Gutsy 7.10.
First my system Specs - Pentium D(64bit) 3GHz, 1GB RAM, 160GB SATA hdd (Win XP), 40GB IDE hdd (Gutsy 7.10). 

my SATA hdd of 160Gb has Win XP loaded on two separate partitions, both loaded before loading Ubuntu Gutsy 7.10.
My IDE hdd of 40Gb hdd has gutsy 7.10 (64bit).

i [COLOR="Blue"]tried [/COLOR]booting from [COLOR="Blue"]Super Grub Cd also[/COLOR] but to no avail. i got the options of Linux but it did not boot and said [COLOR="Red"]menu.lst file not found [/COLOR]and gave error 15. 

Output of [COLOR="Blue"]sudo fdisk -lu [/COLOR]is as follows:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40634062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155   266373764   107587305    f  W95 Ext'd (LBA)
/dev/sdb3       266373765   312560639    23093437+   7  HPFS/NTFS
/dev/sdb5        51199218   133114589    40957686    7  HPFS/NTFS
/dev/sdb6       133114653   215030024    40957686    7  HPFS/NTFS
/dev/sdb7       215030088   264285314    24627613+   7  HPFS/NTFS
/dev/sdb8       264285378   266373764     1044193+   e  W95 FAT16 (LBA)

regards

---

### Post by averagebeatboy on 2007-10-29
The dreaded Error 15 I have had that one before.  There are others on the board who can be of more help with it than I can to you, Sandy.  Lucky for you that you have the disk it might save your system and always always back up the Grub!
If you have backed it up retrieval is easy for someone more experienced than I on the board.  There is the command for either making a copy of Grub or executing the copy you made of Grub.  Never let a newbie give advice!  When you get this 15 Error fixed write down this command and use it all the time!

Boot into Linux:
Type sudo gedit /boot/grub/menu.1st/boot/grub/menu.1st copy

---

### Post by Pumalite on 2007-10-29
Have you tried inverting the boot order of your hard drives in BIOS?

---

### Post by sandysandy on 2007-10-29
> **Pumalite said:**
> Have you tried inverting the boot order of your hard drives in BIOS?

just inverted the boot order of hdd and rebooted. No joy.
in booting options after re-booting, i only get Win Xp and not Ubuntu.
its only with super grub disk that linux is detected but when trying to boot it said menu.lst file not found and gave error 15.

regards

---

### Post by Pumalite on 2007-10-29
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Boot your Live CD mount your drives/partitions, find menu list and post it. If you don't know how to mount your partitions, get a Knoppix Live CD (it mount all your drives/partitions automatically): [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
In Knoppix you are 'root' so you have access to all your files. The command at the Terminal is: cat /boot/grub/menu.lst

---

### Post by sandysandy on 2007-10-29
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Boot your Live CD mount your drives/partitions, find menu list and post it. If you don't know how to mount your partitions, get a Knoppix Live CD (it mount all your drives/partitions automatically): [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
In Knoppix you are 'root' so you have access to all your files. The command at the Terminal is: cat /boot/grub/menu.lst

mounted the drive with live cd.
the [COLOR="Blue"]menu.lst file[/COLOR] is as follows:-

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader	+1

thanx

---

### Post by meierfra on 2007-10-29
You said you get error 15 with super grub. But what happens  when you boot regularly?

Does the grub menu appear?  Do you get any error message?

---

### Post by sandysandy on 2007-10-29
> **meierfra said:**
> You said you get error 15 with super grub. But what happens  when you boot regularly?

Does the grub menu appear?  Do you get any error message?

when i boot normally, the GRUB menu does not appear.
on booting i only get options for Windows XP. I do not get options for Linux at all.

regards

---

### Post by meierfra on 2007-10-29
Do you get the same  behavior regardless whether you boot from the Sata or the IDE drive?

---

### Post by meierfra on 2007-10-29
Do 

```
sudo grub
```

and then at the grub prompt:

```

find /boot/grub/stage1
```

Post the output.

---

### Post by sandysandy on 2007-10-30
> **meierfra said:**
> Do 

```
sudo grub
```

and then at the grub prompt:

```

find /boot/grub/stage1
```

Post the output.

the output is as follows:-

grub> find /boot/grub/stage1
find /boot/grub/stage1
 [COLOR="Blue"](hd0,0)[/COLOR]

regards

---

### Post by sandysandy on 2007-10-30
> **meierfra said:**
> Do you get the same  behavior regardless whether you boot from the Sata or the IDE drive?

thats right,
the behavior is the same regardless of whether the booting sequence is set first to IDE or SATA. in both cases only windows xp boots.

regards

---

### Post by meierfra on 2007-10-31
It looks like Grub never got installed.  To install grub to the MBR of the IDE, 
type the following in a terminal  (with the IDE still first in the boot order)

sudo grub 

and at the grub prompt:

root (hd0,0)

setup (hd0)

quit

Reboot   and you should get the Grub Menu.

---

### Post by sandysandy on 2007-10-31
> **meierfra said:**
> It looks like Grub never got installed.  To install grub to the MBR of the IDE, 
type the following in a terminal  (with the IDE still first in the boot order)

sudo grub 

and at the grub prompt:

root (hd0,0)

setup (hd0)

quit

Reboot   and you should get the Grub Menu.
i have re-installed grub as follows and will reboot now:-
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 

regards

---

### Post by sandysandy on 2007-10-31
> **meierfra said:**
> It looks like Grub never got installed.  To install grub to the MBR of the IDE, 
type the following in a terminal  (with the IDE still first in the boot order)

sudo grub 

and at the grub prompt:

root (hd0,0)

setup (hd0)

quit

Reboot   and you should get the Grub Menu.

i rebooted after reinstalling grub.
No joy. the same win XP comes in the boot options. IDE is still first in booting option.

regards

---

### Post by adrian15 on 2007-10-31
> **sandysandy said:**
> i rebooted after reinstalling grub.
No joy. the same win XP comes in the boot options. IDE is still first in booting option.

regards

1) Are you using 0.9667 version of SGD ?

2) One thing I do not understand is why no menu.lst is found while from the live cd you can see it.

Typing 'c' and:

find /boot/grub/menu.lst

or 

find /grub/menu.lst

does it give you any output?

3) cat (hd0,0)/
and then pressing the <TAB> key does it prompts an error?

4) What do you see when you go to Boot & Tools -> Show Partitions

Do you see one or two hard disks? If you select the hd0 one do you see windows hard disk or do you see the linux hard disk? And if you select hd1? (Note: If you press enter on a partition you come back to the former menu).

5) Depending on what you say here I will ask you to try a new command called liveswap which I have developed which could solve strange configurations as yours.

6) His configuration is strange because when it boots from hard disk "A Hard Disk" is the first one and "B Hard Disk" is the second one. However when he boots from cdrom "A Hard Disk" becomes the second hard disk and "B Hard Disk" becomes the first one. Well... That's bet. We know have to check his answers to my questions.

It seems that I should speed the development of liveswap option menues (currently it is only a command-line command).

Waiting for your answers.

adrian15

---

### Post by sandysandy on 2007-10-31
> **adrian15 said:**
> 1) Are you using 0.9667 version of SGD ?

2) One thing I do not understand is why no menu.lst is found while from the live cd you can see it.

Typing 'c' and:

find /boot/grub/menu.lst

or 

find /grub/menu.lst

does it give you any output?

3) cat (hd0,0)/
and then pressing the <TAB> key does it prompts an error?

4) What do you see when you go to Boot & Tools -> Show Partitions

Do you see one or two hard disks? If you select the hd0 one do you see windows hard disk or do you see the linux hard disk? And if you select hd1? (Note: If you press enter on a partition you come back to the former menu).

5) Depending on what you say here I will ask you to try a new command called liveswap which I have developed which could solve strange configurations as yours.

6) His configuration is strange because when it boots from hard disk "A Hard Disk" is the first one and "B Hard Disk" is the second one. However when he boots from cdrom "A Hard Disk" becomes the second hard disk and "B Hard Disk" becomes the first one. Well... That's bet. We know have to check his answers to my questions.

It seems that I should speed the development of liveswap option menues (currently it is only a command-line command).

Waiting for your answers.

adrian15

thanx for your interest

with respect to sl 2 & 3 the [COLOR="Blue"]output [/COLOR]is as follows:-

grub> cat (hd0,0)/
cat (hd0,0)/

Error 15: File not found
grub> c
c

Error 27: Unrecognized command
grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
 (hd0,0)
grub> 

how do you check sl 1 & 4

1) Are you using 0.9667 version of SGD ?
4) What do you see when you go to Boot & Tools -> Show Partitions

regards

---

### Post by Pumalite on 2007-10-31
This might help (not sure):

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by sandysandy on 2007-10-31
> **adrian15 said:**
> 1) Are you using 0.9667 version of SGD ?

2) One thing I do not understand is why no menu.lst is found while from the live cd you can see it.

Typing 'c' and:

find /boot/grub/menu.lst

or 

find /grub/menu.lst


does it give you any output?

3) cat (hd0,0)/
and then pressing the <TAB> key does it prompts an error?

4) What do you see when you go to Boot & Tools -> Show Partitions

Do you see one or two hard disks? If you select the hd0 one do you see windows hard disk or do you see the linux hard disk? And if you select hd1? (Note: If you press enter on a partition you come back to the former menu).

5) Depending on what you say here I will ask you to try a new command called liveswap which I have developed which could solve strange configurations as yours.

6) His configuration is strange because when it boots from hard disk "A Hard Disk" is the first one and "B Hard Disk" is the second one. However when he boots from cdrom "A Hard Disk" becomes the second hard disk and "B Hard Disk" becomes the first one. Well... That's bet. We know have to check his answers to my questions.

It seems that I should speed the development of liveswap option menues (currently it is only a command-line command).

Waiting for your answers.

adrian15

with respect to sl 2 & 3 the output is as follows:-

grub> cat (hd0,0)/
cat (hd0,0)/

Error 15: File not found
grub> c
c

Error 27: Unrecognized command
grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
(hd0,0)
grub> 

with super grub disk the output is as follows:-
[COLOR="Red"]Boots & Tools - Show Partitions[/COLOR] - is as follows:

partition  linux-ide    linux -scsi   grub    hurd

1               hda            sda        (hd0)    hd0

2               hdb           sdb         (hd1)    hd1

the SGD version is latest (downloaded a week back- will try & check version no somehow)

as you mentioned the disc sequence may be getting inverted. to be sure of this i tried booting winXP with SGD and it did not boot and gave [COLOR="Blue"]error25: disk read error[/COLOR] under one option and in another option said [COLOR="Blue"]error loading operating system[/COLOR]. Otherwise when i boot [COLOR="Blue"]win xp [/COLOR]normally [COLOR="Blue"]from hdd, it boots normally.[/COLOR] so [COLOR="DarkOrange"]i presume[/COLOR] that the [COLOR="DarkOrange"]hdd reading by bios / sgd is different from what live cd sees.[/COLOR]

waiting for your new program eagerly

once again thanx for all your help and interest.

regards

---

### Post by sandysandy on 2007-10-31
> **Pumalite said:**
> This might help (not sure):

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

thanx for the links. am going thru it. output of sgd is posted above.

regards

---

### Post by sandysandy on 2007-11-01
hi guys 
this must be a unique case where the hdd is looked at differently by the BIOS and the live CD. if anyone has faced this problem kindly let me know the solution, if found.

To recapitulate

i have Pentium D 64 bit 3.00 GHz CPU, 1 GB RAM, 160 GB SATA HDD (Win XP) & 40GB IDE HDD with 64 bit Gutsy 7.10. While booting irrespective of hdd booting order, the only option i get is of Win XP + Win XP (Win XP on 2 partitions). I do not get Linux options.
Win XP boots normally. 
when i use Super Grub CD, Linux and windows are both detected, but nothing boots, Win XP shows error25: disk read error ( or error loading operating system) and Linux shows Error 15 Menu.lst file not found.

Kindly help

regards

---

### Post by sandysandy on 2007-11-01
> **adrian15 said:**
> 1) Are you using 0.9667 version of SGD ?

2) One thing I do not understand is why no menu.lst is found while from the live cd you can see it.

Typing 'c' and:

find /boot/grub/menu.lst

or 

find /grub/menu.lst

does it give you any output?

3) cat (hd0,0)/
and then pressing the <TAB> key does it prompts an error?

4) What do you see when you go to Boot & Tools -> Show Partitions

Do you see one or two hard disks? If you select the hd0 one do you see windows hard disk or do you see the linux hard disk? And if you select hd1? (Note: If you press enter on a partition you come back to the former menu).

5) Depending on what you say here I will ask you to try a new command called liveswap which I have developed which could solve strange configurations as yours.

6) His configuration is strange because when it boots from hard disk "A Hard Disk" is the first one and "B Hard Disk" is the second one. However when he boots from cdrom "A Hard Disk" becomes the second hard disk and "B Hard Disk" becomes the first one. Well... That's bet. We know have to check his answers to my questions.

It seems that I should speed the development of liveswap option menues (currently it is only a command-line command).

Waiting for your answers.

adrian15

i hope i am giving the complete answer

1) SGD version is 0.9654 (copyright 2005,06,07 adrian15)
2) grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
(hd0,0)
grub>

3)  grub> cat (hd0,0)/
cat (hd0,0)/

Error 15: File not found
grub> c
c

Error 27: Unrecognized command

4) with super grub disk the output is as follows:-
Boots & Tools - Show Partitions - is as follows:

partition linux-ide linux -scsi grub hurd

1               hda         sda (hd0)  hd0

2 hdb sdb (hd1) hd1

PS - with SGD i tried ADVANCE - special boot - swap
this i think u have developed for hard disk swap.
i was able to boot windows with this after swapping hard disk with this option.
(earlier i could not boot windows with SGD, though it booted normally from hdd on its own) Cannot boot linux.

could u tell me about the[COLOR="Blue"] live swap command.[/COLOR]

regards

---

### Post by meierfra on 2007-11-01
Did you try booting from the sata drive since  you did "root (hd0,0) setup (hd0)"? 

If  that didn't  get you the grub menu,  try  (with "ide" first in boot order) 

sudo grub
root (hd0,0)
setup (hd1)

---

### Post by adrian15 on 2007-11-02
> **sandysandy said:**
> 
could u tell me about the[COLOR="Blue"] live swap command.[/COLOR]
regards

Get 0.9667 version of SGD from [forjamari super grub disk downloads]("http://forjamari.linex.org/frs/?group_id=61").

Go to the Linux, Windows, Boot & Tools, Advanced menu.
Type 'c' key.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
grub>liveswap
Type 'ESC' key.

Now you should see again the Linux, Windows, Boot & Tools, Advanced menu. Use SGD as if your system was a normal one. Why don't you try **GNU/Linux -> Boot Gnu/Linux** you check that your GNU/Linux boots and then you reboot,... you redo what I tell you before (When you reboot the liveswap changes are lost) and then you select **GNU/LINUX -> Fix Boot of GNU/Linux (GRUB) and enjoy at last your permanent GNU/Linux system.**

I suppose that this weekend I will implement the liveswap from easy menues. I have been thinking which was the best way of including it in menues for three or four days and I am convinced on what's the best way.

See you soon with a new SGD version with the liveswap feature included.

adrian15

TIP: You should put an space between map and (hd1) and another space between (hd1) and (hd0).

P.S.: Depending on how the installer guessed the first grub device was you might get some error 21 errors but I think that everything is going ok in your particular situation.

---

### Post by adrian15 on 2007-11-02
> **meierfra said:**
> Did you try booting from the sata drive since  you did "root (hd0,0) setup (hd0)"? 

If  that didn't  get you the grub menu,  try  (with "ide" first in boot order) 

sudo grub
root (hd0,0)
setup (hd1)

This cannot work. When you do that, GRUB is installed in the actual first hard disk, that's it's true, hacker, that's isssss truuuueeee. (Taken from the Free Software Song) :)

But you are telling GRUB that their files are in the first hard disk (hd0) while when she (Sandy is a woman name isn't it?) is going to reboot the GRUB files are found in the second hard disk and thus she will get an error there.

If you use GRUB from SGD or another GRUB disk you need the liveswap command. If you use the chroot method then you can use the device command to define the grub device-linux device equivalence exactly. This is another way of fixing the problem.

adrian15

---

### Post by sandysandy on 2007-11-03
> **adrian15 said:**
> Get 0.9667 version of SGD from [forjamari super grub disk downloads]("http://forjamari.linex.org/frs/?group_id=61").

Go to the Linux, Windows, Boot & Tools, Advanced menu.
Type 'c' key.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
grub>liveswap
Type 'ESC' key.

Now you should see again the Linux, Windows, Boot & Tools, Advanced menu. Use SGD as if your system was a normal one. Why don't you try **GNU/Linux -> Boot Gnu/Linux** you check that your GNU/Linux boots and then you reboot,... you redo what I tell you before (When you reboot the liveswap changes are lost) and then you select **GNU/LINUX -> Fix Boot of GNU/Linux (GRUB) and enjoy at last your permanent GNU/Linux system.**

I suppose that this weekend I will implement the liveswap from easy menues. I have been thinking which was the best way of including it in menues for three or four days and I am convinced on what's the best way.

See you soon with a new SGD version with the liveswap feature included.

adrian15

TIP: You should put an space between map and (hd1) and another space between (hd1) and (hd0).

P.S.: Depending on how the installer guessed the first grub device was you might get some error 21 errors but I think that everything is going ok in your particular situation.

at the grub
i typed:  map (hd0) (hd1)
              map (hd1) (hd0)
              live swap 
it showed [COLOR="Blue"]file system type is iso9660, using whole disk.[/COLOR]
             
then esc

i tried GNU/Linux -> boot GNU/Linux

I got [COLOR="Blue"]Error 15: File not found[/COLOR]

regards

---

### Post by Tipharet on 2007-11-03
I have this same exact issue. I get error 15 on reboot no matter what I have tried. Ive even posted bout and have not got replies like you have.

But basically nothing works, none of these suggestions. the only thing that differs is that usually I can not even boot to windows and it tells me boot/grub/stage1 is not found.

---

### Post by sandysandy on 2007-11-03
> **Tipharet said:**
> I have this same exact issue. I get error 15 on reboot no matter what I have tried. Ive even posted bout and have not got replies like you have.

But basically nothing works, none of these suggestions. the only thing that differs is that usually I can not even boot to windows and it tells me boot/grub/stage1 is not found.

hope ur able to solve the problem along with me.
its just a matter of time.
i am sure with all the help on this forum and thread, a solution will be found.

regards

---

### Post by Tipharet on 2007-11-03
Yeah, its really annoying I didnt have this issue with Fiesty. I know it has something to do with the way grub sees SATA drives.

Heres my thread:
[http://ubuntuforums.org/showthread.php?t=600125](http://ubuntuforums.org/showthread.php?t=600125)

Does anyone think physically disconnecting the IDE drives would actually help?

---

### Post by sandysandy on 2007-11-03
> **Tipharet said:**
> Yeah, its really annoying I didnt have this issue with Fiesty. I know it has something to do with the way grub sees SATA drives.

Heres my thread:
[http://ubuntuforums.org/showthread.php?t=600125](http://ubuntuforums.org/showthread.php?t=600125)

Does anyone think physically disconnecting the IDE drives would actually help?

i take it as a challenge and i have learnt a lot from this issue.
i am sure that this problem of booting will be overcome.


regards

---

### Post by sandysandy on 2007-11-03
> **meierfra said:**
> Did you try booting from the sata drive since  you did "root (hd0,0) setup (hd0)"? 

If  that didn't  get you the grub menu,  try  (with "ide" first in boot order) 

sudo grub
root (hd0,0)
setup (hd1)

[COLOR="Blue"]giving it a shot[/COLOR]

grub> root (hd0,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd1) (hd1)1+17 p (hd0,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

[COLOR="Blue"]EDIT [/COLOR]: backup mbr before using. my mbr got overwritten but i could restore the MBR with backup copy. anyway worth a try. thanx.

regards

---

### Post by sandysandy on 2007-11-04
> **adrian15 said:**
> This cannot work. When you do that, GRUB is installed in the actual first hard disk, that's it's true, hacker, that's isssss truuuueeee. (Taken from the Free Software Song) :)

But you are telling GRUB that their files are in the first hard disk (hd0) while when he (Sandy is a guy's name isn't it?) is going to reboot the GRUB files are found in the second hard disk and thus he will get an error there.

If you use GRUB from SGD or another GRUB disk you need the liveswap command. If you use the chroot method then you can use the device command to define the grub device-linux device equivalence exactly. This is another way of fixing the problem.

adrian15

Hi adrian15

i am eagerly waiting for your new liveswap feature.

regards

---

### Post by adrian15 on 2007-11-04
Test #1
========

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>cat (hd0,0)/<TAB>

Where <TAB> means typing the tab key once or twice which it is a key on your keyboard which form is:


    |<---
    ---->|

and that is above the CAPS LOCK key.

Does it give an error or some files listing?


Test #2
=======

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
liveswap
configfile (hd1,0)/boot/grub/menu.lst

Choose your first Ubuntu line... does Linux boot ok?

Test #3
========

If only Test #2 seems to work ok run this test for making the changes persistent.

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
liveswap
root (hd1,0)
setup (hd0)


========
========

For each one of the tests you are supposed to reboot the machine before it.

Waiting for your answers depending on Test #1 I might have a big bug in Super Grub Disk about menu.lst not being found when it is there (find command has indeed found it).

Sorry for the delay Sandy.

adrian15

P.S.: I will upload on monday or tuesday the new SGD with liveswap included in menues but the one that you are already using has the functionality that you need (but in command line fashion only).

---

### Post by sandysandy on 2007-11-05
> **adrian15 said:**
> Test #1
========

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>cat (hd0,0)/<TAB>

Where <TAB> means typing the tab key once or twice which it is a key on your keyboard which form is:


    |<---
    ---->|

and that is above the CAPS LOCK key.

Does it give an error or some files listing?


Test #2
=======

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
liveswap
configfile (hd1,0)/boot/grub/menu.lst

Choose your first Ubuntu line... does Linux boot ok?

Test #3
========

If only Test #2 seems to work ok run this test for making the changes persistent.

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
liveswap
root (hd1,0)
setup (hd0)


========
========

For each one of the tests you are supposed to reboot the machine before it.

Waiting for your answers depending on Test #1 I might have a big bug in Super Grub Disk about menu.lst not being found when it is there (find command has indeed found it).

Sorry for the delay Sandy.

adrian15

P.S.: I will upload on monday or tuesday the new SGD with liveswap included in menues but the one that you are already using has the functionality that you need (but in command line fashion only).

hi adrian15

thanx for all the effort that ur taking.
the results of the tests are as follows:-

[COLOR="Red"]test 1 [/COLOR]

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>[COLOR="Green"]cat (hd0,0)/<TAB>[/COLOR]

[COLOR="Blue"]ERROR 25; DISK READ ERROR[/COLOR]

[COLOR="Red"]TEST 2[/COLOR]

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)

[COLOR="Green"]liveswap[/COLOR]

[COLOR="Blue"]FILE SYSTEM IS ISO 9660, USING WHOLE DISK[/COLOR]

[COLOR="Green"]configfile (hd1,0)/boot/grub/menu.lst[/COLOR]
[COLOR="Blue"]
DISK READ ERROR[/COLOR]

Though the tests 1 & 2 were not positive, i was able to [COLOR="DarkOrange"]finally boot[/COLOR] into hdd [COLOR="DarkOrange"]using your Super Grub Disk[/COLOR]. I feel more confidant now, that some solution is possible to boot Gutsy  from the hdd normally.

thanxs again for all the guidance. 
looking forward to more inputs.

regards

---

### Post by sandysandy on 2007-11-05
the ubuntu i have booted using SGD ould be the one installed on my 160GB SATA hdd and not the 40GB IDE hdd (system specs Pentium D 3.0GHz, 1 GB RAM, 160 GB SATA HDD (Win XP, Mandriva, Ubuntu7.10) & 40GB IDE HDD (Ubuntu7.10)

[COLOR="Red"]the hard disk details are:-[/COLOR]

sandy@sandy-desktop:~$ [COLOR="Magenta"]sudo find /boot/grub/menu.lst
/boot/grub/menu.lst[/COLOR]
sandy@sandy-desktop:~$ [COLOR="Green"]sudo find /boot/grub/stage1
/boot/grub/stage1[/COLOR]
sandy@sandy-desktop:~$ [COLOR="Red"]sudo fdisk -lu[/COLOR]

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x40634062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74862899    37431418+  83  Linux
/dev/sda2        74862900    78156224     1646662+   5  Extended
/dev/sda5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155   266373764   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *   266373765   312560639    23093437+   7  HPFS/NTFS
/dev/sdb5        51199218   133114589    40957686    7  HPFS/NTFS
/dev/sdb6       215030088   221327504     3148708+   7  HPFS/NTFS
/dev/sdb7       264285378   266373764     1044193+   7  HPFS/NTFS
/dev/sdb8       221327568   229504589     4088511   82  Linux swap / Solaris
/dev/sdb9       229504653   238131494     4313421   83  Linux
/dev/sdb10      238131558   247224284     4546363+  83  Linux
/dev/sdb11      247224348   261136574     6956113+  83  Linux
/dev/sdb12      261136638   264285314     1574338+  82  Linux swap / Solaris
/dev/sdb13      133114653   156440969    11663158+  83  Linux
/dev/sdb14      156441033   166208489     4883728+  83  Linux
/dev/sdb15      166208553   175976009     4883728+  83  Linux

Partition table entries are not in disk order

[COLOR="Red"]My menu.lst is as follows:-[/COLOR]
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,14)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=fee04ac8-860c-4ad0-9262-726d1f0ed7f9 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,14)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=fee04ac8-860c-4ad0-9262-726d1f0ed7f9 ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,14)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


regards

---

### Post by adrian15 on 2007-11-05
> **sandysandy said:**
> the ubuntu i have booted using SGD ould be the one installed on my 160GB SATA hdd and not the 40GB IDE hdd (system specs Pentium D 3.0GHz, 1 GB RAM, 160 GB SATA HDD (Win XP, Mandriva, Ubuntu7.10) & 40GB IDE HDD (Ubuntu7.10)

Although I have not studied it in deep I think I am not going to be able fix this error 25 bug (If it is a bug because I am not sure, it might be that you have a very big hard disk or another thing like the partition table is not correct.)

My advice:

Use SGD to install your 40 GB's grub to the MBR that boots, the other one. This is very easy it is the one that does not have the Ubuntu and it has to be hd0 so you have to run the liveswap commands.

Something like this:
METHOD 1:
```

'c'
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
grub>liveswap
grub>root (hd0,14)
grub>setup (hd0)

grub> cat (hd0,14)/boot/grub/menu.lst

grub> reboot

```
METHOD 2:
```

'c'
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)
grub>liveswap
'ESC'

GNU/LINUX -> FIX BOOT OF LINUX (GRUB)


Select (hd0,14) stage1.


```


Once you have done this you should be able to have the 160 GB hard disk grub when you boot.

Then what I advice you to do is the following thing:

Copy kernel, initrd and System files from 40 GB /boot/ folder to the /boot folder on the 160 GB disk.

Then edit the 160 GB's /boot/grub/menu.lst so that you add the boot options that are found in the 40 GB's /boot/grub/menu.lst but then you have to edit these options so that:

```
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

reads something like:
```

title GB 40 DISK :: Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,14)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a3f64876-1bdd-46dc-ba07-5b209eeaa1cb ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

Do not modify the UUID statement because it has to be the other disk.

Finally you'll have to find pieces of code like this:

```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,14)
kernel /vmlinuz-2.6.22-14-generic root=UUID=fee04ac8-860c-4ad0-9262-726d1f0ed7f9 ro quiet splash
initrd /initrd.img-2.6.22-14-generic
quiet

```

And write this:

```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,14)
kernel /vmlinuz-2.6.22-14-generic root=UUID=fee04ac8-860c-4ad0-9262-726d1f0ed7f9 ro quiet splash
initrd /initrd.img-2.6.22-14-generic
quiet

```

I mean that the hd1 entries are wrong and should be hd0 because your 160 GB hard disk is supposed to be the first one to boot.

I also recommend you to search for something like this:

```

# groot = (hd1,14)

```

and write instead:

```

# groot = (hd0,14)

```


so that kernel updates does not give you nightmares.

Once you have made the modifications make a backup.

You know if you want the 40 GB DISK entries not to be overwritten by a 160 DISK Ubuntu kernel update you should put the lines outside the lines DEBIAN AUTOMAGIC KERNELS LIST.

Any doubts or improvements, make them me know. One problem I detect is what is going to happen when you do a kernel update in the 40 GB DISK you will have to edit manually the 160 GB DISK menu.lst to incorporate the changes.



adrian15

P.S.: When 160 GB's HDD grub is installed to the MBR can you try to type 'c'. And see what ```
cat (hd1,0)/<TAB> 
configfile (hd1,0)/boot/grub/menu.lst


``` gives you? If it is not an error 25 then there's hope for a SGD fix and there is also hope for you linking from the 160 GB's HDD menu.lst to the 40 GB's HDD menu.lst without being aware of the kernel updates.

P.S.2: If you download and use 0.9670 SGD version the EASY LIVE SWAP option runs the:
```

map (hd0) (hd1)
map (hd1) (hd0)
liveswap

```
commands for you.

---

### Post by sandysandy on 2007-11-05
thanx

i will give it a try. i also have mandriva loaded on the 160 GB SATA hdd in addition to ubuntu 7.10 and win xp. (40gb IDE hdd has second ubuntu7.10)

when booting (40gb is first hdd, 160gb is seond hdd in boot priority), i get the mandriva grub screen and i am able to boot into Mandriva and windows normally. Its only ubuntu which is not showing on the booting options. i had tried reloading the grub from ubuntu live cd but it only messed up the mbr, and i used the mbr backup to restore the mbr.

i was wondering that since mandriva is giving booting options for win xp and mandriva, is it possible to add  bootloader entries of ubuntu to the menu.lst of mandriva.( ubuntu is on both 40 gb and 160gb, the 160 gb ubuntu is bootable with SGD)

regards

---

### Post by adrian15 on 2007-11-06
Can you please try this once more?

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
```

grub>root (hd0,0)
grub>configfile /boot/grub/menu.lst

```


About your question, yes, you can edit the mandrake menu.lst exaxtly the same way I adviced you to edit the 160 GB ubuntu menu.lst.

adrian15

---

### Post by adrian15 on 2007-11-06
> **sandysandy said:**
> at the grub
i typed:  map (hd0) (hd1)
              map (hd1) (hd0)
              live swap 
it showed [COLOR="Blue"]file system type is iso9660, using whole disk.[/COLOR]
             
then esc

i tried GNU/Linux -> boot GNU/Linux

I got [COLOR="Blue"]Error 15: File not found[/COLOR]

regards

When you run this command, you did have Mandrake  and the other ubuntu installed to your disk, isn't it? If the answer is true then I have a bug on SGD because if the first hard disk gives an error 25 the selectfile command should continue on searching your other menu.lst files on the other hard disks and present them to you.

Did you have the other distros when running GNU/LINUX -> Boot GNU/Linux ?

If you run (without live swap)  ```
cat (hd1,14)/<TAB>
``` do you get a hard disk error too?

adrian15

---

### Post by sandysandy on 2007-11-06
> **adrian15 said:**
> When you run this command, you did have Mandrake  and the other ubuntu installed to your disk, isn't it? If the answer is true then I have a bug on SGD because if the first hard disk gives an error 25 the selectfile command should continue on searching your other menu.lst files on the other hard disks and present them to you.

Did you have the other distros when running GNU/LINUX -> Boot GNU/Linux ?

If you run (without live swap)  ```
cat (hd1,14)/<TAB>
``` do you get a hard disk error too?


adrian15

[COLOR="Red"]without liveswap[/COLOR] [COLOR="Blue"]the output is as follows:-
[/COLOR]
grub> [COLOR="Red"]cat (hd1,14)/[/COLOR]
possible files are: lost & found system.map-2.6.22-14-generic abi-2.6.22-14-generic config-2.6.22-14-generic initrd.img-2.6.22-14-generic.bak memtest86+.bin vm linuz-2.6.22-14-generi initrd.img-2.6.22-14-generic grub

with GNU/Linux - Boot GNU Linux i could boot ubuntu 7.10 on 160 gb hdd (hd1,14) without using live swap.(No joy on 40gb hdd Ubuntu 7.10)

regards

---

### Post by adrian15 on 2007-11-07
> **adrian15 said:**
> Can you please try this once more?

Go to the GNU/Linux / Windows / Boot & Tools /Advanced menu.
Type 'c'.
```

grub>root (hd0,0)
grub>configfile /boot/grub/menu.lst

```


About your question, yes, you can edit the mandrake menu.lst exaxtly the same way I adviced you to edit the 160 GB ubuntu menu.lst.

adrian15

Can you please answer this question?

Thank you.

adrian15

---

### Post by sandysandy on 2007-11-09
> **adrian15 said:**
> Can you please answer this question?

Thank you.

adrian15

hi adrian15

i got the following:

grub>root (hd0,0)

ERROR 25; DISK READ ERROR

regards

---

### Post by adrian15 on 2007-11-09
Ok. Sandy thank you for the test. I suppose that the problem would be identified if I put some debug messages in the code so that we know the exact reason for the error.

Now it's up to you to Sandy. If you do not mind about 40 GB data I would recommend you to repartitin everything by making sure you make a 100 MB /boot partition at the beginning and see what does happen.

Another thing you can do is what I explained you about putting kernels in the 160 GB data and updating its menu.lst.



adrian15

---

### Post by sandysandy on 2007-11-09
> **adrian15 said:**
> Ok. Sandy thank you for the test. I suppose that the problem would be identified if I put some debug messages in the code so that we know the exact reason for the error.

Now it's up to you to Sandy. If you do not mind about 40 GB data I would recommend you to repartitin everything by making sure you make a 100 MB /boot partition at the beginning and see what does happen.

Another thing you can do is what I explained you about putting kernels in the 160 GB data and updating its menu.lst.



adrian15

hi adrian15

thanx

i have reinstalled ubuntu 7.10 on the 40 gb hdd and it has booted up normally.
[only the network is not configured(internet not working) which i will try to do so now with help from this forum & the other 160gb hdd is not detected ]
thanks for the advice and patience due to which i could get my Gutsy 7.10 up and running and also learning a lot.

regards

---

### Post by sandysandy on 2007-11-10
i formatted the 40 gb IDE hdd again and deleted all the linux partitions on 160gb IDE hdd as the number of partitions had become unmanageable and confusing. i loaded Mandriva 2008 and Gutsy 7.10 on the 40gb IDE hdd, installing grub in default option to hd0 as the 40 gb ide hdd is first in booting sequence.

i am back to the old problem of just getting the win xp in startup menu.
with SGD also the 40 GB hdd is unable to boot.
[COLOR="Blue"]
Menu.lst not found[/COLOR] is displaying.

regards

---

### Post by adrian15 on 2007-11-13
> **sandysandy said:**
> 
i am back to the old problem of just getting the win xp in startup menu.
with SGD also the 40 GB hdd is unable to boot.
[COLOR="Blue"]
Menu.lst not found[/COLOR] is displaying.

regards

Did you do the small 100 MB /boot partition in the 40 GB hard disk as I suggested you?

adrian15

---

### Post by sandysandy on 2007-11-16
> **adrian15 said:**
> Did you do the small 100 MB /boot partition in the 40 GB hard disk as I suggested you?

adrian15

thats right. i made the 100mb /boot partition.

the output of sudo fdisk -lu is also appended below for reference ( if required)

[COLOR="Red"]ubuntu@ubuntu:~$ sudo fdisk -lu[/COLOR]

[COLOR="Blue"]Disk /dev/sda: 40.0 GB[/COLOR], 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc0c9e151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+  83  Linux
/dev/sda2          192780    78156224    38981722+   5  Extended
/dev/sda5          192843     8369864     4088511   83  Linux
/dev/sda6        74862963    78156224     1646631   82  Linux swap / Solaris
/dev/sda7         8369928    16177454     3903763+  83  Linux

Partition table entries are not in disk order

[COLOR="Blue"]Disk /dev/sdb: 160.0 GB,[/COLOR] 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    51199154    25599546    7  HPFS/NTFS
/dev/sdb2        51199155   133114589    40957717+   f  W95 Ext'd (LBA)
/dev/sdb3       133114590   179301464    23093437+   7  HPFS/NTFS
/dev/sdb5        51199218   133114589    40957686    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

regards

---

### Post by adrian15 on 2007-11-17
I gave up. You can try to activate or inactivate the LBA support in your bios to see if it works then though.

adrian15

---

### Post by bumanie on 2007-11-17
Sandysandy, I have read the post and some of the problems you are having, I also had, although there are some differences too. At one stage I 'lost' my gub menu.lst too. The way I retrieved it was by doing a system recovery, however this may not be possible for you because it seems you can't boot in at all. When I had problems I at least could boot into either xp or feisty via sgd. 
Check out this thread [http://ubuntuforums.org/showthread.php?t=610852](http://ubuntuforums.org/showthread.php?t=610852)
I don't know whether anything in there will help, but maybe if you read through it may give you some ideas.
I would look at page 7 in particular and see what bytejuggler suggested - especially the part on ridding the hard drive of grub. I can't guarantee the same command will suit your needs. I don't know enough. Have a look, you probably can't be any worse off. I guess you have backed up xp onto an external device - if not you should in case something really goes wrong.

---

### Post by sandysandy on 2007-11-18
> **bumanie said:**
> Sandysandy, I have read the post and some of the problems you are having, I also had, although there are some differences too. At one stage I 'lost' my gub menu.lst too. The way I retrieved it was by doing a system recovery, however this may not be possible for you because it seems you can't boot in at all. When I had problems I at least could boot into either xp or feisty via sgd. 
Check out this thread [http://ubuntuforums.org/showthread.php?t=610852](http://ubuntuforums.org/showthread.php?t=610852)
I don't know whether anything in there will help, but maybe if you read through it may give you some ideas.
I would look at page 7 in particular and see what bytejuggler suggested - especially the part on ridding the hard drive of grub. I can't guarantee the same command will suit your needs. I don't know enough. Have a look, you probably can't be any worse off. I guess you have backed up xp onto an external device - if not you should in case something really goes wrong.

i can boot into win XP normally. when i boot the computer, the windows options comes automatically.
the only problem is booting into ubuntu. 

thanx

---

### Post by sandysandy on 2007-11-18
> **adrian15 said:**
> I gave up. You can try to activate or inactivate the LBA support in your bios to see if it works then though.

adrian15


thanx.

just for info. my motherboard is gigabyte 945 series. i hope that this is compatible with linux.

regards

---

### Post by bumanie on 2007-11-18
i can boot into win XP normally. when i boot the computer, the windows options comes automatically.
the only problem is booting into ubuntu. 

Sandy, 
If I read everything correctly, you have been trying to put ubuntu onto seperate hard drive, is this correct? When I had problems, apart from gutsy not seeming to install correctly for some reason, I think was left with remnants of grub on my slave drive. This, I think, was mucking everything up. Maybe if you format that drive via windows or via bytejuggler's instructions or use dban or something similar, you may have luck with trying a fresh install. It may not work, but it is worth a try. Wiping the drive clean may be the best thing to do, start from scratch with ubuntu.

---

### Post by sandysandy on 2007-11-18
> **bumanie said:**
> i can boot into win XP normally. when i boot the computer, the windows options comes automatically.
the only problem is booting into ubuntu. 

Sandy, 
If I read everything correctly, you have been trying to put ubuntu onto seperate hard drive, is this correct? When I had problems, apart from gutsy not seeming to install correctly for some reason, I think was left with remnants of grub on my slave drive. This, I think, was mucking everything up. Maybe if you format that drive via windows or via bytejuggler's instructions or use dban or something similar, you may have luck with trying a fresh install. It may not work, but it is worth a try. Wiping the drive clean may be the best thing to do, start from scratch with ubuntu.

thanx

i think i will give it a try. which is the best way to wipe the hard drive. is it advisable to wipe the MBR also to remove the grub traces. again which is the best way to wipe the MBR.

regards

---

### Post by bumanie on 2007-11-18
> **sandysandy said:**
> thanx

i think i will give it a try. which is the best way to wipe the hard drive. is it advisable to wipe the MBR also to remove the grub traces. again which is the best way to wipe the MBR.

regards

Sorry for taking so long to answer, but I started writng something else.
Are you able to see the hdd from windows through the device manager? If so you can format via windows. It will format your hdd into NTFS. You can then try and install ubuntu again. In your case, try the normal (ie slower) format, rather than the quick format option.

---

### Post by sandysandy on 2007-11-18
> **bumanie said:**
> Sorry for taking so long to answer, but I started writng something else.
Are you able to see the hdd from windows through the device manager? If so you can format via windows. It will format your hdd into NTFS. You can then try and install ubuntu again. In your case, try the normal (ie slower) format, rather than the quick format option.

i cant see it from windows. i can try from gparted cd to format the 40 gb hdd.
how do i format the mbr to remove grub traces.

thanx

---

### Post by bumanie on 2007-11-18
Did you look via device manager under disk management?

---

### Post by Pumalite on 2007-11-18
> **sandysandy said:**
> i cant see it from windows. i can try from gparted cd to format the 40 gb hdd.
how do i format the mbr to remove grub traces.

thanx
 DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
After that format with Gparted Live CD.

---

### Post by sandysandy on 2007-11-18
> **bumanie said:**
> Did you look via device manager under disk management?

at present i am online on Open SUSE 10.3. 
do i look for device manager under windows XP or Ubuntu live Cd.

thanks

---

### Post by bumanie on 2007-11-18
> **sandysandy said:**
> at present i am online on Open SUSE 10.3. 
do i look for device manager under windows XP or Ubuntu live Cd.

thanks

Via xp. Right click my computer, go to disk management. Or do as pumalite suggests and download dban onto either a floppy or cd and use it. I have never used it, but it meant to clean/scrub disks very well.

---

### Post by sandysandy on 2007-11-18
> **Pumalite said:**
> DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
After that format with Gparted Live CD.

thanks for the info.

regards

---


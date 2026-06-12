---
title: "meerkat and linx not getting along..."
date: 2010-10-13
forum: Apple Hardware Users
---

### Post by jjex22 on 2010-10-13
Below is the question I originally posted this morning. If you are having this problem scroll down to the third post for the solution :)

'just installed 10.10 on a 2003 emac with osx tiger and ubuntu 10.04 already on it. 

partition map is
dev/hda1-partition map
dev/hda3-bootstrap partition
dev/hda4-ext4 linux partition (10.04)
dev/hda5-swap
dev/hda6-ext4 (10.10)
dev/hda7-netbsd
dev/hda8-apple osx
dev/hda9-shared data.

I was expecting yaboot to be a pain as usual, but got a glimmer of hope when i booted and pressed 'L', then tab and saw my old linux listed as 'hda3-Linux' so typed it in and hit return, saw the ubuntu 10.04 slash, thought it would work ..

then get 

'No init found. try passing init= bootarg.

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _'

any ideas anyone? for the record 10.10 seems to be working fine though i havn't really got around to testing properly as I've already had to fix yaboot for netbsd and now I'm on this... really wish there was an Easy bcd for old macs!

thans in advance guys!'

---

### Post by jjex22 on 2010-10-13
here's where I'm at now -

The problem is with the 10.10 mini.iso installer. I have tried redownloading etc, but same prob. Reinstalling 10.04 does not affect the 10.10 install (other than making itself the default) but installing 10.04 before 10.10 always results in this init prob, 10.10 before 10.04 wors for both boots just fine. 

Also installing 10.10 then 10.04  and booting into 10.10 and running ybin (to auto boot into 10.10) damages 10.04 again.

As I have just reinstalled both systems twice, I have no interest in working out the yaboot problem -(as I have a deep seated hatred for yaboot and do not enjoy these bi annual irritations) I just changed the default os from 10.04.

---

### Post by jjex22 on 2010-10-13
Okay so I got some lunch, a cup of tea and some Jaffa cakes and cooled off!:popcorn:

Then came back to fix the problem. Here is the solution -I think it may well apply to all multi linux booting ppc maverick though untested:

the problem lies at the bottom of the /etc/yaboot.conf file (as expected)

sudo nano -w /etc/yaboot.conf

scroll down passed all the 10.10 info and mac osx info untill you get to


## This entry automatically added by the Ubuntu installer for an existing
## Linux installation on /dev/hda*.


look at the image described underneath this text. The problem is in the 4th row down where it says

append="root=/dev/hda3 ro quiet splash"

and change the /dev/hda (or /dev/sda if you have a sata drive) number ('3' above) to the number of the partition the other linux os is actually on. It's that simple.

You may also want to change the label of the other os from /hda*-linux to something easier to type, I made mine 'lts' as both are ubuntu's.

then exit with 'control x'

making sure you save the file as /etc/yaboot.conf.

then

sudo ybin -v

and your done you should now be able to multi-boot linux and have meerkat as the default os.
 

I'm not sure if the installer is putting the 3 in because it's where my bootstrap partition is or if like the lucid mini.iso it expects to find a linux partition on the third partition but I'm certain the error is related to the fact that that is the only line in the image description listed in the form of /dev/hda instead of Open Firmware friendly language.

I can't be sure but I think this causes the init problem by confusing the boot process before it gets to the initrd location description on the line beneath.

Hope this helps anyone having difficulties!

---


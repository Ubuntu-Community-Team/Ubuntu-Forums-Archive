---
title: "dpkg: unrecoverable fatal error"
date: 2011-03-09
forum: Any Other OS
---

### Post by Dr.FrankenStein_ on 2011-03-09
Hi, i'm using Linux Mint Meerkat 2.6.35-27-generic. Pretty much all im trying to do is remove chromium-browser for no specific reason just that currently it is broken...(but still works fully) I really just would like to reinstall. With apt 0.8.3ubuntu7 This is what i get. 

drfrankenstein ~ $ sudo apt reinstall chromium-browser
[sudo] password for drfrankenstein: 

The following packages will be REINSTALLED:
chromium-browser{b} 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

The following packages have unmet dependencies:
chromium-browser: Depends: chromium-browser-inspector but it is not going to be installed.

Depends: chromium-codecs-ffmpeg (>= 0.6) but it is not going to be installed. or chromium-codecs-ffmpeg-extra (>= 0.6) but it is not going to be installed.
The following actions will resolve these dependencies:
Remove the following packages:
1)     chromium-browser            
Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  chromium-browser{a} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 51.7MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 207061 files and directories currently installed.)
Removing chromium-browser ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
--then nothing  {p.s. aptitude apt-get same thing}

---

### Post by coffee412 on 2011-03-09
fork failed: Cannot allocate memory

How much memory you got in that puppy??

---

### Post by irlandes on 2011-04-01
This may not be relevant, but any time you get a cannot allocate memory error message, do one thing first.

Open a terminal and type:

top <enter>

Then see if it shows any swap.

On multi-boot Linux systems, or perhaps on a linux system where a new distro is installed, it changes UUID when you format a partition.

So, if no swap (shows 0) in your terminal, type:

sudo blkid  <enter> followed by password

Note the UUIDs shown.

Now open a second terminal and type

sudo kate <enter> then your sudo password, and wait for kate to open up.  (Vi fans can do that, too if you wish)

In kate, open /etc/fstab  and compare the UUID's stated for each volume.

If they are different, copy them from the terminal listing by highlighting the id, and then Ctrl+Shift+c, then Ctrl+v to replace the UUID in fstab.

Edited:  Once they are the same, of course, SAVE the new /etc/fstab and reboot to enable mount for any partitions whose UUID was wrong.Ed


This may not be the case, but it should be checked via top before you do a lot of other stuff. It's called a process of elimination.

---

### Post by irlandes on 2011-04-01
I forgot to mention that when you have multi-boot system, you will have to fix /etc/fstab on each and every distro when a UUID is changed by installation/partitioning format of a partition.  Or, you get some really strange errors.

Maybe Saikee on Justlinux has a fix for this, since he installs more then 100 OS on one HD, but I don't know what it is.

---

### Post by Dr.FrankenStein_ on 2011-06-11
sorry this issue has long been fixed -- irlandes thanks for the swap check commands and info on UUID partitions as this makes alot of since and could be accountable for past issues.

Coffee412 -- 255mb RAM ...  Working with a dinosaur I know

Thanks again guys

---


---
title: "fsck at boot never finishes"
date: 2011-07-16
forum: Any Other OS
---

### Post by flemur13013 on 2011-07-16
Howdy!

I'm trying to run fsck at bootup.  I do "sudo touch /forcefsck" and reboot.  It's never finished in an hour or so, so I decided to let it run overnight.

About 12 hours later I see:

```
/dev/sda1: 161123/1921360 files (0.2% non-contig) [and the block counts]
HOME: 3961/4096000 files (0.9% non-contig)
```I enter "C" to continue.

df says:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             30233896   3454456  25243628  13% /
/dev/sda8             64500840   4397012  56827376   8% /home
/dev/sda6            376828640  42633672 334194968  12% /ntfs
/dev/sda5            252065656  33551232 205710220  15% /data
```These partitions are on a 750G SATA drive; "home" is fairly small, about 57G with 5G used, and /home is labeled HOME.

What's going on?

[Edit: I'm running Mint 9/fluxbox which is supposedly ubuntu 10.04 underneath]
[Edit: I'm not getting any errors and there's no problem booting, I just want to run fsck!]

---

### Post by Herman on 2011-07-16
You were right to allow it to run overnight, you should never interrupt a file system check while it's in progress as severe file system damage could result.
Maybe there's some problem there that the boot-up file system check is getting stuck on and isn't quite able to fix.

The fsck at boot-up is good, but not as good as running a full file system check from a live CD. 

You can use your Ubuntu Desktop Live CD that you used to install with or any Ubuntu Live CD as long as it contains the same version as your installed version of Ubuntu or newer.
EDIT: Or Mint Live CD.

You can either do it the point and click way or the command line way.

For the point and click way, open GParted and right-click on the partition you want to have a file system check run in and click 'check' from the right-click menu, then click 'apply' in a couple of different places and wait a few minutes for the process to complete.

If you like doing things using the command line, open a terminal and assuming your file system is ext2,3 or4, run 'sudo e2fsck -C0 -p -f -v /dev/sda1' ```
sudo e2fsck -C0 -p -f -v /dev/sda1
```Where: /dev/sda1 contains an ext series file system
Where: The file system in /dev/sda1 is not mounted

The -C0 option, (C zero) will cause a progress bar to display a tumbling bar leading a row of = (equal signs) across your terminal as the file system check progresses. I think it's kind of cool.
The option -p stands for 'preen', -f stands for 'force' (even if the file system doesn't think it really needs checking just yet), and -v is for 'verbose', so it will give you a nice report as soon as it finishes to let you know what happened.

I'm not sure exactly what kind of file system check Ubuntu runs at boot time now, strangely it doesn't seem to be included in any logs. I'm pretty sure it used to run fsck -C -R -A -a in times past. The fsck program is not an actual file system checker, but a file system checker manager, which is useful because programmers can incorporate it in programs to run file system checks automatically, such as at boot time, without the need to determine exactly what file system they're dealing with. The fsck program does that, and runs a kind of standard file system check which is okay for most of the time but is not able to fix all problems.

If you want to fix file system problems then it's better to run the file system check program for your specific file system yourself rather than through fsck because then you can run it directly with the options relevant to your requirements. (man e2fsck).

If you don't have time to mess around with the command line stuff, that's okay, GParted runs 'e2fsck -f -y -v /dev/sdx,y' for you.
The -y option means if it finds problems it can't fix it will just automatically unlink files to the lost+found without bothering to ask you for permission for every file. Then you can recover them later if you want. It's relatively rare for that to happen, thank goodness.
GParted also runs 'resize2fs' for you just to make sure your file system fills your partition, (useful if your operating system has been restored from a whole-of-partition backup).

The GParted file system check is great for most users as it is point and click and will fix just about all fixable file system problems.

---

### Post by szal on 2011-07-16
> **flemur13013 said:**
> [Edit: I'm running Mint 9/fluxbox which is supposedly ubuntu 10.04 underneath]
Which, strictly speaking, disqualifies you from being supported here, since your not running one of Ubuntu, Kubuntu, Xubuntu, Edubuntu or other supported spin-offs (particularly Lubuntu; no idea about Fluxbuntu…), but Linux Mint. Take my word with a grain of salt though, since it’s possible to tag threads with “other OS”.

But I agree, 12+ hours for a fsck run is a heckuva lot of time. On my 500 GB SATA HDD, fsck’ing the 400 GB ext3 partition takes approx. 20 minutes.

---

### Post by Perfect Storm on 2011-07-17
Moved to Other OS/Distro Talk.

---

### Post by flemur13013 on 2011-07-17
> **Herman said:**
> ...
The fsck at boot-up is good, but not as good as running a full file system check from a live CD. 

You can use your Ubuntu Desktop Live CD that you used to install with or any Ubuntu Live CD as long as it contains the same version as your installed version of Ubuntu or newer.
EDIT: Or Mint Live CD.
...


I ended up running the gparted and cmd line fsck(s) from the Ubuntu CD (IIRC the Mint CD won't let you do it) and both finished almost immediately.  It's a PITA, but not needed very often.

Thanks, I'll give up trying it at boot, I've seen references to all kinds of problems with that for whatever reason.

---


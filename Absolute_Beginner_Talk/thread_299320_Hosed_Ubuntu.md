---
title: "Hosed Ubuntu"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-11-14
Well, I have done it again. I have hosed my desktop. I was trying to downgrade from edgy to dapper. I went into my sources and changed everything from edgy to dapper. After I did the upgrade I couldn't get back to either edgy or dapper. All I get is a message that says: login/sh: can't access tty;job control turned off.I tried to access it by entering sudo apt-get install ubuntu-desktop, but that was of no help.
Any Ideas?](*,)
I was thinking about using the live cd and re-installing dapper, but I am afraid I will lose all my stuff. At least I do know where it is located. I installed my /home on a different partition.

---

### Post by Drakkor on 2006-11-14
Woulda been nice if you just imaged your Dapper partition,and could just restore it. BTW,why to go Edgy>Dapper ?

---

### Post by HareBall on 2006-11-14
> **Drakkor said:**
> Woulda been nice if you just imaged your Dapper partition,and could just restore it. BTW,why to go Edgy>Dapper ?

I have ran that don't into stuff that I don't like about it. I liked Dapper better. I mostly upgraded for Firefox 2. I have had OOo crash trying to run .pps files.
Doesn't make much difference now as I have hosed the desktop.

---

### Post by bodhi.zazen on 2006-11-14
Nice !

---

### Post by HareBall on 2006-11-14
> **bodhi.zazen said:**
> Nice !

What's nice about it? I can't get on my computer. I am posting from my wife's laptop using XP.:(

---

### Post by misha680 on 2006-11-14
I think I would just go with reinstalling dapper from the live CD especially if you have a separate home partition. During the edgy beta period, I went dapper -> edgy -> dapper -> edgy and then finally stayed with edgy after most of the bugs got fixed. In fact, I did not even have a separate /home partition, and the live cd will not let you install without reformatting your root partition, so I had to repartition to make a home, then copy everything back over, and repartition again. Should be much simpler for you.

Good luck.
Misha

p.s. Actually, I guess before you do that, you could try to boot into single user mode ("recovery mode" in grub) and type:

aptitude -f install

or maybe

aptitude dist-upgrade

Maybe it can resolve dependencies (aptitude is a lot better than apt-get and synaptic package manager). But it probably will be easier just to reinstall.

---

### Post by Velotix on 2006-11-14
Sounds like the Ubuntu repositories aren't designed to handle downgrades.

> I was thinking about using the live cd and re-installing dapper, but I am afraid I will lose all my stuff. At least I do know where it is located. I installed my /home on a different partition.

Reinstalling Dapper is probably your best bet at this point, especially if you have a separate /home partition.

As for Firefox 2, in future just get it from Mozilla. Not hard to do, [url=http://www.mozilla.com/firefox/] the link here lights up like a christmas tree. You can't miss it. ^^

*is impressed that Firefox manages to detect the OS you're using and change the download link accordingly* Cool script. :)

---

### Post by bodhi.zazen on 2006-11-14
> **HareBall said:**
> What's nice about it? I can't get on my computer. I am posting from my wife's laptop using XP.:(

Nothing, of course :p

I have toasted my share of Ubuntu installs in my time :lol:

Why not just re-install? is there something you need from the old ubuntu? if so, do you need assistance with data recovery?

It may be a problem with your initrd or grub.

Can you post /boot/grub/menu.lst ?

Otherwise, boot from the Live Cd and re-install grub:

[Re-install grub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by K.Mandla on 2006-11-14
I think that "job control turned off" error comes about from the way Edgy arranges Grub, as opposed to the way Dapper does it. 

I think (but I don't know) you just need to edit your menu.lst to correct it, and with some luck it might boot up again.

There's a thread [here]("http://www.ubuntuforums.org/showthread.php?t=292533") about it. Good luck.

---

### Post by bodhi.zazen on 2006-11-14
This is also a nice thread: [Nice !](http://www.ubuntuforums.org/showthread.php?t=174537)

---

### Post by HareBall on 2006-11-14
> **Velotix said:**
> Sounds like the Ubuntu repositories aren't designed to handle downgrades.



Reinstalling Dapper is probably your best bet at this point, especially if you have a separate /home partition.
How do I Install and make sure I don't overwrite my home partition? Also, when I install and have access to my home partition, how do I change it so everything works like it is supposed too?:-k

---

### Post by ron999 on 2006-11-14
Posted in error, sorry.

---

### Post by HareBall on 2006-11-14
> **HareBall said:**
> How do I Install and make sure I don't overwrite my home partition? Also, when I install and have access to my home partition, how do I change it so everything works like it is supposed too?:-k

bump

---

### Post by bodhi.zazen on 2006-11-14
> **HareBall said:**
> bump

[list=number][*]Just currious, did you look at grub or the last link I sent?
[*]Is /home it's own partition? if so, no problem, just install (I do not think your problem is with /home).
[*]If not, you will have to back up /home, install, then restore. I would archive /home and save the archive (tar) to a removable media.[/list]

---

### Post by HareBall on 2006-11-14
> **HareBall said:**
> How do I Install and make sure I don't overwrite my home partition? Also, when I install and have access to my home partition, how do I change it so everything works like it is supposed too?:-k

OK, what next? I have reinstalled dapper, now I don't have access to my old /home partition. I made sure not to reformat that partition when I reinstalled.

---

### Post by HareBall on 2006-11-14
> **bodhi.zazen said:**
> [list=number][*]Just currious, did you look at grub or the last link I sent?
[*]Is /home it's own partition? if so, no problem, just install (I do not think your problem is with /home).
[*]If not, you will have to back up /home, install, then restore. I would archive /home and save the archive (tar) to a removable media.[/list]
I couldn't get to my grub. I couldn't get to anything to do with Ubuntu. When I did my reinstall I made sure not to overwrite my /home partition. Now I don't know how to get back to it. My desktop looks just like it did when I first installed Ubuntu Dapper. Except that it has my windoze drive mounted, but not my /home partition. It is sdb1.
I tried to get it to boot into one of the kernals, but all I ever got was basically nowhere. If I was lucky, I got to a message telling me: can't access tty; job control turned off.
most of the time it just would run so far and just seem to stop.

---

### Post by bodhi.zazen on 2006-11-14
> **HareBall said:**
> I couldn't get to my grub. I couldn't get to anything to do with Ubuntu. When I did my reinstall I made sure not to overwrite my /home partition. Now I don't know how to get back to it. My desktop looks just like it did when I first installed Ubuntu Dapper. Except that it has my windoze drive mounted, but not my /home partition. It is sdb1.

Post /etc/fstab please.

I think you should boot to recovery mode, rename your current /home to /home.bak and add this to fstab:> /dev/shb1 /home auto users 0 2

Then reboot.

---

### Post by HareBall on 2006-11-14
> **bodhi.zazen said:**
> Post /etc/fstab please.

I think you should boot to recovery mode, rename your current /home to /home.bak and add this to fstab:

Then reboot.

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ext3    defaults        0       2
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Everything on sda is my Windows XP and Grub.

---

### Post by bodhi.zazen on 2006-11-14
> **HareBall said:**
> Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ext3    defaults        0       2
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Everything on sda is my Windows XP and Grub.


Thank you. boot to recovery mode.

move /home to /home.bak or better:```
rm -rf /home
```

Change:```
/dev/sdb1 /media/sdb1 ext3 defaults 0 2
```

To:```
/dev/sdb1 /home ext3 nodev,nosuid 0 2
```

Reboot.

_Note_: I assume /dev/sdb1 is you old home and not a copy or archive?

See here for more information: [Move Home](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by HareBall on 2006-11-14
> 

_Note_: I assume /dev/sdb1 is you old home and not a copy or archive?

You assume correctly:p

---

### Post by HareBall on 2006-11-14
> **bodhi.zazen said:**
> Thank you. boot to recovery mode.

move /home to /home.bak or better:```
rm -rf /home
```

Change:```
/dev/sdb1 /media/sdb1 ext3 defaults 0 2
```

To:```
/dev/sdb1 /home ext3 nodev,nosuid 0 2
```

Reboot.

_Note_: I assume /dev/sdb1 is you old home and not a copy or archive?

See here for more information: [Move Home](http://www.psychocats.net/ubuntu/separatehome)

When I tried /dev/sdb1 /home ext3 defaults 0 2
I got a message bash: /dev/sdb1: permission denied.

---

### Post by HareBall on 2006-11-14
> **HareBall said:**
> When I tried /dev/sdb1 /home ext3 defaults 0 2
I got a message bash: /dev/sdb1: permission denied.

Now I am getting a message: Your home directory is listed as: '/home/larry' but it does not appear to exist. etc, etc
I had this one time before and the only way out was to reinstall yet again.
:confused:

---

### Post by bodhi.zazen on 2006-11-14
You could re-install, when you do choose sdb1 as home without re-formatting.

You may just be facing a permissions problem (or be homeless :) ).

[list][*]Did you delete or move the old /home ?
[*]Make a new /home```
sudo mkdir /home
```
[*]Are you working in recovery mode?
[*]Try this fstab entry:```
/dev/sdb1 /home ext3 nodev,nosuid 0 2
```
[*]If you get an error message:
[indent][list][*]mount as root```
sudo mount /dev/sdb1 /home -0 nodev,nosuid
```And check permissions of /home and /home/user_name.[/indent][/list][/list]

---

### Post by HareBall on 2006-11-15
> **bodhi.zazen said:**
> You could re-install, when you do choose sdb1 as home without re-formatting.
Reinstalling it is. I figured out what happened before. I didn't tell it to make sdb1 my /home.](*,) 
Thanx for all the help. One of these days I'll learn to do some of this without prompting.:-k

---

### Post by bodhi.zazen on 2006-11-15
Nice !

---

### Post by HareBall on 2006-11-15
> **bodhi.zazen said:**
> Nice !

Well it turns out I think I  managed to overwrite my /home after all.
I can't find it. I have looked at all of my mounted partitions and it doesn't show. Here is what I found using a terminal:

larry@larry-desktop:~$ cd /home
larry@larry-desktop:/home$ ls
bin    dev   initrd          larry       media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib         mnt    root  sys  var
cdrom  home  initrd.img.old  lost+found  opt    sbin  tmp  vmlinuz
larry@larry-desktop:/home$ 

Any ideas would be welcome.

---

### Post by bodhi.zazen on 2006-11-15
> **HareBall said:**
> Well it turns out I think I  managed to overwrite my /home after all.
I can't find it. I have looked at all of my mounted partitions and it doesn't show. Here is what I found using a terminal:

larry@larry-desktop:~$ cd /home
larry@larry-desktop:/home$ ls
bin    dev   initrd          **larry**       media  proc  srv  usr      vmlinuz.old
boot   etc   initrd.img      lib         mnt    root  sys  var
cdrom  **home**  initrd.img.old  lost+found  opt    sbin  tmp  vmlinuz
larry@larry-desktop:/home$ 

Any ideas would be welcome.

What is in home and larry ? (/home/home and /home/larry)

Looks like this is a backup and not your old home partition.

---

### Post by HareBall on 2006-11-15
> **bodhi.zazen said:**
> What is in home and larry ? (/home/home and /home/larry)

Looks like this is a backup and not your old home partition.

Nothing in /home/home, even when I show hidden files and just desktop and examples in /home/larry unless I show hidden files.
I guess it's gone:(

---

### Post by bodhi.zazen on 2006-11-15
> **HareBall said:**
> Nothing in /home/home, even when I show hidden files and just desktop and examples in /home/larry unless I show hidden files.
I guess it's gone:(

/home/larry at least looks like a home directory, but I assume you are missing some data.

I am so sorry, but the only other thought I would have are:[list][*]Hidden files in /home (.Trash), and lost+found. :(

---

### Post by HareBall on 2006-11-15
> **bodhi.zazen said:**
> /home/larry at least looks like a home directory, but I assume you are missing some data.

I am so sorry, but the only other thought I would have are:[list][*]Hidden files in /home (.Trash), and lost+found. :(
I tried it in /home and there wasn't anything showing up. I haven't tried to show hidden files in lost+found.
I think it is all gone now:( 
If they weren't gone, I am sure my music file would show up on the desktop. It doesn't.

---


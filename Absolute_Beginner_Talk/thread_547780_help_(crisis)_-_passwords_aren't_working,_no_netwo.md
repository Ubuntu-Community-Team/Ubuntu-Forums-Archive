---
title: "help (crisis) - passwords aren't working, no network &amp; can't mount flash drive"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ZenMasta on 2007-09-10
I had finished configing ubuntu server this weekend and everything was working flawlessly. Not usint a window manager, just webmin. Then I come in this morning and the box wont get an IP and then obviously non of the computer file shares would work nor could I login to webmind. 

On top of that the root passwords are not working and I'm totally frustraded. I've even installed a 2nd nic to see if the first one failed but it doesn't even list the new one when I type ifconfig.

So now, I'm trying to just backup files so I can reformat but it's not mounting my usb flash drive. I have been able to use this same flash drive on other ubuntu desktops... although I don't believe it would make a difference but the ones it had worked on previously were using gnome window manager.

When I plug in my flash drive this is what displays on the console

[     75.885591] sdb: assuming drive cache: write through
[     75.902577] sdb: assuming drive cache: write through

when I type df -k 
this is all that shows

/dev/sda1
varrun
varlock
procbususb
devshm

The same is displayed before and after plugging in the usb flash drive.

When I type
tail -f /var/log/messages 
here's what displays


usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
scsi 2:0:0:0: Direct-Access LEXAR      JUMPDRIVE PRO 0   PQ: 0 ANSI: 2
SCSI device sdb: 503808 512-byte hdwr sectors (528MB)
sdb: Write Protect is off
sdb: sdb1
Attached scsi removable disk sdb
Attached scsi generic sg2 type 0


If anyone can help me out with this you'd make my day. I'm at sooo frustrated right now :confused:

Thanks in advance,
Rob

---

### Post by Soybean on 2007-09-10
Ok... what passwords aren't working exactly? You seem to be able to log in...?

Regarding the flash drive,
```
sudo fdisk -l /dev/sdb
```
might help to figure out what's going on.

---

### Post by ZenMasta on 2007-09-10
Oop I wasn't specific. The root/sudo passwords are not working. 

I was able to type 
fdisk -l /dev/sdb and that displayed something like

Disk /dev/sdb: 257MB

Device Boot
/dev/sdb1      Fat 16

I was then able to type cp /home/dir/myfile /dev/sdb 

it took a few seconds to display a blank console so I figured the delay was it actually copying the file. But then after that I could not type cp /home/dir /dev/sdb
it said, cp: ommitting directory '/home/dir'

Finally, I could not plug the flash drive back into my windows pc because it said it wasn't formatted so it's absolutely critical that I use a file system that I can read on windows (but considering the console said Fat16 I don't see what the problem is).

---

### Post by ZenMasta on 2007-09-10
At this point I need to figure out some other option because I've tried reformatting the drive on windows (both fat 16 and fat 32) and when I plug it back into ubuntu it says a bunch of different stuff that is just overwhelming me.

I assume not but is there any way to reset the root password without the root password using recovery mode or something?

---

### Post by ZenMasta on 2007-09-10
I connected the ubuntu server and one of our windows pcs to an old netgear router and it was atleast able to get an IP from that. 

(our main router is actually a pfsense box and a cisco managed switch)

So currently I'm backing up all the files to a windows pc and I'm just going to reformat and try again.

So I appreciate you trying SoyBean.

---

### Post by bodhi.zazen on 2007-09-10
Well, ubuntu locks the root account, so no setting the root password is not the problem.

Hard to know without some of the error messages, but I am going to suggest you may have deleted your user from the admin group (possible others ?)

Boot to recovery mode and you can check group membership with 

groups <username>

You can add your user to various groups via the command line or editing /etc/group manually (with nano)

```
adduser <username> <group>
```

Or in /etc/group add your user at the end of a line, comma delineated.

---

### Post by Soybean on 2007-09-10
As bodhi.zazan says, if you can log in but not sudo, you probably need to get your user account back into the admin group. Rebooting into recovery mode is likely your best bet. On the other hand, it does sound like things have gotten a bit messed up in general there, so a fresh install is probably wise.

> **ZenMasta said:**
> I was then able to type cp /home/dir/myfile /dev/sdb 

Oh... actually, what you wanted to do there was mount /dev/sdb1 to a different directory (anywhere  in your filesystem; under /mnt or /media is standard), and copy your file to that directory. I'm not sure why the command you typed worked, but it may have been doing something crazy. ;)

> But then after that I could not type cp /home/dir /dev/sdb it said, cp: ommitting directory '/home/dir'

That's just because "cp" doesn't copy directories by default, and it's perfectly normal. I mean, aside from the fact that copying to /dev/sdb shouldn't work, as I was just saying.

You either want to use "cp -r" ro copy recursively (copy the directory and all subdirectories), or "cp /home/dir/* <target>" to copy all non-directory files in /home/dir

Good luck!

---

### Post by ZenMasta on 2007-09-10
It's too late for me to try any of those suggestions now because I've already scrubbed the drive.

But I will say that I did try recovery mode previously and I couldn't continue because it asked for the password and none of the ones I tried would work.

SoyBean, I had a typo in my original post... when it worked I was copying a specific file (just forgot to put an extension in my post) but I guess this is all moot now though because I'm reformatting. I'll remember that recursive bit for future reference though I'm sure.

Thanks again.

---


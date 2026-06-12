---
title: "move /home to new  partition"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by dr_alejandro on 2007-10-06
I want to move /home to a new partition in a different HD. I have follow direction from a couple of blogs. I already used Gparted to create a partition (hdb1). So far I have done 

$ sudo mkdir /mnt/newhome
$ sudo mount -t ext3 /dev/hdb1 /mnt/newhome
$ cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
$ sudo umount /mnt/newhome

But when I execute the next command

$ sudo mv /home /old_home

I get 

mv: cannot move `/home’ to `/old_home’: Device or resource busy 

I  did cd / and tried to execute the mv command from that directory and got the same result

I went to the loggin screen and did ctr+alt+F1 logged as root and tried to do the mv command and same thing.

Please don't refer me to [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) .

I installed ubuntu using wubi does that matter?
Does anybody knows how to implement that mv command?

Thanks for your time.

---

### Post by taurus on 2007-10-06
You cannot move /home/$HOME while you are using it!  Try doing that from a recovery mode from GRUB menu.

---

### Post by dr_alejandro on 2007-10-06
How do I do that?
How do I go to the recovery mode?
What is GRUB?

I'll appreciate your time.

---

### Post by taurus on 2007-10-06
When you first turn on your computer, you will see the screen about your video and/or RAM.  Then, you will see a GRUB screen and you have 3 seconds to press a key or else it will boot Ubuntu.  Press ESC at that screen and you will see a menu.  Scroll down to the second option (usually) that says something about Recovery Mode and boot from that.  It will drop you into a prompt as root so you don't need to use the sudo in front of a command anymore.  That's what we call recovery mode.

When done, reboot your machine with

```
shutdown -r now
```

---

### Post by ryanVickers on 2007-10-06
> **taurus said:**
> .../home/$HOME...

I'm pretty sure that the variable "$HOME" is the _full_ path, so what you have there would result in "/home/home/username" ;)

---

### Post by dr_alejandro on 2007-10-06
taurus;

I booted in the recovery mode and logged as root but I still get the same result when I try
 
mv /home /old_home

I installed ubuntu through wubi. Does that matter?

How can I use the command prompt from a different directory?

---

### Post by taurus on 2007-10-06
Can you post the output of this command from a prompt in the recovery mode?

```
df -h
```

---

### Post by dr_alejandro on 2007-10-06
root@mofongo:~# df -h
Filesystem		Size	Used	Avail	Use%	Mounted on
/media/host/wubi/disks/system.virtual.disk
			7.4G	2.9G	4.2G	41%	/
varrun			506M	12K	506M	1%	/var/run
varlock			506M	0	506M	0%	/var/lock
procbususb		506M	116K	506M	1%	/proc/bus/usb
udev			506M	116K	506M	1%	/dev
devshm			506M	0	506M	0%	/dev/shm
lrm			506M	33M	473M	7%	/lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
			939M	846M	46M	95%	/home
root@mofongo:~#

---

### Post by dr_alejandro on 2007-10-06
root@mofongo:~# df -h
Filesystem                        Size     Used    Avail    Use%    Mounted on
/media/host/wubi/disks/system.virtual.disk
                                        7.4G    2.9G   4.2G      41%    /
varrun                             506M   12K    506M      1%      /var/run
varlock                            506M    0       506M       0%     /var/lock
procbususb                     506M   116K  506M      1%      /proc/bus/usb
udev                               506M   116K  506M      1%      /dev
devshm                           506M    0       506M      0%      /dev/shm
lrm                                   506M  33M    473M      7%      /lib/modules/2.6.20-16-generic/volatile
/media/host/wubi/disks/home.virtual.disk
                                       939M   846M  46M        95%    /home
root@mofongo:~#

---

### Post by dr_alejandro on 2007-10-06
sorry I tried to space it better so it looks more clear but when I submit the post it changes the spacing

---

### Post by taurus on 2007-10-06
> **dr_alejandro said:**
> root@mofongo:~# df -h
Filesystem                        Size     Used    Avail    Use%    Mounted on
/media/host/wubi/disks/system.virtual.disk
                                        7.4G    2.9G   4.2G      41%    /
varrun                             506M   12K    506M      1%      /var/run
varlock                            506M    0       506M       0%     /var/lock
procbususb                     506M   116K  506M      1%      /proc/bus/usb
udev                               506M   116K  506M      1%      /dev
devshm                           506M    0       506M      0%      /dev/shm
lrm                                   506M  33M    473M      7%      /lib/modules/2.6.20-16-generic/volatile
/[B][COLOR="Blue"]media/host/wubi/disks/home.virtual.disk
                                       939M   846M  46M        95%    /home[/COLOR][/B]
root@mofongo:~#

Is that the new /home or the old one?

---

### Post by dr_alejandro on 2007-10-06
the original home, so the old one

---

### Post by dr_alejandro on 2007-10-07
I was looking online and I found LVPM (Loopmounted Virtual Partition Manager). It allows you to increase the size of the /home directory with a few clicks :) You must have installed Ubuntu through Wubi or Lubi. So I did this instead of moving /home to a new partition.

Thank you for your help.

---

### Post by derekr44 on 2007-10-07
Just an FYI (I did this not more than two days ago), you need to use your copy command from the CLI and be logged in as root, not yourself.  Once you log in as yourself, your /home folder is in use.

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
[http://wiki.linuxquestions.org/Add_a_new_hard_drive](http://wiki.linuxquestions.org/Add_a_new_hard_drive)

---


---
title: "New to Ubuntu"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by martinckl on 2007-12-31
Hello all:

I am new to Ubuntu and just install Ubuntu on my new hard drive that also have a second hard drive containing Windows XP in it. What do I need to do in order for me to share the files between the two hard drives? I would very much appreciated if you can show me step by step how to do it or guide me to the proper direction.

Regards

Martin

---

### Post by taurus on 2007-12-31
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number 1.

---

### Post by martinckl on 2007-12-31
Thanks for the quick reply. What does this command do for me? And do I need any other commands after that?

Regards

Martin

---

### Post by taurus on 2007-12-31
It displays your harddrive partitions so I would know which partition your ntfs filesystem is. Then, you need to gedit /etc/fstab and add an entry to it so your ntfs partition will be mounted automatically each time you boot.

---

### Post by martinckl on 2007-12-31
Thanks for the reply again. It show as follow:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfba5fba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18707   150263946   83  Linux
/dev/sda2           18708       19457     6024375    5  Extended
/dev/sda5           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ac96545

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS
mleung@C2DQ:~$

---

### Post by taurus on 2007-12-31
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ntfs-3g   defaults   0   0
```
Save it and close down gedit window.  Now, install ntfs-3g driver (so you can write to it), create a new mount point for it, and mount it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -a
ls -la /media/sdb1
```

---

### Post by martinckl on 2007-12-31
Hello:

I think I understand that you help me put my Windows XP hard drive (which is the NTFS or  you call it sdb1) under media and it seems to work after reboot. But I can not see any of my folders and files in the sdb1 folder under media. What did I do wrong?

Regards

Martin

---

### Post by taurus on 2007-12-31
What are the output of these commands?

```
df -h
ls -la /media/sdb1
```

---

### Post by martinckl on 2007-12-31
as follow:

mleung@C2DQ:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  2.3G  132G   2% /
varrun               1005M   84K 1005M   1% /var/run
varlock              1005M     0 1005M   0% /var/lock
udev                 1005M  100K 1005M   1% /dev
devshm               1005M     0 1005M   0% /dev/shm
lrm                  1005M   34M  971M   4% /lib/modules/2.6.22-14-generic/volatile
mleung@C2DQ:~$ ls -la /media/sdb1
total 8
drwxr-xr-x 2 root root 4096 2007-12-31 22:13 .
drwxr-xr-x 4 root root 4096 2007-12-31 22:13 ..
mleung@C2DQ:~$

---

### Post by taurus on 2007-12-31
Okay, I bet if we try to mount it by hand, it will complain about you didn't shut down windows cleanly so you have to use the force option to mount it.

Run

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
and see what happens.

---

### Post by martinckl on 2007-12-31
You are absolutely correct. Please refer below:

mleung@C2DQ:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
[sudo] password for mleung:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0
mleung@C2DQ:~$

---

### Post by taurus on 2007-12-31
So, you either boot windows up and shut it down cleanly (means no hibernation or sleeping mode).  Then, boot into Ubuntu to see if /dev/sdb1 is mounted to /media/sdb1 now or you can use the force option now if you wish.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
ls -la /media/sdb1
```

---

### Post by martinckl on 2007-12-31
If I am using the Force option what is the potential damage or disadvantage will I be facing?

Martin

---

### Post by taurus on 2007-12-31
If you don't feel comfortable with the force option, then reboot your machine to windows and run a scandisk.  Then, shut it down cleanly this time and will see if Ubuntu mounts it automatically when it boots up.

---

### Post by martinckl on 2008-01-01
Ok thank you very much for helping and I will do as you suggested and see what happen. I might have to trouble you again later on and thanks again.

Regards

Martin

---

### Post by martinckl on 2008-01-01
Hello again:

Firstly, I wish you and your family a happy new year and secondly I would like to thank you for helping me for the past hours. It is now working great! But there are something about a certain command line that I don't really understand. Please help me throughly comprehend the concept of this command and its functions. Please see below:

sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -a
ls -la /media/sdb1

*note that my problem lies with the second, third and forth command lines where it states "-3g" at the end of the second line. Also I am wondering why the "sdb1" is inside the "media" and not just at the root of the hard drive on the third line. Since I am a Windows user switching to Ubuntu, I have gotten used to seeing a separate hard drive by itself or the folder in the root directory of a hard drive. Even though I know that you are right by putting it under media, I am still confused about the reason of the placement of the folder when there are so many other folders you can put it under. Please explain.  Lastly, the problem I have in the fourth line is a minor thing where there is a "-a" at the end, would that be just a variable or is it something specific?


P.S: Are there any books/websites based on the basics of the command lines of Ubuntu or Linux out there that can assist me with my troubles.? If so please inform me of any that you think may help me.

---

### Post by taurus on 2008-01-01
> **martinckl said:**
> 
sudo apt-get update
sudo apt-get install ntfs-3g  <-- [COLOR="Blue"]Install ntfs-3g driver so you can read and write to ntfs partition.[/COLOR]
sudo mkdir /media/sdb1  <-- [COLOR="Blue"]Create a mountpoint.  You can call it whatever you want here.[/COLOR]
[COLOR="Blue"](If you want to mount it to /windows, you can too.  Just create a mountpoint /windows and mount /dev/sdb1 there.)[/COLOR]
sudo mount -a  <-- [COLOR="Blue"]Mount all the partitions in /etc/fstab.  If partition is already mounted, it moves on.  If it hasn't been mounted, it will mount it.[/COLOR]
ls -la /media/sdb1


If you want to know more about the mount command, just look at the manpage with

```
man mount
```

---


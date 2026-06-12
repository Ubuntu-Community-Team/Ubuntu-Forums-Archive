---
title: "/boot partition showing full and cannot get K7"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-20
I have a 48MB /boot partition
Here is what I did: 

using Adept I installed linux-k7

I checked /boot/grub/menu.lst and no entry for k7 was in there.
so I did:
sudo update-grub

here is what happened:

Updating /boot/grub/menu.lst ... /sbin/update-grub: line 940: /boot/grub/menu.lst.new: No space left on device 

Why is this???

In Konqueror it shows properties for /boot:

23 files, 1 sub folder taking up 14.9MB
Then free disk space shows: 0B out of 47.1MB 

Why?  Its like there is no space left, but really there is.

How do I get the K7 kernel working when I can't even save the menu.lst?

---

### Post by oscar on 2006-06-20
48MB isn't very much so you will have to make sure that there are no kernels in there that you do not use. Using synaptic search for and remove all of the old linux-headers and linux-images that you no longer use.

---

### Post by xoros on 2006-06-20
??  why does it show only 14.9MB being used then?

There should be space left.

---

### Post by taurus on 2006-06-20
What is the output of this command from a terminal then (Applications -> Accessories -> Terminal)?
```

df -h

```

---

### Post by xoros on 2006-06-20
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             973M  221M  753M  23% /
varrun                252M   96K  252M   1% /var/run
varlock               252M  8.0K  252M   1% /var/lock
udev                  252M  180K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/hda3              48M   48M     0 100% /boot
/dev/hda10             23G   68M   22G   1% /home
/dev/hda1              10G  4.0G  6.1G  40% /media/hda1
/dev/hda2              21G  4.5G   16G  23% /media/hda2
/dev/hda9             4.8G   33M  4.8G   1% /tmp
/dev/hda7              15G  1.7G   13G  12% /usr
/dev/hda8             2.0G  298M  1.7G  16% /var
tmpfs                 252M   18M  234M   8% /lib/modules/2.6.15-25-k7/volatile
```


hmm... that shows that it is all used.  
Is there any way for me to give it more space now?  I want to keep my 386 kernel in case the k7 doesn't work.

---

### Post by taurus on 2006-06-20
Now, how about
```

ls -la /boot

```

---

### Post by xoros on 2006-06-20
```
total 15154
drwxr-xr-x  5 root root     528 2006-06-20 07:56 .
drwxr-xr-x 22 root root     600 2006-06-20 07:50 ..
-rw-r--r--  1 root root  266619 2006-05-23 11:56 abi-2.6.15-23-386
-rw-r--r--  1 root root  265879 2006-06-14 07:17 abi-2.6.15-25-k7
-rw-r--r--  1 root root   69878 2006-05-23 08:47 config-2.6.15-23-386
-rw-r--r--  1 root root   69743 2006-06-14 06:42 config-2.6.15-25-k7
drwxr-xr-x  2 root root     408 2006-06-20 08:03 grub
-rw-r--r--  1 root root 6775307 2006-06-12 08:00 initrd.img-2.6.15-23-386
-rw-r--r--  1 root root 3563520 2006-06-20 07:56 initrd.img-2.6.15-25-k7
-rw-r--r--  1 root root   94760 2005-10-25 05:32 memtest86+.bin
-rw-r--r--  1 root root  725460 2006-05-23 11:56 System.map-2.6.15-23-386
-rw-r--r--  1 root root  733216 2006-06-14 07:17 System.map-2.6.15-25-k7
-rw-r--r--  1 root root 1414477 2006-05-23 11:56 vmlinuz-2.6.15-23-386
-rw-r--r--  1 root root 1492560 2006-06-14 07:17 vmlinuz-2.6.15-25-k7

```

I am not understanding why 'df -h' is showing full??  seems odd to me.

---

### Post by taurus on 2006-06-20
```

du -h /boot

```

---

### Post by xoros on 2006-06-20
```
180K    /boot/grub
15M     /boot

```

---

### Post by taurus on 2006-06-20
You don't have /boot/lost+found!!!

What does your /etc/fstab look like then?

Also, it's kind of weird that you have two different modules loading at the same time, /lib/modules/2.6.15-23-386/volatile & /lib/modules/2.6.15-25-k7/volatile.

---

### Post by xoros on 2006-06-20
[QUOTE=taurus]What does your /etc/fstab look like then?[/QUOTE]
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs defaults        0       1
/dev/hda3       /boot           reiserfs notail          0       2
/dev/hda10      /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda9       /tmp            reiserfs defaults        0       2
/dev/hda7       /usr            reiserfs defaults        0       2
/dev/hda8       /var            reiserfs defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by xoros on 2006-06-20
Should I try starting over and re-installing all of ubunutu?  I have no idea what I did though.

---

### Post by xoros on 2006-06-20
I did a re-install,  things are not looking much better.  nothing shows /boot/lost+found  and 'df -h' shows /boot at 88% full with 42MB being used.

ls -la shows:
```
total 9157
drwxr-xr-x  5 root root     336 2006-06-20 07:57 .
drwxr-xr-x 22 root root     592 2006-06-20 07:37 ..
-rw-r--r--  1 root root  266619 2006-05-23 12:56 abi-2.6.15-23-386
-rw-r--r--  1 root root   69878 2006-05-23 09:47 config-2.6.15-23-386
drwxr-xr-x  2 root root     376 2006-06-20 07:57 grub
-rw-r--r--  1 root root 6775753 2006-06-20 07:51 initrd.img-2.6.15-23-386
-rw-r--r--  1 root root   94760 2005-10-25 06:32 memtest86+.bin
-rw-r--r--  1 root root  725460 2006-05-23 12:56 System.map-2.6.15-23-386
-rw-r--r--  1 root root 1414477 2006-05-23 12:56 vmlinuz-2.6.15-23-386

```

This is from a clean format and install of kubuntu 6.06 off alternate cd!!!   What am I doing wrong?

---

### Post by graigsmith on 2006-06-20
couldn't he delete his apt cache?

---

### Post by graigsmith on 2006-06-20
my linux boot partition takes up 3.6 gigs.  and i actually have it set to a 15 gig partition, which now that i think about it, is a pretty large waste of space.

---

### Post by xoros on 2006-06-20
I guess if I need to re-format again,  I will try to resize the boot partition. 
But what is a recommended size for it then?  
What is shown being used and what is being occupied seems to be 2 entirely different things!!  What the hell??

---

### Post by taurus on 2006-06-20
Maybe you should consider using ext3 for /boot instead of reiserfs!!!  In other words, set /boot as ext3 and everything else as reiserfs...

---

### Post by xoros on 2006-06-20
> Maybe you should consider using ext3 for /boot instead of reiserfs!!! In other words, set /boot as ext3 and everything else as reiserfs...

Is that what the problem is?  Can I keep it the same size or what size is better? 100MB ?  500MB?  300000000000000000TB?   How does a person know how much space it is going to use?????????

---

### Post by taurus on 2006-06-20
Could be but 50MB for /boot should be enough for 2 kernels or so.  I have two kernels, the i386 default and i686-smp, and /boot only uses 23MB,

12K     /boot/lost+found
171K    /boot/grub
19M     /boot

---

### Post by anaconda on 2006-06-20
You could do as I.
make your 48MB boot partition your GRUB-partition, and move the contents of your current /boot to the same partition than the rest of your system..

you would have to edit your fstab-file, so that nothing is mounted to /boot , because then you would actually have stuff in /boot...  And you could also mount the Grub-partition somewhere, so that you can edit menu.lst if you want.. how about /Grub..

Then you would have an independent grub-partition, so that when you reistall ubuntu, or whatever you newer lose your boot loader. You could still boot your other OS:ses.. eg. other linuxes, and windows...

You dont need anything else in the GRUB partition than Grub... ~5MB ?

---

### Post by xoros on 2006-06-20
taurus: thanks, you were correct making /boot ext3 did the trick.  Thank you!! :)

anaconda: that sounds interesting,  but not quite following you.  You mean to put the contents of /boot to root?  and just have the grub files in /boot?  But I have grub installed to the MBR;  does that matter in this too?

---


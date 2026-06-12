---
title: "LiveCD problems"
date: 2007-12-23
forum: Apple PPC Users
---

### Post by woopud on 2007-12-23
I'm trying to run Ubuntu on my B/W G3/400, booting from the liveCD and typing "live"  gets me to the large UBUNTU print and the orange progress bar, after going back and forward for a minute or so I get the following:

/bin/sh: can't access tty; job control turned off
(initramfs)

Bert

---

### Post by erfahren on 2007-12-23
your trying to run it on what? 

I've heard of that coming up when the hardware is too old to run Ubuntu. If that's the case try Xubuntu and see what that does.

---

### Post by RelativelyQuantum on 2007-12-23
I've experienced the same problem, and I can safely say my hardware is _not_ too old. I've tried to run Edgy, Feisty, and finally Dapper on a brand new black macbook, 160 GB HDD, 1 GB RAM, 2.2 GHz Core duo processor, with the same results each time. First I wind up with an x server error; the live cd seems not to recognize my screen. That, to me, sounds like a problem with the software; ie, _it_ is too old. I thought modifying the x server before burning the ISO might solve the problem, but right not I have no idea how to do that. Does this happen on the Gutsy installation?

---

### Post by erfahren on 2007-12-23
> **RelativelyQuantum said:**
> I've experienced the same problem, and I can safely say my hardware is _not_ too old. I've tried to run Edgy, Feisty, and finally Dapper on a brand new black macbook, 160 GB HDD, 1 GB RAM, 2.2 GHz Core duo processor, with the same results each time. First I wind up with an x server error; the live cd seems not to recognize my screen. That, to me, sounds like a problem with the software; ie, _it_ is too old. I thought modifying the x server before burning the ISO might solve the problem, but right not I have no idea how to do that. Does this happen on the Gutsy installation?
do you think this might work? [http://ubuntuforums.org/showthread.php?t=448809](http://ubuntuforums.org/showthread.php?t=448809)

---

### Post by RelativelyQuantum on 2007-12-23
wow...thanks alot! This looks like it's exactly what I needed. I'll post again once I've tried a few things and [I hope] gotten around the problem, so that anyone in the same situation can learn from my experience.

---

### Post by RelativelyQuantum on 2007-12-23
Well that's rather disappointing. I just reinstalled Leopard after the attempted installation wiped it from my hard drive. In any case, when I tried to modify my xorg.conf, the machine simply created a separate file and disallowed me from accessing the xorg setting on the CD. I'll keep trying, but it anyone has information it would be more than helpful.

---

### Post by king_arthur on 2007-12-25
> **woopud said:**
> I'm trying to run Ubuntu on my B/W G3/400, booting from the liveCD and typing "live"  gets me to the large UBUNTU print and the orange progress bar, after going back and forward for a minute or so I get the following:

/bin/sh: can't access tty; job control turned off
(initramfs)

Bert

Your hardware should be fine, I would suggest you start troubleshooting from here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

/P

---

### Post by woopud on 2007-12-29
Well, I tried it using this info [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) but it still won't work. After typing: live-nosplash-powerpc video=ofonly break=top I get to the busybox with the blinking cursor but it won't let me type anything, the cursor just stay's in place blinking.

Bert

---

### Post by roazena on 2007-12-29
"break=top" usually kills the keyboard for me, too. I suspect it breaks before the keyboard driver is loaded. Try omitting that parameter.

---

### Post by indianajoost on 2007-12-29
I have excactly the same problem. My keyboard is also dead after ```
live-nosplash-powerpc video=ofonly break=top
```.

When I don't use 'break-top' the process stops at busy box shell and when I try
```
modprobe ide-core
``` and then
```
exit
``` I get the following errors:

cp unable to open '/root/var/log/' no such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed no such file or directory
mount: Mounting /sys on root/sys failed no such file or directory
mount: Mounting /proc on root/proc failed no such file or directory
Target filesystem doesn't have /sbin/init

Does anyone know what to try next?

P.s. Bert, wat doet een Nederlander in Colorado?;-)

---

### Post by woopud on 2007-12-29
> **indianajoost said:**
> I have excactly the same problem. My keyboard is also dead after ```
live-nosplash-powerpc video=ofonly break=top
```.

When I don't use 'break-top' the process stops at busy box shell and when I try
```
modprobe ide-core
``` and then
```
exit
``` I get the following errors:

cp unable to open '/root/var/log/' no such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed no such file or directory
mount: Mounting /sys on root/sys failed no such file or directory
mount: Mounting /proc on root/proc failed no such file or directory
Target filesystem doesn't have /sbin/init

Does anyone know what to try next?

P.s. Bert, wat doet een Nederlander in Colorado?;-)

I get exactly the same thing.

Bert

---

### Post by chayzer on 2008-01-03
Came to that same problem.. finally had to go back to an older version and then upgrade afterwards.. not ideal but it got me going.

---

### Post by woopud on 2008-01-03
> **chayzer said:**
> Came to that same problem.. finally had to go back to an older version and then upgrade afterwards.. not ideal but it got me going.

What version did you use ?  And did you use the LiveCD ?

Bert

---

### Post by chayzer on 2008-01-03
I actually went back to 6.10 (edgy) as it was the last officially supported release. Upgraded it to feisty and feisty worked well. I would suspect you would be perfectly fine using the feisty disk and I might go back and do a clean install of feisty and one upgrade once I work the kinks out. Tried to upgrade to gutsy and it wouldn't boot. Just got the busybox screen...

```

modprobe ide-core
exit

```

That got it to boot into gutsy. Then I tried the adding ide-core to /usr/share/initramfs-tools/modules and running update-initramfs -u, which did nothing for me. It would still boot to busybox, but booting into 'old' at yaboot prompt would boot nicely. So i just updated symlinks in /boot to point to my other kernel. I imagine there's some sort of yaboot configuration or some other way that isn't brute force.. 

but I used

```

ln -s -f /boot/initrd.img-2.6.'whatever kernel boots' /boot/initrd.img
ln -s -f /boot/vmlinux-2.6.'same as above' /boot/vmlinux
```

and then

```

ln -s -f /boot/initrd.img-2.6.'whatever kernel you want as old in yaboot' /boot/initrd.img.old
ln -s -f /boot/vmlinux-2.6.'same as above' /boot/vmlinux.old

```

USE AT YOUR OWN RISK. If you don't have the proper symlinks in there, you're kinda hooped for booting. Did that once and luckily the Edgy disk has a 'rescue' boot option, not sure about the feisty disk.

So basically running everything gutsy on the feisty kernel for now.. and wait until there's a kernel update I guess.. might try compiling a kernel tonight...

---

### Post by chayzer on 2008-01-03
Actually a safer way to boot into other kernels would probably be to add them to your /etc/yaboot.conf

But where's the fun in that.

---

### Post by chayzer on 2008-01-03
Okay.. from what I can tell, it looks like you edit up your /etc/yaboot.conf file with whatever different kernels you want to have as an option to boot.

```
sudo ybin
```

Will write your conf file to the bootstrap so when you restart yaboot has some different boot options. Now it's just time to figure out why ide-core isn't loading properly...

---

### Post by woopud on 2008-01-11
Well, couldn't figure out the liveCD so i got the alternate install cd (7.04).   After boot I type "install" hit enter, then it says "loading kernel" then ...black screen...  nothing happens.   Any commands I can type besides install ?

Bert

---

### Post by woopud on 2008-01-12
Well, i finaly got it to boot, I had to disconnect my internal Zip drive but now it won't startx... I saw something on here before about editing the video modes before booting.   Anyone can point me in the right direction ?

Bert

---

### Post by woopud on 2008-01-13
Well, I was finaly able to install 7.10 using the alternate install cd, installation was a breeze and I can now dual boot between OS X and Ubuntu !

Bert

---


---
title: "Boot problem after apt-get update"
date: 2007-03-30
forum: Apple Intel Users
---

### Post by PictureThis on 2007-03-30
I did a "sudo apt-get update/sudo apt-get upgrade", rebooted and can now not get beyond the Kubuntu splash screen. The progress bar fills only halfway before the screen turns black and I end up with a blinking cursor. Keyboard input is recognized, I can type letters but pressing "Esc" writes "^[" on screen.

If I press the power-button the Kubuntu splash screen shows itself again and my MacBook shuts down.

I can not press "Esc" to get into the menu during the GRUB loading stage.

Any other possibility of booting into recovery mode/bringing up the terminal or should I start looking for my LiveCD?

Edit: I'm back in business. I remember seeing a <ctrl><alt><F2> command but that didn't do anything, for the MB pressing <fn><ctrl><alt><F2> presented the login option. I did a "sudo dpkg-reconfigure xserver-xorg" and after rebooting could resume "Feistying" :)

---

### Post by x64Jimbo on 2007-03-30
I'm not too sure of what happened to your install, but I do know that apt-get is rapidly becoming deprecated, and the preferred apt package manager is aptitude.

---

### Post by Gen2ly on 2007-03-30
Check the disk with fsck from the Live CD.  Add the appropriate drive and filesystem-type.
> fsck.ext3 -pf /dev/sda3
reiserfsck --fixfixable /dev/sda3

---

### Post by PictureThis on 2007-03-30
> **Dirk.R.Gently said:**
> Check the disk with fsck from the Live CD.  Add the appropriate drive and filesystem-type.

Thanks:
```
ubuntu@ubuntu:~$ sudo fsck.ext3 -pfv /dev/sda3

  137439 inodes used (5.57%)
    1408 non-contiguous inodes (1.0%)
         # of inodes with ind/dind/tind blocks: 7039/101/0
 1088350 blocks used (22.05%)
       0 bad blocks
       1 large file

  117056 regular files
   13028 directories
     134 character device files
      26 block device files
       2 fifos
      87 links
    7182 symbolic links (6589 fast symbolic links)
       2 sockets
--------
  137517 files
```

No error codes so it seems all is well in that area. ReiserFS is not present on my MB.

---

### Post by trevelyn on 2007-04-01
my macbook did this too, as i was following the instructions to get xgl working.  In KDE I decided to update the system with the 182 new updates, and X would just freeze the whole computer at boot.  I had to just re-install.  When i did the full system upfdate with plain old Ubuntu and gnome it went flawlessly.

---


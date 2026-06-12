---
title: "edgy hangs at upsplash"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by goofey24 on 2007-01-06
my machine is edgy eft. i am having a problem getting to login screen. using live dapper cd to access form. when i turn on my computer it hangs at the progress bar. ](*,) thank you

---

### Post by Maxcribbin on 2007-01-06
Had similar problem.
I disconnected my hard drive.
Booted.

Reconnected it then rebooted.
reconfigured startup devices at bios so hard drive was no 1.

An it worked...

Dont understand it, but it worked?


Carl.

---

### Post by taurus on 2007-01-06
Boot into LiveCD.  Open a terminal, Applications -> Accessories -> Terminal, and mount your harddrive from it.

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming Edgy is on /dev/hda1...)
```
Now, you need to edit /boot/grub/menu.lst on the harddrive to remove the quiet splash from the kernel entry so you can see exactly where the problem is when it boots...

```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```
Scroll down near the end until you see the line that starts with **kernel**.  At the end of that line, remove both **quiet splash** and save it.  Unmount it with

```
sudo umount /mnt/ubuntu
```
and reboot.  Don't forget to remove the LiveCD so it will boot from the harddrive.  Now, what is the last line on the screen before it hang?

---

### Post by DougieFresh4U on 2007-01-06
Dawn, follow tarus is gonna assist, get me on cell

---

### Post by goofey24 on 2007-01-07
this is where I am stuck at this point. The fixes recomemended didn'twork. When I turn machine on,it goes through the grub deal and it gets to progrss bar and hangs andthen after a minute it goes to flashing cursor in upper left corner. I am using dapperlive cd to beon forum and I am running edgy on machine. I hope some one can help as I am new at this linux thing, thanks

---

### Post by taurus on 2007-01-07
Sounds like an X problem! Can you log in from the console with your username and password at all?  If you can, try to reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
(If not sure about a question, just use the default value and use vesa as the driver for your graphic card.)
```

---

### Post by goofey24 on 2007-01-07
Ican get command line from grub.other than that I am stuck with live cd as I am on now, good morning to you :)

---

### Post by taurus on 2007-01-07
When you see the screen about GRUB, press Esc (you have three seconds to do that or it will boot Ubuntu) and use the down arrow to highlight the recovery mode.  Boot from that.  Does it work at all?  Do you see a prompt?

---

### Post by goofey24 on 2007-01-07
tried that and it ask for login then pword then hangs below pword flashing cursor

---

### Post by taurus on 2007-01-07
The recovery mode shouldn't ask you for a login name and password since it will boot directly into X!  You said that you can run the LiveCD from your computer, right!  Boot up the LiveCD and at the prompt, post the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by goofey24 on 2007-01-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by taurus on 2007-01-07
> **goofey24 said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$

Okay.  Here is what we are going to do.  We will mount your harddrive from the LiveCD and then we will copy the working version of xorg.conf from the LiveCD to your harddrive.  Hopefully, that would fix the problem that you are experiencing with X on your computer.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo diff /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf 
sudo umount /mnt/ubuntu
```
Now, reboot and remove the LiveCD so your machine can boot from the harddrive.  See if the GUI login screen comes up or not!

---

### Post by goofey24 on 2007-01-07
sorry no luck.when reboot it ask for login and pword on blackscreen then starts going through pages and pages of numbers & jibberish, so I am back on live cd again. does this mean I should reinstall again or is this fixable?

---

### Post by taurus on 2007-01-07
I am not sure exactly I understand your problem!  When you turn on your computer, it asks you for a login name and password before it boots?

---

### Post by goofey24 on 2007-01-07
it starts loading kernel and starts it'scountdownto press escape for grub then black screen with login shows up it says unknown $ login_ then ask for password then starts scrolling through pages and pages of numbers and words

---

### Post by taurus on 2007-01-07
Probably best to reinstall Ubuntu again.

---


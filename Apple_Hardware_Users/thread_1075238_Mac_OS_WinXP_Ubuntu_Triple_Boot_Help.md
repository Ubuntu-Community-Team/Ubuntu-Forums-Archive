---
title: "Mac OS/ WinXP/ Ubuntu Triple Boot Help"
date: 2009-02-20
forum: Apple Hardware Users
---

### Post by SpAM_CAN on 2009-02-20
I am lost here.

I have a macbook 2.1 and I currently have Mac OSX and Windows XP installed. When I install Ubuntu into my empty partition (Yes I have a swap partition too) rEFIt does not show and Mac OSX will not start, and the firmware cannot detect any operating systems. So i go into my LiveCD and delete Linux. I restart and Mac OSX shows again! No rEFIt however but I just have to re-enable that.

Can anyone help? This is what my Disk Utility says: (I know there is 2 Linux Swaps) [IMG]http://i716.photobucket.com/albums/ww166/SEANIXproductions/SnapzProXScreenSnapz001.jpg[/IMG]

I heard about this GRUB thing but I am clueless about what to do with it.

---

### Post by SpAM_CAN on 2009-02-20
I think I might have done it, but will post if otherwise.

---

### Post by SpAM_CAN on 2009-02-20
Got it. Just had to set mount point to "/" and install boot manager to the same partition as Ubuntu. Then I used partition tool in rEFIt and viola! Triple boot on my MacBook! Now all I need is another OS and QUADBOOT!

You can lock this thread if you want :popcorn:

---

### Post by cyberdork33 on 2009-02-20
> **SpAM_CAN said:**
> Got it. Just had to set mount point to "/" and install boot manager to the same partition as Ubuntu. Then I used partition tool in rEFIt and viola! Triple boot on my MacBook! Now all I need is another OS and QUADBOOT!

You can lock this thread if you want :popcorn:
Good job. You also seemed to have created multiple swap partitions in the process of installing more than once.

---

### Post by SpAM_CAN on 2009-02-20
Yeah I know, but as they are mounted even when using the LiveCD I can't get rid of them :(

---

### Post by cyberdork33 on 2009-02-20
> **SpAM_CAN said:**
> Yeah I know, but as they are mounted even when using the LiveCD I can't get rid of them :(
unmount them :)

see the "swapoff" command. (I also think it is an option when you right click on it in gparted.)

---

### Post by SpAM_CAN on 2009-02-20
It wouldn't let me unmount them, but I will try that command. Thanks!

---

### Post by SpAM_CAN on 2009-02-21
Huh... I deleted the Swap partitions, and when I tried to make one big one in its place, but it comes up with an error. Says that it can't recognize it and comes up with a format "Unknown", and that it does not have the correct permissions.

Anyone?

---

### Post by cyberdork33 on 2009-02-22
> **SpAM_CAN said:**
> Huh... I deleted the Swap partitions, and when I tried to make one big one in its place, but it comes up with an error. Says that it can't recognize it and comes up with a format "Unknown", and that it does not have the correct permissions.

Anyone?where does it say that? You might need to modify your fstab file.

---

### Post by SpAM_CAN on 2009-02-22
It says that I don't have the right permissions when I boot up Gparted, and it can't read it properly and when I partition the Linux Swap it comes up with some kind of error then the partition file system is labeled Unknown.

What is a fstab file?

Oh and it may interest you that at the time of the error my Windows installation on Partition 2 died. Could be a messed up partition table maybe?

---

### Post by cyberdork33 on 2009-02-22
> **SpAM_CAN said:**
> Oh and it may interest you that at the time of the error my Windows installation on Partition 2 died. Could be a messed up partition table maybe?
it sounds like it.

Is gparted prompting you for the admin password?

fstab tells your system what partitions to mount on startup

---


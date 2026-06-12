---
title: "Error message"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by CoreDefence on 2007-07-17
Hi,
I'm trying to set up Ubunu on a system I've been tinkering with. OS starts to boot OK then I get this error message:

'Failed to start X server (your graphical interface) It is likely it is not set up correctly'

The graphics card is GForce4 MX440 

Any suggestions?

Thanks in advance,
Core

---

### Post by overdrank on 2007-07-17
> **CoreDefence said:**
> Hi,
I'm trying to set up Ubunu on a system I've been tinkering with. OS starts to boot OK then I get this error message:

'Failed to start X server (your graphical interface) It is likely it is not set up correctly'

The graphics card is GForce4 MX440 

Any suggestions?

Thanks in advance,
Core

Hi if you select ok and get to the command prompt and enter your user name and password then enter the command
```
sudo dpkg-reconfigure xserver-xorg
```
answer the questions and if you dont know the answers then leave the default answer given and restart
```
sudo shutdown -r now
```
hopefully this will get you to the gui and then you can search the forums for that video card.

---

### Post by useResa on 2007-07-17
You could try to reconfigure your X server by issuing the following command ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CoreDefence on 2007-07-17
Thanks for the suggestions, I'll try them now, fingers crossed.
Core

---

### Post by AlexenderReez on 2007-07-17
i suggest you to correct using live cd rather than 

> sudo dpkg-reconfigure xserver-xorg

system detect is better than our configuration....like this..boot in live cd then...

create mount point ,mount your root partition --->

open terminal --->
> sudo mkdir /mnt/correct
sudo mount /dev/*d** /mnt/correct

*d** = your partition like sda1 or hda1
> sudo chroot /mnt/correct su

> gksudo gedit /etc/X11/xorg.conf

open another terminal

> gksudo gedit /etc/X11/xorg.conf

copy all text in second text editor that open from second terminal and replace it to first text editor that open from first terminal....

> sudo reboot

---

### Post by CoreDefence on 2007-07-17
Oh dear! Far too advanced for me. I think I'd better start another thread, explain my situation in detail and see if I can be directed twards 'Absolute Numpty's' Forum.

Thanks for the replies, I'll post again in more detail.

Core

---


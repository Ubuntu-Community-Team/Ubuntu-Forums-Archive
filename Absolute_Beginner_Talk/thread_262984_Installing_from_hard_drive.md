---
title: "Installing from hard drive"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Wien_Sean on 2006-09-22
Ok this has been a weeks worth of trying to get my damn laptop working. I have trying to install Ubuntu (64 bit), XP, and OSX. I got OSX installed on one of the partitions. The DVD drive is dying so it can hardly be used to boot but I can get the boot screen from the live CD, but then the system hangs (I waited hours). I did check to make sure the disk is fine and it is. Right now I have the hard drive out of the laptop and connected to my desktop running XP, so I can move files and access the drive. I am running VMWare also, so I can install Ubuntu onto a virtual machine and access the Linux partition. Is there anyway to use what I have to start an install, or to move the files over and then start the install that way? I am sorry if this doesn't make any sense but I have been working on this every waking hour for the past week trying to get these various OSs to install. Also it won't boot from a USB drive, the bios doesn't support it. Also this is an AMD64 3200+. Let me know if need more specs. Thanks!

---

### Post by Brunellus on 2006-09-22
if the machine can boot from ethernet, and you have another computer to serve as a netboot server, you can install ubuntu over the network according to this howto

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by Wien_Sean on 2006-09-22
Wow fast reply, I haven't even finished copying over the XP install files. I do have the PXE option also so I will give it a shot. I am not new to Linux but this kind of stuff seems a but over my head at the moment but I will give it a try and get back to you, Cheers!

---

### Post by Wien_Sean on 2006-09-22
Alright, done! And it turns out that a similar method can be used for installing XP. It is a lot more complicated. Basically booting a BartPE iso via PXE and then starting the XP install, ugh. Thanks!

---

### Post by Brunellus on 2006-09-22
> **Wien_Sean said:**
> Alright, done! And it turns out that a similar method can be used for installing XP. It is a lot more complicated. Basically booting a BartPE iso via PXE and then starting the XP install, ugh. Thanks!
YEHEY!  always cool to see something like this work right.

My only netboot install so far was an exercise in creepy voodoo.  It worked, and it felt weird to see it working over the network like that.  

You wonder if a university linux usergroup wouldn't just offer a bootserver for this sort of thing to make installations quick over their local academic network

---

### Post by Wien_Sean on 2006-09-23
Yeah it was a bit strange having an XP setup boot up a Linux install over a network. The XP install is not going as planned. I never would have thought I would see the day when it was faster and more simple to install Linux than Windows.

---


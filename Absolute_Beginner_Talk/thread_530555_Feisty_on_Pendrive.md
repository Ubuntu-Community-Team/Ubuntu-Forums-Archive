---
title: "Feisty on Pendrive"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-08-20
Basically I want to install feisty on my 2 GB USB Pendrive, somehow, so I can boot from it, and use it as a livecd when I want to. Now the problem is, I don't have an ISO of feisty, ( and can't because of my bandwidth policy), so can I manually install feisty, via the livecd and make partitions and such on my pendrive and have that work?

Dr Small

---

### Post by Hobo Joe on 2007-08-20
Well, I'm not sure on this, but you MAY be able to copy the .iso off of the liveCD and put it on your flash drive.

---

### Post by Dr Small on 2007-08-20
Honestly, I didn't think there was a iso on the livecd... :|

---

### Post by logos34 on 2007-08-20
> **Dr Small said:**
> Basically I want to install feisty on my 2 GB USB Pendrive, somehow, so I can boot from it, and use it as a livecd when I want to. Now the problem is, I don't have an ISO of feisty, ( and can't because of my bandwidth policy), so can I manually install feisty, via the livecd and make partitions and such on my pendrive and have that work?

Dr Small

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) (N.B.--read down to the 'Comments' section)

To make an ISO from your CD, place the media in your drive but do not mount it. If it automounts, unmount it.

[COLOR="Red"]dd if=/dev/cdrom of=ubuntu-7.04-desktop-i386.iso [/COLOR]

Creates iso in your /home/user dir

---

### Post by Dr Small on 2007-08-20
> **logos34 said:**
> [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) (N.B.--read down to the 'Comments' section)

To make an ISO from your CD, place the media in your drive but do not mount it. If it automounts, unmount it.

[COLOR="Red"]dd if=/dev/cdrom of=ubuntu-7.04-desktop-i386.iso [/COLOR]

Creates iso in your /home/user dir
Why I never.....
Hey, thanks. I was still searching and found [this page](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/), but it was for edgy, so I think I'll try your way first.

Edit, So if I get the iso of the disc, how can I put that on my pen drive and make it bootable?

Thanks.

Dr Small

---

### Post by logos34 on 2007-08-20
> **Dr Small said:**
> Why I never.....
Hey, thanks. I was still searching and found [this page](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/), but it was for edgy, so I think I'll try your way first.

Edit, So if I get the iso of the disc, how can I put that on my pen drive and make it bootable?

Thanks.

Dr Small

Actually, you can work from the live cd, soyou don't need the iso (but that is the command for making one should you ever need to)

Hopefully the bug mentioned in the comments was resolved for the Feisty final release.

---

### Post by Dr Small on 2007-08-20
Well, once I make the iso of the cd, how can I put that iso on my usb pen drive and then boot from ubuntu with that? I still don't get the jist of that.

Dr Small

---

### Post by logos34 on 2007-08-20
again, you don't actually need the iso.  You can do everything from the ubuntu live cd you already have.  Read the link I gave you or the one for edgy you posted.

---


---
title: "Installing from a external usb HD"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by catdogdo on 2008-02-25
As the title suggest, I would love to know if its possible to make a partition onto an external, then install (for me) Ubuntu. Now, I have done a few Google searches, and just wanting to see if anyone has done it successfully.

Basically, what I want to know is:
         *how to create the partition
          *What software to use to partition
          *and how to actually install Ubuntu onto the External HD
(if you want more info, speak up)

Just a few other optional things:
            *Would this be just like Linux installed onto a normal HD
            *Can I use compz-fusion(I think thats what its called)
If there is somthing that I did not include for installing, just include that specific task where it should go
otherwise, if this is not possible, then just say so.
(remember ask if you dont get anything that I said, speak up)

---

### Post by catdogdo on 2008-02-25
(one quick note, its to an external, not from)

---

### Post by backflip on 2008-02-25
I'm not quite clear on what you are seeking, but I'm running ubuntu from an external drive and I'm using it now. I physically unhooked the internal drive and changed the BIOS to boot from USB first. I then installed ubuntu, using the manual option which let me make a root, /home and swap partitions.  Now when I boot if I have the usb drive switched on (it has its own off/on switch) I boot into Ubuntu and if I have the external drive off I boot into Vista. I think the safe thing to do is disconnect your internal drive so that nothing (i.e. grub) can be installed there.
 I've no problems whatsoever doing it this way.

---

### Post by catdogdo on 2008-02-25
i understand what u did, all im confused with is for doing the partition part.
basicly, what i figure is make the partition fat32 then do what youve done, then
select the space for ubuntu, then install

is there a specific way to partition a usb hd? (keep bout 30gigs for ubuntu, 90gigs for storage)

---

### Post by SkidShot on 2008-02-26
Complete walk through can be found here: [http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253]("http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253")

Somewhere on that site is posted how to partition USB pendrives with fdisk as well (I believe in the gutsy pendrive howto).
The proces on a HD should be the same.

---

### Post by catdogdo on 2008-02-28
ok, ive gotten to actualy setting up ubuntu (v7.10) and when around 88%, gave me an error "cant mount drive" something like that.
--------------------------------
and btw, i wanted to make a partition so i could use one part for actuall storage, but the problem is the error. 
--------------------------------
basicly, my partitions that i would have are : ext3, swap, and ntfs <- (ntfs for storage)
im gonna try again tomorrow, and post pics.

---


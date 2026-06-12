---
title: "Copying partitions with gparted"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by YodaMstr on 2008-02-23
Ok, so I was figuring that when I moved away and started college, I'd have some more time to actually dive deep into Ubuntu.  But of course, using Ubuntu now, I've got things all set up just how I want them.  I've got an external USB HDD, so my question is this.  If I copy all my partitions to the external drive, would it be possible to simply copy them back to the original drive to reinstall everything how I have it?  Basically I'm asking if gparted can make an exact copy/back-up of Ubuntu that I can just paste back.  If so, what problems would I encounter on a reinstall with my /boot files being on a separate partition?  I'm hoping this makes sense.  I just want to be able to mess around with an install that I can wipe and reinstall without remorse for a little while.

---

### Post by taurus on 2008-02-23
Sounds to me like you want to make an image of your drives so you can just copy it back in case something goes wrong.  For that, partimage is what you want.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by YodaMstr on 2008-02-23
Alright, thanks.  I'll give that a try.  However, I would like to know if I'll have a problem with the bootloader if my /boot partition is on a separate partition.  Also, I was wondering if this same image effect could be created by using gparted's copy/paste function.  Just to save myself some time and have an easier way to go about things.

---


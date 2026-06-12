---
title: "libATA problem(supposedly)"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by shriphani on 2007-05-31
I apologise because I have made a post in the Hardware and Laptops section pertaining to a cdrom issue. So if the moderators can delete it I would be grateful. 

I upgraded last night to the 2.6.20-16-generic kernel. Prior to this my harddisk was /dev/sda and my cdrom drive was /dev/scd0. After the upgrade my harddisk became /dev/hda and my cdrom drive became /dev/hdc. I looked up System ---> Preferences ---> Hardware Information and found that my CDRW + DVD R was of IDE bus type. I couldn't mount my dvd and changed /dev/scd0 in my /etc/fstab to /dev/hdc. I was able to manually mount my dvd after this but totem wouldn't recognise it. To play anything I had to manually point it to /media/cdrom0. 
I rebooted with the 2.6.20-15-generic kernel and my hard disk again became /dev/hda and cdrom changed to /dev/scd0 and everything works fine.
Does this mean libATA doesn't 'fly' with the 2.6.20-16-generic kernel ?

---


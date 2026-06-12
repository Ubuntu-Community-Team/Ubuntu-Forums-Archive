---
title: "Looking to Install 14.04 on MacBook Pro mid2010 that already has 16.04"
date: 2016-09-23
forum: Apple Hardware Users
---

### Post by dannyalvin on 2016-09-23
Having problems with a 16.04 install that I performed on a Macbook Pro Mid 2010,  Not dual boot.  Realizing that this may have been a mistake, I want to install 14.04 which I am advised is a more stable environment.  I created a bootable USB flash drive with 14.04 and I tried pressing Option (altkey) when I hear the chime on restart.  I am not getting to the boot drive options as I did when I Booted 16.04 from an El Capitan environment.  What I get is Internet recovery, but from there I cannot get to the USB drive to boot.  I can access Disk Utility and could wipe the partition with 16.04, but then what?  I am a new comer to Linux.

---

### Post by QIII on 2016-09-23
Moved to Apple Hardware Users.

Hopefully the right people will see it here.

---

### Post by &amp;KyT$0P# on 2016-09-23
> **dannyalvin said:**
> I created a bootable USB flash drive with 14.04 
How did you create it?
Are you using a 14.04.1 iso?

---

### Post by apple-apple on 2016-09-23
I'm sorry; I'm not sure how. But I do have a question... What problems are you having with 16.04?

---

### Post by Bucky Ball on 2016-09-24
> **halogen2 said:**
> How did you create it?


> **apple-apple said:**
> I'm sorry; I'm not sure how.

How would you know how? You didn't start this thread ... :-k

---

### Post by dannyalvin on 2016-09-24
The main problem is with the wireless connection.  I have the correct broadloom driver installed. Right now my work around is that after I start up, I close the laptop for a few, and then reopen it.  Viola, the connection is made. Aside from that, I am not having too many other issues, though 16.04 seems quirky.  The other issue has nothing to do with the version I am using but more with my inexperience with Linux and learning the commands to be used in the Terminal.  To get around the wireless issue, I thought I would use a usb wireless, but ran into a problem trying to compile the drivers.

---

### Post by &amp;KyT$0P# on 2016-09-24
> **dannyalvin said:**
> The main problem is with the wireless connection.  I have the correct broadloom driver installed. Right now my work around is that after I start up, I close the laptop for a few, and then reopen it.  Viola, the connection is made. Aside from that, I am not having too many other issues, though 16.04 seems quirky. 
Wait, back up.  Are you now looking to fix 16.04 instead of doing this? -
> **dannyalvin said:**
>  I want to install 14.04 which I am advised is a more stable environment. 

Either way is fine, it's up to you, just let us know and make sure to avoid letting drive-by posts distract from you answering questions to help you towards **your** goals here.  Thanks.

---

### Post by apple-apple on 2016-09-27
Dannyalvin, I think the wifi drivers you installed are the proprietary ones. I would try uninstalling the proprietary driver and installing the open source version, b43. Btw use b43 not b43-legacy. May be easier than doing an entire os reinstall.

---


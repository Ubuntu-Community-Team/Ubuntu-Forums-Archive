---
title: "Username?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by imcmcstc on 2006-09-21
New to Ubuntu and just installed it on a spare tower.  It is asking for a usnername and I only remember creating a password.  I looked over everything I could find for a default but to no success....anyone?

---

### Post by avidsensei on 2006-09-21
have you tried your name?

---

### Post by avidsensei on 2006-09-21
or just reinstall

---

### Post by imcmcstc on 2006-09-21
I've tried everything from my own name (which I don't believe I ever typed in the install) to the name I named the computer to even dumb things like default or guest or ubuntu.  I'm sure the password is what I set but I don't remember making a username.

---

### Post by imcmcstc on 2006-09-21
> **avidsensei said:**
> or just reinstall


Some what of a long install.....it was actually my third install that didn't freeze and fail video.

---

### Post by avidsensei on 2006-09-21
well you havent tweaked anything yet im assumeing so i would say just do a fresh install if you already have the partitions set up it should only take 20 or 30 min

---

### Post by imcmcstc on 2006-09-21
true.........work, brain!!!!

---

### Post by avidsensei on 2006-09-21
previous statement retracted. reinstalling is really going to be one of your only options. with windows you can get a linux bootloader and hack out the pasword file. but id doesnt work the other way around

---

### Post by imcmcstc on 2006-09-21
Okay, I'm in the install and it's in the installing base system phase and I was asked for a password but no username...not again.....

---

### Post by nereid on 2006-09-21
Use a boot disc and change add another user to the system

```

mkdir /mnt/my_linux
mount /dev/$YOUR_LINUX_PARTITION /mnt/my_linux
chroot /mnt/my_linux
useradd -m -G users,admin -s /bin/bash $NEW_USERNAME
passwd $NEW_USERNAME
exit

```

Substitute $YOUR_LINUX_PARTITION with your linux partition (eg. hda1) and substitute $NEW_USERNAME with your new username. Maybe you need to add your new user to some groups but you can do this later with the GUI utility (you can do this also on the command line if you know how to do it).

---

### Post by imcmcstc on 2006-09-21
OEM is the default username.  Thanks to all who replyed.  I missed that minor yet major piece of info at the tail end of the install.  Thanks again!

---

### Post by NordicRX8 on 2006-09-21
Because you mentioned that you had issues installing, and you finally figured out what the default username was ("OEM"), can I assume this was an "alternate" install??

I just installed unbuntu last night for the second time (first attempt crapped out my pc), and I clearly remember the setup/install program, asking for real name, username and passwords.

Good info to know for future installs.

Thanks.

---

### Post by imcmcstc on 2006-09-21
It's actually funny that you should ask because I was looking at web based tech support screen shots and they were nothing like what I had been dealing with but yet the end result was a full install.  So, I don't know if I somehow found a crappy copy of the installation process or what but like you say, on the screen shots it clearly asks for a desired username and password.  I honestly thought I was shot until I read every line of script and found that the default was oem in my case.  Who know's.:confused:

---


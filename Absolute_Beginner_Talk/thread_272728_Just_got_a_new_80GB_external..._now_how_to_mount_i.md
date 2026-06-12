---
title: "Just got a new 80GB external... now how to mount it..."
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-06
How do I mount ubuntu on my external hard drive without any trouble?  Thanks.

---

### Post by firebirdworks on 2006-10-06
Humm... Is it the same as putting it on a Jump Drive?

---

### Post by jordanmthomas on 2006-10-06
Are you wanting to mount the drive in Ubuntu, or install Ubuntu on the drive?

---

### Post by Medieval_Creations on 2006-10-06
The command will be something like this 'sudo mount /dev/<sda_some#> /<folder_name>', if it's a usb external drive.

Example:
sudo mount /dev/sda1 /mnt/Storage_EXT3

---

### Post by Titus A Duxass on 2006-10-07
I just plugged mine, waited a little while (30 secs approx.) and off it went.

I do have problems if I boot up the pooter with the ext disc plugged in, the boot process freezes.

---

### Post by bulldog on 2006-10-07
Just plug it in and it should appear under your /media folder.

---

### Post by whistl3r on 2006-10-07
If it doesnt automount check the cables to your harddisk. If it doesnt work go to system>administration>disks, select your disk and mount it where you like.

---

### Post by firebirdworks on 2006-10-07
Um...sorry, I didn't clearify myself.  I want to load ubuntu on my external hard drive so I can boot ubuntu from it.  Basicly install is so t will boot.

---


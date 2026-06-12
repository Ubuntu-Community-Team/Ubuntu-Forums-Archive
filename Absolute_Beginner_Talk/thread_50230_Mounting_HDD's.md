---
title: "Mounting HDD's"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by Phixion on 2005-07-19
Hi, I converted one of my HD's to ext3, after doing it i copied my data back onto it, but when i enter a folder I get an orange lock symbol on each file. (shown below)

[http://www.kan.myby.co.uk/phixion/Screenshot.png](http://www.kan.myby.co.uk/phixion/Screenshot.png)

This is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hde1       /mnt/d          ntfs        ro,auto,uid=1000 0 0
/dev/hdc1       /mnt/e          ext3

```

the drive I mounted was hdc1... have I entered the wrong command? If so what should I have in there.

I'm guessing my issue is to do with this.

Cheers.

---

### Post by dataw0lf on 2005-07-19
It's mounting read only.

Put this in it's options field:

defaults,errors=remount-ro

Should be fine after that.

---

### Post by Phixion on 2005-07-19
[QUOTE=dataw0lf]It's mounting read only.

Put this in it's options field:

defaults,errors=remount-ro

Should be fine after that.[/QUOTE]

I changed it but the mp3s are still locked, should i be using chmod 777? I used it on /mnt/e/mp3 but it didn't change all the mp3 files to read write execute :/

---

### Post by Wolki on 2005-07-19
[QUOTE=Phixion]I changed it but the mp3s are still locked, should i be using chmod 777? I used it on /mnt/e/mp3 but it didn't change all the mp3 files to read write execute :/[/QUOTE]

to have chmod go through directories, you need to add the option -R.

---


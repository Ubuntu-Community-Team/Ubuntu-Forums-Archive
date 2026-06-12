---
title: "No Sound on ABIT Mobo"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2008-02-02
I have [this motherboard]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332") in my desktop, it is a ABIT NF-M2S with Socket AM2, AMD64.

Ever since upgrading to Gutsy the sound doesn't work.  Previously, when I was running Fiesty, I used [this link]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and followed the instructions to install the sound drivers, but now I try the same thing and can't get it to work.  It is very possible I am doing something wrong, but I am doing the same thing I did with Fiesty, and I got that one to work.

The driver versions are newer, perhaps that is my problem, but the error I get comes up when I run the "sudo cp" command, pasted below.


> jason@SAMSON:/usr/src/alsa$ sudo cp /home/jason/Downloads/alsa-driver-1.0.15.tar.bz2
cp: missing destination file operand after `/home/jason/Downloads/alsa-driver-1.0.15.tar.bz2'
Try `cp --help' for more information

---

### Post by azimuth on 2008-02-02
jason@SAMSON:/usr/src/alsa$ sudo cp /home/jason/Downloads/alsa-driver-1.0.15.tar.bz2
cp: missing destination file operand after `/home/jason/Downloads/alsa-driver-1.0.15.tar.bz2'
Try `cp --help' for more information

You might try: sudo cp /home/jason/Downloads/alsa-driver-1.0.15.tar.bz2  /usr/src/alsa/

---

### Post by kc5hwb on 2008-03-20
That seemed to work, but now I get a new error when running the ./configure command.

jason@SAMSON:/usr/src/alsa/alsa-driver-1.0.15$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---


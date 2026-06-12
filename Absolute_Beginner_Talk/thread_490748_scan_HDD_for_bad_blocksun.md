---
title: "scan HDD for bad blocksun"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by rlnunez on 2007-07-02
How can I scan HDA1 within ubuntu for bad sectors?

---

### Post by reset3x on 2007-07-02
You can boot with a live cd open a terminal and run fsck /dev/hda1 or it may be /dev/sda1 ... It's not recommended to do this with the drive mounted...

---

### Post by GMachine_24 on 2007-07-02
hi...

you might want to run

username@computername:~$man fsck | more 

to find options available for use with fsck

---

### Post by rlnunez on 2007-07-02
I tried to run sudo fsck /dev/hda1 from the live cd and it only gave me the number of blocks being used and that was it. I do appreciate the help though.

---

### Post by reset3x on 2007-07-02
try what GMachine_24 suggested... it will give you more info...

---

### Post by sonofusion82 on 2007-07-02
not sure if it is available in ubuntu, i gotta check but in openSUSE and ReiserFS i used to use badblocks, [http://www.die.net/doc/linux/man/man8/badblocks.8.html]("http://www.die.net/doc/linux/man/man8/badblocks.8.html")

---


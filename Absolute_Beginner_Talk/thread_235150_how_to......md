---
title: "how to....."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-12
how to reverse the command "sudo chmod -r /dev/hdc".   Now i got my cd-rw not workin please help me out :(. thanks

---

### Post by pdub on 2006-08-12
How about:

sudo chmod +r /dev/hdc

---

### Post by arnaudlegrand on 2006-08-12
chmod -R 777 /dev/hdc:)

---

### Post by rck_hitokiri on 2006-08-12
ok i got it ok... now please, how do i change me permissions for my cd-rw? this is the output error i recieve:


mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



--see that its write-protected and read only... thats why i cant burn anything, how do i change this? thanks guys. for the help.

---

### Post by pdub on 2006-08-12
What program are you using to burn?

Your device should have the following permissions

brw-rw-r-- 1 root cdrom 22, 0 2006-08-10 11:02 /dev/hdc

You can check by typing:

ls -al /dev/hdc

---


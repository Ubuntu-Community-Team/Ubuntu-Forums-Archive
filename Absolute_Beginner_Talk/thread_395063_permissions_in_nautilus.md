---
title: "permissions in nautilus"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by richardi on 2007-03-27
hello,
I'm new to ubuntu and managed to set up a dualboot with XP with a shared FAT32 partition for read write file storage between both OS and am quite pleased with myself! Ubuntu looks great and I can't wait to get online. But.....I have a crappy usb modem from my ISP. Found the howtos and been to flashtux and done some downloading and installing and now having some problems like the output below:
> richard@richard-desktop:~$ /usr/bin/eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

/proc/bus/usb/005/003: Permission denied
/proc/bus/usb/005/001: Permission denied
/proc/bus/usb/004/001: Permission denied
/proc/bus/usb/003/002: Permission denied
/proc/bus/usb/003/001: Permission denied
/proc/bus/usb/002/009: Permission denied
/proc/bus/usb/002/008: Permission denied
/proc/bus/usb/002/007: Permission denied
/proc/bus/usb/002/006: Permission denied
/proc/bus/usb/002/001: Permission denied
/proc/bus/usb/001/001: Permission denied
ERROR can't find your GlobeSpan GS7470 USB ADSL WAN Modem
ERROR eciadsl-synch: failed 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

nice: cannot set niceness: Permission denied
ERROR: failed to connect
richard@richard-desktop:~$


So I thought I need to try more synch files so I went back to flashtux and got this:
eciadsl-synch_bin.tar.bz2
which I need to unpack in /etc/eciadsl
So I tried to do it by dragging and dropping in nautilus but can't figure out how to get permission to write to /etc

Can anybody help me - I like trying to solve problems but feel like the answer to this one is probably bleedin obvious. I just can't get it.
put me out of my misery please.
thanks
Richard

---

### Post by STREETURCHINE on 2007-03-27
in terminal type

              ```
gksudo nautilus
```

that will open nautilus with root permission

---

### Post by mcduck on 2007-03-27
You need to open nautilus as root user. To do that hit Alt-F2 and run 'gksudo nautilus'.

For more info about root and sudo/gksudo in Ubuntu you should read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by richardi on 2007-03-28
thanks alot chaps.
I'm really impressed with the Ubuntu community and the willingness to help a newbie. 
Looking forward to playing with that this evening.
Richard

---


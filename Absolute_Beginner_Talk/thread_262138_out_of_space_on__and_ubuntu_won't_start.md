---
title: "out of space on / and ubuntu won't start"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-09-21
I made DVD-rip use / instead of /home, accidentally. I did discover it at some point, closed ripping, but somehow even the last 500 Mbs of the space left got lost. I then deleted the directory DVD-rip from / using sudo nautilus and the directory got lost, but the space did not get free. I wasn't able to remove the DVD-rip with sudo rm DVD-rip in the recovery mode, because "no such file or directory".

Ubuntu won't start any more, I am now in Windows XP :(

---

### Post by davmac on 2006-09-21
If you've still got the original dapper install CD you should be able to boot up from this.

Then you can go looking for the .trash directory and delete the contents.

Hope this helps,

Dave Mac

---

### Post by 1002285 on 2006-09-21
Thanks.
Do you think this can be done in recovery mode? If I only knew, where the trash was.
But I can find the CD, too.

---

### Post by bulldog on 2006-09-21
Your trash is located in your /home folder as .trash [hidden]

You can mount your existing install.

Boot the live cd and do in a terminal,

sudo mkdir /mnt/restore

sudo mount /dev/hda? /mnt/restore

Go to the restore folder and you are able to clean up your disk.

[put your Ubunt-partition here]

---

### Post by 1002285 on 2006-09-21
I can't mount the Ubuntu partition while running Live CD. It finds it, but "cannot mount, ... because not removable media" or sth.

---

### Post by 1002285 on 2006-09-21
I cannot see .trash in the home folder even when I choose "view hidden files".
I have /home on a separate partition, but the OS partition / is the one that is full. I can't seem to find .trash on that partition yet.

---

### Post by 1002285 on 2006-09-21
Ok, I found the trash, it was in a place like /root trash or sth. I missed it somehow earlier.
Thanks

---


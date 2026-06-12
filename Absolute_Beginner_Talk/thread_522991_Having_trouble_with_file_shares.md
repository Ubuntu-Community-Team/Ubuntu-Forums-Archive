---
title: "Having trouble with file shares"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-08-11
Greetings,
I'm trying to set up a couple of file shares on my server so that I can drop files there from other machines on the network. The relevant parts of my network are all using Ubuntu. Anyway, I've tried to set up an NFS share. The files for the share are located at:
/shared/binaries/_MP3

/shared is where I mounted my data drive.

Anyway, I have both samba and NFS available on the machine. I went to Shared folders under the System menu and added this folder. I set it up as an NFS share. I'm trying to make it available to all machines on my network (192.168.3). However, I still can't seem to access it when I try to browse to it from another machine. Is there another way I'm supposed to be doing this?

Thanks,
Will

---

### Post by GMachine_24 on 2007-08-11
Hi:

Perhaps it's a typo, but your IP addresses must have four separate numbers, e.g. 192.168.0.103

You typed 192.168.3

Were you just using shorthand or is that the actual address you're using? And the shared folders you mention, they are on a Windows machine, I presume?

---

### Post by gantww on 2007-08-11
Actually, I'm trying to authorize the 192.168.3.x network. The IP addresses for that group (other than the file server) are dynamically assigned.

---

### Post by gantww on 2007-08-14
Any ideas? How do I specify the network that it allows? I'm not finding any useful documentation.

---


---
title: "Windows shared internal and  external storage solutions?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by yasoumalaka on 2006-10-11
I've been trying to find a good thread on this and I couldn't find one. I'm shure there is one out there but these forums are like a jungle that grows rapidly everyday. Hopefully I've put the right tags to make this easily searched.

Anyways I have a bunch of internal and external hard drives that I use as storage and want to be able to share among windows and linux. I did some reading and finally decided on EXT3 as the file system using Extfs.sys as the windows driver to allow me to read and write to the disk. Currently it works great. I'd like this thread to have people share their setups or what they think would be best for sharing drives between windows. Also since I'm a newb I haven't got all my permissions set up right yet, but I know Ill need them because I'll have azureus writing to the drive. Whats the best way? Should I sudo azureus to give it permission ((:KS edit sudo can cause problems with graphical applications. Use gksudo:KS ))? Or is there a better way? Let the community know. If  I can get this sorted out I'll be on my way to using Ubuntu all the time except when I get an itch to play F.E.A.R. Thanks for any input.

---

### Post by aysiu on 2006-10-11
It would make more sense to change permissions on the drive than to use *sudo azureus* (or *gksudo azureus* is probably more appropriate).

---

### Post by yasoumalaka on 2006-10-11
Ok thanks you're right. I'm a newb didn't know sudo caused problems with graphical applications.

---

### Post by aysiu on 2006-10-11
> **yasoumalaka said:**
> Ok thanks you're right. I'm a newb didn't know sudo caused problems with graphical applications.
You can read more about it here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Do you need help changing permissions on the drive?

---

### Post by yasoumalaka on 2006-10-11
Yeah that would help and I'll post it at the top with credit to you. So people can find what they're looking for more easily. Thanks.

---

### Post by dannyboy79 on 2006-10-11
> **yasoumalaka said:**
> I've been trying to find a good thread on this and I couldn't find one. I'm shure there is one out there but these forums are like a jungle that grows rapidly everyday. Hopefully I've put the right tags to make this easily searched.

Anyways I have a bunch of internal and external hard drives that I use as storage and want to be able to share among windows and linux. I did some reading and finally decided on EXT3 as the file system using Extfs.sys as the windows driver to allow me to read and write to the disk. Currently it works great. I'd like this thread to have people share their setups or what they think would be best for sharing drives between windows. Also since I'm a newb I haven't got all my permissions set up right yet, but I know Ill need them because I'll have azureus writing to the drive. Whats the best way? Should I sudo azureus to give it permission ((:KS edit sudo can cause problems with graphical applications. Use gksudo:KS ))? Or is there a better way? Let the community know. If  I can get this sorted out I'll be on my way to using Ubuntu all the time except when I get an itch to play F.E.A.R. Thanks for any input.

since you'll be sharing between winbloz and linux, you can use samba or ftp. i am not sure if azereus works over ftp so you might be stuck with samba. i just posted a great link to setting up samba between winbloz and linux. i'll be right back.

got it, here you go [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by yasoumalaka on 2006-10-11
I'm sorry that is not isn't what I meant. I'm on a dual boot setup. I just want to be able to read and write to the drives in either windows or  linux and want people to  discuss the best setups for this. Fortunately I haven't  had to  do much to  share through the network with my laptop.  I just go to network servers and my shared windows folders show  up.

---


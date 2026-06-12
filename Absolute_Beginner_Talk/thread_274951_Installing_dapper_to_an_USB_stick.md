---
title: "Installing dapper to an USB stick"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Agren on 2006-10-10
I want to create a diskless HTPC using Ubuntu. I have the machine running ubuntu, it works, but I really want to reduce the noice, thus I'd like to remove the disc and have a separate file server for data. 

However, the machine I intend to use as a fileserver is not very fast (400 Mhz/128MB ram) so I don't think that some form of thick client is to think about.

So now my idea is to boot the HTPC from a USB stick, I have read the Howto on using a USB stick as a "live USB" but I am worried that the lack of swap will be a problem. Is there any way to do a proper  install to an USB stick? 

Or, if there is not, is there any chance of running the "live USB" will actually be enough? The machine currently have 512 MB ram, and I expect to use it mostly for playing music and movies, but I am also toying with the idea of buying a tv-card and running some sort of MythTV installation on it. 

Anyone have any help and/or opinions on my plan? Should I scrap it directly or may it be viable?

Thanks in advance
Agren (newbie :) )

---

### Post by Agren on 2006-10-23
shameless bump.

No one has any idea?

---

### Post by fimblo on 2007-05-19
So lets see. have I misunderstood you if you have two machines- one fileserver and one htpc?

fileserver 400Mhz/128M
htpc is XMhz/512M

I think it should work- booting and running from usb stick should work well. But if you do do this, keep in mind that you cannot write as many times on flash memory as on a harddrive. So use several usb sticks. Eg:
Root partition 4G
/usr 4G
/var 512M
swap 1G

make sure you set noatime mount option on / and /usr so that you dont write to the flash drive every time you access a file on them.

On typical linux systems, /var is written to regularly (logs, pids, etc), and on memory intensive systems, swap will also be heavily used. Therefore it could be a good idea to keep them on separate flash memory from the rest, so that when they die you will be able to replace them with other cheap memory.

This leaves us with the /tmp directory, which is also written to alot- After installing your system you can boot off a rescue CD and create a directory /var/my_tmp. After this you can remove the normal /tmp directory, then symlink it to /var/mytmp. (alternatively you can partition the flash memory for /var into two parts, and mount them into place).

Im messing around with this right now as I write this message, we'll see how it goes.

cheers and good luck.

---


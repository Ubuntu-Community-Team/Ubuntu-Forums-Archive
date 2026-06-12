---
title: "More samba issues"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by argyl3 on 2006-09-20
Okay, well, I've had some success in mounting a samba share, however, each time I go to mount it, I get this weird error.

shrotriyee@aristotle:~$ sudo mount -t smbfs -o username=mukhopa4,password=******* shrotriyee/Desktop/coral

timeout connecting to 35.9.20.18:445
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
6166: session request to CORAL.CSE.MSU.ED failed (Read error: Connection reset by peer)
timeout connecting to 35.9.20.18:445

But the thing is, it mounts fine, I can see all my files and whatnot. I also have a windows xp computer with this mounted at the same time. Is that what's causing the timeout?

Also, I tried using the connect to server option, since the server I want to connect has an SSH option, and I get that pretty little icon on my desktop, and when I right click, I have the option to unmount the drive. It's not that I'm too opposed to doing stuff in the command line, it's just  whatever makes my life easier, right? =) So I was wondering if there was a way to do the same with the samba share.

Thanks,
Shro

---


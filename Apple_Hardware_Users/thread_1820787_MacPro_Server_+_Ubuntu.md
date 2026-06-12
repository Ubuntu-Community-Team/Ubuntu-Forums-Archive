---
title: "MacPro Server + Ubuntu ?"
date: 2011-08-08
forum: Apple Hardware Users
---

### Post by Lasastard on 2011-08-08
Hi,

we recently purchased a MacPro Server at work, but I would like to install Ubuntu Server on it b/c OsX doesn't really work for me...

Anyway, it would appear that there are several pitfalls with such a step, some of which are outlined in the Ubuntu FAQ

- dual boot recommended for firmware upgrades
- driver issues
- partitioning


So I guess I am interested in hearing whether anyone has successfully installed Ubuntu Server in dual boot on a current-gen MacPro with a Raid setup. Not sure whether the latter would in any way affect the process, but I am guessing it is something to be aware about?

Thanks!

---

### Post by steve@donsolaris on 2011-09-23
Ive just bought a used PowerMac G5 for use as a home server, the main issue i found was with Apples dodgy dvd drives.  But once installed its been very stable and worked really well.  I use ssh for a shared drive, media server software for running video to my Ps3 and deluge (client/server) for the odd bittorrent.

For admin I use VNC server and although it tends to make the CPU spike some, it gets there in the end.  (my mac however is only single core).

I also had some difficulty running the server headless, I got around this by plugging an old KVM switch into the video card to fool it to thinking it had a monitor connected.

Hope this helps you

Steve

---


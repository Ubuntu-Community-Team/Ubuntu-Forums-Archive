---
title: "Installed 7.04 AMD64 Server keeps asking for CD"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Sysco Kid on 2007-05-24
Hi,

SCO to ubuntu  noob here.

I've installed 7.04 AMD64 Server edition and once booted ran the following as root, 

apt-get install build-essential

which loads (I hope) all the essentials I the server would need.

However, when I downloaded and tried to install a  .deb package, I am asked to insert the Original Ubuntu 7.04 AMD64 Server CD disk.

How can I copy/install the necessary files off the CD, so as not to be asked for the disk?

many thanks.

---

### Post by Bachstelze on 2007-05-24
First off, build-essential contains gcc and all other development libraries. You won't need it unless you plan to compile software from source.

As for your CD issue, just comment out (or delete) the lines regarding it in /etc/apt/sources.list and it will stop asking for it.

---

### Post by starcraft.man on 2007-05-24
Easy fix I think... you don't actually have to copy files. It is just that the CD is listed in your sources list and not commented out.

You have to manually open up your sources.list file (its in etc/apt/sources.list of course) and then just put a # in front of the entry that lists your CD as a source. That should be it :).

I hope I'm right, I've yet to really play around with servers on Ubuntu much >.>.

Edit: Hymn by a millisecond >.>.

---


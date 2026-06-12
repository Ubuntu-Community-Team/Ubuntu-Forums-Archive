---
title: "How to mount *.iso-file and use xDVDshrink to.. Well.. Shrink it ;)"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-06-09
Hello!

I have a little problem with DVD-iso mounting and shrinking. I just can't seem to get it to work. When I try to use the mount command that repeats itself it different threads, I get something that can remind of a help file that explains different uses of the command. There are a lot of words there that are unknown to me, so if someone can help me to make kind of a "dummy-guide" that tells just what to write, if the file is located in the home-folder, and it is called for example problem.iso, and how I get to shrink it in xDVDshrink.
xDVDshrink is a very simple program, but perhaps a bit to simple, because I can't get it to work, even when I use a DVD disc.

By the way, I am not talking about the windows program DVDshrink, I am talking about the linux program xDVDshrink.

---

### Post by darkali on 2006-06-09
If you are in the same folder as the file:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount problem.iso /media/iso/ -t iso9660 -o loop

This will mount the iso to /media/iso, open xdvdshrink browse there and open the folder, start using it.

---


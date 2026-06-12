---
title: "Azureus troubles (once more)"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Vorticon on 2007-09-18
Hello. Once more i have a little problem with azureus. this time i didn't do anything fancy with automatix or whatever, just plain installing from the add/remove tool in the menu.

Whenever i try to start a torrent i get an error message saying:

Error: Failed to create parent directory '/home/<username>/etc../'

I am guessing it has something to do with permissions? I found a somewhat similair post like this but that one was about a fat32 drive that was mounted. My problem unfortunately occurs also on the one and only drive i have which is ext3.

Help please :(

P.S. It runs okay when i use "sudo azureus", but i don't think this is the way it's supposed to be runned right?

---

### Post by Harpoon on 2007-09-18
You are correct that running it a root is a bad idea.  The problem may be in how you installed it.  As I recall, you have the option of installing for "all users"  or "this user only."  If my suggestion below does not work, then go to the package manager and mark AZ for complete removal and "apply."  When that is done, reinstall making sure to choose the "this user only" option.

A workaround might be this:
Places >> home >> file tab >>create folder.  Name it whatever you like (mine is torrents).  When you add the torrent to AZ, set the download location as /home/<username>/torrents (or use the browse function in AZ).  This will avoid any permissions problems.  Only do the reinstall if this fails to solve the problem.

---

### Post by Vorticon on 2007-09-19
Solved! It seemed that i created the "download" directory in my home folder one time when i was in super user mode in nautilus. The permission of my download folder was set to root only so that's why it didn't work. Linux isn't that hard, you just have to get used to it :)

---


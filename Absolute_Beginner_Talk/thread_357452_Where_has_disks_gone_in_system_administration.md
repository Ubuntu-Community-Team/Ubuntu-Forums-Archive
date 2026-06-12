---
title: "Where has disks gone in system administration"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by chris90uk on 2007-02-09
My MP3 player screwed up because Ubuntu couldn't finish unmounting the device, so I want to format it. But the disks option has gone. I am using Edgy. Any ideas?

Thanks.

---

### Post by ingo on 2007-02-11
Sorry to hear about your MP3 player. So you just unplugged the device even though it was probably busy. As you found out this is not a good idea. Read
man umount
on the shell for more info on how to unmount properly. Also make sure that all programmes that access the device point elsewhere (such as konqueror for kde or the relevant gnome equivalent). 

As for reformatting - there are any number of ways, but see whether you have gparted installed on your system. If not, do 
> sudo apt-get install gparted
That should help you reformat your player.

---


---
title: "hdd help"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by asalim2k on 2005-10-13
hello all.  i just installed ubuntu about 20 min ago and been playing around with it.  im an absolute newb when it comes to linux, but i wanna give it a try.  my problem right now is that i cant gain acces to any of my other partitions.  there are 3 that i wanna see (one has XP on it, another has videos and another has audio).  can someone help me out.  tell me what commands and such i have to put in the terminal.  thanks for all the help.

---

### Post by luckyaba on 2005-10-13
Go to system>administration>disks
then under that you will see the drive and the partitions on that drive.. find the windows partition in there and then set the access path to .... 

"example" /mnt/windows    

then in the command line type 

mount /dev/hda1 /mnt/windows

---

### Post by Alexander Kirillov on 2005-10-13
[QUOTE=asalim2k]hello all.  i just installed ubuntu about 20 min ago and been playing around with it.  im an absolute newb when it comes to linux, but i wanna give it a try.  my problem right now is that i cant gain acces to any of my other partitions.  there are 3 that i wanna see (one has XP on it, another has videos and another has audio).  can someone help me out.  tell me what commands and such i have to put in the terminal.  thanks for all the help.[/QUOTE]
See here:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by onesojourner on 2005-10-13
I went to system>administration>disks and It just never loads. its been loading for 30 minutes. I just closed it and reopened it and it still keeps loading. is it supposed to do that?

---

### Post by luckyaba on 2005-10-13
I'm guessing here... but no. 

Just follow the link Alexander posted for you.

---


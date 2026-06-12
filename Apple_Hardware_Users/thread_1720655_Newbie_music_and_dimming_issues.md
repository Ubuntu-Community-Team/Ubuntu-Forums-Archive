---
title: "Newbie music and dimming issues"
date: 2011-04-03
forum: Apple Hardware Users
---

### Post by buzzboy on 2011-04-03
I'm a recent convert and I'm running 10.04 on a MBP 5,5 with Leopard. I have been through the FAQ and fixed the items that needed tweaks to work correctly. My dimming however is very funky. The F1 and F2 keys work to dim the screen but they do it super slowly, as in it takes about 30 seconds+ to go from full dim to full bright. Is there an easy fix for this? 

Also I am having permissions issues accessing my music across the partition. From OSX looked for permissions and couldn't find anything other than allowing sharing. From linux the music folders have Xs on them not allowing me to view them or use the music from them.

---

### Post by buzzboy on 2011-04-07
I've been searching around and I still can't access my music or really any files on the HFS+ partition. I can access apps but that does me no good. Also I can access a dropbox but for playing music this is again no good.

---

### Post by sauferkel on 2011-04-07
about the dimming:
are you using pommed? there you could change the "step value" for the keys in the config file  /etc/pommed.cfg

normally you should be able to read from the osx partition, do not know whats wrong there.

---

### Post by buzzboy on 2011-04-07
I am using pommed. I went and the step size is 1 or 2. I notice no difference between the two. However, sometimes when I hit the button it goes fast but usually it goes pretty slow still.

---

### Post by buzzboy on 2011-04-08
Back to the music issue. It was an apple issue. Even changing permissions to allow everyone read&look wouldn't let me access my music. So I moved all my music to a folder that is accessible and I can now get to my music. I then tried to set up the fstab to automatically mount my hfs+ partition upon boot. I am trying to mount /dev/sda2 in a folder called /media/music that I created. I think I followed the instructions correctly but  when I booted I got an error that it couldn't mount that partition. 

The line I added to fstab

/dev/sda2   /media/music   hfsplus   user,auto,file_umask=0111,dir_umask=0000   0   0

---


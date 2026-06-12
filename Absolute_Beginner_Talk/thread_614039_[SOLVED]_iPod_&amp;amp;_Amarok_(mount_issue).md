---
title: "[SOLVED] iPod &amp;amp; Amarok (mount issue)"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-11-15
Because amarok loves me so much, it has decided not to want to mount my iPod when I plug it in. It mounts and unmounts fine itself in Ubuntu, but when I push connect in Amarok, it asks for commands to run upon connect and disconnect. I'm clueless with that stuff :confused:

Also, is there anything I should know about transferring mp3's from my library to my iPod in Amarok? Is it just drag and drop?

Thanks :):)

---

### Post by Inxsible on 2007-11-15
Amarok needs to know about your iPod too. Simply mounting it in nautilus doesn't work. When you connect your iPod, it should ask you for the mount point and such. 

you can also access it by:
1) Connect your iPod
2) In amarok, go to Settings>>Configure
3) Click on media devices
4) Click on autodetect devices, if the iPod is not already detected. 
5) select Apple iPod Media Device as the plugin from the drop down list.

After that you should be good to go

---

### Post by Kymus on 2007-11-15
> **Inxsible said:**
> Amarok needs to know about your iPod too. Simply mounting it in nautilus doesn't work. When you connect your iPod, it should ask you for the mount point and such. 

you can also access it by:
1) Connect your iPod
2) In amarok, go to Settings>>Configure
3) Click on media devices
4) Click on autodetect devices, if the iPod is not already detected. 
5) select Apple iPod Media Device as the plugin from the drop down list.

After that you should be good to go

oh drat, I guess that's why all my yelling at it didn't make it work any better. :-D

Connected and transfered everything fine, thanks!

---

### Post by Inxsible on 2007-11-15
> **Kymus said:**
> oh drat, I guess that's why all my yelling at it didn't make it work any better. :-D

Connected and transfered everything fine, thanks!you are welcome :D

---

### Post by Crafty Kisses on 2007-11-15
This is why I love AmaroK, it's so simple.

---

### Post by Pevichaey5 on 2007-11-16
my problem relates to this

i have an old 20gb ipod 3rd generation i think

i open amarok, click connect, all fine, choose my songs to sync and fine

so it is in the transfer queue, but when i begin transfer the % bit goes really fast, but the songs don't appear on my ipod :(

cheers

---

### Post by Mike Armstrong on 2007-11-20
I have a ? 4G 30Gb ipod, Banshee detects it fine but has to rewrite the database with I think an older version, gtkpod finds it too but Exaile and gpixpod fail to see it at all even when mounted and pointed straight at it? this is in ubuntu Gutsy. The problem with banshee is that if you reconnect to itunes even manually with no sync, it rewrites the database and then banshee can't see it. if it then rewrites it again you end up with all your tracks 0.00 length and unplayable.

---


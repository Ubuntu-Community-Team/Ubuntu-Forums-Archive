---
title: "Ubuntu Bootcamp- Access Mac folders"
date: 2010-01-18
forum: Apple Hardware Users
---

### Post by jlubey on 2010-01-18
hey quick question about ubuntu/ mac on the same machine. i succesfully installed ubuntu onto a second partition of my macbook, the first being snow leopard. how do i access my mac files from ubuntu? when i boot into ubuntu the mac hard drive shows up, but whenever i click on a file it says i do not have enough permission, even in the "public" folder. i have checked on the mac partition and all my files are read/write access for everyone. any ideas?
thanks

---

### Post by linuxopjemac on 2010-01-18
write access you can only achieve when you disable journaling from within OSX. I can recommend to just copy the files to your Ubuntu drive as root and to then chown them to your user iD. your ID in Ubuntu differs from that in OSX. I would not touch those files honestly. Just copy them to your Ubuntu partition.

```
cp -R /mnt/osx /home/user_linux/documents/osx
``` (for example)
```
chown -R user_linux.user_linux /home/user_linux/osx
```

---

### Post by jlubey on 2010-01-18
ok thank you.  i was hoping to access my music library on my mac (about 60 gb worth) from the ubuntu partition. its not really worth copying that whole library over, ill just listen to my ipod or something lol
thanks!!

---

### Post by linuxopjemac on 2010-01-18
you can read them as root at least, I guess that if you would give 'others' the permission from within OSX to read, then it would be possible .

from within OSX:

```
chmod -R +r /Users/OSXname/path/to/music
```

---

### Post by linuxopjemac on 2010-01-18
it's possible if the foregoing does not work, you might have to make the files executable. I am not sure how playing of mp3 works.

```
chmod -R +x /Users/OSXname/path/to/music
```

---

### Post by jlubey on 2010-01-18
ok thank you so much! i entered that in terminal, ill let you know if it worked (i cant boot into ubuntu right now, my mac is busy downloading an update)
thanks again!!

EDIT:
thank you so much i got it to work!! you are the best!!! :D

---


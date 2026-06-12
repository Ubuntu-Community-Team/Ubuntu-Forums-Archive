---
title: "Run scripts on OS startup"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by priyaaank on 2006-05-11
Hi,

I want to run some "sudo commands" like following

sudo chmod -R 755 xyz 

when My linux bootx up. Have ubuntu 8) 
Please let me know how can I do it, so that I don't have to do it manually everytime. I could set permissions in fstab, but that mounts the drive and sets the permissions for whole drive. And individual permissions are lost when drives are mounted again, on next startup. How could I preserve those alternatively. 

Please let me know, how I could write generic linux commands and run them as scripts on startup.

Thanks in advance!

---

### Post by lol on 2006-05-11
Just add a link to your script in the proper runlevel (/etc/rc2.d usually)

If you want an example of startup script to see how it's done, check those in /etc/init.d, that's always a good start.

---

### Post by Kobalt on 2006-05-11
Or you can add your command in System>Preference>Sessions>Programs at start up...

My Ubuntu is a french one, I hope the names are quite the same in english :)

---

### Post by 3rdalbum on 2006-05-11
Thanks Kobalt, that helped me too!

---

### Post by Kobalt on 2006-05-11
You're welcome *3rdalbum* !

---


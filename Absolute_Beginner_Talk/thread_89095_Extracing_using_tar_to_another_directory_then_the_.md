---
title: "Extracing using tar to another directory then the tar files"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by marlun on 2005-11-11
Hello!

I'm totally new to Ubuntu and I've stumbled up on a little problem. 

I downloaded a file, lets call it file.tar.gz, into my home directory. I managed to gunzip it so it became file.tar, but heres where my problems stars. Now I wanted to extract the tar file using tar into another directory then the one the tar file was in. I wanted to extract it into /var/www/. I read the "man tar" I asked on the ubuntu irc channel but didn't get anything that helped me with my problem. In the end I had to extract it to the same directory as the .tar file and then use mv to move it to /var/www/.

Is it not possible to let tar extract a tar file into any directory then the one it's in?

Thanks in advance!

-Marlun

---

### Post by apjone on 2005-11-11
just 
$tar -xf filename.tar
$cp -r filname/* /var/www/

---

### Post by Kvark on 2005-11-11
Try this:
```
tar -C /path/you/want/it/in -xf archive.tar
```

---

### Post by marlun on 2005-11-12
[QUOTE=Kvark]Try this:
```
tar -C /path/you/want/it/in -xf archive.tar
```[/QUOTE]

Thank you Kvark! It worked really great after I figured out I had to use "sudo" in front of it :)

---


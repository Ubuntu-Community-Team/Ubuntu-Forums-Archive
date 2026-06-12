---
title: "Daemon tools?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-11
Hello anyone who knows some good program that i can mount image with?

---

### Post by Najand on 2006-09-11
no need for a program. just use the mount command:
```

$ sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom

```

For unmounting just do 
```

$ sudo umount /media/cdrom

```

---

### Post by haxer on 2006-09-11
is that all? but how do i play it (its about mounting a movie file)

---

### Post by jdong on 2006-09-11
Huh? Mounting a movie file? what kind of file is it? Or is it an ISO of a DVD?

---

### Post by Najand on 2006-09-11
The command above will mount your iso file to /media/cdrom
Hmm, when you mount it, usuall multimedia player can mount it. Can't they?

---

### Post by haxer on 2006-09-11
Its a file i have downloaded you know one of these elegal "piratebay is actualla swedish and im swedish but i dont usually download things ther becouse it sucks monkeyballs" 


Hmm.. so if i want to play it deos it come a window where i can select whisch player i want to use?

---

### Post by Najand on 2006-09-11
Why don't you mount the file and then check what is inside it by checking out the /media/cdrom folder?

---

### Post by haxer on 2006-09-11
Hasent finished downloading its about 2h left :P so its hard to check it now i would have done it i swear instead of taking time with questions :)

---

### Post by jdong on 2006-09-11
LOL, tell ya what... once it finishes downloading, post the filenames/extensions so we know what we're dealing with.... It should be quite straightforward.

And oh yeah, for all educational purposes of teaching you how to deal with media files under Linux, we will assume you have been granted permission to download the movie from the copyright owner ;)

---


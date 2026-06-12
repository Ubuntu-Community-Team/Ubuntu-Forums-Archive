---
title: "rsync and samba backup"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by illumeo on 2007-09-21
I have a samba share from a windows machine mounted on my ubuntu server.  I want to do an back up of it using rsync. Will this work? I want rsync just to copy the changes each time.

Thanks

Illumeo

---

### Post by bubbalouie on 2007-09-21
I use the grsync front end, so far it has worked, though I also do a less frequent tarball backup to be safe.

To install **sudo apt-get install grsync**

---

### Post by illumeo on 2007-09-21
Thanks for the idea but i don't run the gui on my server just the command line. I would like to avoid installing the gui if i can.  

Thanks

illumeo

---

### Post by hyper_ch on 2007-09-21
that should work fine... if the samba folder is mounted on your server then you can use rsync the way you normally do...

---

### Post by illumeo on 2007-09-22
thanks hyper_ch

---

### Post by hyper_ch on 2007-09-24
so it worked?

---

### Post by illumeo on 2007-09-24
yes it is working but sometimes rsync decides that the files have "changed" (at least that is what i think it is doing ) and so copies them again.
Not sure why or how i can stop it.

---

### Post by viz_e on 2007-10-16
> yes it is working but sometimes rsync decides that the files have "changed" (at least that is what i think it is doing ) and so copies them again.
Not sure why or how i can stop it.

I have the same problem here. The issue seems to be related to how rsync handles attributes over a samba connection.
For instance, rsync adds the "execute" attribute to some of my files in the remote directory. Hence, these files are always different to it in late executions. This does not happen if I copy to a local directory

Any ideas how to solve this? Any help appreciated.

Thanks

---

### Post by hyper_ch on 2007-10-16
well, the problem is that windows doesn't use the same permission scheme as *nix systems do.

---

### Post by viz_e on 2007-10-17
Is there a way to tell rsync to ignore the attributes when checking for different files?

Thanks again.

---

### Post by hyper_ch on 2007-10-17
See yourself:
```

man rsync

```

---


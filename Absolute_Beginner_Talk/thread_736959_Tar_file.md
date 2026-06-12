---
title: "Tar file"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by tobyimages on 2008-03-27
Hi i've downloaded a Tar file that is sat on my debian desktop, when i unpack it as root in the terminal it unpacks on to the desktop instead of the correct locations in /. What am i doing wrong?

Thanks

---

### Post by Bachstelze on 2008-03-27
When you untar a file, it is automatically extracted in the current directory. If you want to extract it to an alternate location, you can specify it with the -C parameter, like this :

```
tar xzvf myArchive.tar.gz -C /myFolder
```

---

### Post by tobyimages on 2008-03-27
Marvelous thats all i need to know. Thanks!

---


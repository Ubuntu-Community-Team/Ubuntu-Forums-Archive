---
title: "How do I empty a directory but keep the directory?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by kpkeerthi on 2007-03-22
```

$Home/
    ... temp/
               ... dir1/
               ... dir2/
               ... dir3/
              ... file1.bak
              ... file2.bak

```

I need to periodically cleanup the temp folder. I have a script in $HOME that I would run as required. I want to keep temp/ but wipe out completely any files and subdirectory contained within /temp.

Right now i'm CD'ing to temp and then rm -rf *. But I would want to acheive the same result from $HOME.

---

### Post by Efros on 2007-03-22
delete the directory and then create a new one of the same name would work for me.

---

### Post by kpkeerthi on 2007-03-22
Oh yes... that would work. I'm stupid. LOL!

---

### Post by Bachstelze on 2007-03-22
```
rm -rf ~/temp/*
```

---

### Post by kittyhawk63 on 2007-03-22
[http://www.tuxfiles.org/linuxhelp/fileman.html](http://www.tuxfiles.org/linuxhelp/fileman.html)

---

### Post by kpkeerthi on 2007-03-22
> rm -rf ~/temp/*
Thank you.

---


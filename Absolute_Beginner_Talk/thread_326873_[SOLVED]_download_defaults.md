---
title: "[SOLVED] download defaults"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-28
can someone please tell me where to set the defaults for downloads. (which directory)

Can the directory called examples be safely deleted without causing unknown problems. I have enough of those already.


Thanks

---

### Post by wpshooter on 2006-12-28
Are you doing the via the DESKTOP (live CD) or are you doing this on a hard drive installation of Ubuntu ?

---

### Post by squrl on 2006-12-28
This is on an installed system

---

### Post by amo-ej1 on 2006-12-28
i think you can happily deleted the examples directory.

you don't mention which download directory you wish to change. If you want to change the firefox default download directory take a look at Edit -> Preferences -> Main -> "Save files to" and change that folder.

---

### Post by squrl on 2006-12-28
Thanks that was painless :)

---

### Post by wpshooter on 2006-12-28
> **amo-ej1 said:**
> i think you can happily deleted the examples directory.

you don't mention which download directory you wish to change. If you want to change the firefox default download directory take a look at Edit -> Preferences -> Main -> "Save files to" and change that folder.

Before you do this, go to the home directory and create yourself a sub-directory of home called "download".  I recommend making the name lower case.

---

### Post by shrimphead on 2006-12-28
IIRC the examples directory that's in your home direcotry is simply a link to the actual examples directory. It's however been given root privileges and therefore must be deleted with 
```
sudo rm examples
```

(this is from memory, I deleted mine ages ago, so apologies if it hasn't got root permissions, either way this should work)

---

### Post by amo-ej1 on 2006-12-28
my download directory is /tmp ;) 

since i did that the amount of trash that started to grow has really diminished ;)

---


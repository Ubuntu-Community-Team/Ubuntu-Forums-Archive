---
title: "new hard drive"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by seanmbarrett on 2007-02-03
hi i finally mounted my new hard drive in ubuntu 6.10 and it can read it. it is fat 32 format. but i also need to be able to write to it. i have searched and cannot find what i need to do. it says it is root . thanks sean

---

### Post by taurus on 2007-02-03
Did you mount it through /etc/fstab?  What does /etc/fstab look like then?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by seanmbarrett on 2007-02-03
hi,
   my fstab looks like 
/dev/hdb1 /media/secondharddrive vfat user,fmask=0111,dmask=0000 0 0

hope this helps sean

---

### Post by taurus on 2007-02-03
What if you change it to

```
/dev/hdb1   /media/secondharddrive   vfat   iocharset=utf8,umask=000   0   0
```

---

### Post by seanmbarrett on 2007-02-03
taurus,
        that seems to have worked. thanks. i really like the idea of linux and and am really unhappy with the way windows is going and ubuntu is a good change. i do have another question i need to get my dvd player to read dvds is there anything i can do? oh yeah and i need to get my webcam to work. any info to get me there woiuld be appreciated.  thanks sean

---

### Post by taurus on 2007-02-03
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by seanmbarrett on 2007-02-03
oh i forgot say i am using amsn and giam for msging. thanks

---

### Post by seanmbarrett on 2007-02-03
thanks again taurus, my dvd is up and runnning. sean

---


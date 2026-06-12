---
title: "moving folder one owner to another"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-02-25
My ftp server is set up but the folder used for uploads / downloads is owned by root , so no one can read / write to it. 

How do I change that so it's owned by , say "guest" ? I know it's going to be sudo chmod (something or other) .... but I don't see any options to change owners ...

---

### Post by solar george on 2007-02-25
You need to use chown.

```
sudo chown -R guest:guest *uploadfolder* 
```

Replace *uploadfolder* with the upload location.

---

### Post by koconnor100 on 2007-02-25
my goodness what a pain.

forgot to give "user" upload privilidges...lol

he's uploading now...finally !!!!

:guitar:

---


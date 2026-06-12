---
title: "Mounting iso files"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-09
I understand how to mount the files, but where should I mount them? I tried to make an iso directory in /mnt but it said access denied...

---

### Post by R6V2 on 2008-04-09
Just use something like Roxio, and then  insert a CD, right click the .iso file and choosing: Write to CD or something. This will find the drive with the cd, and all you have to do is press: OK! :)

---

### Post by tamoneya on 2008-04-09
```
sudo apt-get install gmountiso
``` Then look in your applications menu.

---

### Post by bidget on 2008-04-09
I've already installed that, what I'm asking is where should I mount the iso files?

---

### Post by ibutho on 2008-04-09
> **bidget said:**
> I understand how to mount the files, but where should I mount them? I tried to make an iso directory in /mnt but it said access denied...

Use "sudo mdkir /mnt/somedir" to create the directory and then to mount an iso file, you would do
```
sudo mount -o loop -t iso9660 filename.iso /mnt/somedir
```

---

### Post by bidget on 2008-04-09
Ah I just left the sudo part off of the front. What does sudo actually mean?

---

### Post by FuturePilot on 2008-04-09
> **bidget said:**
> Ah I just left the sudo part off of the front. What does sudo actually mean?

**Su** **Do**
sudo will run that one command with root privileges.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ene_dene on 2008-04-09
I don't think it's important where you mount them, mount them where ever you want. But if you want to use /mnt directory write sudo before command for mounting, if mounting in some directory in your home directory you don't need sudo.

---

### Post by bidget on 2008-04-09
Alright I got it :) Thanks everyone!

---


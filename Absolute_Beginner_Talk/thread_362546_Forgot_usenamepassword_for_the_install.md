---
title: "Forgot usename/password for the install"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by desi.bacha on 2007-02-15
I has installed Ubuntu before going to holidays and now I have forgotten.

How can I reset or what is the default user/password when you install the ubuntu first time.

Thanks

---

### Post by Bachstelze on 2007-02-15
At the GRUB screen, you have a "recovery mode" option, choose it and you will get a root prompt. Then

```
cat /etc/passwd | grep 1000
```

will give you your username, you can then do

```
passwd USERNAME
```

to set a new password.

---

### Post by desi.bacha on 2007-02-15
Wow that was very prompt, I am already liking this forum.

I am pretty new to linux(try to switch over from windows), so help me understand how I can get that "At the GRUB screen" or how will I see that screen.

Thanks

---

### Post by PPAAUULL on 2007-02-15
ok do you have a GRUB menu when you boot up where it lets you choose what OS you want to boot into?

---

### Post by Bachstelze on 2007-02-15
GRUB is the default bootloader used in Ubuntu (i.e., the pice of software that load the actual OS). The GRUB menu refers to something like [this](http://img150.imageshack.us/img150/1682/grub4kt.jpg) you see when you start your computer. Sometimes, the menu is hidden and you just see "Press ESC to show menu", just press ESC and it will apear.

---

### Post by desi.bacha on 2007-02-15
No I have not set as multiboot. 

I was fed up from windows so just wiped that off and all I have is ubuntu now.

---

### Post by Bachstelze on 2007-02-15
> **HymnToLife said:**
> GRUB is the default bootloader used in Ubuntu (i.e., the pice of software that load the actual OS). The GRUB menu refers to something like [this](http://img150.imageshack.us/img150/1682/grub4kt.jpg) you see when you start your computer. **Sometimes, the menu is hidden and you just see "Press ESC to show menu", just press ESC and it will appear.**

This should be your case then ;)

---

### Post by PPAAUULL on 2007-02-15
HymnToLife is right. That is what you need to do to get there.

---

### Post by snowwolf on 2007-02-15
ok here's my problem.  Someone gave me this computer and it has ubuntu on it.  it also has a password that I don't know.  

I have tried doing what is said above but all i get is a error 15 file not found.

Keep in mind I have never used ubuntu or even heard of it till i booted this computer up.

If I can't get into it can I just install xp the usual way or do i need to do something different?

thanks for any help

---

### Post by desi.bacha on 2007-02-15
You should follow the above said documentation, I think this will get you into the box loaded with Ubuntu.

Do not switch back to XP, has you seen a forum which helps you so fast and accurately.

I am also in similar boat but I know the answer now and tonight I will login back to my old box.

---

### Post by Bachstelze on 2007-02-15
If you just want to install XP, you can indeed install it the "usual" way, booting from the CD and deleting all existing partitions before.

---

### Post by snowwolf on 2007-02-15
I meant to tell you that ubuntu is the only OS I have on the system.

thanks again

---


---
title: "Opening .rar file."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by And1945 on 2007-05-01
Hi all.

Im still a newbie in Ubuntu, but I must say that I absolutely love it.
Anyway, I have a .rar file, that I cant open with the default archive managing, xarchiver or karchive.

Whats going on? Can anyone shed some light on this? I could on my revious Ubuntu installation, so it might be something I did.

---

### Post by supersonicdarky on 2007-05-01
```
sudo apt-get unrar
```

---

### Post by Tomosaur on 2007-05-01
I can't remember the exact name of the package you need to install, but I think it may be 'unrar'. This should provide the archive manager with .rar functionality. If it isn't unrar, then just search for rar related packages in Synaptic. I know I had to manually install a package, but I can't remember the name unfortunately.

---

### Post by Bachstelze on 2007-05-01
Rar is a non-free format so it's not supported by default in Ubuntu for legal and/or ethical reasons. You need to install a plugin for it :

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by And1945 on 2007-05-01
> **supersonicdarky said:**
> ```
sudo apt-get unrar
```
Gives me an error with that unrar is an unvalid command.

Dont worry... i typed it in the terminal... im not that new anymore :)

Edit: I had to add install in the command, that did it.

> **Tomosaur said:**
> I can't remember the exact name of the package you need to install, but I think it may be 'unrar'. This should provide the archive manager with .rar functionality. If it isn't unrar, then just search for rar related packages in Synaptic. I know I had to manually install a package, but I can't remember the name unfortunately.

**Terminal:** sudo apt-get install unrar

> **HymnToLife said:**
> Rar is a non-free format so it's not supported by default in Ubuntu for legal and/or ethical reasons. You need to install a plugin for it :

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)
So after that 40day trial runs out, I cant work with rar files in Ubuntu anymore?

---

### Post by Bachstelze on 2007-05-01
Ytu're supposed to   apt-get *install* unrar

See the link I posted.

---

### Post by And1945 on 2007-05-01
> **HymnToLife said:**
> Ytu're supposed to   apt-get *install* unrar

See the link I posted.
I did, and I got it working. But my question remains... after the 40 day trial, does my support for rar files end?

---

### Post by teddybairs1 on 2007-05-01
What forty day trial? rar and unrar are from the repos. I never had to agree to a forty day trial. Also, if you need to install a package, often synaptic, under System -->Administration, is a lot easier to do a search in than using apt-get. Just my preference anyway.

---

### Post by Bachstelze on 2007-05-01
[http://packages.ubuntu.com/feisty/utils/rar](http://packages.ubuntu.com/feisty/utils/rar)

there seems to be a 40-day trial indeed.

---

### Post by teddybairs1 on 2007-05-01
Oh, didn't see that. But it doesn't turn off on you after forty days.

---

### Post by And1945 on 2007-05-02
> **teddybairs1 said:**
> Oh, didn't see that. But it doesn't turn off on you after forty days.
Sweet. I hope it doesnt do that on me either.

---


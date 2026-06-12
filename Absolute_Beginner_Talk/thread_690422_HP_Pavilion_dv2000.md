---
title: "HP Pavilion dv2000"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by necrodealer on 2008-02-07
Ok all Im new to Linux, and really dont know too much about the tech of comps, but I can try to figure most things out. Unfortunetly I just cant seam to get my wifi to work. Anyone have any simple way of explaining the process to me, that would be muchly appreciated.

---

### Post by myddewji13 on 2008-02-07
i have the same type of laptop you do...and i finally got my wireless working...but before i can help...what type of card do you uhave? .. (if you dont noe....the exact model of your pavilion might help...its on the bottom of your laptop on the white sticker)...

---

### Post by myddewji13 on 2008-02-07
ok...easier way....hit alt-f2 ..type in gnome-terminal 
then type in 
```
lspci
```

paste output into your post and ill see if i can help

---

### Post by Golem XIV on 2008-02-07
I have also a dv2000 and I fixed it using information from [this article]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

My specific wireless adapter goes under step 2b, but having also a dv2000 doesn't mean much - there are several variants.  Hopefully the link will help in any case.

Note that the downloading of the Windows drivers from the Compaq FTP site didn't work right away since the site does not recognize PASV FTP.  Personally, I fixed it by installing FileZilla from the repositories (**sudo apt-get install filezilla**) and setting it to Active FTP, then connecting and downloading.

Good luck!

---


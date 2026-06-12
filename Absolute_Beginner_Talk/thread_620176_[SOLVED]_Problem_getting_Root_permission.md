---
title: "[SOLVED] Problem getting Root permission"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-11-22
OK, I've searched the forum, found lots of posts that start to answer the question, but then drop off into sudo speak and I get lost. Can someone please tell me how to get root permission?  I tried to modify my menu.lst file in grub, had it all set, went to save it and got "Can't save, you don't have root permission."  I get this on almost every file I try to move, copy or save. 

I am a total newbe to Ubuntu, but it looks great. Please help:confused:

Thanks

---

### Post by taurus on 2007-11-22
Applications -> Accessories -> Terminal
```
**gksudo** gedit /boot/grub/menu.lst
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-11-22
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Cannaregio on 2007-11-22
> **Don1500 said:**
> OK, I've searched the forum, found lots of posts that start to answer the question, but then drop off into sudo speak and I get lost. Can someone please tell me how to get root permission?  I tried to modify my menu.lst file in grub, had it all set, went to save it and got "Can't save, you don't have root permission."  I get this on almost every file I try to move, copy or save. 

I am a total newbe to Ubuntu, but it looks great. Please help:confused:

Thanks


From a terminal:

```
sudo -i
```


and you'll be root after giving your password just once.
But beware: being really and continuously root in a GUI environment is insane and you'll regret it pretty soon. Sudo everytime you need a root command, it is MUCH safer.

---

### Post by Don1500 on 2007-11-22
Thanks, you would not believe the journey I've been on. Did what you said, (gedit....) and my system locked up so bad I had to reinstall. Your fault? I doubt it. Reinstalled and for some reason my password wouldn't work. Had to reinstall again. Anyway, I have Ubuntu up and running again, and I'll leave the menu.lst alone for a while. At least I know how to do it now, thanks to all....Have a Happy Thanksgiving.:popcorn:

---

### Post by bodhi.zazen on 2007-11-22
> **Don1500 said:**
> Thanks, you would not believe the journey I've been on. Did what you said, (gedit....) and my system locked up so bad I had to reinstall. Your fault? I doubt it. Reinstalled and for some reason my password wouldn't work. Had to reinstall again. Anyway, I have Ubuntu up and running again, and I'll leave the menu.lst alone for a while. At least I know how to do it now, thanks to all....Have a Happy Thanksgiving.:popcorn:

LOL

while not the method I would have used, glad it worked out ...

---


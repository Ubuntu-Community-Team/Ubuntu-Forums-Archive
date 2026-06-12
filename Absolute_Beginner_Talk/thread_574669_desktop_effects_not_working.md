---
title: "desktop effects not working"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by prakhar on 2007-10-13
I have installed ATI driver still desktop effects not working

I disabled ATI driver now no display after login

---

### Post by jvc26 on 2007-10-13
If you are using the fglrx driver you will need to use xgl, as at present it doesn't support AIGLX. There are instructions for this in the community documentation (see [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)) If you removed the driver then obviously you won't have one at startup and hence you won't get a graphical login. Which ATI card do you have? You may be able to use the free drivers, or alternatiovely flgrx with xgl
Il

---


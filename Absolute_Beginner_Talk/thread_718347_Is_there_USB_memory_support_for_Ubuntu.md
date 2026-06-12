---
title: "Is there USB memory support for Ubuntu?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-08
Is there USB memory support for Ubuntu like Vista?

---

### Post by the-edmeister on 2008-03-08
See my USB memory stick thread here:
[http://ubuntuforums.org/showthread.php?t=717471](http://ubuntuforums.org/showthread.php?t=717471)

I can't get my memory stick with data from a W2K system recognized in either Ubuntu or openSUSE.


Ed

---

### Post by adi_das on 2008-03-08
Is the USB Flash memory support for Ubuntu?

---

### Post by ubuntu27 on 2008-03-08
I have seen a forum How-to for Use USB as a memory. I will look for it and post the link. You should look for it too.

---

### Post by PeterJS on 2008-03-08
Would it be as simple as creating a swap file on a flash device? or is there something more complicated and arcane to that will give you that little speed boost by cutting out the file system abstraction and treating it as raw memory?

---

### Post by ubuntu27 on 2008-03-08
I coud not find it. I swear I saw a how-to or Tutorial on how to to this. 
If I remember correctly, it mentioned about formating the Flash or USB drive as Swap. ANd then they did something else.... 

The clses thing I found is [this thread]("http://ubuntuforums.org/showthread.php?t=208026")


Well, I have to go. Its 11:57 PM here

---

### Post by prshah on 2008-03-08
If you mean like ReadyBoost, there is no direct support as such. You can, as suggested by PeterJS  create a swap on your usb drive (see [http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435) ) but this memory will only be used when your system memory is running low, so it will not help with caching.

Cheers,
PRShah

---


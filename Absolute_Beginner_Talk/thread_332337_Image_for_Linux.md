---
title: "Image for Linux"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by dsmithnc on 2007-01-05
I am trying to install Image for Linux from Terabyte Unlimited.  The directions tell me to make sure the "edd" is enabled in linux.  I have determined that it is not even present in my release of 6.06.  How does one go about adding that to the kernel?

Dick

---

### Post by 23meg on 2007-01-06
I just checked and the edd module doesn't get loaded and can't be added with "sudo modprobe edd" in my Edgy installation. Perhaps it's outdated, or removed from the Ubuntu kernel for some other reason. You may have to compile it manually, and if it's deprecated, it may cause unwanted behavior due to a possible conflict. 

Did you look into Free software alternatives for making disk images?

[http://www.systemimager.org](http://www.systemimager.org)
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.mondorescue.org/](http://www.mondorescue.org/)

---

### Post by dsmithnc on 2007-01-06
> **23meg said:**
> I just checked and the edd module doesn't get loaded and can't be added with "sudo modprobe edd" in my Edgy installation. Perhaps it's outdated, or removed from the Ubuntu kernel for some other reason. You may have to compile it manually, and if it's deprecated, it may cause unwanted behavior due to a possible conflict. 

Did you look into Free software alternatives for making disk images?

[http://www.systemimager.org](http://www.systemimager.org)
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.mondorescue.org/](http://www.mondorescue.org/)

Well, yes, I have tried a couple but had problems with them, particularly partimage.  I'll check out your other suggestions.  Thanks much.

Dick

---


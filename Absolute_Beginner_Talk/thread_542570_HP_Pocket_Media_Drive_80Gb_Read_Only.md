---
title: "HP Pocket Media Drive 80Gb Read Only"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-09-04
Hi all, 

I recently got [this]("http://www.shopping.hp.com/product/desktop/desktop_hp/storage/1/accessories/RF242AA%2523ABA;HHOJSID=3Rd8G8QD9dmBTLtLKjzMhYqbYnN4yRLlVNvwwG5Vc4y0h4GLGhxG!-1830859331") given to me, and when i plug it in, i can view all the files on it, and everything looks good, except that it is read only... any ideas on how i make this so that i can write to it? 

Thanks

Patrick

---

### Post by RaZer0r on 2007-09-04
what's the filesystem? NTFS? or fat16-32?
I assume it's ntfs, and that is the reason you are not able to write on it.


```

sudo apt-get install ntfs-config

```


Now, it's rather easy. Just launch ntfs-config via the menu (in system tools) or via the terminal :

```

gksu ntfs-config

```


If your NTFS partitions are not yet configure, it will ask you to choose a name that will be use as mount point. Just put the name you want.
Then just enable write support for internal and/or external device, and that's all.

---

### Post by ozPATT on 2007-09-04
Hi thanks for that... I just tried what you said, and enabled write support for external device, but I am still not able to write to it. Will I need to restart for changes to take effect? Also how do i find out what format it is? 

Thanks

Patrick

---

### Post by wolfen69 on 2007-09-04
rebooting cant hurt. it is probably ntfs.(since most people use windows)

---

### Post by nonewmsgs on 2007-09-04
man there's been a ton of these issues with thumbdrives/flashdrives/pocket media.  the pain is that the indexing isnt working because there's a million and 5 different names.  has there been any real solutions?

---

### Post by nowshining on 2007-09-05
you have to configure it first :) did you put in a name for it 

applications - system tools - NTFS configuration tool

and enable both - however I fogot exactly how to but if I remember correctly ou need to click under name or something and input a name...

---


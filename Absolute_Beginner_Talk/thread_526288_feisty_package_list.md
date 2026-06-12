---
title: "feisty package list"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Jeff_Wright on 2007-08-15
I am installing feisty fawn and am selecting ubuntu-standard, ubuntu-desktop. I was hoping to find a list of all of the packages installed with each choice. I found the list of packages available for feisty here:

[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

But it does not identify the packages that are installed by default.  

I would like to have a list so that I can create a netboot install with a preseed file that provides a complete set of the packages I need.

Thanks,

Jeff

---

### Post by nanotube on 2007-08-15
> **Jeff_Wright said:**
> I am installing feisty fawn and am selecting ubuntu-standard, ubuntu-desktop. I was hoping to find a list of all of the packages installed with each choice. I found the list of packages available for feisty here:

[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

But it does not identify the packages that are installed by default.  

I would like to have a list so that I can create a netboot install with a preseed file that provides a complete set of the packages I need.

Thanks,

Jeff

hm, well, /after/ you make a fresh install, you can make a list of all the packages that are installed. 
just use command 
```
dpkg --get-selections
```
 will give you a nice long list of installed packages.

don't know where you'd get such a list prior to installation.

---

### Post by overdrank on 2007-08-15
> **Jeff_Wright said:**
> I am installing feisty fawn and am selecting ubuntu-standard, ubuntu-desktop. I was hoping to find a list of all of the packages installed with each choice. I found the list of packages available for feisty here:

[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

But it does not identify the packages that are installed by default.  

I would like to have a list so that I can create a netboot install with a preseed file that provides a complete set of the packages I need.

Thanks,

Jeff

HI you can get a history in synaptic manager under system,administration, synaptic manager. Under file History. Good luck and welcome hope this helps.

---

### Post by Jeff_Wright on 2007-08-15
dpkg --get-selections

appears to do the trick, thanks!

I would be a very good idea, IMHO, if ubuntu included a package list of each flavor of feisty though.

Jeff

---

### Post by nanotube on 2007-08-15
> **Jeff_Wright said:**
> dpkg --get-selections

appears to do the trick, thanks!

I would be a very good idea, IMHO, if ubuntu included a package list of each flavor of feisty though.

Jeff

glad it worked out for you :)

i wouldn't be surprised if the list is actually out there somewhere... i just don't know where to look for it. :)

---


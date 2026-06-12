---
title: "applesmc: FS! : read arg fail"
date: 2012-05-08
forum: Apple Hardware Users
---

### Post by lael on 2012-05-08
I have a bunch of read arg fails in my syslog after upgrading to 12.04
```
...
[  313.771886] applesmc: FS! : read arg fail
[  318.824256] applesmc: FS! : read arg fail
[  323.879707] applesmc: FS! : read arg fail
[  328.949428] applesmc: FS! : read arg fail
[  334.001656] applesmc: FS! : read arg fail
[  339.058661] applesmc: FS! : read arg fail 
...
```
some write failures too.  

What do these mean? 

MacBookPro6,1, Ubuntu 12.04, I've also installed macfanctld from the mactel ppa.

---

### Post by drtheradio on 2012-05-08
Upgrading has never worked for me.


I gess too much stuff is changed. and rearrange.

I recommend 
backing every thing you want to keep and doing a fresh install.

you can move evey thing you want to keep to a folder named Mystuff .

Now you can do this off the live cd. I'M not sure where your web favorites are saved. mabe Mozilla or firefox folder.

but any way ...It would be a Miracle if you got your upgrade to work as good as a clean install.

also
you could have bad disc.

Look at the Smart Status in Disk Utility . It usually tells you if you have bad sectors

---

### Post by Kallun on 2012-05-08
> **lael said:**
> I have a bunch of read arg fails in my syslog after upgrading to 12.04
```
...
[  313.771886] applesmc: FS! : read arg fail
[  318.824256] applesmc: FS! : read arg fail
[  323.879707] applesmc: FS! : read arg fail
[  328.949428] applesmc: FS! : read arg fail
[  334.001656] applesmc: FS! : read arg fail
[  339.058661] applesmc: FS! : read arg fail 
...
```
some write failures too.  

What do these mean? 

MacBookPro6,1, Ubuntu 12.04, I've also installed macfanctld from the mactel ppa.

No idea what that issue is, but it certainly looks SMC related.

Try [resetting the SMC](http://support.apple.com/kb/HT3964). That might do the trick :)

---

### Post by lael on 2012-05-08
> **drtheradio said:**
> I recommend backing every thing you want to keep and doing a fresh install.

I misspoke, I did do a fresh install next to my 10.10 partition.
My 10.10

---

### Post by drtheradio on 2012-05-09
If its not on anouther partions you will have problems.
you should shrink your partion with fdisk...and make two partions.
hope this helps...

---


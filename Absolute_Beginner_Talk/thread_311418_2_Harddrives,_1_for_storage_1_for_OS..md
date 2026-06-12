---
title: "2 Harddrives, 1 for storage 1 for OS."
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by Iskander on 2006-12-02
Ok Guys, Sorry to say Im giving up on Ubuntu, Yes its true its a great Operating system It just doesnt quite meet my expectations in graphics, and yes I have tried Gimp. What I want to know is, how would I remove ubuntu from my 30GB and make it storage and also remove grub that way It will boot up WIN2k And Ill have both Harddrives operational, On Windows XP the 30GB Being my Storage Drive. And the 15GB Being My OS Drive. Oh, Yes And I need to be able to remove GRUB So I dont get any Grub Errors at Boot.

---

### Post by LLRNR on 2006-12-02
Sorry you don't like Ubuntu... So this is the way to get back to Windows:

You can easily do that from the XP install CD. Boot from it, choose Recovery Console mode, then first do 
```
fixmbr
```which will restore your MBR => you'll get rid of GRUB this way, and then use```
diskpart
```to first remove your ext3 partition(s), and them repartition them (i.e. recreate them the "Windows" way, with a drive letter), then - depending on the drive letters assigned by *diskpart*, do```
format d: [ or e:, f:, ... ]
```

LLRNR

---

### Post by turbojugend_gr on 2006-12-02
I hope you 'll be back here some time m8, maybe that adobe of yours decides to port to Linux, would this do it for you?

To your question now, I 'll say that I second LLRNR (how couldn't I, he's a Dio fan too..;)).

---


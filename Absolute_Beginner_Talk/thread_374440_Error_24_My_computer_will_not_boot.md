---
title: "Error 24/ My computer will not boot"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-03-02
Today my computer started behaving very badly. I have successfully used ubuntu on my hard drive for a few weeks now and it was working perfectly yesterday. Then this mourning I tried to log into my computer and it denied me. I know my own username and password and tried several times again, but each time it denied me. Then I decided to turn the power off and restart. Now every time the hard drive loads, it says GRUB Loading... 
Error 24

I would greatly appreciate any help you can give so that I can continue using my Ubuntu computer again. Thanks. 

:guitar:

---

### Post by carlosfocker on 2007-03-03
this error points to following in the grub manual:

```
24 : Attempt to access block outside partition
    This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 
```

This most likely means hard drive problems.  You may want try running the Live CD and using the following

```
sudo e2fsk /dev/<partition with os>
```

It is referenced in this post [http://www.ubuntuforums.org/showthread.php?t=210819](http://www.ubuntuforums.org/showthread.php?t=210819)

---


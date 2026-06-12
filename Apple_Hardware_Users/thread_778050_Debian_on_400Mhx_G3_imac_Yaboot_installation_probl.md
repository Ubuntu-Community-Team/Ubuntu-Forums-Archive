---
title: "Debian on 400Mhx G3 imac??? Yaboot installation problem"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-05-01
I just tried to install Debian 2007 on my imac. It worked fine until I got to the yaboot part...it said that it could not install yaboot. It says to manually boot with the /vmlinux kernel on partition /dev/hda3 passed as kernel argument.........??? What does that mean? My system is unbootable. How can I fix this??

---

### Post by shgadwa on 2008-05-01
Here is someone with the same problem that has slightly more detail....

[http://ubuntuforums.org/showthread.php?t=25907](http://ubuntuforums.org/showthread.php?t=25907)

---

### Post by shgadwa on 2008-05-01
Also, I had the drives automatically formatted....any  way to fix this without reinstalling the OS and chancing the same problem twice?

---

### Post by shgadwa on 2008-05-01
Sorry for multiply posts but I keep thinking of how to help you guys help me...

Furthermore, I cannot get past the boot prompt (it seems that debian only has one boot prompt) and I cannot get past it. It says unknown or currupt filesystem, I am assuming because it does not ahve yaboot installed.

---

### Post by stream303 on 2008-05-02
> **shgadwa said:**
> It says to manually boot with the /vmlinux kernel on partition /dev/hda3 passed as kernel argument.........??? What does that mean?

It means that it can't find the root partition, so you would have to manually tell it so at the second-stage boot: prompt

```
Linux root=/dev/hda3
```

You can help us help you better by not creating multiple threads with nearly the same subject matter - now the help is scattered, and likely to be ignored because of that.  It makes it very hard for us to concentrate our efforts to help you, although I'll do my best.

---

### Post by shgadwa on 2008-05-02
> **stream303 said:**
> It means that it can't find the root partition, so you would have to manually tell it so at the second-stage boot: prompt

```
Linux root=/dev/hda3
```

You can help us help you better by not creating multiple threads with nearly the same subject matter - now the help is scattered, and likely to be ignored because of that.  It makes it very hard for us to concentrate our efforts to help you, although I'll do my best.


Ok...I will try that. I will also try to narrow my posts.

---

### Post by oswaldkelso on 2008-05-02
I would check you have boot enabled. If you startup from your net install cd (hold down the c key on boot) you can run through the setup untill partitioning. important choose manual! look at you partition table and see if there is a B in the bootable partition.
if not set it.
if it looks ok press tab to get (goback) and you'll get the install yaboot to hard disk option try that

---


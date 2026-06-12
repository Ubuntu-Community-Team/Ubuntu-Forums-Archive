---
title: "rm /bin"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by arrrghhh on 2007-07-30
i rm'd /bin... and when i went to cp the /bin directory off my home computer, i got an error and i couldn't get everything from my /bin directory.  what can i do?  can i just copy the /bin directory from an expanded .iso to the local machine in xubuntu?  thanks!

---

### Post by KIAaze on 2007-07-30
What error did you get?
Which files can't you copy?

As root, you should be able to copy everything.

---

### Post by Famicommie on 2007-07-30
Why on Earth would you delete /bin? That's where many important system tools are kept!

Your best bet would be to boot from the LiveCD, mount your hard drive with:```
sudo mount -t ext3 /dev/hda1 /mnt
``` and copy the files from the /bin directory on the LiveCD to the hard drive ```
sudo cp /bin /mnt/bin
```

In the first command, replace /dev/hda1 with the actual location of your linux install. If you don't know how to find that, feel free to ask for more help :D

---

### Post by heimo on 2007-07-30
I too was thinking about what Famicommie above suggests. It'd be interesting to know if that works. Be sure to use same version of Ubuntu LiveCD as your installed system. (The same one you installed from.)

---

### Post by arrrghhh on 2007-07-30
> **Famicommie said:**
> Why on Earth would you delete /bin? That's where many important system tools are kept!

Yea... I didn't notice which directory I was in... thought I was in the directory for my USB key, NOT the main directory on the localmachine!  I messed up, rookie mistake.

Thanks for the advice, that's all I really wanted to know - is if I can just replace all the files from the /bin directory on the livecd... I'm tryin it now!

edit - forgot to update the thread... the livecd suggestion worked like a charm!  thanks a bunch!

no more n00b mistakes... sheesh!  the first few months of linux are a HUGE learning curve!

---


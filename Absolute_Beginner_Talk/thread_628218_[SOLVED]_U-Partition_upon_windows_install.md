---
title: "[SOLVED] U-Partition upon windows install"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by itix on 2007-12-01
I have problems again. I formatted  and reinstalled my windows partition today, and of course it was as windows-ish as it always is, and disabled my Ubuntu partition. Anyone knows any commands i can run from the live-CD terminal, or any graphical interface which enables it on the live-CD (prefer the last)??

---

### Post by ItsMitsHere on 2007-12-01
What do you mean by windows disabled your UBUNTU partition? Do you mean that your ubuntu partition is not mounted while running windows? or do you mean that the ubuntu partition is mounted but you can not access the data. Or you mean that you want to boot from ubuntu partition (i.e.you want dual boot system)? 

As for running live cd, you can always access all the linux supported partitions from live cd, even windows partitions!

---

### Post by antoz on 2007-12-01
By reinstalling windows you got rid of GRUB so provided this is all you did you can reinstall grub with the help of the Live CD.
Check the link there is a lot of reading but about half way down it tells you how to do that.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Hope this helps,A

---

### Post by itix on 2007-12-01
Thanx, I'll try.

---

### Post by jordanmthomas on 2007-12-01
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I always use an Ubuntu LiveCD to install Grub.
Basically, it's just this:
```
sudo grub
```
and in the grub prompt
```

root (hd0,0)
setup (hd0)
quit

```

Your setup will likely vary, though, so check the link above.

---

### Post by itix on 2007-12-01
Solved :D
Thank you all for taking your time.

---


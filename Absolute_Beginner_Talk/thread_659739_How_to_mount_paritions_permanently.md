---
title: "How to mount paritions permanently"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-01-06
Hi.
I configured my system to have three partitions.
The two partition seem to be unmounted and I have to click on each partition to mount them and to give each one a label (disk and disk-1).
How to make them mounted permanently?
Thanks.

---

### Post by Rocket2DMn on 2008-01-06
Have a look at these 2 links:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Definitely post back if you have specific questions, just include the output of
```

cat /etc/fstab
sudo fdisk -l
```
Good luck!

---

### Post by HuBaghdadi on 2008-01-06
Sorry, I didn't tried it yet as I'm far from my Laptop.
One more question:
Why Linux lists disk and disk-1 under /media directory upon clicking on them?
If I mounted them permanently, will they still under /media or I have to move them away?
Thanks.

---

### Post by Rocket2DMn on 2008-01-06
When you  mount them permanently, they will have an entry in /etc/fstab and you will be able to mount them with any name you want (the /media directory is where we tend to place them, but you don't have to call them "disk").

---


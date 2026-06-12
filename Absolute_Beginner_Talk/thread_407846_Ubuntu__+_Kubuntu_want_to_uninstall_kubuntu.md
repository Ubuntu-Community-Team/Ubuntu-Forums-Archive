---
title: "Ubuntu  + Kubuntu want to uninstall kubuntu"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by USAgent on 2007-04-12
Hello, my problems is as follows.
I have had Ubuntu (Feisty Fawn) for a few weeks now and enjoy it. Yesterday my wireless stopped working and it was driving me crazy. So I popped in my Kubuntu live cd, and the wireless was working fine. So I installed Kubuntu on a new partition, and after finding out what I needed to do to fix my Ubuntu wireless I went back to Ubuntu and the wireless worked. Great. Now after going back to Ubuntu, I realized that I gave Kubuntu a much larger partition than I needed to. I not only would like to "uninstall" Kubuntu, but also give the space that is on that partition (along with the linux swap file it created) back to Ubuntu. I have gone into Gparted  and tried deleting, reformating it, but nothing ever happens. Can someone please help? 
Thanks in advance.

---

### Post by USAgent on 2007-04-12
*Bump* :(

---

### Post by machoo02 on 2007-04-12
If you are using Gparted, be sure that your kubuntu partitions are not mounted at the time.  ```
sudo umount /kubuntu/partitions
```Alternatively, you could use the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to delete the kubuntu partitions.

---

### Post by USAgent on 2007-04-12
Hey thanks alot, I ended up using the Gparted Live cd, and it worked like a charm thanks again :D

---


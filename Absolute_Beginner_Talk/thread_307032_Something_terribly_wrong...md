---
title: "Something terribly wrong.."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Villa on 2006-11-26
Last night I turned off my computer manually (pressing shut down button) because my computer froze. Now when I turned it on today, it said something about disks failing and there was just white writing on the black screen. I can't scroll up to see what it said in detail, because I was typing in some random stuff to restart my computer. I'm running Ubuntu 6.10.


How do I restart my computer? What has likely happened?

Please help!

---

### Post by taurus on 2006-11-26
Do you remember which program caused your computer to freeze?  See if it boots again by pressing the reset button on the case...

---

### Post by Villa on 2006-11-26
Not sure. It was just that my computer was running really sluggish, and I tried to restart but then everything forze. I was running firefox and vlc media player at the time.

---

### Post by taurus on 2006-11-26
What's the spec of your machine anyway?  Usually around summer, the power here goes out all the time because of severe weather and my machine just comes right up.  Do you know what filesystem you use?

---

### Post by Villa on 2006-11-26
Hi awfully sorry about the late reply. =( It turned out ok though, I pressed the reset button as you said, and it started back up as normal. =)

My specs are: Gigabyte K7 Triton series GA-74M400M(F) | Athlon XP 2500+ | 512MB DDR333 | 9200SE 128MB | Seagate 160GB | LG GSA-4167B DVD-rom | 19" LCD BenQ FP91G+

Sorry I don't know what filesystem I use. =(

Thanks for the help!

---

### Post by taurus on 2006-11-26
You probably use ext3 which is much better than ext2 in term of crashes and power outages...  And if you want to know, look in /etc/fstab.

```
cat /etc/fstab
```

---


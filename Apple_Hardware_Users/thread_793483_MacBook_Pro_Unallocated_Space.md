---
title: "MacBook Pro Unallocated Space"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by fily on 2008-05-13
So I decided to remove Ubuntu so I can later install it as a triple boot with Windows XP. I deleted the SWAP and the actual Linux partition, but now, I'm left with 20GB of unallocated space that I can't do anything with basically. I can't access it in Mac or restore it back into just the Mac partition. 

Any ideas on how I can restore the 20GB into my mac partition, so basically restoring everything?

Thanks in advance.

---

### Post by macaholic on 2008-05-13
YOu should be able to use the "diskutil" comamnd udner OSX to resize your current partition to acommedate the unallocated space. Have a look [here]("http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes") for more info.

---

### Post by fily on 2008-05-13
I don't understand what I'm suppose to do looking at that tutorial..

---

### Post by macaholic on 2008-05-13
Alright, I'll try to walk you through it, however it's been a while since I did it myself. first off, what is the output of ```
diskutil list
```

---

### Post by fily on 2008-05-13
I don't know if I'm allowed to post pictures, but here's what comes up.

[img]http://farm3.static.flickr.com/2260/2491217844_7b13237e07_o.jpg[/img]

---

### Post by macaholic on 2008-05-13
Sorry about that, forgot I was suppsoed to be helping you and was readign some other forum posts. First off it is best if you post terminal outputs wrapped wit hthe 'code' option (# sign). Secondly, let me make sure of something, do you want to add 20gbs to your current partition?

---

### Post by fily on 2008-05-13
Well, see, I partitioned my harddrive, so that there was two partitions, one for my Mac stuff, one for Linux. I erased Ubuntu, and now I'm left with the unallocated 20GB. I want to add the 20GB to my Mac partition.

---

### Post by macaholic on 2008-05-13
What is the output of```
diskutil resizeVolume disk0s2 limits
```

---

### Post by fily on 2008-05-13
And actually I just figured it out. But I still want to thank you greatly for spending a little while trying to help. Thank you so much.

---

### Post by macaholic on 2008-05-13
> **fily said:**
> And actually I just figured it out. But I still want to thank you greatly for spending a little while trying to help. Thank you so much.
No problem, always good to figure it out yourself. Good for you for actually trying to fix it yourself. Many people on these forums will just mindlessly follow commands, and essentially have others fix all their problems for them.

---


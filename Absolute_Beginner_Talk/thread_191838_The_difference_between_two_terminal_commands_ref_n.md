---
title: "The difference between two terminal commands ref: nvidia-glx"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-08
Hi,

I managed to uninstall my Nvidia driver and was left with only a terminal.  I used the terminal to reinstall my Nvidia driver and all is well again.

My question relates to these two commands. Do they do the same thing or is one better than the other?

Thanks.

```
sudo apt-get install nvidia-glx
```


```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

...

A follow-up question. 

glxgears doesn't give a FPS readout. Is there a program that I can use to test the FPS? I installed penguin-racer but hope there is something dedicated to this task.

Thanks.

---

### Post by mcduck on 2006-06-08
the second command makes sure that you also get restricted modules (that are needed for nvidia drivers to work). You might not need to do that, if you already have them installed. (If you install different kernel, install 'linux-686 or linux-K7 metapackage, and you'll also automaticly get restricted modules)

For glxgears, run this :
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```
..and you'll get the fps redings :D

---

### Post by u.b.u.n.t.u on 2006-06-08
Thank you mcduck!

6600+ average :grin: 

(I wasn't benchmarking :-\" )

---


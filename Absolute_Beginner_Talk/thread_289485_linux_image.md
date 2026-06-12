---
title: "linux image"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-10-31
I just installed ubuntu i386 on my AMD64 - I know it's not the right one, but I had problems with the 64 version of ubuntu.  Anyways, I was wondering if I need to install another image.  686 perhaps? smp? I'm new at this sort of thing and I don't really know what I'm doing.  I'm worried I'm going to break my system.  Which reminds me, if I install a different image, am I going to break any of my programs already installed?  Hopefully someone can clear this up for me.  Thanks

Edit:  I just ran "uname -r" and this is the output:

2.6.17-10-generic

Is this the optimal kernel to have on edgy with amd64 3000+?

---

### Post by cotcot on 2006-10-31
You need to pick up the 64 bit image from [http://ubuntu.mirrors.skynet.be/pub/ubuntu.com/releases/edgy/]("http://ubuntu.mirrors.skynet.be/pub/ubuntu.com/releases/edgy/"). I  prefer the Alternate 64 bit.

If you want to keep the i386 than you will have to find free space on your disk to install the 64 bit.

---

### Post by CeeDub on 2006-10-31
Thanks for your help, but how exactly do I do that?  Is it as simple as installing a program?  Will it break any of my programs already installed?

---

### Post by mahy on 2006-10-31
I think cotcot is wrong, i guess what you want to do is to install a new KERNEL image, not download a new cd image. As far as i'm concerned, the 'generic' image is ok for AMD64.

---

### Post by 3rdalbum on 2006-10-31
You might want to look at the k7 image - it's more optimised for your CPU than the generic one is.

```
sudo apt-get install linux-k7
```

---

### Post by rlozano on 2006-10-31
i suggest a safer and better way for you to do it, but quite a long way.

clean install is always the best rather having patches here and there, cuz as you go along, you may not be able to trace the problem.

686 is for celereon processor.

i suggest you download a new image of ubuntu for and64 and do a fresh install. :-k

---


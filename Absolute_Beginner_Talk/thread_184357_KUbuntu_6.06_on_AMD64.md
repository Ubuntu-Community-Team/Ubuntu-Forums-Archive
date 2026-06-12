---
title: "K/Ubuntu 6.06 on AMD64"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by exigentsky on 2006-05-29
Hi everyone,

A friend has recently had quite a few problems with Windows and has taken my suggestion to try Linux (SUSE or K/Ubuntu). He has an AMD Athlon 64 4000+ processor and wants to make the best use of his hardware. Thus, only a 64 bit Linux distribution can be considered.

 I'm leaning towards Ubuntu, but I have never tested the 64 bit version. How is Dapper Drake on an AMD 64? Would it be possible to easily get Flash, 3D, and all the video codecs working? If so, are there any obstacles I should be aware of?

Thanks in advance! :)

---

### Post by chadk on 2006-05-29
I haven't been able to get the K7 or 686 kernel to work very well.  They boot up but the graphics are real slow.  The 386 kernel works fine though.  Strange.

---

### Post by nalmeth on 2006-05-29
I don't know the situation in Dapper, but with Breezy you had to create a 32-bit chroot environment to run the 32-bit apps like flash, that you mentioned.

I did this for a while, and creating the environment was quite easy (follow howto), but ended up just going with the 386 kernel, and then installing the 686 kernel for my hyperthreading. Have done the same for dapper.

My performance is quite good.

---

### Post by exigentsky on 2006-05-31
With all this in mind, it sounds like running the 64 bit version isn't too practical at the moment. I suppose I will just recommend that he run the 32 bit version after all. It can't be *that* much slower and I assume that everything will work painlessly.

---


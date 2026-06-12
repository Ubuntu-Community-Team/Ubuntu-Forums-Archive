---
title: "re compiling kernal, amd 64? k7? help !!"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-09-14
Hi,
Im in the process of compiling the new 2.16.6 kernal however I not sure what to pick for my processor type.
Currently I ve installed the 32 bit version of dapper but I ve got an amd turion 64. 
Can I pick amd 64 from the qconf menu? what should I pick?

help please!!!!

many thanks in advance!

---

### Post by Najand on 2006-09-14
Use:
```

uname -r 

```
to find out which one is that.

---

### Post by bplus on 2006-09-14
> 2.6.15-26-386
is what uname -r returns. buthow does this help me?

---

### Post by Najand on 2006-09-14
Then it is a i386 version.... Anyway why  don't you  wait for Ubuntu Official Kernel Update? It comes with patches needed for communiication with other parts of your Dapper.

---

### Post by bplus on 2006-09-14
Ubuntu runs a lot slower than my winxp install, i heard this can speed it up.
oh well its worth a try.....

---

### Post by bplus on 2006-09-14
what would happen if I tried to compile a kernal specifying my processor as amd 64? (as it is a amd turion 64)

---

### Post by Najand on 2006-09-14
Some of your  already  installed packages like Xserver, et cetra might conflict with your Kernel and fail. Do backups before continuing.

---

### Post by Kilz on 2006-09-14
> **bplus said:**
> what would happen if I tried to compile a kernal specifying my processor as amd 64? (as it is a amd turion 64)

It wouldnt work. If you want performance , instead of a kernel compile, Install the operationg system designed for your hardware. The amd64 version. While some people tell you about 32bit "its eaiser" they dont know for sure and dont know the downsides. Installing a 32bit os on 64 bit hardware can cause problems in some cases.

---

### Post by bplus on 2006-09-14
thanks,
just to confirm, it will be ok to pick amd64?

thanks again

---

### Post by Kilz on 2006-09-14
> **bplus said:**
> thanks,
just to confirm, it will be ok to pick amd64?

thanks again

No you cant use a 64bit kernel with a 32bit os. If you want a 64bit kernel install the 64bit os.

---

### Post by Najand on 2006-09-14
Yes, I agree with that. It is better to install UBUNTU for 64-bit computers.

---

### Post by bplus on 2006-09-14
thanks for your help.
think I mite just format my ubuntu install and install 64 bit version!

---


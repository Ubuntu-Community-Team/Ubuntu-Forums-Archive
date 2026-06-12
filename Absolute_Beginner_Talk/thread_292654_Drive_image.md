---
title: "Drive image"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-11-04
Hi,

Could anyone suggest a could app for making a mirror image of your drive? I haven't been able to find one in Package manager so I thought I'd ask the forum for some tips on apps you guys use.

Thanks,

Rudolf

---

### Post by bulldog on 2006-11-04
Maybe is this link of some help,

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by RudolfMDLT on 2006-11-04
Thanks - But I need to create the image to a network drive(Using FTP), any possible way of doing this while I'm still in Ubuntu with all the drives mounted?

---

### Post by bulldog on 2006-11-04
I'm not a user of partimage myself,but I don't think you can make an image with the drive mounted.

But I could be terrible wrong about that though.
Sorry can't help you with that.

---

### Post by CatKiller on 2006-11-04
> **RudolfMDLT said:**
> Thanks - But I need to create the image to a network drive(Using FTP), any possible way of doing this while I'm still in Ubuntu with all the drives mounted?

**dd** would do it, but I wouldn't know how to spit the data aver the network. dd just makes a bit-by-bit copy of a thing and puts that copy on another thing. Very powerful.

---

### Post by RudolfMDLT on 2006-11-04
Thanks! I'll try it!:)

---

### Post by Drakkor on 2006-11-04
Where would one find **dd** ?

---

### Post by CatKiller on 2006-11-04
> **Drakkor said:**
> Where would one find **dd** ?

On the command line of UNIX-like systems.

[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)
[http://www.mcsr.olemiss.edu/cgi-bin/man-cgi?dd](http://www.mcsr.olemiss.edu/cgi-bin/man-cgi?dd)

It's included in the **coreutils** package.

---


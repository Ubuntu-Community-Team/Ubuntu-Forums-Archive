---
title: "is there a substitute to WINE?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-07-18
Hello All, 

   Apparently I cannot install wine into my computer because of issues with AMD64. Is there another substitute for WINE that I can install for my computer? I don't know that much software yet   so all recommendations are always greatly appreciated!!!

Crazydiver

---

### Post by Outrunner on 2007-07-18
Not really There's Crossover which has a 30 day trial and then you have to pay for it and there's Cedega for games(which you also have to pay for). That's all.

And there's really no point in using 64 bit Ubuntu, unless you need to do processor intensive tasks in which case every bit of speed counts... You're much better off using 32 bit. it has better support.

---

### Post by Famicommie on 2007-07-18
[https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

---

### Post by Malibu Illusion on 2007-07-18
> **Outrunner said:**
> And there's really no point in using 64 bit Ubuntu, unless you need to do processor intensive tasks in which case every bit of speed counts... You're much better off using 32 bit. it has better support.

FUD.

Why not have the advantage of running in a 64-bit environment, while also still having access to pure 32-bit applications?  There's no reason not to; you just have to take a few extra steps to set up a chroot or, in many cases, just have a lib32 folder with 32-bit dependencies in.

---

### Post by crazydiver on 2007-07-18
Hello all!

  Thank you for the comments and recommendations...  

Malibu Illusion, I hope you don't mind but how exactly do you do the stuff you just said with chroot?

 Thanks all!!!

---

### Post by Malibu Illusion on 2007-07-18
Check:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
or
[http://danieldandrada.blogspot.com/2006/09/ubuntu-chroot-environments.html](http://danieldandrada.blogspot.com/2006/09/ubuntu-chroot-environments.html)
or....pretty much anything here:
[http://www.google.co.uk/search?hl=en&q=ubuntu+chroot&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=ubuntu+chroot&btnG=Search&meta=)

In relation to the 32bit libs on amd64:
[http://www.google.co.uk/search?hl=en&q=ubuntu+32-bit+libraries+64+bit&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=ubuntu+32-bit+libraries+64+bit&btnG=Search&meta=)

Particular to note: ia-32libs.  Might want to search for that too to work out what to do.

In short, Google is your friend.

Take care.

---

### Post by Outrunner on 2007-07-18
> **Malibu Illusion said:**
> FUD.

Why not have the advantage of running in a 64-bit environment

What advantages? The speed difference is hardly noticeable in day to day tasks so I don't see the point of getting 32bit apps to work for a minor speed increase. 

Whatever floats your boat, I guess...

---

### Post by vbmds on 2007-07-18
I'm running wine on 64bit ubuntu. Installing wine was as easy as following the instructions on the wine site.

---


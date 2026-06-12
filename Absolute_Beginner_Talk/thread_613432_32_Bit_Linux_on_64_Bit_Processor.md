---
title: "32 Bit Linux on 64 Bit Processor"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-14
Are there benefits to running 32bit linux on a 64 bit processor?
will it run faster? What's the difference?

---

### Post by Dr Small on 2007-11-14
64bit will run faster, although I have never used it myself, but I hear that it may be a little bit more difficult to get flash or whatnot. You'd have to ask some 64bit users here.

Dr Small

---

### Post by Hospadar on 2007-11-14
For the average user, you really arn't going to notice a whole lot of difference.  A 64 bit machine has bigger registers and wider busses that allow for speedier and/or more accurate calculations on the same amount of clock time.

From a user perspective though, probably the biggest thing that you'll notice is that a lot of software, especially proprietary stuff like hardware drivers, doesn't run as well/at all on 64 bit.

So if you are just going to use your machine for normal stuff, or even relatively advanced stuff and you just want it to work well, I'd go with 32 bit.

If you are planning on doing some super-intensive computing work, or have custom software you want to run on a 64 bit machine for the added power, then use the 64 bit.

---

### Post by mistergq on 2007-11-14
I tried out 64 bit Fiesty earlier this year, and within a day or 2, went back to 32 bit.  Someday, it will be faster, but the support is not there yet.

---

### Post by jordank on 2007-11-14
Lets say i'm bruteforcing keys through basic c programs? I would assume, since this is a very lengthy process, i would assume 64 bit would be better, yeah?

---

### Post by rfruth on 2007-11-14
64 bit is no doubt faster but its a 32 bit world ...

---

### Post by Inxsible on 2007-11-14
> **rfruth said:**
> 64 bit is no doubt faster but its a 32 bit world ...
as it was once a 16 bit world :)

---

### Post by jordank on 2007-11-15
Hrmm, it seems kind of silly for me to revert to 32 bit. I feel as if my processor is more utilized by having the 64 bit version.  Regardless of the fact that most applications are running in 32 bit, i'm sure time will take it's toll and 64 bit is soon to come.

---

### Post by misfitpierce on 2007-11-15
64 bit OS runs faster on 64 bit cpu. 32 bit will just run on 64 bit cpu and few programs are avail more for 32 bit. Although you can make 32 bit programs run on 64 bit ubuntu but it does take some special installing. Flash and such for 64 bit is now very easy as a side note.

---

### Post by Inxsible on 2007-11-15
> **misfitpierce said:**
> 64 bit OS runs faster on 64 bit cpu. 32 bit will just run on 64 bit cpu and few programs are avail more for 32 bit. Although you can make 32 bit programs run on 64 bit ubuntu but it does take some special installing. Flash and such for 64 bit is now very easy as a side note.True. Installing flash is just as easy as in 32 bit.

---

### Post by jordank on 2007-11-15
If i wanted to install flash without any special installation, would i have to wait for Ubuntu to patch to cover that install, or is that something that flash has to release - compatability with 64bit ubuntu?
Which end is responsible for working with 64bit ubuntu? Is it ubuntu or the program?
Sorry if that was clouded.

---

### Post by Inxsible on 2007-11-15
> **jordank said:**
> If i wanted to install flash without any special installation, would i have to wait for Ubuntu to patch to cover that install, or is that something that flash has to release - compatability with 64bit ubuntu?
Which end is responsible for working with 64bit ubuntu? Is it ubuntu or the program?
Sorry if that was clouded.If you mean flash (adobe flash) will be installed by default, don't hold your breath on it.

Adobe is proprietary software and Ubuntu has a policy not to include any proprietary software by default. so you will have to run atleast one command to install it. its easy as```
sudo aptitude install flashplugin-nonfree
```of course your universe and multiverse repos need to be enabled.

The program should be 64 bit compatible. Even 32 bit Windows apps may or may not work in 64 bit Windows

---


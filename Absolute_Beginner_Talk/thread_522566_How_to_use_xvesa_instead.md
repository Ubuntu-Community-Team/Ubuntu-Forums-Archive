---
title: "How to use xvesa instead?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-08-10
Okay, on an old laptop running Ubuntu 6.06 LTS, it was only able to install in safe graphics mode. So the resolution is all low and it looks odd whenever it starts.

I  have heard (somewhere) that using Xvesa instead of Xorg is better for older laptops?

Is it possible to change to use xvesa instead?  

And if so, how?

Cheers for any  help you can give.

---

### Post by overdrank on 2007-08-10
> **Neon_Knight said:**
> Okay, on an old laptop running Ubuntu 6.06 LTS, it was only able to install in safe graphics mode. So the resolution is all low and it looks odd whenever it starts.

I  have heard (somewhere) that using Xvesa instead of Xorg is better for older laptops?

Is it possible to change to use xvesa instead?  

And if so, how?

Cheers for any  help you can give.

Hi I think you are a little confused on the terms. First if you can give us some info on your system by posting the output of the command in terminal 
```
lspci
```
Then terminal is located under application,accessories, terminal. This will tell us your graphics card. The vesa you are describing is a driver used for older or not supported graphic cards.

---

### Post by Neon_Knight on 2007-08-10
> **overdrank said:**
> Hi I think you are a little confused on the terms

Yeah, I thought I might have been.  I just read somewhere (ages ago) about using old laptops to use xvesa instead of xorg.  That's my extent on the knowledge of it.   


(I will post the output of that command tomorrow - currently updating)

---

### Post by kerry_s on 2007-08-10
post all your specs.

if your computer is old and slow you should be running xubuntu or better yet a custom install.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by W6LQR on 2008-07-09
So, the computer I'm using is too old for UBUNTU! It runs Windows 98 just fine and the Linux folks are always saying it's less demanding of resources than Windows. 

Give me Xvesa which works fine with Puppy Linux and Damn Small Linux as well as an old version of RedHat Linux.

Jerry

---

### Post by ithcy on 2008-07-10
Linux IS (in general) less demanding of resources than Windows. Ubuntu, however, is NOT less demanding of resources than Windows 98. Ubuntu and Win98 are separated by many generations of Moore's Law.

You might want to try Debian. Ubuntu, as you probably know, is based on Debian, but Debian gives you a lot more options at install-time than Ubuntu. You can easily install Debian such that it will run very well on old hardware, and will be a lot friendlier (especially for an Ubuntu user) than Puppy or Damn Small Linux.

---


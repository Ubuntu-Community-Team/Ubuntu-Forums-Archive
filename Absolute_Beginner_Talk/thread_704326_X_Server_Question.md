---
title: "X Server Question"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by lledurt on 2008-02-22
I am new to Ubuntu(1 year) but I have been trying to get under the hood.  I have been experimenting with Xwindows ability to display remotely. I am not an expert, but I have read the book X Power tools, so don't think because I my know a command or two that I have any idea what I am doing.

if I enable hosts my laptop computer with (I do realize the security risk)

laptop:~$ xhost +

and then run xclock on my desktop

desktop:~$ xclock -display laptop:0

I get the clock on my laptop.  Cool.  

My question is why does it not work the other way around?

My desktop is running xinerama (it does not work on my twinview one either).  I have tried desktop:0.0 also.  Both desktops have an nvidia driver.

xdpyinfo shows 

name of display:     :0.0 on both of the desktops and the laptop.

Any ideas or direction?

Thanks 
P.J.

---


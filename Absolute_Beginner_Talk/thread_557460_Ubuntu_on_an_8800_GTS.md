---
title: "Ubuntu on an 8800 GTS?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by sekelly on 2007-09-22
Hi all,

Recently I acquired an 8800 gts 320 Mb. I want to run Ubuntu as my primary desktop environment, with a secondary windows XP partition that allows me to play games that I am unable to get working in Linux.

I'm not completely new to Linux, but I would still consider myself a beginner. I tried installing a week or so ago but was unable to reboot after using the nvidia drivers and decided to reformat (at the time I was under the impression the 8800 gts wasn't supported). 

Recently I was perusing the nvidia site to get my windows xp drivers and stumbled across the linux drivers for this card. I was just wondering if anyone has installed this kind of set up and how it worked for them? 

I don't want to go through the partitioning and install process if it is simply not going to work.

Thanks in advance for any help.

---

### Post by skymera on 2007-09-22
where dd you get the driver from?

and the GTS is supported.

i have the 640 :)

---

### Post by conehead77 on 2007-09-22
look here:
[http://www.ubuntuhcl.org/pub/reviews.php?product_id=312]("http://www.ubuntuhcl.org/pub/reviews.php?product_id=312")

---

### Post by sekelly on 2007-09-22
Oh, I was under the impression they weren't.

I'll take a look at that link.

Thanks for the responses.

---

### Post by CaptainInsaneO on 2007-09-22
I used to have that exact card before I upgraded to the 8800gtx with 768mem. I guarantee that card works great in Ubuntu, all you need to do is a full system/kernel update and then run a program called Envy. It will auto-install the latest video drivers from nVidia for you, no muss and no fuss.

Here's a link for you: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sekelly on 2007-09-22
Thanks, I'll try that method.

---

### Post by C.S.Cameron on 2007-09-23
Tried Envy yesterday to see if it would load the new drivers, (100.14.19), but it is still loading the old ones.

---

### Post by Pumalite on 2007-09-23
ENVY has been a shot in the dark for me. I prefer to go to: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html), and install them the hard way. You always know what you'll get.

---

### Post by Uber Nooblett on 2007-09-23
I have the 640mb version of the same card, no issues at all :) just need to download newest drivers from NVIDIA, go into console login at startup, type 
```
telinit 3
```
if it goes to the log in prompt again, just exit back to text, log in as super user, get to the directory where you downloaded to and type 
```
sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
```
follow instructions and jobs a good un :)

---


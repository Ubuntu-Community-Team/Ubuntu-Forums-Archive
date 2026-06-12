---
title: "Screen Configuration lost with Updates"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Milliways on 2008-01-04
On a quiet afternoon I loaded a lot of Updates I had been avoiding and YET AGAIN Ubuntu lost my video setup and started in low graphics mode.

I am getting to be a dab hand at running "sudo dpkg-reconfigure xserver-xorg", but it still takes me several goes to get it right.

Even though it seems to find the correct modes for my Monitor (a new Samsung 740B) when I restart it doesn't have the native 1280*1024 and I have to manually select the monitor.

Is there any way to prevent his happening.
Should I backup xorg.conf ?

---

### Post by kpkeerthi on 2008-01-04
What graphics card do you have? And how did install your driver? 
I suggest you follow the steps detailed [here]("https://help.ubuntu.com/community/Video") and install your driver along with proper dependencies to prevent this from happening in future.

---

### Post by Milliways on 2008-01-04
> **kpkeerthi said:**
> What graphics card do you have? And how did install your driver? 
I suggest you follow the steps detailed [here]("https://help.ubuntu.com/community/Video") and install your driver along with proper dependencies to prevent this from happening in future.
I am using a Nvidia RIVA TNT2 Model 64 and the nv driver.
I was using the driver installed with Restricted Device Manager, but not at the time of my other problems.

Originally I did nothing special - just installed Ubuntu 7.04 using an old CRT.
I upgraded to 7.10 but guess my first problems started when I installed a Belkin KVM Switch to enable me to share a monitor with another computer.

Thanks for the links - these look very useful, and I will work through these hints.

---


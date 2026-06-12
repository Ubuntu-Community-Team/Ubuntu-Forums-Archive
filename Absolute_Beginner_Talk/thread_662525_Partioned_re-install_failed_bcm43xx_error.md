---
title: "Partioned re-install failed: bcm43xx error"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by BC_Potter on 2008-01-09
Hi;

I just partitioned my HP vista machine and installed Gutsy for the first time. The is my first time using Linux, so please be gentle.

Anyways, I've been trying to get my broadcom wireless card working, but it just hasn't happened. I've tried both the ndiswrapper approach and fwcutter approach and both seem to fail(I've tried *many* different walkthru's). Each time I follow the recommendations, i don't get any sort of wireless support. 

I suspect that at this point, I have munged the whole thing for good.( I suspect iit might be a IRQ issue, since they wireless card and graphics card IRQ addresses don't match those in vista.... for another post)

Luckily, getting the wireless and video to work(I got the video card working using ENVY) was the only setup I did in Gutsy, so I would like to re-install the whole thing from scratch. (while keeping my vista partition).

This [post=504602][color=blue]post[/color][/post] recommends that re-installing ubuntu is uber-easy, but I'm having a serious problem. When I pop in the CD, I go to 'install' and a bunch of scripts start racing past. But eventually, the system gets hung up on

*'bcm43xx:Error: microcode "bcm43xx_microcode5.fw" not available or load fail*.

 From this point, nothing seems to happen, where I've either received the terminal interface, or that error messages repeats with about a 20 second delay. I suspect this is happening because of some of the walkthrough's I have gone through. (I have deleted and blacklisted the bcm43xx driver, as per previous instructions I can no longer find)

So, I think that ugliest solution would be to re-format my Linux partition from vista and start from scratch. Any recommendations?

---

### Post by mikeyphi on 2008-01-09
> **BC_Potter said:**
> 
So, I think that ugliest solution would be to re-format my Linux partition from vista and start from scratch. Any recommendations?

That sounds like the best option! - Just delete the Linux partition and then run your LiveCD again.
No need to reformat or change the size of any partitions. When you get to the partition stage of the Ubuntu install process - choose to use the free space.

---


---
title: "Resolution stuck at 800 x 600"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tumler on 2007-05-15
Hey,
everytime I install kubuntu theres a little drama about getting the right resolution for my monitor (1024 x 768 | Intel i810), but after a little tweaking it works.

After upgrading to Fiesty 7.04 I've been having trouble for about 3 hours :/

I followed the advice on [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and the 915resolution program causes errors, and then followed the user comment at the bottom of the page and that didn't work either... 

I tried quite a few different things and still no luck... I've got no idea


Please could someone help.. Or if anyone has any advice please post.

Thanks

---

### Post by bmk789 on 2007-05-15
Have you tried editing /etc/X11/xorg.conf or running

sudo dpkg-reconfigure xserver-xorg

---

### Post by prince_alfie on 2007-05-15
Thanks guys for this bit of code! IN fact, it worked perfectly on my alienware :D:popcorn:

---

### Post by tumler on 2007-05-16
Yes I have tried both editing my xorg.conf file and reconfiguring the xserver...

I am quite lost.

EDIT-----

Good news it works.
I tried the same thing I did last night except when I reconfigured the xserver I put the resolution choice as 1280 x (i forgot :) ) and 1024 x 768  AND when it gives you the option between "Simple  /   Medium  / Advance"  I picked medium and put in 1024 x 768 @ 60hz as the preferred setting...  Edited the xorg.conf to change driver from "i810" to "intel".... and installed xserver-xorg-video-intel (universe)

Which I had done all last night except the only change was I added that higher resolution... So when my comp started I just changed it down to 1024 x 768


Hope this helps others :D

---


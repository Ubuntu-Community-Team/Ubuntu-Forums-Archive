---
title: "Ubuntu 7.10 install hangs"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by pjp on 2007-10-19
I am loading Ubuntu 7.10 on an Acer TravelMate 230 lap top.
This is my first attempt at loading Ubuntu.
It starts just fine and then it gets to where it does the check for the battery etc and it stops at the following point

* Running local boo

I have tried Video drivers from Intel as the card is a 845gl card, I saw that the video card can be a problem on a post.  It seem no matter what I do this is where it grinds to a halt. 

I need some help.  Could someone please give me some ideas.  Thanks.

---

### Post by p_quarles on 2007-10-19
I've heard that there's a known bug with battery detection on some laptops with 7.10. Have you tried installing it while it's on AC? 

Apart from that, it's possible you have a bad installation disk. Did you run the MD5 checksum? Did you burn the disk at a slow (<= 4x) rate?

---

### Post by pjp on 2007-10-19
Yes I have tried it on ac and yes the disk is verified.

---

### Post by p_quarles on 2007-10-19
You might give the alternate installation disk a try. In my experience, that can override some problems that are relatively easy to fix once you've got the OS installed. 

One other possibility: is the laptop connected to the network during the installation? I've had installations over wireless go bad because it thought it could access the network, but it wasn't working. My solution in that case was to hook it up via Ethernet. If your wireless card works in the live CD, you may just need to turn off your router's encryption during the install.

---

### Post by Arthur Archnix on 2007-10-19
Are you using the live cd to install? A lot of install problems can be managed by simply using the alternate cd and installing in text mode.

---

### Post by pjp on 2007-10-20
I have not tried it with the network cable plugged in.  Think of it now windows 2000 server had that problem.  If it had a network card it needed to be plugged into a hub or switch.  I will try it and let you know how it has gone.

---

### Post by pjp on 2007-10-20
I have now tried it with the network plugged in.  Same problem.  I am downloading the alternate cd now.  Does this mean that if I install it from this cd I will not get the gui screen?  How do I ensure that when I install it from the alternate cd I get all of the nice graphics screen?

---

### Post by Perfect Storm on 2007-10-20
It's a text installer, but not difficult to use.

---

### Post by Tyke91 on 2007-10-20
just because you use the alternate install disk doesnt mean you don't get the shiney graphics. you ubuntu should be just like everyone else's after you do the install.

---

### Post by pjp on 2007-10-20
OK Thanks.  I am just downloading the alternate CD,  hopefully that will work.  I have also tried installing with the original without a ntfs partition on the hdd but the problem has not changed.  Once I try the alternate cd I will let you know if it worked.  I have my fingers crossed!

---

### Post by Perfect Storm on 2007-10-20
I have made a new sticky in the beginners forum you might to check for some advice :)
[http://ubuntuforums.org/showthread.php?p=3579069#post3579069](http://ubuntuforums.org/showthread.php?p=3579069#post3579069)

---

### Post by The_Wizzy on 2007-10-24
I have just finished an install when it originally hung!

I did not want to download yet another 700MB file(we have poor broadband in Australia) so i looked around for other ways to fix the problem. When i looked at the processes list there were quite a few that were not necessary/using up a lot of system resources. 

After killing these processes(sorry i didnt write them down) The install went without a hitch. It slowed in some sections(resizing NTFS partition) but this i believe is to be expected. 

With a bit of patience you can complete the install with your normal disk.

Josh

---


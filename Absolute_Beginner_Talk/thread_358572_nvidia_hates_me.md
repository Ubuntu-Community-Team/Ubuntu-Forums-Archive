---
title: "nvidia hates me"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by hfw on 2007-02-11
I am very new to Ubuntu, and trying to get everything working.  I did the Edgy Kernel Updates, and then downloaded the Nvidia-glx.  When I try to 

$sudo nvidia-glx-config enable

I get:
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

Which I can't figure out b/c the version info in Synaptic is identical.

Any help would be appreciated.

-hfw

---

### Post by Maestro23 on 2007-02-11
Remember seeing many posts from Nvidia users in the long post on the kernel update and Nvidia.  Should be a solution in there.

[http://ubuntuforums.org/showthread.php?t=356408&page=36](http://ubuntuforums.org/showthread.php?t=356408&page=36)

---

### Post by Titus A Duxass on 2007-02-11
Simple solution is to use Automatix2 to install the nvidia drivers.

---

### Post by Balder on 2007-02-11
> **hfw said:**
> sudo nvidia-glx-config enable

I get:
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

Any help would be appreciated.

My experience is that &#8221;sudo nvidia-glx-config enable&#8221; never works.

Try this instead: 

Install the Nvidia driver via Synaptic

Then &#8211; in a terminal &#8211; type: sudo dpkg-reconfigure  -phigh xserver-xorg

(Notice space between reconfigure -phigh)

Press Enter

Pick the Nvidia driver

Press Enter

Choose the right resolution for the monitor (800x600 or whatever you prefer)

Press Enter, close the terminal and reboot.

It worked for me...  :)

---

### Post by r4ik on 2007-02-11
Try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by hfw on 2007-02-11
Thanks for all of the replies.  After reading through about 30 pages of the thread in the first reply I found a link to Envy.  That did the trick.  Nvidia likes me. Beryl likes me. 

It's great to get such quick responses to a question.  
hal

---

### Post by r4ik on 2007-02-11
The link is right above you're last post maybe i should include it's "Envy" :)

---

### Post by hfw on 2007-02-11
Too bad I didn't get your reply with the link to Envy before I read thirty pages in that other thread!

oh well.   I learned a good bit reading through that much.  Including, if one person posts a problem, ten post "me too!"
:lolflag:

---

### Post by mrbungle on 2007-02-11
> **r4ik said:**
> Try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this is the one i use and being a newbie worked great and was easy as pie :KS

---

### Post by Repent on 2007-02-11
Save yourself some time and go here  [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) and just follow their instructions it's fast and easy. It's what I used after the update, when all the other ideas didn't work. 

Looks like you may have fix your drivers save this link it really is easier  than the others I have the page book marked.
:roll:

---


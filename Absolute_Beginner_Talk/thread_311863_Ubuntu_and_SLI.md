---
title: "Ubuntu and SLI?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-12-03
I'm long overdue for a serious hardware upgrade so I'm gonna get myself something sweet for christmas.  Any issues with Nvidia SLI and Ubuntu? 

I'm thinking even if ubuntu isn't optimized for sli it won't matter, nothing I do in linux is that demanding.  Anything you could share with me would be great!

---

### Post by testbenchdude on 2006-12-04
> **BlueStreak said:**
> I'm long overdue for a serious hardware upgrade so I'm gonna get myself something sweet for christmas.  Any issues with Nvidia SLI and Ubuntu? 

I'm thinking even if ubuntu isn't optimized for sli it won't matter, nothing I do in linux is that demanding.  Anything you could share with me would be great!

First off, if you're not planning on doing anything "demanding" graphically speaking, I have to ask why you'd want an SLI setup? If I were you, I'd get a 512mb 7950GT and use the money you would have spent on a second card for a better processor or something...

I have an SLI setup because I still do a lot of gaming on my Windows partition. I installed the NVidia drivers in Ubuntu through Automatix2, and it performs flawlessly. I have yet to actually install any linux games, but so far so good. The only thing I don't like is that the NVidia Settings program (installed automatically under Applications > System Tools) doesn't appear to see both cards and only gives me temps for one... But when I type this into a terminal **lspci -n | grep 0300** shows two cards. Oh well. :) Oh yeah--I've got 2 7900GTs. 

Cheers!

---

### Post by rdsii64 on 2007-09-26
> **testbenchdude said:**
> First off, if you're not planning on doing anything "demanding" graphically speaking, I have to ask why you'd want an SLI setup? If I were you, I'd get a 512mb 7950GT and use the money you would have spent on a second card for a better processor or something...

I have an SLI setup because I still do a lot of gaming on my Windows partition. I installed the NVidia drivers in Ubuntu through Automatix2, and it performs flawlessly. I have yet to actually install any linux games, but so far so good. The only thing I don't like is that the NVidia Settings program (installed automatically under Applications > System Tools) doesn't appear to see both cards and only gives me temps for one... But when I type this into a terminal **lspci -n | grep 0300** shows two cards. Oh well. :) Oh yeah--I've got 2 7900GTs. 

Cheers!
I have a sli board but I don't entend to do any game on my Linux box. what I would like to do is use twin view to run up to 4 monitors on my Linux box.

how much of a pain is this going to be.

---

### Post by overdrank on 2007-09-26
> **rdsii64 said:**
> I have a sli board but I don't entend to do any game on my Linux box. what I would like to do is use twin view to run up to 4 monitors on my Linux box.

how much of a pain is this going to be.

Hi maybe have a look here
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by rdsii64 on 2007-09-26
> **overdrank said:**
> Hi maybe have a look here
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
thanks I bookmarked that thread so I can refere back to it.

---

### Post by overdrank on 2007-09-26
> **rdsii64 said:**
> thanks I bookmarked that thread so I can refere back to it.

Hi I have a question? Why to you keep responding to the old threads? :confused:

---

### Post by anewguy on 2007-09-26
> **overdrank said:**
> Hi I have a question? Why to you keep responding to the old threads? :confused:

Hi!  Been wondering the same thing about quite a few users, and I think I know why.  When we are new and come into the forums, we are told to research, research and research - the forums, online documentation, etc..  My suspicion is that some people are actually taking that to heart (maybe they read a few of the not-so-nice replies posted on some threads) and are REALLY going through the stuff on the forum.  So, they find something, and decided "I'm supposed to post here because otherwise I might get bitched at for posting a new thread".  Just my suspicion!:)

---

### Post by PsycoGeek on 2007-09-28
Some new info regarding SLI performance on Linux:

[NVIDIA SLI:Linux vs Windows]("http://www.phoronix.com/scan.php?page=article&item=860&num=1")

---


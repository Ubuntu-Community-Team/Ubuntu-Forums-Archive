---
title: "Buying a MacBook Pro"
date: 2009-08-16
forum: Apple Hardware Users
---

### Post by abdo88 on 2009-08-16
Hi all,

As my laptop is getting pretty old, I am considering buying a MacBook Pro. I have few questions:

1- I am considering buying a setup with an SSD. First, if anyone tried it, is it worth it? Can it cause problems with Ubuntu (forgive my noobness =))?

2- apple.com claims that the battery life is 7 hours, can anyone confirm this? Is that true even on Ubuntu or only on Mac?

3- I am thinking about either 2,53 or 2,88 processor? Will the difference be felt? Any first hand experiences?

4- On the hardware compatibility page, I find several versions of MacBook Pro.. if I buy one from apple store now, will it be 5,5?

I am sorry if my questions were already asked somewhere else.. I tried to search but those were the questions that I did not manage to find a satisfactory answer for..

Thanks.

---

### Post by amd-64 on 2009-08-16
> **abdo88 said:**
> 
Hi all,

As my laptop is getting pretty old, I am considering buying a MacBook Pro. I have few questions:

1- I am considering buying a setup with an SSD. First, if anyone tried it, is it worth it? Can it cause problems with Ubuntu (forgive my noobness =))?



Got a 15" last week and just about completed setting it up, it is a 5,3. The main problems so far: sound (needs workaround), heat (specially if you get the discrete graphics 9600) and I have not tried the 9400 because I don't think EFI is that ready yet. Overall it is still very much worth it, the quality is certainly there.  

> 
2- apple.com claims that the battery life is 7 hours, can anyone confirm this? Is that true even on Ubuntu or only on Mac?


I can confirm the 7 hr for Mac only, quite amazing. The best I saw for ubuntu was 3 hrs. I assume if you get the base model with only the 9400 graphics you may do better because the discrete GPU does get hot. I have not seen any one reporting the 7 hr in Ubuntu.

> 
3- I am thinking about either 2,53 or 2,88 processor? Will the difference be felt? Any first hand experiences?


I have the 2.66 GHz, but it is running at 1.6GHz most of the time. I would say it is not that important. The big difference is going to be between the P processors (very low power) and the T processors (mobile but not very low power). I don't know if you would get 7 hr in Mac if you have the 2.88 GHz because i think it is a T. I had to dig for this information because Apple does not really tell you on the spec sheets. I also wanted the larger drive and the discrete graphics so I got a P8800. Gentoo forums keep a good track of specs. 

> 
4- On the hardware compatibility page, I find several versions of MacBook Pro.. if I buy one from apple store now, will it be 5,5?


The 13" is 5,5 and the 15" is 5,3. It is possible the 17" is a 5,4

> 
I am sorry if my questions were already asked somewhere else.. I tried to search but those were the questions that I did not manage to find a satisfactory answer for..

Thanks.


No problem. Good luck with your decision.

---

### Post by AlanR8 on 2009-08-16
Just bought a 13 inch Pro for my son who's about to go off to Uni! My comment would be that I would just leave it alone. The Mac is a great OS, end to end user friendly.

Wouldn't suit me at all, I just LOVE tinkering and getting my hands dirty! That's why I love Linux.....keeps me busy for hours.

---

### Post by abdo88 on 2009-08-16
Thanks for your reply.

I have a few questions remaining though:

1- I still want to know how good is the SSD (solid-state drive).
2- There is no page for 5,3  here: [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages?](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages?)
3- For the sound problem, does a solution exist?

Thanks! :)

---

### Post by amd-64 on 2009-08-16
Abdo88: 

I don't know about the SSD. I have a 320GB SATA drive. 

All of the 5,5 (and even 5,1) instructions apply to 5,3. The main point is to get the latest drivers for everything.

The solution for sound is to update ALSA drivers as per [http://http://ubuntuforums.org/showthread.php?t=1188849]("http://http://ubuntuforums.org/showthread.php?t=1188849")

Also, suspend and hibernate work fine. Shutdown works but not restart. "sudo init 6" ends in blank screen.

By the way, although the webcam works, I still cannot get skype to work under linux. No issues with Mac.

---

### Post by jrusso2 on 2009-08-16
I have the 13 inch Macbook pro.  It dual boots with Vista and runs Linux in a virtual box.

The main problem is heat.  Runs from 122 to 165 degree cpu temp.

I would stay away from SSD for now until the technology has stabilized.

As far as battery life under normal use its like 3 hours, to get 7 you must have to darken the screen and turn off wireless and blue tooth and not run videos.  I have never seen close to that much battery life.

---

### Post by amd-64 on 2009-08-16
I have been looking into smcfancontrol for the heat problem. I think it works well. 
Get it from here [http://ubuntuforums.org/showpost.php?p=6933921]("http://ubuntuforums.org/showpost.php?p=6933921")

---

### Post by abdo88 on 2009-08-17
Thank you very much. Your answers have been a great help :).

---


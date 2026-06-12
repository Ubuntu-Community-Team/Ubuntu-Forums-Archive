---
title: "Quad Core &amp; Linux"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-11-14
Anybody using a quad core processor with linux? Any thoughts, suggestions or actual testimony, please reply. My next computer I want to be a quad and want to make sure of compatibility, thanks.

---

### Post by skymera on 2007-11-14
it should be compatible way past 8 cores.
up to 16 i think.

but 4 cores no problem.

---

### Post by prodigalson666 on 2007-11-14
Awesome, thanks for the info!

---

### Post by njparton on 2007-11-14
Yep, runs on the Q6600 in one of my PC's no probs at all :)

---

### Post by prodigalson666 on 2007-11-14
Sounds good, how much ram can linux support for dual and quad core right now?

---

### Post by Keith_Beef on 2007-11-14
OK for me...

Quad core, all drives SATA, no probs.

Beef.

---

### Post by inversekinetix on 2007-11-14
it worked out of the box on my system,  i would suggest however, that unless you have any 64bit applications you MUST run, stick to the 32bit version of Ubuntu.

---

### Post by jordank on 2007-11-14
16-core?
Thats absolutely insane.
what would that even be used for?

---

### Post by Chayak on 2007-11-14
> **jordank said:**
> 16-core?
Thats absolutely insane.
what would that even be used for?

Well engineering, high end video processing, 3d rendering, and anything that takes a lot of processor time and will take advantage of multiple processors.  It's generally things at a level that the average home user doesn't do.

---

### Post by saru411 on 2007-11-15
> **inversekinetix said:**
> it worked out of the box on my system,  i would suggest however, that unless you have any 64bit applications you MUST run, stick to the 32bit version of Ubuntu.

Why would you cripple your multi core processor by running only 32 bit? Stop spreading FUD! I started on 64 bit and i had very few issues as a linux n00bie. Since Dapper Drake(6.10) , Ubuntu has run everything just fine. The only issue you should run into is Java applets for your browser. I would recommend using Kilz script to install a 32 bit version of firefox, my personal preference is Ice Weasel.([http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)) If you have other issues stop by 64 bit support. We are a helpful bunch.

---

### Post by bithkits on 2007-11-15
> **saru411 said:**
> Why would you cripple your multi core processor by running only 32 bit? Stop spreading FUD! I started on 64 bit and i had very few issues as a linux n00bie. Since Dapper Drake(6.10) , Ubuntu has run everything just fine. The only issue you should run into is Java applets for your browser. I would recommend using Kilz script to install a 32 bit version of firefox, my personal preference is Ice Weasel.([http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)) If you have other issues stop by 64 bit support. We are a helpful bunch.

First you say telling people to install the 32bit version is "fud", after which you recommend installing the 32bit version of firefox? Why? In your own words that would be crippling the processor...

Then you go on to say that the processor is crippled by 32 bit? Have you ever stopped to think about the fact that the reason you have so little trouble with the 64bit version is that most applications are 32bit and will run in a 32bit environment even when executed in a 64bit environment? The performance gain is negligible. 

There are only two reasons why a user should install 64bit IMO:
1 - to run programs that are encoded specifically for a 64bit environment
2 - to overcome the 4GB 32bit memory barrier (as in, if you are running more than 4gigs)

Although I hear that Linux can access greater amounts than 4gigs even on the 32bit system...

As far as I know (I am not a programmer) JAVA app's are encoded to be impartial to a 32 or 64bit environment. So you will find that they probably have trouble running in 64bit as a result of the non-specific programming style that JAVA has

---

### Post by saru411 on 2007-11-15
I think that if you you have a pc that can run faster you should run it at that speed. The ONLY issue i have is java's lack of 64 bit support. this is not an ubuntu issue, and ubuntu 64 bit runs great. telling someone to run their chip at an inferior speed sounds questionable at best, IMO. There are very large gains in many areas while running 64 bit, some of which are dvd ripping and file  compression/decompression. Maybe you do not use these so much, but I for one do. You might also note that synaptic has less than 1percent difference in program availability in 64bit vs 32 bit. It could be possible that you haven't tried 64 bit since dapper drake, or maybe you just believe all of the FUD going around the forums. I am one of the many that have installed 64bit ubuntu and i help out as often in that forum as possible. You really would not believe how many people come in there spreading FUD just to be an ***. oh, and as for installing a 32 bit browser, it is the ONLY issue i still have on 64bit linux. I would have to say that that is a very small issue to deal with considering all of the other issues people run into. It's true that you most likely will not notice a difference in performance with 64 bit firefox vs 32 firefox, but browsers are not very cpu intensive. So, recommending to install an app that is 32 bit to get the only issue i still find plaguing 64 bit working is not unreasonable. In fact i feel installing in 32 bit and then switching would be 1.) more time consuming, 2.) a waste of a great processor, 3.) less pressure on java to get with the program!

if you dont agree that's fine, but i wouldnt recommend telling someone to run something that wasnt meant for their machine. the age of 64 bit is here. stop being scared

---

### Post by insane_alien on 2007-11-15
seeing as linux is run on a large sellection of supercomputers with hundreds and thousands of cores and more RAM than you can shake a polish sausage at i'm pretty sure it can run on a quad core.

i'm on a quad core, 8GB RAM machine(well, actually i'm at uni now so i'm not but i have one at home) and it works flawlessly with gutsy 64-bit.

---

### Post by Dripbagulhos on 2007-11-15
> **inversekinetix said:**
> it worked out of the box on my system,  i would suggest however, that unless you have any 64bit applications you MUST run, stick to the 32bit version of Ubuntu.

I won't be so conservative about 32 bits... I've been using Ubuntu 64 bits since Feisty. With Gusty I have no problem running everything that I want and I don't have any special need on 64 bit software.

---

### Post by ukripper on 2007-11-15
64-bit doesn't lack any support at all, it is mere misconception created during early days of ubuntu. Major apps and drivers are supported with 64bit too. Howevr,there are always work around!

---

### Post by inversekinetix on 2007-11-15
> **bithkits said:**
> First you say telling people to install the 32bit version is "fud", after which you recommend installing the 32bit version of firefox? Why? In your own words that would be crippling the processor...

Then you go on to say that the processor is crippled by 32 bit? Have you ever stopped to think about the fact that the reason you have so little trouble with the 64bit version is that most applications are 32bit and will run in a 32bit environment even when executed in a 64bit environment? The performance gain is negligible. 

There are only two reasons why a user should install 64bit IMO:
1 - to run programs that are encoded specifically for a 64bit environment
2 - to overcome the 4GB 32bit memory barrier (as in, if you are running more than 4gigs)

Although I hear that Linux can access greater amounts than 4gigs even on the 32bit system...

As far as I know (I am not a programmer) JAVA app's are encoded to be impartial to a 32 or 64bit environment. So you will find that they probably have trouble running in 64bit as a result of the non-specific programming style that JAVA has

Thanks for saying that.  I am only 3 weeks into using linux and spend lots of time trawling the forums and hanging out on irc trying to learn as much as I can.  I have seen lots of people complaining about problems with 64bit systems and OS, i just passed on what I had heard.  I thought that was a good thing.

---

### Post by JurB on 2007-12-07
Is a Quad core cpu always 64-bit?

---

### Post by gn2 on 2007-12-07
> **JurB said:**
> Is a Quad core cpu always 64-bit?

Mainstream retail Quad Core CPU's can all run a 32-bit or 64-bit operating system, it's just a matter of personal preference which is used.

---


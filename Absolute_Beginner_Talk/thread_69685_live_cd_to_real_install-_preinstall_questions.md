---
title: "live cd to real install- preinstall questions"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by netwench on 2005-09-27
hi all,

i'm so impressed with the quality of answers and the amount of patience on this forum that i'm embarrassed to ask this question.

put me in the "advanced windows/beginner's linux" category please. used debian for work 10 years ago at isp's but now I barely remember how to list a directory. so please be gentle... :)

i've tried installing different flavors of linux over the years, but some hardware issue (and lack of friendly support teams like yourselves) has always prevented me from finishing the install. I work on broken windows machines all week long- i can learn, but am tired by the weekend of working on machines. 

So I pop in the live cd and it just RUNS! ok, I know it's off the cd, but here's my question. That thing detected my internet connect (cable modem thru belkin wireless router- machine was wired though) easier than any windows machine- i didn't touch a thing. I was hoping this was a sign of things to come.

I guess what I want to know is, is there anything I can use (device manager?) off the live cd to see if everything will be detected easily? I looked and there are many "unknowns" listed but I don't know if that's just because it's just off the cd. 

I'm thinking of trying to put this on my boyfriend's dell 8300 machine (p4 3.0, 512 ram, standard config from dell) in dual boot (grub on floppy) and i guess i'm trying to head off any roadblocks ahead of time so i'm trying to do my research ...
thank you for any advice you can give! I would really love someday to be able to have him surf the web with the gui and me pop my mail off and read it in good ol' fashioned pine...

-netwench

p.s. and yes, the line about my boyfriend means i'm a chick getting her boyfriend to use linux. when asked about what he thought about his computer (while running the live cd) he said "what's the big deal? so the pictures are different- i still can get to all my web sites.. it works doesn't it."  i'm a geek but he's a normal human being -you guys have done a stupendous job.

---

### Post by mlomker on 2005-09-27
> I guess what I want to know is, is there anything I can use (device manager?) off the live cd to see if everything will be detected easily? I looked and there are many "unknowns" listed but I don't know if that's just because it's just off the cd. 


Not really.  There are tools like **lsmod** to list drivers that are loaded and **lspci**, **lsusb**, and others to list what hardware is seen...but that doesn't mean that they work.  The liveCD is intended for you to install and try things out (sound, networking, etc) prior to install.

Other versions of linux do a bang-up job of running from CD because that's all they were designed to do.  Download a copy of Knoppix if you'd like a good test.  Just because Knoppix works doesn't meant that Ubuntu will out of the box...it usually just means that it is *possible* to make the hardware work with linux.

---

### Post by netwench on 2005-09-28
well, thanks for your advice. i went ahead and installed it last nite on his 120 gig sata drive- it was flawless!! i didn't have to touch a thing and i never had to configure anything for internet- it was all found perfectly. that was eaiser than any easy windows installation any day!!!

thanks!!

-netwench

---


---
title: "Another partition thread"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by toontastic on 2006-08-08
Hi first time poster and newbie to Linuz and Ubuntu so be really nice and gentle please [-o<  

Right I've read through a load of partition threads, followed links to hundreds of different websites and looked through there instructions but I'm still very confused or stupid one of the two.

So far I have downloaded Ubuntu and made a Live Disk of it, put it on an old computer I had and loved it. The problem is it's just far to slow on that computer, the machine only has just over 256mb memory (it has a very strange amount can't remember off the top of my head) and something like a 600Mhz processor, so I guess it's no suprise it's a bit slow.

Anyway I have a newer machine which I build last year, which has 1gb Ram and a good processor in it. The problem is like I said it was build last year so it's now got plenty of stuff on it.

The hard drive is a single 250gb hard drive which I didn't get round to partitioning off so it's basically just one big massive hard drive with windows and all my stuff on it. I believe off the top of my head (i'm at work so not near computer) that there is about 180gb left. 

My plan was to give Linux about 50gb which I'm sure will more than cover it while I try it out and see if I should use it all the time.

As part of using it I will want to use Wine cause it would be nice to be able to play CSS on Linux instead of Windows :) Don't know if that makes a difference as it's already installed on Windows because I'd also like to be able to see my main drive (E:) on both Linux and Windows if possible.

Now some of the info for partitions mentions just moving the slider slightly along and it will work out how much Windows currently takes up, how much Linux needs and do the work itself but I'm a bit worried about this seen as I have a working version of Windows.

So I hope someone will be able to advice me on the best way to partition my drives and exactly how to go about it through installing Linux.

Thanks in advance. :D

---

### Post by orb9220 on 2006-08-08
!) Well the first things that can cause partitioning software to throw fits is fragmentation. So defrag,Defrag,DEFRAG! I had problems with ubuntu chocking on partition that wasn't defragged.

2) You cannot run windows programs from windows with Wine. What this entails is like I downloaded dvdshrink to my home folder then in a term I run wine dvdshrink.exe which is the installer. Wine setups a phony windows folder structure in your home foleder then installs it there. then you add the program to wine with the winecfg command. Not that many games work, Like my fav is the splinter cell series and those are a big NO way Hosay.

3) linux and windows access to partion. Well their is a driver? for linux that will let you read and write to ntfs. Otherwise you can only mount and read ntfs. My setup I have a seprate 120 that is fat32 and my xp partition and ubuntu can both read and write to it.

My setup is 2 drives 1)80G first partition is 12GB xp second partion is ubuntu root that is know as / which is 15GB and third partion is /home for home partion of 48GB and 1GB for linux-swap. My second HD is 112GB fat32 for my pics music video's game installs on xp side.

Hope this helped some.

---

### Post by toontastic on 2006-08-09
Yep that helps alot. I understand now that you cannot run windows programs through Wine so thats ok.

My main problem however is the actual process of partitions. Most things I have read seem to discount the fact I would have anything on Windows. And when they don't they dont seem to explain well enough for me how to partition the actual drive to have Linux, everything I've got on Windows and the shared drive. This is what I really would like to know. I believe from reading one tutorial that when the partition wizard screen appears if I choose to create my own, then move the current partition just slightly then press ok it will work out where my windows partition is and then include a Linux partition. Is this correct ?

---

### Post by calvinthomas on 2006-08-09
Yes, at least for me partitioning from installing off the live CD was so easy to do! I'm not an expert or anything it just does it for you, tell it how much space you want Linux to use (I said 8Gb) and can't fill it and it will do the rest for you!

Calv

---


---
title: "Performance: Memory or CPU?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-02-10
After looking at this thread

[http://ubuntuforums.org/showthread.php?t=349828](http://ubuntuforums.org/showthread.php?t=349828)

I agree. PIII 750 256mb with Dapper and some things are not quick - anything from the "Places" menu, Mozilla stuff and definitely Open Office. 

Its not as quick as the equivalent stuff on a PIII 500 W98 box - exception Mozilla stuff.

Swap does'nt seem heaviliy used and memory looks generally free. ps -ef shows X as the biggie on CPU usage.

I've always thought memory is king - but bearing in mind I am battling to convert a housefull of Windows users (almost everything but ME here) - should I be looking for more engine power?

Is there a recommended spec for Dapper/ Edgy/Feisty out of the box?

My next PC is Edgy.

---

### Post by jpeddicord on 2007-02-10
There is no spec for the main Ubuntu tree to speed up things for older CPUs (although speed is always updated).

The best thing to do is to install Xubuntu. Xubuntu was created just for the purpose of older PCs. If you want to install it alongside ubuntu, just install **xubuntu-desktop** in Synaptic. If you want to download a CD of it, visit [http://xubuntu.com](http://xubuntu.com).

Jacob

---

### Post by seijuro on 2007-02-10
I'd recommend 512 memory I have a tower running a 1.8 ghz amd cpu with 256 memory and it zips along pretty good but I can tell it would be happier with more memory comparing it to my laptop which has 512 it has a faster cpu and cd rom than my laptop but because of the memory the live cd loads slower on the tower. A friend of mine claims that if you have 1gig+ of ram you can pretty much ignore the swap space. I just recently installed Kubuntu on an old dell for a friend I'm not sure of the specs but it was old enough that it didn't even have a cd burner in it. Its a little slow compared to my lappy or tower but everything runs flawlessly and it's still faster that it was with windows xp.

---

### Post by getaboat on 2007-02-10
Thanks for the replies so far.

My "job" computer is a 2.4Ghz laptop with 512 mb memory with XP Pro and quite honestly its a bit of a dog. 

I'm looking at building a cheap PC for Edgy (PHP/SQL development) and it looks like 1Ghz+ and 512Mb with at least 128mb graphics (not on board) would be a good starting point.

---

### Post by risbac on 2007-02-10
I think memory is always the most important to look at. Because when you don't have enough, it just turns your computer into a very irritating tool, as the hard drive is just so slow compared to RAM. So you can actually FEEL a sudden slowdown. 

If your CPU is not that fast, then it will just work at its speed, and that's it, not sudden "what's going on now???". 

I know it's a lot about how you feel in front of your computer rather than the actual speed. But that's what matters for the user I think. 

512Mo of Ram is really what is needed for a very pleasant desktop with Ubuntu. Even with an "old" CPU. XP is running better with 256Mo I think. I don't say it's perfect, but that it's better than Ubuntu. When it comes to 512Mo, I think Ubuntu is just running great. So under 512, go for Xubuntu, or just make sure you load as few things as possible with Ubuntu.

---

### Post by nickoli_02 on 2007-02-11
I'd have to agree, you can really feel when you don't have enough RAM, but a slower CPU you won't notice too much. I use a laptop every day with Intel Centrino 1.73GHz. It's scaled down to 800MHz to conserve power and I never notice it (you're very rarely using above 50% of your CPU resources in every day computer usage anyway). If a process needs more CPU power than it automatically scales up to 1.73GHz. 99% of the time I'm sitting at 800MHz, and it responds just fine.

---


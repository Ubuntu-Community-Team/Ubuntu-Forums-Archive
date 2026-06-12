---
title: "COMPIZ: Hangs Pc bec. of Flash sites!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-16
One time I missed Compiz, so I decided to use it again.

I adjusted the Animation settings, I made it a little rough, meaning, not that smooth, probably that's the reason why Ubuntu crashes or Compiz crashes, thus bringing me the restarted Gnome without the animations.

Now, I tried it again, I really missed the shadowing and the animations.

But sad, in my opinion, you will STILL experience the optimum performance of Ubuntu when Compiz is off.

Now to continue, when accessing some flash-based sites while Compiz is on, my processor goes to 100% and system load increases up to 9.0! CPU Frequency goes to the maximum of 1.70GHZ!

Then the entire Ubuntu OS hangs, when I am playing a song via imeem.com and accessing YouTube at the same time.

I decided to turn off the computer manually then use Ubuntu Linux without Compiz.

Not a problem, tried doing it again. I was able to listen to a music via imeem.com and check out some videos at YouTube.com at the same time, 2 flash based sites.

Ubuntu did not crashed or hang. I can access other websites as well and run other applications. Although, CPU Freq. is 1.70GHz, processor is 100%, and sometimes the system load increases, sometimes not.

I think there's a memory leak with Flash 9. Is some fix to this? Even a snapshot fix or something? Because In Windows I can visit flash-based sites without making the system eats all of my memory or makes the system hang a bit, until it is unusable.

Is there a beta version of Flash 9 with a memory leak fix? Another thing, is there a beta or alpha or any super latest version of Compiz? I wanna try it out, hoping those kind of issues I experienced above are, probably and hopefully fixed.

My theory, a conflict between Flash and Compiz. Agree?

---

### Post by duncan.hawthorne on 2008-03-18
i think you would need to do more tests that one each way

flash cant be fixes by anyone here, adobe controls it and keeps the source code
not a good idea to try a new compiz, just wait for hardy heron release of ubuntu.

you could try making a new firefox profile (ie starting firefox with --profilemanager in terminal) or using less extensions.

It is true that flash sometimes does crash firefox, but generally it is getting better and seems to be much better in firefox 3 in hardy (at least for me)

---

### Post by Xiong Chiamiov on 2008-03-18
I suppose you should be able to guess if there's a memory leak in Flash by looking at how much memory it's using when first started and after it's been running a while.  I had problems with flash crashing Firefox until I switched to Swiftweasel (which doesn't make any sense, really).  You can also try using Kazehakase or Opera.

---

### Post by StOoZ on 2008-03-18
im experiencing the exact same issue, I think it has something to do with Firefox rather than compiz
I tested opera and all was find,much faster, but as overall I hate this browser,so I removed it and im with FF at the moment.
I guess this issue will be addressed in FF3.

---

### Post by karlo on 2008-03-22
> **duncan.hawthorne said:**
> i think you would need to do more tests that one each way

flash cant be fixes by anyone here, adobe controls it and keeps the source code
not a good idea to try a new compiz, just wait for hardy heron release of ubuntu.

you could try making a new firefox profile (ie starting firefox with --profilemanager in terminal) or using less extensions.

It is true that flash sometimes does crash firefox, but generally it is getting better and seems to be much better in firefox 3 in hardy (at least for me)

Why not try the new version of Compiz? Isn't it advisable? Why? OR will it have conflicts with the default-installed Compiz that is named as Advanced Desktop Effects?

> **Xiong Chiamiov said:**
> I suppose you should be able to guess if there's a memory leak in Flash by looking at how much memory it's using when first started and after it's been running a while.  I had problems with flash crashing Firefox until I switched to Swiftweasel (which doesn't make any sense, really).  You can also try using Kazehakase or Opera.

Swiftweasel, it's optimized for the processor that you are using, right? Well in Opera, flash-based sites does not work completely, even for the beta version.

Also, I think a temporary solution to avoid Firefox crash with flash-based sites is to download a Firefox or Swiftweasel plugin called Flashblock.

> **StOoZ said:**
> im experiencing the exact same issue, I think it has something to do with Firefox rather than compiz
I tested opera and all was find,much faster, but as overall I hate this browser,so I removed it and im with FF at the moment.
I guess this issue will be addressed in FF3.

Hopefully it will be Addressed in FF3. If only there's an Alpha or Beta version of Flash that has a temporary fix with the memory leak we're experiencing.

---


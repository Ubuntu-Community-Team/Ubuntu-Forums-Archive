---
title: "Would This Computer Require 32-Bit Ubuntu or 64-Bit Ubuntu?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-18
My  friend is buying a new computer. Inside, it has a *AMD Athlon 64 X2 Dual-Core 4400+*. Will this require the 64-Bit version of Ubuntu? Also, how do I find out what Bit version of Ubuntu is already installed on a PC?

Thanks for your time.

---

### Post by nsimeone2000 on 2008-02-18
It can use either, I have about the same settings and I use 64-bit, but, if you use 64-bit, there is no flash drivers support, (but I am sure there are workarounds)

If he is new to Linux and Ubuntu I would recommend 32-Bit....I am thinking of reinstalling onto 32-bit right now as a matter of fact.....

Edit Oh yea, make sure you use the alternate CD!  and I would only use 7.04, 7.10 doesn't look stable enough, (especially if the computer is an HP)

---

### Post by sb12 on 2008-02-18
the athlon 64 means its 64 bit, you can use either though

---

### Post by bumanie on 2008-02-18
You can use either the 32bit or 64bit OS with that processor. If you are not particularly linux savvy, most users suggest starting with the 32bit version is better. The 32bit works fine with a 64bit processor.

---

### Post by smartboyathome on 2008-02-18
I would suggest the 64 bit for your computer. It can do pretty much everything that the 32 bit can do, plus you can get flash working by installing with a script on this forum.

---

### Post by nsimeone2000 on 2008-02-18
> **smartboyathome said:**
> I would suggest the 64 bit for your computer. It can do pretty much everything that the 32 bit can do, plus you can get flash working by installing with a script on this forum.

Do you have a link to that script?

---

### Post by smartboyathome on 2008-02-18
> **nsimeone2000 said:**
> Do you have a link to that script?

Right [here]("http://ubuntuforums.org/showthread.php?t=476924"). Also, run these commands to get flash in firefox 3 beta 3:
```
sudo mv /usr/lib/firefox-3.0-3.0b3pre/plugins /usr/lib/firefox-3.0-3.0b3pre/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0-3.0b3pre/
```

---

### Post by Atomic Dog on 2008-02-18
I agree with Bumanie.  32 bit will make your life easier if you are not a savvy user.  I run 32bit on my laptop because I want things to work without much hassle.

---

### Post by Paqman on 2008-02-18
I've been using 64-bit ever since switching to Ubuntu a year or two ago. There used to be some issues with 64-bit but now they've pretty much all been dealt with. There's no reason not to use 64-bit if your processor supports it.

---

### Post by steveneddy on 2008-02-18
> **Paqman said:**
> I've been using 64-bit ever since switching to Ubuntu a year or two ago. There used to be some issues with 64-bit but now they've pretty much all been dealt with. There's no reason not to use 64-bit if your processor supports it.

Agreed - the 64 bit version has everything you need and if it doesn't, you can always compile it.

I've been on 64 bit for 5 months now and it does work smoother and the laptop is snappier than 32 bit.

Intel Core 2 Duo with 2 gig RAM

---

### Post by Crumpets and Jam on 2008-02-18
Would he miss out on any potential performance if I went for the 32-Bit version of Ubuntu?

---

### Post by Anduu on 2008-02-18
> **Crumpets and Jam said:**
> Would he miss out on any potential performance if I went for the 32-Bit version of Ubuntu?

A hardcore user would notice the difference but I doubt the casual user would....

---

### Post by deadmnky on 2008-02-18
personally i use the 64 bt with that processor and am new to linux. i have had hardly any problems with using ubuntu 7.10 is been a couple of months now roughly.

---

### Post by dcstar on 2008-02-19
> **Paqman said:**
> I've been using 64-bit ever since switching to Ubuntu a year or two ago. There used to be some issues with 64-bit but now they've pretty much all been dealt with. There's no reason not to use 64-bit if your processor supports it.

Exactly, there seem to be a lot of people who had problems with immature 64bit distros ages ago and they still bag it, the current distro has few issues and I wish that those with out of date experiences would keep them to themselves.

---

### Post by Anduu on 2008-02-19
> **dcstar said:**
> Exactly, there seem to be a lot of people who had problems with immature 64bit distros ages ago and they still bag it, the current distro has few issues and I wish that those with out of date experiences would keep them to themselves.

Errrr...who excactly is bagging on the 64bit version?

All I see are two people saying they might have a slightly easier time sticking with 32bit seeing as they are new users.What is wrong with that?

---

### Post by oedha on 2008-02-19
> **Crumpets and Jam said:**
> Would he miss out on any potential performance if I went for the 32-Bit version of Ubuntu?

of course......64 OS made for 64 computer......
even 32 is also fine with the machine
64 will bring you to the advance performance of your computer

---

### Post by JoshuaRL on 2008-02-19
> **nsimeone2000 said:**
> It can use either, I have about the same settings and I use 64-bit, but, if you use 64-bit, there is no flash drivers support, (but I am sure there are workarounds)

If he is new to Linux and Ubuntu I would recommend 32-Bit....I am thinking of reinstalling onto 32-bit right now as a matter of fact.....

Edit Oh yea, make sure you use the alternate CD!  and I would only use 7.04, 7.10 doesn't look stable enough, (especially if the computer is an HP)

I also have to take issue with this.

I am running 64bit on my computer and I have that exact processor, just the 4200+.  I have had only a couple issues, and everyone that installs an OS will have some, no matter the computer or OS.

Buying a 64bit computer and running 32bit OSs on there is like buying a Corvette and taking the spark wires off of 4 cylinders.  Sure, you could probably go check your mail in it, go to the store probably.  But if you wanted to do anything really cool you'd be missing out.

I've heard you can tell the difference in encoding, compiling, rendering, and virtualization.  But everything tends to be a little snappier and a tad bit faster.

At least that's how I feel.

---

### Post by adlerhn on 2008-02-19
Is it possible to upgrade from an existing 32-bit installation to a 64-bit one?

Is it so easy as installing a package in Synaptic that contains the 64-bit version of the kernel and libraries, or should I install everything from scratch?


Regards!

---

### Post by JoshuaRL on 2008-02-19
I would really suggest against even trying.  A lot of apps are 64bit too, so I wouldn't even want to imagine how hard it would be to "upgrade" to 64bit.  And that's if it's even possible.

Which I highly doubt.


And as far as 7.10 not being stable, I can't get behind that either.  I am running 64bit 7.10 and had almost no problems loading it onto my computer.  Almost all the issues with Gutsy have been solved, whether 32bit or 64bit.  Sure, some things are a little differen.  But if you're into Ubuntu haven't you gotten used to that already?

In my experience 64bit Ubuntu works a ton better than 64bit Windows.  It's a well-developed distro in its own right.

---

### Post by Wynne G Oldman on 2008-02-19
I use both 32 and 64 bit Ubuntu (on different machines) and I was a newbie last year. I can tell the difference in performance. 64 bit seems a bit snappier on the same machine as 32 bit. If you're doing a lot of processor hungry stuff, like video encoding, then you can really tell. You may have the odd problem with both versions, but there shouldn't be anything that you can't resolve with the help of these Forums. Feel free to have a look through my history for answers to a lot of common problems.

---

### Post by sandysandy on 2008-02-21
> **Wynne G Oldman said:**
> I use both 32 and 64 bit Ubuntu (on different machines) and I was a newbie last year. I can tell the difference in performance. 64 bit seems a bit snappier on the same machine as 32 bit. If you're doing a lot of processor hungry stuff, like video encoding, then you can really tell. You may have the odd problem with both versions, but there shouldn't be anything that you can't resolve with the help of these Forums. Feel free to have a look through my history for answers to a lot of common problems.

i agree 64 bit is definitely faster. i am running both versions on same computer and the difference in speed even in booting up is appreciable.

regards

---


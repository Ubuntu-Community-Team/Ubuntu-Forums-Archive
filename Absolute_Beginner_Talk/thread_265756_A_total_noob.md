---
title: "A total noob"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by headsh0ts on 2006-09-26
Hey there.

3 days ago i was using windows, today its ubuntu! god fed up with windows problems (and youtube videoes showing the cube won me over :)) 

Anyway! Ive happily downloaded and installed ubuntu, but now im totally clueless as to what to do now. theres no cube, and i dont know how to do anything

Ive gone through pages and pages of information, advice, how to install this and that, but to be fair i need something in plain english laid out infront of me, all the wikis ive found confused me, its all a bit overwhelming.

With work i cant find the time to sit down and suss all this out. ive gone through topics here to find something simple to read but no luck, if anyone can point me in the right direction id greatly appreciate it.

Sorry if its a stupid question and im wasting your time :)

laters.

---

### Post by jordanmthomas on 2006-09-26
[http://wiki.beryl-project.org/index.php/Ubuntu](http://wiki.beryl-project.org/index.php/Ubuntu)

Has some good guides about getting compiz (cube-using window manager) running.
They are in the middle of a switch to a different name and I think the packages are offline for now, so you may have to wait a week or so before you can get it.

---

### Post by steve.horsley on 2006-09-26
Here is a good starter guide: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Feel free to ask here when you have specific problems. One post for each problem will probably be best. There's no rule against asking lots of questions. But try searching the forum first - may questions are asked and answered repeatedly - several times a day sometimes.

Can't help you with the cube - haven't dared risk scrambling a working system yet. I'll probably give it a spin (pun intended) when Edgy comes out next month.

---

### Post by Architeuthis on 2006-09-26
Aiglx will be preinstalled in Edgy!
Here you can find more info about it: [http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx)
This is some sort of windows vista like eyecandy system, 

and maybe you can check out 3ddesktop (its in the repositories)

---

### Post by tetrahedron on 2006-09-29
I am not understanding...

XGL does all those advancement features in the X windows, like the cube, wobblely windows, stretch and twist windows, rain drops, etc.. etc..

right?

so does AIGLX that is built into X.org 7.1 as found in Edgy do this as well?


And then Compiz or Beryl allows transparency, blur and what not for themes?



THis is kinda of confusing, I would like to have awesome eye-candy.. and I just purchased a new laptop from system76 so I would love to show it off to friends, co-workers and family.

Can someone please explain to me the differences of XGL and AIGLX, yes I already read that XGL was more of hack and AIGLX had built in support of X.org... I mean how can I do those wonderful demo videos I have seen with XGL using AIGLX.. 

or am I just way off here?

---

### Post by skymt on 2006-09-29
All the effects you see on Youtube (cube, wobble, etc) are from a program called Compiz. It needs a hardware-accelerated 3d graphics system, which can be either XGL or AIGLX. As you said, XGL is a hack, AIGLX is better. AIGLX will be in Edgy.

There was recently a fork of Compiz called [Beryl](http://forum.beryl-project.org/topic-4591-beryl-informations-announcement). This broke most of the documentation, for various complicated reasons. Beryl isn't released yet.

I recommend you wait for Edgy (or upgrade now, it's pretty stable in my experience) and wait for someone to write a howto for Beryl/AIGLX on Edgy.

---

### Post by jordanmthomas on 2006-09-29
You can already get Beryl on Edgy by using the same repos from when it was called compiz.
Follow the compiz guides, but whenever installing a package, use what's in this link (emearld, beryl, etc)
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
The guide is for Nvidia cards and will have you use AIGLX.
You can still use XGL from other tutorials if you wish.
For now, you kind of just have to mix and match tutorials.

---

### Post by Demoted on 2006-09-29
I never found Dapper Ubuntu to be extensively hard to switch to from Windows.  It's got that good old Windowsy graphic interface to add and remove programs so you're not entirely stuck using command line in terminal/console.  The hardest thing would be remembering program names for downloading and what all each program does.  Then again, I'm an absolute Ubuntu n00b myself, which is why I'm here.  :)

---

### Post by tetrahedron on 2006-09-29
> **jordanmthomas said:**
> You can already get Beryl on Edgy by using the same repos from when it was called compiz.
Follow the compiz guides, but whenever installing a package, use what's in this link (emearld, beryl, etc)
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
The guide is for Nvidia cards and will have you use AIGLX.
You can still use XGL from other tutorials if you wish.
For now, you kind of just have to mix and match tutorials.

I appericate the input/advice... but will installing Beryl on Edgy (w/AIGLX built in) give me the same fancy eye-candy I see when watching demo videos of XGL (like on the Novell site or as seen on various YouTube videos about XGL)?

---

### Post by qamelian on 2006-09-29
> **tetrahedron said:**
> I appericate the input/advice... but will installing Beryl on Edgy (w/AIGLX built in) give me the same fancy eye-candy I see when watching demo videos of XGL (like on the Novell site or as seen on various YouTube videos about XGL)?

Definitely. XGL / AIGLX essentially just gives you the speedy rendering needed for the effects. The effects themselves are provided by beryl / compiz and their assorted plug-ins.

---

### Post by jordanmthomas on 2006-09-29
>  will installing Beryl on Edgy (w/AIGLX built in) give me the same fancy eye-candy I see when watching demo videos of XGL
On my computer, AIGLX is WAAAY faster than XGL and always has been (i915 chipset)
Beryl is just compiz with more effects and some optimizations here or there...so anything on the XGL videos you've been watching is possible with AIGLX / beryl

---

### Post by tetrahedron on 2006-09-29
> **qamelian said:**
> Definitely. XGL / AIGLX essentially just gives you the speedy rendering needed for the effects. The effects themselves are provided by beryl / compiz and their assorted plug-ins.

sweet! thanks this what I was looking for.

---


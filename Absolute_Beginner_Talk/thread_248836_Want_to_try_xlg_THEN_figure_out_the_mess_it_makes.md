---
title: "Want to try xlg THEN figure out the mess it makes"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-01
Good evening people...Just read some other linux newcomers request for advice on installing this XLG AND his numerous responses to mabey get used to Ubunto first before he  tries more complicated stuff....

Well i too  would like to give it a go and reckon I could probably follow one of the tutorials BUT im not sure i can even use the XLG with this 3 year old pc.........

I had previously checked and remember getting the"NO RENDERING" message in the terminal with whatever command it was that i used.I`ve had to reinstall
a couple of times so did`nt get time in this first couple of weeks but am
raring to go now...

Im not just new to linux but pc`s in general so am not up to speed like most of you`se with various graphics cards and their capabilities(OR lack of).
I do know my sound and graphics is the onboard variety and i also noticed that my screen resoloution is a bit less than it was with xp but i do intend on adding the higher resloutions to the xorg.conf once i get a better idea of my graphics and what their cabable of(IF anything).

My graphics card(or chip) is a VT8375 Prosavage8 KM266/KL266...(VT8633 APOLLO pro266 AGP)..???????????????......S**T OR WHAT?????

I hope THAT means something to someone and they could mabey tell me if it`s even viable to think i can attempt to do what needs done with that ???

I dont mind breaking things IN FACT i enjoy it.....

GOOD STUFF AS EVER.......THANKS FOR ANY ADVICE(OR warnings](*,) :grin: )

P.S..not bothered about "HOW"....just "IF"

EDIT:.......I would`nt ask but there aint a single mention of THAT thing anywhere on here.......:confused:

---

### Post by Dinerty on 2006-09-01
I personally would not install xgl/compiz on a production system (Your main computer, as it is Alpha software, which means it's buggy, it may do funny things to your computer, like use alot of memory or crash for instance and not work the way you think it should)

I don't know much about your onboard card, but from what information i could find on it, I'm not sure whether xgl would be amazing on it, xgl is dependent on graphics.

xgl is very configurable though and you can turn it down, but wheres the fun in that !

---

### Post by xpod on 2006-09-01
See this is my worry...Wether it`s even feasable....JUST the trying it is all the fun i need.If it works then fine and if not...then it`s still fine.

I do intend on buying some fancy new hardware but im happy just seeing what messes up on this lot and what dont.Ive actually got a Kubunto sys upstairs so i might try it on that.It`s about the same age but im not sure whats inside it.

I aint worried about buggy beta software as i used enough of it in my short time with windows.I think im just attracted to the fact that it`s MORE likely to break than not.....:twisted: 

Either that or i`ll settle for my simple glx(gears)....LOL...looks simlar:shock: :wink:

---

### Post by Warbo on 2006-09-01
XGL works on a LOT of hardware, it doesn't have to be particularly new. A pretty full list is here: [http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL)

Remember that AiGLX and XGL offer the same features, so if one isn't supported on your card then the other might be (AiGLX mainly works on Free Software drivers, so if you are using a proprietary driver then you may have to use XGL because those drivers might not implement the features that AiGLX uses yet)

Personally I have used Compiz on a system with Nvidia GeForce2 32MB graphics card (using XGL) with no problems in terms of speed (but Compiz itself still crashes a lot), and I have also tried it on an ATI Radeon 9250 on AiGLX, although the Free Software's reliance on Mesa (software rendering) for transparency made it crawl.

Anyway, there is no harm in trying, so just follow the guides: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by xpod on 2006-09-01
Thanks m8....I just recall running some command that apparently gave an inital idea of wether it was possible or not and i got a "no rendering"
Message back..BUT then i see loads of stuff on adjusting your graphics
card to MAKE it work or vice versa with turning down the application
using it(xlg etc)....SO i`ll give it a go on the other pc tommorow or sunday once ive digested the tutorial properly.

Just did`nt want to try if i was 100% impossible BUT im begining to learn that theres usually a way round most situations...
In fact ive suprised myself with some o the situations ive wriggled out of
this last few months(after wriggling INTO them:-\" )

If it`s "possible" to put a daft cube on one o these things then i`ll get a daft cube on one.......Least thats the weekend sorted](*,) :-D

---


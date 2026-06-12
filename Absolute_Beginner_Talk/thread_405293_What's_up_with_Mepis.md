---
title: "What's up with Mepis"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by moxiot on 2007-04-09
I couldn't believe my eyes when i popped in the live cd of the new Mepis 6.5 distribution and my beloved broadcom card worked right away. i have been to hell and back with this card. i have tried many distros just to see if it worked. nothing seemed to work, only the fwcutter and that was about it (this is for my laptop btw [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif))
What was even more amazing is that it works way faster than windows. i'm not bsing ok. i took me 35 minutes to download what in windows took me an hour. same connection, same place, same file.
I'm still sticking to ubuntu because among many other things of the support forums. Anyways, i know i might sound silly asking this but is there any way to extract the driver from Mepis and put it in ubuntu? Is that plausible?

Ok, then, thanks a bunch

---

### Post by Bachstelze on 2007-04-09
> **moxiot said:**
> I couldn't believe my eyes when i popped in the live cd of the new Mepis 6.5 distribution and my beloved broadcom card worked right away.

That means it installed non-free stuff and maybe illegally, to hell with Mepis !

To answer your question, ye, it would be very surprising if you couldn't do the same with Ubuntu, but we need to know what exactly Mepis did to tell you...

---

### Post by aysiu on 2007-04-09
If you like Mepis, use Mepis. It is now based on Ubuntu anyway.

---

### Post by moxiot on 2007-04-09
Ok, easy now. i dindnt know i was stepping in to forbidden land here. so if Mepis managed to get my bcm to work right away illegally to hell with them, heck to hell with them anyways, i don't really like the distro. I was only asking how it was possible that's all, i didn't know it was illegal or anything like that. 

My apologies.

What do you mean by "what exactly Mepis did to tell you..."

---

### Post by Bachstelze on 2007-04-09
I mean the way it installed the driver, so we can tell you how to do th same thing in Ubuntu. Also, knowing the exact model of your card might help.

---

### Post by moxiot on 2007-04-09
Nothing, i mean it worked right away and it was under the wlan0 interface. I didnt go into the terminal or anything. My model is : Dell 1390 wlan.
Thats all i know, i already uninstalled Mepis because as i said i didnt feel confortable and i couldnt get the sound to work and movie playback was dreadful, and their forums suck, etc, etc, 

My computer is  a Gateway MX-6447

---

### Post by Bachstelze on 2007-04-09
```
dmesg | grep bcm43xx
```

something there ?

---

### Post by justin whitaker on 2007-04-09
> **moxiot said:**
> Ok, easy now. i dindnt know i was stepping in to forbidden land here. so if Mepis managed to get my bcm to work right away illegally to hell with them, heck to hell with them anyways, i don't really like the distro. I was only asking how it was possible that's all, i didn't know it was illegal or anything like that. 

My apologies.

What do you mean by "what exactly Mepis did to tell you..."

Mepis is perfectly legal, although I avoid it because, and I can't believe I am saying this, but the license is a bit restrictive for me. 

I want to be able to use a distro I am using as a potential base for my own OS or distribution at some point, and Mepis is delivered under a hodgepodge of licenses which prevents you from tampering with it too much. 

That does not mean that Warren is not cognizant of the legalities of the distro he is shipping. He's very adverse to getting hauled into court. I believe he's gone out and gotten the clearance to deliver the drivers and applications where redistribution is not allowed. 

*shrug* 

Whatever your stance on the license, it sure does work as advertised, doesn't it?

---

### Post by Bachstelze on 2007-04-09
Apparently, it wasn't advertised since moxiot saud it was amazing so, correct me if I'm wrong, Mepis seemsto install some non-free stuff without the user knowing it. An OS that would do something on my machine - especially install stuff and non-free stuff even more so - without telling me what it did, how it did it and why it did it is not one I would trust, let alone use.

---

### Post by SorenK on 2007-04-09
Isn't "illegal" a bit of an overstatement?  Even closed source drivers are meant to be used to support the hardware they are written for.  There might be a potential conflict in an EULA, but "illegally, to hell with Mepis!" is probably overstating things a bit.

Mepis hasn't been wonderful and sharing their source code, but they have technically complied with GPL.  I don't really support the Mepis project at all, but if it can install drivers for something Ubuntu can, perhaps the real issue isn't one of licenses but of implementation.

As far as their resistance to the simple task of providing source code, I can see both sides of the issue.  If you give a friend the ubuntu cd do you also give them a copy of all the source code of all the gpl stuff that might be on it?  Or do you simply let them get it through a package if they are interested?  

To assume that their implementation of driver installatian might somehow be illegal is a bit much.

That said, Mepis should definitely alert the user before installing any non-free software or drivers.  This is the type of thing EULAs are for.  Full disclosure.

Easiest thing to do, find out what driver it's using and do it yourself with Ubuntu.  That way you can check any license issues yourself directly with the driver maker.  If it's one of Mepis' changes to the kernel that makes this easy installation possible, then this may not be a real solution.

---

### Post by justin whitaker on 2007-04-09
> **HymnToLife said:**
> Apparently, it wasn't advertised since moxiot saud it was amazing so, correct me if I'm wrong, Mepis seemsto install some non-free stuff without the user knowing it. An OS that would do something on my machine - especially install stuff and non-free stuff even more so - without telling me what it did, how it did it and why it did it is not one I would trust, let alone use.

Isn't that the whole point of Mepis? They don't say: "We are all about full disclosure". They say: "It just works." This is the Point and Click version of Linux, remember?

Mepis is for people that want their system to work, don't care how it gets done, and are happy with things as it's served to them. 

So, FSF-lovers need not apply, I guess. 

To me, it's always seemed incongruous to swap out one proprietary system for a GPL system that is just as proprietary (in it's own way), but alot of people seem to like it.

---

### Post by moxiot on 2007-04-09
ok dsmeg | grep bcm43xx didn't return anything, i'm only using the livecd. 
ndiswrapper -l returned the following without me having installed any drivers at all:

demo@1[demo]$ dmesg | grep bcm43xx
demo@1[demo]$ ndiswrapper -l
airplus : driver installed
bcmwl5 : driver installed
        device (14E4:4311) present
bcmwl5a : driver installed
lsbcmnds : driver installed
lsbcmnds6 : driver installed
lstinds : driver installed
mrv8k51 : driver installed
netr33x : driver installed
prismnic : driver installed
wlanuig : driver installed
wlipnds : driver installed

it seems that i have awakened pandoras box here, but let me ask something here. i own the wireless card, therefore is it legal for me to try to extract the drivers from mepis and install them in ubuntu, which is what i wanted to do and why i initiated this thread. moreover, is it moral? i mean i own the hardware.
if it's ok could you guys show me how, otherwise is 20 bucks for linuxant, which i'm happy to pay, as long as it works as i've tried out everything to get this sucker to work.

---

### Post by justin whitaker on 2007-04-09
> **moxiot said:**
> ok dsmeg | grep bcm43xx didn't return anything, i'm only using the livecd. 
ndiswrapper -l returned the following without me having installed any drivers at all:

demo@1[demo]$ dmesg | grep bcm43xx
demo@1[demo]$ ndiswrapper -l
airplus : driver installed
bcmwl5 : driver installed
        device (14E4:4311) present
bcmwl5a : driver installed
lsbcmnds : driver installed
lsbcmnds6 : driver installed
lstinds : driver installed
mrv8k51 : driver installed
netr33x : driver installed
prismnic : driver installed
wlanuig : driver installed
wlipnds : driver installed

it seems that i have awakened pandoras box here, but let me ask something here. i own the wireless card, therefore is it legal for me to try to extract the drivers from mepis and install them in ubuntu, which is what i wanted to do and why i initiated this thread. moreover, is it moral? i mean i own the hardware.
if it's ok could you guys show me how, otherwise is 20 bucks for linuxant, which i'm happy to pay, as long as it works as i've tried out everything to get this sucker to work.

That's a good question: My guess is no, but I'll let someone with more legal knowledge than me answer that!

Have you tried ndiswrapper?

---

### Post by Bachstelze on 2007-04-09
Holy crap, Mepis installed an awful lot of useless drivers in ndiswrapper, that's even worse than I thought ! (Not from a legal but technical point of view.)

To answer your question, sadly, the fact tha you bought the card does not mean that you can do whatever you want with it but that you can use it *only* in ways approved by Broadcom and I'm not sure that includes using it in Linux.

So yes, Broadcom are true a**holes and if you want to give them the middle-finger and use their stuff without their permission, that's fine with me and that's way besides my point. My point is that the drivers are non-free and Mepis installed them without noticing you. Today, Mepis installs wireless drivers, tomorrow maybe it'll install spyware or worse...


And to make things clear, no, I have nothing against non-free softwate as such. I even use some non-free software myself but I installed it myself, knowing exactly what I was doing.

---

### Post by moxiot on 2007-04-09
yeah i've tried the wrapper many times, i will give it another go when feisty comes out, who knows, otherwise is linuxant. thanks alot for all the replies i sure learnt alot, i will never use Mepis again, not that i was going to but there you go. good job i posted this, know i know.

---

### Post by Bachstelze on 2007-04-09
Why wait ? Now, you know your card works with ndiswrapper and you even know wich driver you need. So go ahead and install the same one in Ubuntu, there is no reason it wouldn't work.

---

### Post by moxiot on 2007-04-09
i rather wait and do an clean install of feisty on my hdd. if it doesn't work then, i'll stick with edgy. it's been a while since i tried the ndiswrapper and i wouldn't want to mess anything up now, i'm really afraid of that. thats why i want to do it with a clean install. and i think i read that feisty will have better support for the bcm chipset . as far as my drivers, i think the ones i used are the right ones because they work with windows and with linuxant, i followed all the howto's to the t and none of them worked even when they were working for other people. but yeah, i'll grab them from mepis and try it again in like two weeks or so.
many thanks for everything.
take care

---

### Post by AdrianTM on 2007-04-09
> My point is that the drivers are non-free and Mepis installed them without noticing you.

Huh? The license of everything is on the CD, there's no rule anywhere that somebody has to tap on your shoulder and yell at you "hey that's a proprietary driver" if you care about that you read the license. 

I personally use free drivers if there are available if they are not I chose not to buy the card... but if some people have already those cards that work only with proprietary drivers is pretty ludicrous to blame MEPIS that they provide drivers for hardware that people have.

And it's funny how you claim that MEPIS is crap when...  MEPIS works, but Ubuntu doesn't.

> Today, Mepis installs wireless drivers, tomorrow maybe it'll install spyware or worse...

Today you spread FUD, what are your plans for tomorrow?

---

### Post by raldz on 2007-04-09
most people really don't care as long as everything works... I use MEPIS and Ubuntu on two different machines.. both distros are great, but MEPIS is easier.. everything just works in my machines.. and I don't really care how Warren made it happen as long as I'm using Linux... if at some point Ubuntu or MEPIS wouldn't work in my machines, then I would definitely look for other distros... and again I don't really care much as long as all my hardware are working fine.. that's what GNU all about.. freedom to choose...

MEPIS and Ubuntu are great in their own rights... lots  of people are devoting their precious time without expecting anything in return just to make these distros work.. so please stop spreading FUD..

---

### Post by buster on 2007-04-09
I doubt someone in the business of selling hardware would care if a user got it to work using 'proprietary' drivers. They usually give drivers away. And the more people who can buy and use their hardware, the better. (If the driver is owned by a third party, such as Microsoft, the situation might be different.)

Not the same situation as multimedia codecs at all. Or operating systems.

Worth thinking about though, I suppose.

---

### Post by awakatanka on 2007-04-10
To HymnToLife do you know why gnewsense is there? Because Ubuntu doing the same thing with some stuff like Mepis is doing.

> Ubuntu has included firmware, and used proprietary drivers since its inception. That&#8217;s always been a slightly uncomfortable proposition, as Mako observed, but it&#8217;s been true since the Warty Warthog. Source : [http://www.markshuttleworth.com/archives/84](http://www.markshuttleworth.com/archives/84)

---

### Post by SilverBear on 2007-04-10
> **HymnToLife said:**
> That means it installed non-free stuff and maybe illegally, to hell with Mepis !
.
:confused: 
No. That's not what it means.
Apparently you don't understand much about device drivers in general and Broadcom drivers in particular:
[http://bcm43xx.berlios.de/?go=home](http://bcm43xx.berlios.de/?go=home)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

As it relates to Mepis:The developer stated he used the latest version of ndiswrapper and the Broadcom windows driver to achieve improved support for the chip. 
[http://www.mepis.org/node/13081](http://www.mepis.org/node/13081)
[http://www.mepis.org/node/13201#comment-50229](http://www.mepis.org/node/13201#comment-50229)
What your definition of "free" is, I don't know. It is true Mepis is offering  configurations with both the reverse-engineered Open Source bcm43xx driver and the proprietary driver from Broadcom.

Illegal? I doubt that any company that *offers the driver for use* with it's hardware is going to claim it's* illegal to use it! * And you can download broadcom proprietary drivers elsewhere, not just from a broadcom website. For examples:
[http://www-307.ibm.com/pc/support/site.wss/MIGR-63623.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-63623.html)
[http://members.driverguide.com/driver/detail.php?driverid=88453](http://members.driverguide.com/driver/detail.php?driverid=88453)

[QUOTE=HymnToLife]
 	Why wait ? Now, you know your card works with ndiswrapper and you even know wich driver you need. So go ahead and install the same one in Ubuntu, there is no reason it wouldn't work.[/QUOTE]
Well, you ought to do some research on the Forums, the Documentation  and in Bug reports  before you go giving people advice. There have been a number of reasons it hasn't worked up until very recently:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/73759](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/73759)
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468)

Very recently on the forums, it is suggested to overcome the longstanding Broadcom problem by doing yourself what the Mepis developer offered out-of-the-box: use the latest ndiswrapper with the proprietary Broadcom driver designed for Windows:
[http://ubuntuforums.org/showthread.php?t=346083](http://ubuntuforums.org/showthread.php?t=346083)

I have not spent much time here on the Forums for a couple months --actually since December.  But I seem to remember this as a pleasant place to find --or offer-- helpful information.  I don't think wild accusations about topics with which you are unfamiliar do much credit to our Ubuntu community, or to the distro, or to Linux in general. 

Now, why did Mark name this distro "Ubuntu?" What does that mean?

---

### Post by raldz on 2007-04-10
It seems someone is reading too much tabloids lately and cried foul without doing his homework...  These types of people are bad for the Ubuntu and Linux Community... instead of spreading collaboration and being helpful, is instead spreading rumors and hate...

At least we know now in this thread who is credible and NOT...

---

### Post by DarkN00b on 2007-04-10
If you have a Broadcom 43xx based card, check [here]("http://ubuntuforums.org/showthread.php?t=405990"). I made this just for people who were having problems with their Boradcom cards.

Also read about my concerns over its legality [here]("http://ubuntuforums.org/showthread.php?t=405219").

Basically, it probably isn't legal, but I paid for the card dammit, and I *will* use it.

---

### Post by moxiot on 2007-04-10
boy oh boy. i only wanted to find another solution for all my ndiswrapper troubles but guess what, i got it to work last night. this was fun, hell nobody answered my question but i had a laugh reading all this posts.

---

### Post by 79spitfire on 2007-04-10
> boy oh boy. i only wanted to find another solution for all my ndiswrapper troubles but guess what, i got it to work last night. this was fun, hell nobody answered my question but i had a laugh reading all this posts.

Some days are like that!  :lolflag: 

At any rate, if I needed it, I'd use it in a heartbeat.....

---

### Post by lamalex on 2007-04-11
GG hymn. I still like you for what it's worth; For the most part all of your posts on this forum are helpful and knowledgeable, and I agree with your side that Mepis should make it more clear that it's installing proprietary drivers. It was my understanding that it WAS illegal for any Linux distro to ship with OOB support for broadcom cards due to firmware legality. I'm also not a lawyer. Either way, "just working," imo isn't as important to me as "working correctly without tons of unnecessary BS to bog down my system." I'm not a big fan of brute-force attacks, not the most elegant solution.

---

### Post by m_pav on 2007-04-11
> **Iamalex said:**
>  Either way, "just working," imo isn't as important to me as "working correctly without tons of unnecessary BS to bog down my system." I'm not a big fan of brute-force attacks, not the most elegant solution.

Ideas have been tossed about concerning legality and the likes, but for Iamalex to use a term like brute force is way out of line and nothing short of BS. I have always found that those with the least knowledge make the most false accusations and are more likely to spread propaganda than those that have carefully researched a subject first.

Providing drivers for hardware has been a global effort between all true linux adherents and the developers that take the time to talk nicely to hardware vendors has brought us a long way but we all know that not many hardware vendors give us much, if any thought in the design of their wares, so many of the drivers used in the linux kernel had to be reverse engineered from the start and this is still an on-going battle. Using a neat little program like ndiswrapper to use the install routines from a inf file is a very clever way to get unsupported devices working without reverse engineering the whole driver. How is that illegal?

Have we forgotten the systems we run all had to have hardware drivers written for them at some point in time? Has anybody stopped for even a moment to consider why the live cd they started with and defend with religious zeal works on so many different hardware platforms? Hundreds, if not thousands of hardware drivers are preloaded onto the ubuntu live cd, some are coded right into the kernel, others are pluggable modules and yet others are loaded manually. Surely, this must be nothing other than the "BS and brute force" Iamalex is talking about? Hyppocrite! Get your facts straight before blindly accusing another of the very thing you treasure.

Linux is all about choice and if you want to run Mepis but you do not want or need the additional driver modules for your particular wireless card, then take them out, but never ever claim it to be a brute force attack or BS. It only shows your ignorance.

HymnToLifes zeal is undeniable and it's wonderful that she tried to help, but maybe she should be denied her "legal linux" for a time and go back and spend time with uncle bill to regain some perspective on what linux is all about before spreading propaganda, again, ignorance in action.

So that you all know where I come from, I am a presenter at our local LUG. I tried ubuntu and I could not get on with gnome, in particular nautilus, it's too restrictive for my advanced requirements, then I tried kubuntu, but it too was just too weak and featureless, so I searched for an undiluted but uncluttered KDE desktop system, found Mepis and it fits the bill for me very nicely. Remember, it's all about choice.

Ubuntu is a very nice system and I like it alot, but it's not my choice of distro. I still download and give away ubuntu CD's and I will install it on peoples systems without hesitation. There is a linux distro for every user and we are all on the same side are we not?

Mike P

---

### Post by Bachstelze on 2007-04-11
> **m_pav said:**
> 
Ubuntu is a very nice system and I like it alot, but it's not my choice of distro.

Neither is it mine, if you read my profile, though it is the one I recommend to newcomers, too. And I guess you should look at yourself a bit more before accusing others of ignorance. As the old saying goes, "When you know Slackware, you know Linux. When yoiu know RedHat, you know RedHat." Sorry but I do not consider myself "on the same side" as Mepis, Mandriva and friends and I wonder how that makes me "ignorant".

I don't know if you know it but the French parliament recently made the desition to switch to Linux. You'd have thought everyone in the Linux community would be happy with it ? Too bad, they chose Ubuntu and the boss of Mandriva wrote a letter full of stupid propaganda saying that because Mandriva was French, the French absolutely had to use it and that Ubuntu was a "concurrent" in the "market". I was stunned, wondering if it was really Linux he was taking about. Sadly, it was. If the stupid guy considers other distros as "concurrents", I'm perfectly fine thinking the same about Mandriva and to tell you the truth, Mandriva can die, I'll even be happy with it. We don't need people like that.

---

### Post by lamalex on 2007-04-11
> **m_pav said:**
> Ideas have been tossed about concerning legality and the likes, but for Iamalex to use a term like brute force is way out of line and nothing short of BS. I have always found that those with the least knowledge make the most false accusations and are more likely to spread propaganda than those that have carefully researched a subject first

Brute force was a metaphor for just trying everything until it works. Which is the concept behind what Mepis did to get his card working, it just loads every possible driver into ndiswrapper. Before you attack me maybe should read more carefully into what I said. I'm sorry if you're not a native English speaker or a avid reader who would be more familiar with literary devices such as metaphors.

---

### Post by Bachstelze on 2007-04-11
Litterature is no good for business, I guess ;)

---

### Post by Voyage on 2007-04-11
Hello

Well this was interesting reading, must say this having tried Ubuntu it did not work well with my Ati card at the time so i moved on tried various other distro's again no luck till i tried Mepis and  Bl**dy *ell it worked real good. 

Now having moved from Win to Linux in Dec and of course i am a total Newbie as far as Linux is concerned,  I and probably 1000s of people just want Linux to work whatever the disto and when it does it's great. 

As for somthing being illegal well i would not know, thats for Lawyers and the Like. 

I thought as Linux users we all wanted the world to use Linux whatever the distro. 

But this slagging of one distro to another will firghten people off and to make matter worse no one seems to know if it is illegal or not.

Makes me wonder if this is the start of things to come!

Voyage a happly Linux user

---

### Post by AdrianTM on 2007-04-11
> I thought as Linux users we all wanted the world to use Linux whatever the distro. 

Different people have different goals don't make the mistake to believe that if people use the same OS, have the same goals (not even if they use the same distro).

> But this slagging of one distro to another will firghten people off and to make matter worse no one seems to know if it is illegal or not.

That's the exact definition of FUD: Fear, Uncertainty, Doubt, that's something that usually Microsoft (using tools like SCO) uses against Linux, but that's also something that people in Linux community use against other distros that they don't like for some reasons. If you want an example of FUD go no further than this thread.

---

### Post by lamalex on 2007-04-11
> **HymnToLife said:**
> Litterature is no good for business, I guess ;)

I guess we can't all be as fine and cultured as me eh?:redface:  So let's mark this thread closed! No more beating up on Mepis. Some of us may not agree with their methodology, but that doesn't necessarily make them wrong (I however am always right, but I don't play the zero-sum game, so Mepis got lucky this time ;-) ).

---

### Post by bcmiller on 2007-04-11
I had no idea that Mepis was this good!  It has Ubuntu people sounding like the people who critique Ubuntu.  I'll have to try it out!

It's sad how some people try to pull one distro down over another.  Recommendations should always be balanced with some statement about how "it's all linux" or something.  I started with Slackware and it's nowhere near as easy as Ubuntu but it's the same linux and it can do everything Ubuntu can do if you work on it.

The fact that Mepis made something easy is great.

It seems like some linux people are like the crabs in the pot that keep pulling down the crab that almost made it out.  Hopefully we can get out of our own way in time to really gain mainstream acceptance.  

It's like we all live in a trailer park across the street from a mansion and we are jealous of the doublewide with a deck...

---

### Post by AdrianTM on 2007-04-11
> It's like we all live in a trailer park across the street from a mansion and we are jealous of the doublewide with a deck...

:lolflag: I'm sure the guy stole to be able to afford something like that, not to mention that you don't need all that crap... :guitar:

---

### Post by oblio on 2007-04-11
Hi Folks, 

This is not a funny thread at all, as some might believe.  It was started here, spreading unsubstantiated innuendo and fud about Mepis. Hiding behind craftfully worded (or should I say engineered?) responses doesn't constitute real courageous behavior.  Have the courage to admit having crossed lines that you shouldn't  - as advocates of the Ubuntu principles.  And as plain decent folks.  Do something about it.

For what it is worth:
I gave up almost a year ago on Kubuntu (I don't like Gnome which is used in Ubuntu, so I do not use that), after having participated in betatesting prior to the 6.06 release.
But I neither loathe, nor hate, nor spread fud about kubuntu or ubuntu. 

There is a wealth of very useful information on this forum.  And a lot of crap.   Think about it..

Regards,   Ko

---

### Post by Bachstelze on 2007-04-11
I am not advocate of Ubuntu principles. I am advocate of my own principles, whether you like them or not.

---

### Post by AdrianTM on 2007-04-11
I hope you know the difference between principles "I don't like and don't want to use proprietary stuff" and FUD and slander "they do illegal stuff".

---

### Post by Bachstelze on 2007-04-11
I suggest you take reading classes, because I wrote "maybe illegal", meaning that I wasn't 100% sure of myself but has serious doubts about it. Also, as I stated afterwards, I do use proprietary software, that was not my point...

I strongly dislike distributors that want to turn the Linux world into a market, who see other distributions as "concurrents" who need to b eliminated. In short : who use Microsoft-like methods to evolve in the Linux world. As I stated earlier, I do notconsider myself "on the same side" than such people.

---

### Post by AdrianTM on 2007-04-11
Please don't be so kind to suggest I take reading classes, please read the definition of FUD to see how a nice example of FUD you provided.

"maybe illegal" is just a weasely way to accuse or spread FUD without taking responsibilities for your words.

---

### Post by m_pav on 2007-04-11
> **HymnToLife said:**
> Sorry but I do not consider myself "on the same side" as Mepis, Mandriva and friends and I wonder how that makes me "ignorant".


It appears to me you speak much of what you know little. Mepis, Mandriva?? You put Mepis in the same camp as Mandriva? Your ignorance is greater than I thought. I agree with AdrianTM, you are spreading FUD and maybe that is your true agenda? I am of course ignorant in this regard, but at least I admit when I am ignorant.

Your ignorance comes from the fact that you slagged another distro on nothing more than a whim. You jumped to a conclusion without checking it out for yourself and in your responses to a technical question, you used a religious name "hell" which has nothing to do with the original question. Instead of helping, you threw this thread into a flurry of confusion and the original posters response was one of being overwhelmed. 

If you have nothing good to say, then say nothing. Even a daft person is thought to be wise when they hold their tongue. First rule of business, never slag a competitor. It is like putting a stumbling block in somebody's way but if it is undeserved, it will roll back onto you, even if you deny that it is happening.

I see this exact thing happening here but the worst thing is you slagged a sister distro, not a competitor. If you're zealous for your own cause, use it for the good of the whole community, and check things out for yourself before casting stones. I'm here because I really like linux and I think more people should be using it, no matter what flavour. 

My thoughts on Mandriva? It's more expensive than microsoft if you want to do much more than browse the web. Locked down repos are not my idea of a good thing for anyone other then the one that holds the lock and the key, but if thats what somebody wants to use, all power to them, I promise I will not assign them to hell. They will probably move away from that concept to a more friendly one like Mepis or one of the other distros, but coming across a post like yours may scare them away. Elmer FUD (blind)

---

### Post by Bachstelze on 2007-04-11
Okay, can someone please just move this somewhere else ? It has nothing whatsever to do with Ubuntu support, never had since the beginning and I have nothing more to say here.

---

### Post by awakatanka on 2007-04-12
> **HymnToLife said:**
> Okay, can someone please just move this somewhere else ? It has nothing whatsever to do with Ubuntu support, never had since the beginning and I have nothing more to say here.

Maybe you shouldn't make a post with misinformation about a distro. Something the distro that the OP uses at this moment also does.

Maybe be a bit more careful with this kind of things in a beginner section where a beginner believes everything what a more experienced user post, even if it's you're own opinion.

Saying something maybe illegal but point him to do something that maybe illegal isn't smart to then.

---

### Post by buster on 2007-04-14
Closing this thread would be good. Someone could start a thread on the legalities involved with drivers, someone else could start a thread on notifying users of the drivers used, and a third person could start a thread on overloading a distro with unnecessary drivers. As it is this thread seems more like a battle than a sharing of information.

---

### Post by n3tfury on 2007-04-14
> **AdrianTM said:**
> Please don't be so kind to suggest I take reading classes, please read the definition of FUD to see how a nice example of FUD you provided.

"maybe illegal" is just a weasely way to accuse or spread FUD without taking responsibilities for your words.

well said.


and no reason to close this thread, just move it someplace where it can keep going as a lively discussion.

---

### Post by factotum218 on 2007-04-25
Dont you have a "I switched to Ubuntu lolroflcopter!!" blog to maintain or something?

---


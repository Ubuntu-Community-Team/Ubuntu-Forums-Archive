---
title: "Macbook Pro"
date: 2008-07-09
forum: Apple Hardware Users
---

### Post by TedPacyga on 2008-07-09
Hey,

I am interested in purchasing a brand new Macbook Pro 15" Laptop, the 2.4 or 2.5GHz one (haven't decided yet).  I was wondering if there are any problems with this laptop and Ubuntu.  I will most likely be using 8.07.  By using a Mac, I will probably triple boot, will I not get the same performance as a regular laptop?  I would think it be the same, since Macs are just expensive Intel based laptops, but I want to make sure before making the purchase.

One more thing, since I am already asking a question here about Macs I might ask this one as well.  I am planning on taking this laptop to college, and am quite scared of getting it stolen, I am going to be a freshman so I don't really know what happens yet.  Do people actually steal laptops in college, I know it depends on where you go, but just let me know your experiences.  Do you guys know of any good protection against thet?  I looked into some locks, but mehh, I was looking for something more.

Thanks.

---

### Post by cyberdork33 on 2008-07-09
> **TedPacyga said:**
> I am interested in purchasing a brand new Macbook Pro 15" Laptop, the 2.4 or 2.5GHz one (haven't decided yet).  I was wondering if there are any problems with this laptop and Ubuntu.  I will most likely be using 8.07.  By using a Mac, I will probably triple boot, will I not get the same performance as a regular laptop?  I would think it be the same, since Macs are just expensive Intel based laptops, but I want to make sure before making the purchase.yes, running other OSs on Macs is much like running it on a similarly equipped PC. For more detailed information about the Macbook Pro and its quirks with Ubuntu, see the wiki page. Be sure to also look in the links at the top of the page for more information that is not specific to the latest version of the Macbook Pro.
[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

> **TedPacyga said:**
> One more thing, since I am already asking a question here about Macs I might ask this one as well.  I am planning on taking this laptop to college, and am quite scared of getting it stolen, I am going to be a freshman so I don't really know what happens yet.  Do people actually steal laptops in college, I know it depends on where you go, but just let me know your experiences.  Do you guys know of any good protection against thet?  I looked into some locks, but mehh, I was looking for something more.Do people actually steal laptops in public? Why would a college campus be different? I may not be so concerned in your dorm room (if you have one), but I wouldn't just leave it sitting on a park bench or anything... lock it in your room when leave without it, keep it in your backpack (or whatever) when you leave with it. I think the same concern would apply on your college campus as would in your local starbucks, library, park, or other public locations that people use a laptop computer.

---

### Post by TedPacyga on 2008-07-09
I understand it might have been a dumb question but what ever.  Yeah, I guess that that is pretty common sense stuff, I just wanted some feedback. Also, thanks for the link, I will have a look.

---

### Post by cyberdork33 on 2008-07-09
> **TedPacyga said:**
> I understand it might have been a dumb question but what ever.  What about anything I can do to prevent theft, like in my dorm, I am not going to leave it on a bench anywhere.  Also, thanks for the link, I will have a look.
Didn't mean to make it sound like that. It is not a dumb question. I just wanted to make a point that your college is just like any other public location and there are not really any "special rules" or anything that people abide by.

Someone mentioned that the small safes that are often in hotel rooms hold a macbook air just great. you might be able to pick of a fire safe at walmart that it can fit in... Other than that the cable locks are about as good as it gets.

You can look into [Lojack]("http://www.lojack.com/pages/laptop.aspx") if you are really that concerned about it.

---

### Post by TedPacyga on 2008-07-09
Thanks, I will check out some safes, and I looked into some of the cable locks, but the reviews I read for them said they didn't work good on the Macbook Pro.  I looked at all the ones at the apple store, and some on newegg.  Do you know of any locks that work good with the Macbook Pro.

---

### Post by cyberdork33 on 2008-07-09
> **TedPacyga said:**
> Thanks, I will check out some safes, and I looked into some of the cable locks, but the reviews I read for them said they didn't work good on the Macbook Pro.  I looked at all the ones at the apple store, and some on newegg.  Do you know of any locks that work good with the Macbook Pro.
all cable locks are pretty much standard... there is a little key looking thing that fits into a slot then turns and locks in that position. the cable is looped around something immovable (or as immovable as you can get). If they are saying they do not work right with your machine there must be something specific about the macbook pro. I don't own one myself so I can't say much. Anyway, if someone REALLY wanted you computer, the cable lock wouldn't be a problem to cut, much like a cable lock for a bicycle.

---

### Post by hajk on 2008-07-09
May be you want to hear also from someone who actually just recently bought the 15" MBP (Penryn) that you are considering.

1. Get the shiny LED screen. If you're not convinced, then go to an Apple store and compare side-by-side with a matte LCD screen -- seeing is believing.

2. The 2.4GHz processor is fast enough, the upgrade to faster speed isn't worth the money.

3. Just accept the minimum 1GB RAM, but then replace it with as much as you can afford in the aftermarket (I installed 2x 2GB = 4GB). It may be that Mac OS X Leopard cannot use it all, but Windows and Linux can.

4. Most hardware features of the MBP can be made to work well in Linux, although it will take some time to hunt down the solutions in various wikis and forums. 

Things that don't yet work in Linux: fancy features of the touchpad like scrolling, tapping, etc (just the mouse function works fine); keyboard backlighting works, but isn't really usable because the applesmc kernel module fills the logs with an unending stream of debugging messages; the wireless Broadcom 4328 rev 05 chip works in Ndiswrapper, but may not connect with WPA/WPA2 security enabled (for some it does, for others it doesn't -- I'm in the latter category). Some of these problems may have been overcome by the time you install the next version of Ubuntu 8.10.

5. Things that work very well in Linux: CPU frequency scaling. Just with the regular ondemand policy, the processor cores amble along at 800MHz (that's about 33%) most of the time, only to speed up when doing some processing-intensive work (like upgrading packages). With my MBP sitting all day on a wooden tabletop (not the best surface for cooling) the processors have a temperature of 31 degrees C (that's 88 deg F for you Yanks); the HD has a temperature of 39 deg C (102 deg F). The bottom is just pleasantly warm to the touch, not hot; the top of the case even feels cool. The fans are idling at around 2000rpm, barely audible. I notice that Mac OS X runs decidedly hotter than Linux.

6. I use a Kensington cable and lock. While this is not going to stop a determined crook, it will frustrate the occasional grab-and-run thief.
Keeping it hidden, in a locked cupboard or zipped backpack, also helps.

7. Triple-booting you say? Do it if your college insists on students paying the M$ tax... and for no other reason. Dual-booting is definitely recommended since firmware upgrades need Mac OS X; I use the rEFIt boot manager (you need the latest version from SourceForge). 

Don't install Windows because you want to use the MBP as a gaming machine, despite it having a decent NVidia graphics card -- the problem is that good-looking smooth aluminium case will surely drop out of your hands when the action gets going... It may anyway, you've been warned.

8. Get a protective carrying case or sleeve. I use the Incase, which has plenty of storage for notes and also easily holds something like the Airport Express, which can act as a wireless bridge in Linux to join a wireless AP with WPA/WPA2 security in case you also have the Broadcom problem that I have.

Success!

---

### Post by cyberdork33 on 2008-07-09
> **hajk said:**
> Things that don't yet work in Linux: fancy features of the touchpad like scrolling, tapping, etc (just the mouse function works fine); 
Have you used the new driver...?
[http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)

Sorry for the OT chat!

---

### Post by hajk on 2008-07-09
Yes, I looked at them. These things aren't that important to me, so I've decided to wait until these new modules are officially admitted to the kernel. Just more OO.TT., I'm quite happy with using a Linksys WET54G wireless bridge to tide me over my present Broadcom problems, also fits inside my Incase (including the power brick). And finally, OOO.TTT once more: that Linksys is powered by 5VDC, so could conceivably be powered via one of the USB ports of the MBP, just needs a spare power plug and some soldering effort.

---

### Post by TedPacyga on 2008-07-09
Thank you for all of that information.  I have some more questions after reading that.

1)  Why would there be an option to upgrade to 4GB RAM on the Apple website if OS X doesn't support it?  I'm guessing it's for people that use Windows or what?

2)  One reason I would want the 2.5 GHz one though is because you get a 512 MB card instead of only a 256 MB card, I'm trying to quit gaming and get more into learning to program and make software and stuff, but I don't know what will happen while I am at college, so I don't know if I would want to play some games.  I have to think about that more.

3)  Which Kensington cable and lock do you use, this one looks good to me, but people said bad things about it:
[http://store.apple.com/us/product/T7229LL/A?mco=MTIxODk3Mw](http://store.apple.com/us/product/T7229LL/A?mco=MTIxODk3Mw)

4)Yeah I was going to that with the RAM, you save like 100 bucks at least.

Thanks again for the help guys.

---

### Post by hajk on 2008-07-09
> **TedPacyga said:**
> 

1)  Why would there be an option to upgrade to 4GB RAM on the Apple website if OS X doesn't support it?  I'm guessing it's for people that use Windows or what?Rumour has it that the next version of Mac OS X (Snowleopard?) has full use of that much memory.> 2)  One reason I would want the 2.5 GHz one though is because you get a 512 MB card instead of only a 256 MB card, I'm trying to quit gaming and get more into learning to program and make software and stuff, but I don't know what will happen while I am at college, so I don't know if I would want to play some games.  I have to think about that more.I guess you mean videoRAM, that's true, still you'ld probably be better off investing in a Playstation or some such with a bunch of buddies...> 3)  Which Kensington cable and lock do you use, this one looks good to me, but people said bad things about it....It doesn't really matter, does it? It should at least *look* solid, so as to dissuade the casual thief.> 4)Yeah I was going to that with the RAM, you save like 100 bucks at least.Now you're already talking like a business major...

---

### Post by cyberdork33 on 2008-07-09
> **hajk said:**
> Rumour has it that the next version of Mac OS X (Snowleopard?) has full use of that much memory.
I thought the RAM limit was already fixed?

---

### Post by Phjil on 2008-07-09
I'll throw in on this one as a long time Mac user.

Don't upgrade RAM at the Apple Store. It seems to me that Apple either a) Get their RAM from the RAM angels, delivered to the factory by winged creatures carrying the memory sticks on crushed silk cushions, and fitted by oiled maidens, or b) they think of a number and double and add a bit on for good measure.

After market RAM is considerably cheaper and a doddle to fit. Go with the standard configuration and DIY. It's the way forward.

That was it. End!

And don't believe everything you read on the Apple site. My Macbook can officially take 2GB of RAM. I've got 3GB in here and it uses it all just fine - handy for photoshop and the like.

---

### Post by TedPacyga on 2008-07-09
> I guess you mean videoRAM, that's true, still you'ld probably be better off investing in a Playstation or some such with a bunch of buddies...

Wtf?

Well I am going to go to an apple store right now to check out the laptop, and see if I want glossy or matte.

---

### Post by Vegabondsx on 2008-07-10
As a long time Apple user, here are a few of my suggestions and comments on earlier remarks:

1) OS X can handle 4gb of RAM provided you are on a 64-bit machine, which all the new ones are. Because of the Chipsets in many of the Macs, only 3GB may be utilized in the MBPs. (For now)

2) Ubuntu should run just fine, although a few tweaks will need to be made (not any different than any other computer) You could even use bootcamp to install, just use Ubuntu instead of Windows.

3) Don't buy RAM from Apple. They overprice their RAM. You can use any standard PC RAM from NewEgg or any other store and save a lot of money. Back when I bought my Macbook Pro two years ago you could actually downgrade from a single 1gb DDR2 chip to two 512mb DDR2 chips. I did that and bought a 1gb DDR chip for less than $100 (can't remember the price). I ended up with 1.5gb of RAM and saved about $150 from Apple's upgrade plan. Now you can get 1gb of RAM for $15 and 2gb for $35. Do that.

4)The next version of Leopard is Snow Leopard which will be more of a more minor upgrade focusing on performance and other features "under the hood." Snowleopard will recognize up to 16TB of RAM.

5) I'd recommend getting the Mid-range Macbook Pro. As mentioned before they have the more powerful videocard, which can not be upgraded. In my opinion it's worth getting.

6) Glossy vs Matte is all up to personal preference. There is always an ongoing discussion on this. Glossy tends to have a greater contrast and richer colors, but more glare and can be sometimes harder to color-sync with other devices. The best thing I can suggest is to goto the store and look for your self. I can say two things though about Apple's glossy screen. One, they aren't NEARLY as glossy as the ones found on some laptops, particularly HP ones. This is a good thing, in my opinion. Two, in my opinion there is a noticeable quality difference between the Macbook's glossy screen (the only screen it can have) and the Macbook Pro's glossy screen. The colors and contrast seem much better on the Pro's to me.

7) The Macbook Pros make decent gaming machines. Mine has a Core Duo and an x1600, and while that's no longer that great for playing some of the newer games, it's still decent considering it's two years old and the only thing that has been upgraded has been the RAM. I'd love to have an C2D and 8600. I wouldn't play games on your lap though, as a poster seemed to suggest. The Macbook Pros get hot. It seems they use parts of the case as heatsyncs.

Good Luck!

---

### Post by cyberdork33 on 2008-07-10
> **TedPacyga said:**
> Wtf?
He was saying that if you wanted to game, then you ought to invest in a console.

---


---
title: "IBM Thinkpad X23 (or laptops in general) - known issues with Ubuntu?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by rikc on 2007-03-28
I'm looking to buy a laptop for writing and basic internet browsing, and I'd like to install 6.10 on it.  Because I don't need something very powerful (and because I do not want to spend very much money), I am looking at an IBM Thinkpad X23.  I hear that IBMs are supposed to run linux well, but are there any issues I should know about before making this purchase?  I'm mostly concerned about connecting to WiFi.  The package I'm looking at comes with an Airlink 802.11G USB adapter.  I have limited experience with Ubuntu on this computer, and I haven't worked with any kind of peripherals.  Any advice or tips on what to look out for?

---

### Post by oilchangeguy on 2007-03-28
i suggest you try a google search with your lap tops model and the word ubuntu in the search line. and see what you come up with.

---

### Post by compmodder26 on 2007-03-28
Couldn't tell you about the Airlink adapter, but I'm running Ubuntu on a T60.  Everything has worked out of the box for me except the fingerprint scanner (very easy to set up afterwards though), and the hard drive active protection system (hdaps requires a custom kernel and I really don't want to bother with that, I'm just extra careful not to drop my lappy :)).  My T60 uses an intel 3945ABG adapter and it is supported out of the box.  Again, not sure how well supported the airlink card is, but I would highly recommend anything with the intel cards.

edit: forgot to mention that I have been using Dapper through Feisty with this laptop.

---

### Post by rikc on 2007-03-29
> **oilchangeguy said:**
> i suggest you try a google search with your lap tops model and the word ubuntu in the search line. and see what you come up with.

I did that.  I got [this page](http://www.linux-on-laptops.com/ibm.html), but did not see any information on ubuntu for the model I am purchasing.  Then I made this thread.

---

### Post by Daniel Rehm on 2007-03-31
> **oilchangeguy said:**
> i suggest you try a google search with your lap tops model and the word ubuntu in the search line. and see what you come up with.I'm not sure what that would help since his l concern here is with the wireless adapter, not the laptop itself.

Rikc - it looks like at least some of the Airlink adapters work using ndiswrapper. Without knowing the exact model number, I can't tell for certain... but, worst case scenario you might look into other wireless adapters that are known to "just work" under ubuntu (ie non-broadcom chipsets).

---

### Post by coffeeplease on 2007-03-31
> **compmodder26 said:**
> Couldn't tell you about the Airlink adapter, but I'm running Ubuntu on a T60.  Everything has worked out of the box for me except the fingerprint scanner (very easy to set up afterwards though), and the hard drive active protection system (hdaps requires a custom kernel and I really don't want to bother with that, I'm just extra careful not to drop my lappy :)).  My T60 uses an intel 3945ABG adapter and it is supported out of the box.  Again, not sure how well supported the airlink card is, but I would highly recommend anything with the intel cards.

I've been eying the T60. How has hibernate worked for you? I'm getting mixed reviews through google. Do you have a T60 with intel based graphics?

---

### Post by chili555 on 2007-03-31
I run Edgy on my T60 (ATI graphics) and Feisty on my T23. Sent a cosmetically-challenged T23 to my sister (MeeMaw on these forums) pre-loaded with Edgy. Have not had the slightest difficulty with any of them. 

I have not tweaked suspend/hibernate/cryo-freeze/etc. because I am plugged in 80% of the time.

You might also look here: [http://www.thinkwiki.org/wiki/Category:X23](http://www.thinkwiki.org/wiki/Category:X23)

---

### Post by rikc on 2007-04-01
Okay, I just won the auction for my X23, and it should be here by the end of the week.  I was thinking that in an effort to improve my familiarity with Ubuntu as well as kind of 'give back' to the community, I want to write a log of my installation for [this site]("http://www.linux-on-laptops.com/ibm.html"), which was the first result I found when googling for "IBM thinkpad x23 ubuntu" (now this thread shows up as the first result).  I'm not sure how useful it would be, being such an old laptop and all, but you never know!  My question is, is there anything in particular I should keep track of that is not listed on the site's [template]("http://www.linux-on-laptops.com/submitsample.html")?  I have a good friend who is willing to help me with this, but I figured it couldn't hurt to ask here.

edit: thanks for that wiki link, chili555

---

### Post by rac56 on 2007-04-01
I'm running Edgy on a T23 and it works great.  Suspend works fine and the function and volume keys work as they should.  Performance is excellent.  I have it maxed out with 1gb memory, I am sure that helps in the performance department.  I bought it with a no-name wireless card ("Atmel" it says in Device Manager), and that worked right out of the chute with the native linux drivers.  Hopefully you'll have similar good luck with your setup.

---

### Post by majormajor on 2008-01-10
Hi rickc! I have the same machine. I'm curious if you have suspend problems too.

---

### Post by MeeMaw on 2008-02-10
> **chili555 said:**
> I run Edgy on my T60 (ATI graphics) and Feisty on my T23. Sent a cosmetically-challenged T23 to my sister (MeeMaw on these forums) pre-loaded with Edgy. Have not had the slightest difficulty with any of them. 

I have not tweaked suspend/hibernate/cryo-freeze/etc. because I am plugged in 80% of the time.

You might also look here: [http://www.thinkwiki.org/wiki/Category:X23](http://www.thinkwiki.org/wiki/Category:X23)

and I upgraded my T23 to Feisty from Edgy - no problems! (Well, _I_ am a problem but no problems with Edgy or Feisty. :) )
Enjoy!!!

---


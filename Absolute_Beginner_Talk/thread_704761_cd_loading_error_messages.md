---
title: "cd loading error messages"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by wirelessom on 2008-02-22
Hello,
I am attempting to load "Feisty Dawn"  version 7.04 onto an HP Pavilion laptop. Its a couple of months old and running Vista. Thats why I want to move to Ubuntu. It has the AMD 64 dual processor. I am trying to run the 32 bit version of Feisty Dawn. I seem to have a good burn on the Cd as it loads up fine in an older computer running Windows 2000.
However, on this laptop I get a series of error message after successfully loading a number of components from the cd. All of the errors end with "bcm43xx Microcode5.PW" followed by "not available or failed. Some of the erros are: 155.9120001, 169.9760001, 193.2000001, 218.0280001, 242.8520001, 267.6760001, 292.1440001. 692.9160001, 765.0160001, 888.5160001

What is going on here please.

wirelessom

---

### Post by Crooksey on 2008-02-22
Have you left it loading for a while, because sometimes it will skip the errors and continue to load.

---

### Post by wirelessom on 2008-02-22
Thanks for the quick reply!
I let it try to load for about ten minutes. Is that long enough?

---

### Post by JoshuaRL on 2008-02-22
First of all, welcom to Ubuntu!  And I love when you said this:
> **wirelessom said:**
> Its a couple of months old and running Vista. Thats why I want to move to Ubuntu.
Nice.

Otherwise, I have an explanation for the errors and a few suggestions for you.

First, the errors.  Your hp laptop has the Broadcom micro-wifi with the "bcm43xx" chipset.  Ubuntu can't automatically install and configure the driver for Broadcom chipsets because there aren't any.  Broadcom decided to not make one, and to not release specs so others could make one.  But there's a linux app named Ndiswrapper that will allow you to take windows drivers and run them in Ubuntu.  So it might take a little setup, but you should be able to get wifi working just fine.

Now, i have a few suggestions for you.  First, as you say, you have a 64bit AMD processor.  I have one too, and I would suggest running the 64bit edition.  There are a couple problems you will find in the 64bit edition, but no more than you would find in the 32bit.  And you can be assured that you're running the right version for your processor.

Also, I was wondering why you were running Feisty.  Is is something specific, or just want a stable release?  Because by now Feisty is almost a year old, and almost all the issues with Gutsy have been fixed.  It's a well-featured release and I think you'll like it.

---

### Post by JoshuaRL on 2008-02-22
> **wirelessom said:**
> Thanks for the quick reply!
I let it try to load for about ten minutes. Is that long enough?

Are you using the Live CD or the Alternate CD?

And yes, you should be able to just wait through those errors.

---

### Post by wirelessom on 2008-02-22
Thanks JoshuaRL
Sorry about being slow replying, but just got a  "new" old dog and she is insisting on some attention.
It is a "live" cd. 
Fiesty because I had same problem with another version of Ubuntu. I just want one or the other to load into the laptop and until I get familar with it, don't really care which veLrsion. Got to be better than Vista.
"32" bit becaquse in searching the forums, I had read some were having better luck with it over the "64".
I will try that solution you suggested regarding support for the wireless. But I am not sure how to get that intergrated into the "load up" so it can be used.
Wireless

---

### Post by JoshuaRL on 2008-02-22
No problem wireless, got a "new" old dog myself so I understand.

Why you had the same issue with Gutsy is because of the wireless card.

I know that a lot of people that don't know better say that 64bit is a lot worse.  I run 64bit and have had only a couple issues that I could trace back to it being 64bit instead of 32bit.  And those were pretty minor to fix.  So I would always suggest you use 64bit, it will help spur the transition we're all gonna make anyway.

See if the installation can get all the way through those errors.  It should eventually go through, then use [this how-to](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28gutsy%29%7C%28bcm43xx%29) to fix wireless for you.

---

### Post by wirelessom on 2008-02-22
Thanks again JoshuaRL,
Got that link marked. And will give it a try .
How do I get back to you for a follow up if needed? Just search for this thread and post a "reply"?

---

### Post by JoshuaRL on 2008-02-22
Well, you can go up to the top with the menu Thread Tools and Subscribe to this Thread.  Then when you want to come back to it just go to the top again under User CP (Control Panel) and open Subscribed Threads.

Or you can PM me if you see im online.  But I would suggest you post threads instead since that will allow anyone else with the same problem to search for it and find answers.

---


---
title: "Put more into ensuring the Live CD Boots"
date: 2007-04-12
forum: Beginner Team
---

### Post by phr0ze on 2007-04-12
I know this must be a big deal, but I have at least 4 recent incidents where others could not get into the Live CD on any widely varied system.

1 of these incidents sent the user to Fedora, which he said booted right up.
Another I have tried to solve on several occasions for a friend and to this day, I can't get his system to boot into X.
And the other 2 just lost interest.

Now I didn't have problems with the Live CD on my system, but really the Live CD is an important first impression. I feel more should be put toward making this more robust. For me the last 4 out of 5 people I recommended Ubuntu to could not get it to work. That just doesn't seem like a good indication.

Thanks. Don't move this, I'm not looking for help. Just suggesting something to make Ubuntu easier for beginners.

---

### Post by igknighted on 2007-04-13
> **phr0ze said:**
> I know this must be a big deal, but I have at least 4 recent incidents where others could not get into the Live CD on any widely varied system.

1 of these incidents sent the user to Fedora, which he said booted right up.
Another I have tried to solve on several occasions for a friend and to this day, I can't get his system to boot into X.
And the other 2 just lost interest.

Now I didn't have problems with the Live CD on my system, but really the Live CD is an important first impression. I feel more should be put toward making this more robust. For me the last 4 out of 5 people I recommended Ubuntu to could not get it to work. That just doesn't seem like a good indication.

Thanks. Don't move this, I'm not looking for help. Just suggesting something to make Ubuntu easier for beginners.

This is the kind of thing that needs to go into a bug report... our job is just support, and maily here on the forum.  We are not developers or anything like that.  I would suggest making a bug report of each of the cases and the hardware involved so the devs know what systems it isn't working on and can focus on that.

---

### Post by phr0ze on 2007-04-13
The goals of the Beginning Team is to assist new users to :

1 Evaluate Ubuntu to see if it will fit their needs.

2 Obtain and boot Ubuntu.

3 Install Ubuntu.

4 Transition into Ubuntu.

5 Become members of the Ubuntu community.


I feel a consistently working Live CD is key for parts 1,2,3,4, and 5 above. I have the ability to get a little more info about 2 of the 4 systems which I will try to submit to the place suggested. However, I wasn't here to solve my problems. I'm here to offer some advice for keeping beginners around. It seemed strange to me that such a high percentage of systems could not boot the CD.

It embarrasses me to hand a CD to someone and recommend they try it, when they come back and say it won't even boot. Maybe this is just too broad of a statement which has no resonable approach besides case-by-case.

---

### Post by igknighted on 2007-04-13
> **phr0ze said:**
> The goals of the Beginning Team is to assist new users to :

1 Evaluate Ubuntu to see if it will fit their needs.

2 Obtain and boot Ubuntu.

3 Install Ubuntu.

4 Transition into Ubuntu.

5 Become members of the Ubuntu community.


I feel a consistently working Live CD is key for parts 1,2,3,4, and 5 above. I have the ability to get a little more info about 2 of the 4 systems which I will try to submit to the place suggested. However, I wasn't here to solve my problems. I'm here to offer some advice for keeping beginners around. It seemed strange to me that such a high percentage of systems could not boot the CD.

It embarrasses me to hand a CD to someone and recommend they try it, when they come back and say it won't even boot. Maybe this is just too broad of a statement which has no resonable approach besides case-by-case.

I don't want to sound like we are "shirking responsibility" or anything, but we are doing 1-5 on whatever product already exists.  Our bug reports don't count any more than yours, and we are not devs, we cannot code the fixes.  So while yes, I agree that a more reliable liveCD boot would be awesome, theres really nothing we can do other than give out work-arounds if they exist.  If you need a live CD to show around, try either Knoppix or Sabayon (3.2 mini, DVD is OK too, but video detection fell off in 3.3, so get the 3.2/3.26 version).  Sabayon especially.  It has what is probably the best video detection in linux, and has the proprietary drivers installed to boot... and it can run beryl from the live CD, so it's an impressive show.  I never found a card I couldn't run Sabayon 3.2 on (except perhaps an nvidia 8800, as there was no linux support until the very latest driver).

---

### Post by dptxp on 2007-04-14
> **igknighted said:**
> I don't want to sound like we are "shirking responsibility" or anything, but we are doing 1-5 on whatever product already exists.  Our bug reports don't count any more than yours, and we are not devs, we cannot code the fixes.  So while yes, I agree that a more reliable liveCD boot would be awesome, theres really nothing we can do other than give out work-arounds if they exist.  If you need a live CD to show around, try either Knoppix or Sabayon (3.2 mini, DVD is OK too, but video detection fell off in 3.3, so get the 3.2/3.26 version).  Sabayon especially.  It has what is probably the best video detection in linux, and has the proprietary drivers installed to boot... and it can run beryl from the live CD, so it's an impressive show.  I never found a card I couldn't run Sabayon 3.2 on (except perhaps an nvidia 8800, as there was no linux support until the very latest driver).

Agreed that the beginners team can not change the code and alter Ubuntu. But there surely are known solutions to many known problems. Unless the problem has no solution at present, it may not be really advisable to demonstrate Sabayon (Even perhaps SimplyMepis or FreeSpire) in place of Ubuntu.

All that is needed in documentation are listing of known problems and the solutions that exist for some of these problems. It looks odd when we try to demo something without knowing the chances of it even running live.

---

### Post by bodhi.zazen on 2007-04-14
> **phr0ze said:**
> I feel a consistently working Live CD is key for parts 1,2,3,4, and 5 above. I have the ability to get a little more info about 2 of the 4 systems which I will try to submit to the place suggested. However, I wasn't here to solve my problems. I'm here to offer some advice for keeping beginners around. It seemed strange to me that such a high percentage of systems could not boot the CD.

It embarrasses me to hand a CD to someone and recommend they try it, when they come back and say it won't even boot. Maybe this is just too broad of a statement which has no resonable approach besides case-by-case.
I agree with you to some extent. and IMO hardware recognition if fairly good with Ubuntu.

With that said, however, there are some things that also seem obvious to me. One is that one needs to check hardware compatibility before diving into a new operating system. Many hardware manufactures do not provide Linux drivers, and some that do are proprietary, meaning you, the end user will need to download and install the drivers.

Although providing live CD's can be effective for introducing Linux, the live CD may fail for any number of reasons.

The Beginners Team can help with some of these, for example modifying the BIOS to enable booting from CD. We are not developers of the Ubuntu code, however, and so can not modify the CD itself. The proper proceedure is to file &#8220;bug report&#8221; via launchpad to communicate with the Ubuntu developers. However, Hardware manufactures are beyond Uubntu altogether and for that you would need to bring the issuer up with the manufacturer. If the hardware manufacturer is unwilling to support your hardware, then it would fall to Linux kernel development which is yet another team.

Without further information on the problem(s) it is hard to guide you. We will help you if we can, and refer you on if it is beyond our capabilities.

FYI you can always try somethig like DSL which has excellent hardware recognition.

---

### Post by TwistesdTexan on 2007-04-14
I agree that the devs need to do something with the live CD. I haven't been able to use a live CD since Breezy Badger. All my upgrades were live upgrades. I know there are several people that tell you not to do this but sometimes you have no choice. To every rule there is always an exception.
Edit: I now have the Feisty Fawn installed. I was a beta tester also. I downloaded the DVD version and am able to boot and run the live disk.Ya Hoo. Things are looking up. Thanks to the developers.

---


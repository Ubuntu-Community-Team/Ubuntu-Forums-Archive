---
title: "Can't add/remove applications (list of applications not available wtf?)"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Seriphyn on 2007-10-18
I have been a Ubuntu user since 6.10 and I just installed 7.10 and bumped into problems.

I can't add ANY packages on Add/Remove Applications because it says "The list of applications is not available". So I press reload. It reloads. I click on one of the boxes again, and it comes up with that message again.

Help? Thanks.

---

### Post by Seriphyn on 2007-10-18
bump

---

### Post by shredwheat on 2007-10-18
This may be related to the load on the network servers today, but I don't think they are related.

For now you should be ok installing applications with the Synaptic package manager. It's more powerful, but that makes it harder to use for quick jobs than the Add/Remove. You'll find it under *System->Administration->Synaptic Package Manager*

---

### Post by siege911 on 2007-10-18
I'm getting the same error.

I'm also showing this message on every program that is not already installed on my computer:

> Canonical Ltd. provides technical support and security updates for Adept Manager
Adept Manager cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

Is this just because it's version 7.10 and the software hasn't been updated to work with it or what?

---

### Post by siege911 on 2007-10-19
When you are in Add/Remove go to Preferences. Make sure it's setup to download from the internet. This is what made mine start working.

---

### Post by philinux on 2007-10-19
Dont forget that during the install it disabled some sources in sources.list.

You may have to enable some repo's again

---

### Post by rustybronco on 2007-10-19
applications>add/remove>preferences... and select the desired sources.

---

### Post by vietunion on 2007-10-23
Work great, thanks advance :D

---

### Post by dwf_starband on 2007-10-24
Thanks I had the same problem.  My Internet was down when I installed and the install stalled for a while while doing something with apt-get then said something about not using the network or something like that.  Your solution worked for me now that my internet is up again.

Thanks,

dennis

---

### Post by mirontoli on 2007-10-30
> **rustybronco said:**
> applications>add/remove>preferences... and select the desired sources.

Thank you very much. This helped me too. I'm wondering why the sources are not "on" as default, as they were in Ubuntu 7.04?

---

### Post by nielsrune on 2007-11-03
I had this problem too. Thanks !

---

### Post by Zane217 on 2007-11-04
helped me too   thanks  

this was actually a hard topic to find a solution to in the forums,  I would think more people would have this problem.

Thanks again
Gary

---

### Post by Tom6190 on 2007-11-07
Helped me too. Thanks a lot.

---

### Post by Neodudeman on 2007-12-11
Awesome, thanks, this helped me a lot as well.

What's interesting is that, when it gives the error, it says "The list of applications is not availabe" misspelling "available." However, googles of "The list of applications is not availabe" don't turn up much.

---

### Post by daithi86 on 2007-12-19
this tip helped me as well. couldn't get the gstreamer codec pack installed due to this issue. i also had no network connectivity during install and had to tell synaptic to use internet for package downloads. thanks for the help.

---

### Post by GayRockies on 2008-01-22
Thanks!

This helped me too.  Interesting thing is that when you search for "List of applications not availabe" (or with the missing "l"), you don't find this thread.  The only way I found this thread was by trying to post another.

The reason I had this problem is that when I installed, I didn't want to try to find a network cable for my laptop, and the wireless network (WEP) key was on a flash drive Ubuntu couldn't read during install...  Anyway, turned out the only repository enabled was the CD-Rom (which of course I took out of the drive).

Thanks for the help.  I've been using Ubuntu since Dapper, and I'm quite pleased, though it has not quite replaced Windows on all of my machines.  That's the beauty of dual-boot - the right tool for everything, then Windows for the few things that tool can't do yet!

---

### Post by eth0hNoes on 2008-02-23
> **siege911 said:**
> When you are in Add/Remove go to Preferences. Make sure it's setup to download from the internet. This is what made mine start working.

I'm having the a similar problem. This didn't fix mine, but I did discover that under preferences, everything was unchecked. I checked them all and it appears to be working now.

I believe this happened because when I installed Ubuntu I didn't have an internet connection so Ubuntu just disabled them all.

Yep, it's working now. It was telling me my computer was up to date and now I have 188 updates. Saved me from reinstalling.

Thanks guys.

---

### Post by alez911 on 2008-03-06
> **rustybronco said:**
> applications>add/remove>preferences... and select the desired sources.

Thank you !!!

---


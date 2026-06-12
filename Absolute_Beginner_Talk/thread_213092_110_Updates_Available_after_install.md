---
title: "110 Updates Available after install"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-07-10
Got the install done and it works perfectly.  It even figured out my Linksys WPC11 wireless card.  I'm so happy with the result I'm a bit gun-shy about installing all those updates.  Most are not things I recognize.  Any advice?  Is there a risk of de-configuring something, or mucking up my system?
Has anyone else installed all the updates right after installation?
(Ubuntu 6.06 LTS)
Moshup Trail

---

### Post by John.Michael.Kane on 2006-07-10
I have installed all updates on a fresh install with out issue. you should have no issues. however nothing is perfect it.

---

### Post by Sonofmoog on 2006-07-10
Installing updates is seldom a problem, and often a boon.  One of the first things I do after installing a new system is to add the updates .. and the programs I want that weren't installed from the CD.  If you're new to Linux, I'd recommend installing all securitry updates as soon as you're notified.  Everything else you can install when you feel the need ..

---

### Post by kd7swh on 2006-07-10
You can always go back. I would just download the updates.

---

### Post by moshuptrail on 2006-07-10
I took you advice and installed the whole lot.
No problems.  Everything went smoothly and works fine afterwards.
I am so impressed!  Other distribs are not so solid.  Most dont even have an automated update feature.
M T

---

### Post by DigitalXpert on 2006-07-10
The only update I'd watch out for is kernel updates.  I've had situations where a newer kernel couldn't detect all of my hardware.  But go ahead and do it.  You can always boot off of your previous kernel version and get right back to normal.

As a rule of thumb, always have a previous kernel installed. Never assume the newest is always better.

Hopefully you set up a seperate partition for /home.  Thats the safest thing to do.  Then if some updates hose yer system you can just reinstall ubuntu and all your personal settings and files are safe.

---

### Post by moshuptrail on 2006-07-11
So when I boot, I see a list of kernels.  Is that the previous version that you are talking about?  I have noticed there is a kernel and the same one listed with *safe mode*.  What's that?
(and yes, I did create a separate partition for /home)

---

### Post by DavidFL on 2006-07-11
> **moshuptrail said:**
> I took you advice and installed the whole lot.
No problems.  Everything went smoothly and works fine afterwards.
I am so impressed!  Other distribs are not so solid.  Most dont even have an automated update feature.
M T

Same here. I had to reinstall a windows partition and it took like 12 reboots to get 30 updates done (they make you reboot after certain updates before installign others) !  It was a major pain.  With Ubuntu I was so shocked when it did those 110 update and only asked me to reboot once at my convenience.

---

### Post by erniewinner on 2006-07-11
i've enjoyed updating my install and let the partition be bigger than when i first installed, as i got locked out when i ran out of drive space.
but... what do you do about "blah blah the file is not authenticated" i changed the repositories to "official" only as it worried me but i still see "not authenticated." mmm... what to do? :-k

---

### Post by DigitalXpert on 2006-07-11
The authentication error happens when your computer cant verify the authenticity of the repository your trying to download from.  Theres a key exchange of some type thats supposed to happen I think.  

Check the date and time on your machine.  If your date/time doesn't match the repository's then the key exchange will fail and you'll get that error.  

Correct the time and you should be good.  It happenned to me and thats how I fixed it.

---

### Post by absoludity on 2006-07-12
I've been using Dapper for a while now and never had a problem updating until today... and my time is set correctly. (Like everyone else, I'm blown away by how easy Ubuntu is to use... so satisfying!)

I'm getting the message: "You are about to install software that can't be authenticated". It only started happening today so I'm guessing it's related to these specific updates?

The updates are:
[LIST]
[*]libcupsys2 (and related)
[*]Gimp (and related)
[*]Linux image 2.6.15-26 (and related)
[*]ttf-opensymbol
[/LIST]

I'm sure i can just go and install them anyway, as they're from the official repositories, but thought it might be worth highlighting the issue as it could look bad for newbies.

Hope that helps!

---

### Post by BetaguyGZT on 2006-07-12
More often than not it's safe to install unauthenticated updates. Remember that the list that the Update Manager uses is the same list that Synaptic and Apt-Get uses, and I've never heard of any kind of spyware or virus that messes with that. Of course, look over everything that it wants to update before you download as an extra precautionary measure. You can always remove something from the list of updates if you don't trust it. ;)

---

### Post by erniewinner on 2006-07-12
well my battery is gone. but ubuntu gets its time from the net so it's always correct... i like that!

---

### Post by MonkeyNet on 2006-07-12
Your topic brings to light an interesting theory about Ubuntu updates.

I am lucky to have a broadband internet connection which means that most of the updates will come through rather quickly. However, I still know heaps of people that are still on dialup connections or base ADSL connections at only 256k.

The updates that have come through today alone are around 150mb.

For someone who is using a dialup connection is going to be extremely frustrating.

This does make things the operating system a little unattractive for some people.

Any one elses thoughts on this?

Cheers,

Andrew

---

### Post by MaximB on 2006-07-12
I think it's very good to have updated around 100mb - it's just means that the programs are developing really fast.
in winxp you got many updates too when you first install - but that in the other hand means that there are a millions of bugs in it as the winxp updates doesn't update the programs like in ubuntu (I had an openoffice updates around 50 mb , and MOST of the updates are for programs you installed but NOT ubuntu itself)winxp updates itself.

if you got a modem 56k - you are in a big problem in our days world
as thechnology develops and so are the sizes of the programs and updates.
but I think thar ppl who have 56k modem are usually work offline so I suggest them to use the live DVD so they won't need to download so many programs.

---

### Post by MonkeyNet on 2006-07-12
> **MAXDDARK said:**
> if you got a modem 56k - you are in a big problem in our days world
as thechnology develops and so are the sizes of the programs and updates.

Unfortunately in Australia, the broadband market is shocking. I run a small ISP providing broadband, and the pricing is still way too high for the average consumer. If the market was to be opened up a bit more for competition, then most people would be happy to change.

---

### Post by MaximB on 2006-07-12
> **MonkeyNet said:**
> Unfortunately in Australia, the broadband market is shocking. I run a small ISP providing broadband, and the pricing is still way too high for the average consumer. If the market was to be opened up a bit more for competition, then most people would be happy to change.

and I thought israeli internet speed is slow...
if you don't have a company you can afford only up to 2.5 download and 0.5 upload. - it's very slow compare to others and to the technology
average israeli users have 1.5 - like I do.
and we all pay every month - it doesn't depends how much you download cuz if it was so we all be broke  :)

---

### Post by dickrounds on 2006-07-12
I installed these update without a problem. However, since then when I try to get updates I receive a message which says something to the effect that I need to close one of the file managers.

I have no clue as to how to do that.

Dick Rounds

---


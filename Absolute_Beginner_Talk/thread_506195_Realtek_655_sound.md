---
title: "Realtek 655 sound"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by msfisher on 2007-07-21
I've started threads like this before, but though I've gotten some attentive responses, no one has had an answer that has worked out.  I've looked at some of the existing threads and also not found an answer that worked for me -- in some cases it looks like the person posting the question go no answer at all.  I realize this is a hardware question, but I am still a newcomer to Linux in general and Ubuntu in particular.

I've had the same problem with a whole string of distributions -- Ubuntu dapper, edgy, feisty and gutsy alpha also edgy Kubuntu and Xubuntu; Yoper; Sabayon; PC LinuxOS; Mandriva 2006 and 2007; Xandros 4; Linux Mint and Freespire.  The reason I've used so many is that I'm trying to find ANY distro that doesn't have this problem.  I'm planning on installing Fedora 7 next for the same reason.  The ONLY distro where the sound worked was Xandros 3.  I thought for certain, with its multimedia slant that Linux Mint would work, but no dice.

I have an MSI K8N Neo v 2.0 motherboard with nForce3 250 chipset BUT NOT an NVidia sound chip.  It's a Realtek 655.  Every time I've installed a distro to my hard drive the sound has not worked correctly.  It ALWAYS goes sound-sound-pause sound-sound-pause over and over until whatever the sound in question happens to be is done.  It also eats hugely into resources.  For a sound-enabled startup that means waiting until the startup sound is done before anything else can be done -- anywhere from a couple of minutes to nearly fifteen.  The same is true for mp3's and ogg's.  So the simple solution -- turning off the system sounds -- simply sidesteps one part of the problem.

Here's the real kicker (to me at least) -- the sound works from live CD's.  It also works under Win98 and, in the short while I had it installed, WinXP.

At least one earlier answer had me chase down some sound settings and it looked like the system was mis-identifying the sound as NVidia.  I found two Linux drivers from Realtek, but I'm unsure about which to install -- remember that in spite of how many distros I've tried, I'm still pretty thoroughly a newbie at Linux.

Many thanks in advance for any answers or ideas about how to solve this.

---

### Post by GMachine_24 on 2007-07-22
Hi:

At the risk of adding to your long list of failed, but noble, attempts: Which live disc worked? Was it one of the Ubuntu discs or another version of Linux? It seems to me that is your best avenue - to try to get the driver from that installation. I assume after the live install you did a full install and the sound failed from this Linux version as well (???). 

Man, I'm having my own problems here - the curson jumps around, erases words, sentences, skips up and down the page and opens new windows... you got any ideas why?

Ok, so back to your problem. I did a Net search re: your sound card and Linux but did not find much... one or two other people saying they had problems (but not with Linux) and a couple links to those driver sites . . . for better or worse.

I used a live version of Ubuntu to prove to Compaq that the sound card and speakers in this laptop (Presario R3000) work and that their drivers were the problem - kthey kept telling me I needed to buy new laptop  speakers. I told them they were crazy and went to Nvidia's page (it is an Nvidia sound chip) and found the software I needed - it has the added benefit of sporting a great graphic equalizer.

Anyway, if you have two potential drivers from Realtek, try both. If you're concerned about corrupting your OS, do a full back up before trying each one. Fortunately, with Ubuntu, a full back up doesn't take long.

I feel as if I'm at a birthday party and am blindfolded and swinging a stick, trying to hit the pinata I can't see. I hope at least something here helped.

Best of luck. (I just got my wireless to work on my laptop today after basically hacking the thing myself and, like your situation, there were literally  hundreds of posts on how to do it - none of which worked - so I'm feeling pretty smart.)

gm

p.s. if you have not tried the irc channels yet, you might try those. they're hit or miss but you might get lucky. either way, it can't hurt.

---

### Post by GMachine_24 on 2007-07-22
Ok, so I went to the Realtek site .com.tw and looked at the spec sheet. Didn't help at all. Looked at the drivers they have for Unix/Linux - they are all 2007 releases - which is sort of a miracle. I would just try the generic ones - not the ones for Red Head/FC. 

Also, you've probably been told this, but Linux is sort of notorious for having problems with sound. A couple versions ago of Ubuntu things were a real mess as I had to keep changing the system>references>sound settings depending on where I needed the sound to come from . . . and the sound STILL oesn't work on the Evolution (personal scheduler) alarms. If you haven't played with the sound settings, I'd give that a try as well. I figure you've probably already done this at least 12 dozen times but I'm racking my brain trying to think of something - like they say, all else being equal, the simplest answer is usually the correct one.

gm

---

### Post by msfisher on 2007-07-23
GMachine_24:

Thanks for the effort and the compliments.  I never thought of this as noble, just stubborn and, finally, ticked off.  BTW, I got the same result from Fedora.

As to which live CD's:  All the Ubuntus (dapper, edgy, feisty & gutsy), PC Linux OS, Fedora -- heck, basically all that are available that way.  

I went one step further than you on the Realtek drivers -- I looked inside the tarballs.  As I remember (I don't have them in front of me right now) they contained slightly old versions of the ALSA drivers.  Maybe the problem is to downgrade from the ones currently being installed.  Also, since the problem covers releases based on Gentoo, Debian and Red Hat but wasn't present in an older distro (Xandros 3), I'm wondering if something was changed at a low level regarding hardware detection.  I will, however, look into the sound settings.  Frankly, I really don't want to give up on Linux, but I'm getting damn close.  My only choice looks to be finding an old copy of, say, Mandrake 9 or 10 or old SuSE and try it.  

As to your cursor, the only times I've had my cursor get real flaky, either the battery was real low, there was a cycle-stealing, corrupt app running in the background or the driver had gotten corrupted.  One time, I never did figure it out.  Sorry I can't help you on it, but thanks for your input.  Good luck

---

### Post by jlyn on 2007-09-22
I am even a newer newby:  I looked at the Realtek site and got a referral to
[www.opensound.com](www.opensound.com) 
who is meant to be making a driver.
Does anyone know how to get it? 
Failing that, I will live in silence. . .:(

---


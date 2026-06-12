---
title: "malicious attack or coincidence"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by jhamer9 on 2005-11-21
i woke up on sunday morning ready for another day of exploring my new kubuntu system.  booted my laptop only to find errors upon startup and a failed fsck scan (originally not even sure what that was).  i wasn't able to do anything but press ctrl+d which rebooted my system just to start the process all over again or supply my root password, which i don't have as it's disabled by default in kubuntu.

the few changes and learnings i have had with this system was minimal, so i decided to just rebuild.  no big deal, it would give me a chance to re-visit what i had recently learned, with things like wireless configs, dma activation, setting up samba shares and the like.

as my system was rebuilding i switched over to my knoppmyth pvr system, just find it hung up with no kvm response.  re-booted and saw the same exact errors and process happen all over again, but lucky i was able to supply my root password and re-build the disk errors one at a time (it felt like 100 of them).  this system has been running flawlessly for about six months with no problems and very little down time.

does this sound like a coincidence, or could someone have gained access to my system.  i am very new to linux, but thought i had the necessary security measures in place.  on my home network i am running winxp, and 2 linux systems (knoppmyth and kubuntu).  am i looking to deep into a conspiracy theory or could this really be a coincidence?  and why would this happen in the first place?

after the rebuild i have since installed firestarter on both linux systems.  what other measures should i take or is there recommended reading for keeping the system up to date, secure or be able to look for any possible system breaches (besides... i know, get rid of the windows system)?

sorry for the long post.

---

### Post by Pablo_Escobar on 2005-11-22
Heh, it's hard to judge what could be the cause of this problem, maybe a hard disk failure, but that's only an assumption.
Back to security problems. Firestarter is just a frontend to the iptables (true firewall). To keep Your system secure - update with security updates once in a while when the hit the repos.
Also You can check [https://grc.com/x/ne.dll?bh0bkyd2]("https://grc.com/x/ne.dll?bh0bkyd2")
and test Your system for open ports - possible way of breaching Your system.

---

### Post by jhamer9 on 2005-11-22
Thanks for the feedback.  That's a good web site for checking open port vulnerabilities.  it looks like everything is ok.

i guess it was just some weird misshap with both drives/systems. i thought a power outage at first that may have caused corruption, but i usually have clocks blinking 12:00 after that happens.  unless it was a brown-out, but that might have made things even worse...

---

### Post by towsonu2003 on 2005-11-23
this doesn't sound to be a coincidence to me, to be honest (but then again, I'm a newbie). more like a user error? or environmental? a lightning maybe? or a bad voltage change? 

why would a hacker want to corrupt your linux systems (*both*) while there is possibility to steal info without your knowledge? though a saturday night seems a good time for a hacker to work, it's not like you're using windows (where, I suppose, hackers want to kill it while other code writers want to 'earn' money). And I don't really believe you came accross one of those rare linux viruses that escalate to root privileges (which scares me)... 

are you running servers on these systems (or is there a particular reason you let them run, paying more to electricity)? What kind of servers, if you run it? 

also, is there something you did on both systems? open a file, run a command, visit a website (going to the usual M$ Windows stuff), delete something, configure something (going to the usual linux stuff) etc?

Just brainstorming...

---

### Post by jhamer9 on 2005-11-23
well, as i'm reading about the errors i witnessed, it's user error most likely as i'm still learning the in's and out's of linux, but i don't use either system in the same way at all.

the knoppmyth pvr system isn't used for anything else but recording tv shows.  i haven't used the supplied browser with it in weeks, so i don't think it was somewhere i visited.

the kubuntu system i'm trying to use as my primary system and seeing if i can live without winxp.

as for why someone would want to hack into a linux system... well, maybe a windows fanboy or just a misguided individual...  i don't have the foggiest idea why someone would want to spend time on writing viruses either, but their out there.

and yes, i usually leave all of my systems on throughout the weekend as i never know when i'm going to want to jump on one of them at any given moment and get to work so to speak.

---


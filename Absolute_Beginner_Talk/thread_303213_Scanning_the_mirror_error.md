---
title: "Scanning the mirror error"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by jimmykuruvilla on 2006-11-19
Hi all,

   Sorry to keep making new threads, but it seems this place is so popular old ones get buried fast. 

In any case here is the situation:
I'm getting this message during the install of 6.10, at 82%:
"Configuring apt"
and "Scanning the mirror..."

The install just stops moving at this point. The rest of the live session works fine, but the install won't go any more. 

I've checked the md5 of the iso (64 bit), and I've run the install's check of itself, and both come up with no errors. 

From what I understand it looks as if the install is looking online? for some package management stuff? 

If so the issue may be related to the fact that I can only really visit google web pages in the live session. I haven't tried any other browsers than firefox, but the issue is that non-google pages just keep "waiting for website.com." Not even an error message, they just load forever. The behavior is similar to what the install does. Literally, anything google will load (images, video, groups etc.) but not anything else. Hotmail also works. 

I am running an ASUS K8S-MX mobo. It uses SiS 190 chipset for ethernet, and I've had issues with distros not recognizing it before.  

Thanks for your help, it's been very useful so far. 
~Is there any way to just disable that part of the install?~

~Jimmy

---

### Post by th0mas on 2006-11-26
same issue here :/

help !

---

### Post by Malganis on 2006-12-01
Edit: Nevermind, I just disabled my ethernet card so it just timed out and continued.

---

### Post by rajusns on 2006-12-12
Thanks. Just went to system > administration > networking and deactivated the card. It started installing further.

---

### Post by MonolithTMA on 2007-02-15
Hmmm...installing Kubuntu here. I just disabled my wireless card, but left the other one enabled, and it continued normally. Now lets see if the restart works. Trying to dual boot XP on an i386. I need sleep.

---


---
title: "Just a quick qs. about Updates"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-27
Hello everyone,
I installed Ubuntu about a week back, and today i checked its update manager. It says there are 130 updates needed with a total size of 180 Mb.
Now, i dont have a broaband connection- my dial-up is slow and very costly. My question is..are the updates really necessary? Sure, the new versions must be important...but what about the really smaller ones (going from 2.5.6.1 to 2.5.6.2....something like that). 
If in case i have to install the updates then Linux will be prohibitively expensive for me.
Is there a way i can find a place where the really critical updates are listed?

---

### Post by ciscosurfer on 2006-07-27
If your Ubuntu is on a laptop, go to a coffee shop or internet cafe (any wifi hotspot) and download that way.  Some of the updates are security related, others are simply incremental updates.  Otherwise, it might be time to get some broadband.

---

### Post by Sef on 2006-07-27
> are the updates really necessary?

Yes they are.  Security patches and updates that often help improve security.  Follow ciscosurfer's advice, if you have to pay by the minute.

---

### Post by The Noble on 2006-07-27
It really depends on what each package is. If this is your first update, this will definately be the largest. I would reccommend against updating OpenOffice.org if you are really limited, as this will save you about 30-100 meg of the download if my memory is correct. Most updates for linux are small, so this is a one time thing, basically. 

Updates aren't necessary, and if you want only the security updates, and don't realy care about the others, comment out everything but the main and security repos. In my experience, the main thing you will want to upgrade is anything that connects to the Internet (Firefox, Firestarter, GAIM, etc), and maybe the newest kernel (optional, but takes about 30 meg). The rest are up to you, as they are just filler aps, and may or may not fix bugs or add improvements.

Remember: You are using Linux, even not updated, it is going to be safer than a windows box (Edit: without antivirus/firewall), especially if you get a firewall. But don't be stupid and ignore very important updates, though!

---

### Post by kitt on 2006-07-27
> **The Noble said:**
> It really depends on what each package is. If this is your first update, this will definately be the largest. I would reccommend against updating OpenOffice.org if you are really limited, as this will save you about 30-100 meg of the download if my memory is correct. Most updates for linux are small, so this is a one time thing, basically. 

Updates aren't necessary, and if you want only the security updates, and don't realy care about the others, comment out everything but the main and security repos. In my experience, the main thing you will want to upgrade is anything that connects to the Internet (Firefox, Firestarter, GAIM, etc), and maybe the newest kernel (optional, but takes about 30 meg). The rest are up to you, as they are just filler aps, and may or may not fix bugs or add improvements.

Remember: You are using Linux, even not updated, it is going to be safer than a windows box (Edit: without antivirus/firewall), especially if you get a firewall. But don't be stupid and ignore very important updates, though!


Even with all the trimming down: it still requires some 80-100 Mb of download :-( .Not only is my dial-up slow..but gets disconnected pretty often.
Where do i get information on which are the 'critical' updates?
Also, is updating the kernel important?
And my biggest worry:
What will happen to these updates if i have to install ubuntu again ( due to some problem, etc.) Will i have to update again?? Will these updates be stored in my home folder??

---

### Post by Sef on 2006-07-27
> What will happen to these updates if i have to install ubuntu again ( due to some problem, etc.) Will i have to update again?? Will these updates be stored in my home folder??

Yes, you will have to update again.  So same problem.  It is rare that you need to reinstall Ubuntu (or Linux in general.)

---

### Post by kitt on 2006-07-27
> **Sef said:**
> Yes, you will have to update again.  So same problem.  It is rare that you need to reinstall Ubuntu (or Linux in general.)

This is very sad :-(  because what if i want to switch to a new machine?? 
Isnt there anyway of accomplishing this..?

---

### Post by The Noble on 2006-07-27
If you know how to partition quite well, or follow a guide, I believe you don't have to reinstall your Home folder, although I don't think that is where updates are stored. I guess if you did some searching, you could find where the updates are, and could put them on CDs or flash drives. 

Kernel updates, to my knowledge, are not incredibly important for security. The most important things to update are you browsers, and things that connect to the internet. If you only get applications from synaptic (or trustworthy sources), and have Firefox locked down, you would have to be EXTREMELY unlucky to get any virus. The main thing you have to look out for is rootkits (?... not sure), and even if you did get one, you would probably reinstall anyways, as it is a pain to get rid of them, to my knowledge.

My main Advice:
Backup everything you have often. If things go down south, it would be easier to reinstall. Only update what you have to: Firefox (or opera, etc). Lock your repos to only security updates (in /etc/apt/sources.list) when you update, and you are PERFECTLY SAFE from almost anything the internet can throw at you.

---

### Post by Sef on 2006-07-27
> If you know how to partition quite well, or follow a guide, I believe you don't have to reinstall your Home folder

That is correct.  You don't have to reinstall the home partition.  

> 
Kernel updates, to my knowledge, are not incredibly important for security. 

Not necessarily true.  Sometimes the kernel updates are important for security.

---

### Post by 3rdalbum on 2006-07-27
Don't bother with the updates. Most of the time, they fix rare security issues. In Synaptic, look at the changelog ("Package > Download Changelog").

For instance, I have a GIMP update pending. When I look at the changelog, it tells me that the new version comes from "dapper-security" and that it has fixed a bug whereby somebody could create an image file that executes code on somebody's computer. I've never downloaded a .xcf file and I don't imagine that I ever will, so I can safely skip the GIMP updates.

Gnupg? I don't use it. gtk2-engines-pixbuf? A rare issue with how tabs are displayed; I'll live with the problem if I ever encounter it. Mousepad? Something about language packs - I only use English so I don't need it.

So really, the majority of the updates are security and silly little things. Just run a firewall and you'll be as safe as you need to be on dialup.

---

### Post by navymom on 2006-07-27
I'm not trying to highjack the thread but these issues with dial-up brings up another point to me....if for some reason you get disconnected in the middle of an update and you've received approximately half of it already, does it start over or pick up where it left off?

---

### Post by kitt on 2006-07-27
Thanks everyone..
Now that i have many reassurances..i should stop worrying about security threats and resume playing frozen bubble ;-)

---

### Post by ciscosurfer on 2006-07-27
I understand you are on dial-up, but please consider that security updates are just that: security updates.  They are patches and the like that make your system less vulnerable to problems (exploits, trojans, etc.) and they also make that program (usually) more stable.  If at all possible, download the security updates.  You can accomplish this by commenting out your sources.list or by using System > Administration > Software Properties.  

And just because you don't personally use a program doesn't mean you are any more immune to a security threat.  If it's on your system, and not patched, you're vulnerable to all kinds of attacks that exploit the previous code.  But hey, I'm only a Security Administrator :shock:

---


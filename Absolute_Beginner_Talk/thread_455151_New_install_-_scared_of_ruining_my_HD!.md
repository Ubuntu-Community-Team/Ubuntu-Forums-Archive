---
title: "New install - scared of ruining my HD!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by durfff on 2007-05-26
Hey all, 

Firstly sorry for posting if I'm not meant to, but I ran into some problems last time I tried to install and i'd rather not experience all that again...

I want to install ubunto 6.10 on the same hard drive as my windows xp, it's a 40GB maxtor. I've read all the install guides and how-to's as well as some tips to dual-boot... But I'm still scared of ruining my MBR, cos about 3 months ago I tried to install ubuntu server edition to dual boot with windows xp and it f*%ked the MBR to the point where I had to zero out my hard drive... GRUB error 17 and all that...

Really I just need some encouragement/confirmation that installing the normal way will happen right with 6.10 desktop. I've downloaded the dekstop live cd and I'm ready to boot and install, I'm gonna try to partition using gparted before install...

Anything I should bear in mind or consider before doing so? Any tips on what could go wrong and how I can overcome that?

Cheers to all, I'm looking forward to being part of the Ubuntu community!!!

Fred

---

### Post by starcraft.man on 2007-05-26
This is my favourite [guide]("http://www.psychocats.net/ubuntu/installing") to point people to who hesitate. It should show you everything on the live CD.

Partitioning isn't so scary. Do make sure to back up vital information. Other than that don't worry.

I don't know what your original problem was, but you don't need to zero the drive if you have a problem with MBR. This is my favourite recovery bootloader. Its called [GAG,]("http://gag.sourceforge.net/") it can boot anything in the world I think, download and burn it to a disk, if you have trouble with the MBR then boot to this and let it detect and install itself as the bootloader, should work. You can always then restore GRUB from within Ubuntu.

Thats it, have fun :). Oh and we look forward to having you part of the community :D.

Edit: Oh ya, I agree with pbw, if you can get feisty installed, you'll probably prefer to have it. Up to you though, Edgy is still perfectly functional and supported.

---

### Post by pbw on 2007-05-26
Using 7.04 rather than 6.10 would be my first suggestion. 6.10 isnt LTS nor the current release.

And dont worry, it'll go smooth i'm sure. A grub error isn't much to worry about if you've got a livecd in your pocket ;). Something like that happens, just pop it in your drive and do a quick forum search, or post back and you'll be fixed up in moments :)

-- pbw

---

### Post by cymen on 2007-05-26
Yep, just follow a very clear guide and have faith! It sounds like you're doing all the right things anyway, so we'll see you on the other side. :D

---

### Post by Dzenhax on 2007-05-26
Fred,

     I've done this and redone this.  It should work fine, but please, please do a backup.  If you don't have an external, borrow one.  You can delete the backup once it's done.  Ubuntu is great, but sometimes disks scratch, hard drives get bumped, etc.  Have a plan b.  The windows backup utility works great (only for windows) or try clonezilla ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) )

     You've done your research.  Go for it.  I bet you'll wean off windows within a year.

Congrats

P.S. The server distro is not a thing a newbie should try.

---

### Post by starcraft.man on 2007-05-26
> **cymen said:**
> Yep, just follow a very clear guide and have faith! It sounds like you're doing all the right things anyway, so we'll see you on the other **side.** :D

The DARK SIDE that is :D *evil music plays* MWAHAHAhahahah *cough hack weez* geez, got to work on my evil laugh. Kids are gonna laugh at me...

---

### Post by drowner on 2007-05-26
> **durfff said:**
> Hey all, 

Firstly sorry for posting if I'm not meant to, but I ran into some problems last time I tried to install and i'd rather not experience all that again...

I want to install ubunto 6.10 on the same hard drive as my windows xp, it's a 40GB maxtor. I've read all the install guides and how-to's as well as some tips to dual-boot... But I'm still scared of ruining my MBR, cos about 3 months ago I tried to install ubuntu server edition to dual boot with windows xp and it f*%ked the MBR to the point where I had to zero out my hard drive... GRUB error 17 and all that...

Really I just need some encouragement/confirmation that installing the normal way will happen right with 6.10 desktop. I've downloaded the dekstop live cd and I'm ready to boot and install, I'm gonna try to partition using gparted before install...

Anything I should bear in mind or consider before doing so? Any tips on what could go wrong and how I can overcome that?

Cheers to all, I'm looking forward to being part of the Ubuntu community!!!

Fred

Welcome!

You just gotta look out during the installation process... after you partition, but before ubuntu installs your videocard drivers it makes your computer catch fire.












I'm just kidding, you'll be fine ;)

---

### Post by durfff on 2007-05-26
Wow! Thanks so much for all the lightning-fast replies!!!!

Right, quick explanation for the choice of 6.10 rahter than 7.04: I have an ATI Radeon 9200SE graphics card and it doesn't seem to be supported after 6.10, and as I've not used Ubuntu before and from what I've read in various forums, it might be quite a challenge to get it to work under 7.04... So I guess until I can buy myself some new hardware, I'll stick to that! But that should be soon, the reason why I wanted to try Ubuntu in the first place is because windows is doing my head in, and I wouldn't mind something more stable on my soon-to-come new machine... So when I get it I'm sure I'll go for 7.04 (and I've already downloaded the iso for that :D)

Oh, and the reason why I had to zero out my disk was becasue, well, I don't have ANY other computer at hand, no other internet connection (apart from my mobile phone lol), and the only tool I had at hand was my hard drive disk... tried-everything-got-upset-couldn't-get-more-tools-zeroed-out. Haha

Well now I've got xp back up and running and my iso is md5sum checked and burnt... Ready to go.

I'll let you know how I get on!

Cheers again!

Fred

---

### Post by drowner on 2007-05-26
Oh, and keep a bucket of water handy.

You'll thank me when it happens.










(im just kidding again)

---

### Post by starcraft.man on 2007-05-26
> **durfff said:**
> So I guess until I can buy myself some new hardware, I'll stick to that! But that should be soon, the reason why I wanted to try Ubuntu in the first place is because windows is doing my head in, and I wouldn't mind something more stable on my soon-to-come new machine... So when I get it I'm sure I'll go for 7.04 (and I've already downloaded the iso for 

Remember to pick up a machine with an nvidia card, they have best support (and if you want wireless, try to avoid linksys, its a pain to set broadcom cards up). That should be it. We support almost everything else easily out of box or via small tweaks :).

Hope it goes well.

---

### Post by durfff on 2007-05-26
Haha!

Well I'm on the dark side now. Was well worried that GRUB wouldn't perform for some reason, but I shall trust linux software from now on :) -> perfect boot options, windows still working fine (well as far as windows works lol) and I've been playing around in ubuntu for a while now, it's great. 

Only thing I still need to do to be completely operational and lower the rate of my postings on this forum: connect to the internet. I have 2 options: a USB dongle on one hand (D-LINK DWL-G122 revision C1) or a wireless PCI card (Gigabyte GN-WP01GT). Thankfully I still have windows running so I can access the 'net and find info, and I've read somewhere that the Gigabyte GN-WP01GS works out of the box in Ubuntu, so chances are the ~T will as well...

Lol I just really want to watch some episodes of lost on Ubuntu, I've got the last 2 that I've not seen yet and watching them on 'buntu would be a great thing :)

Thanks for all the help and support, if I can help anyone in any way I'll get on the case (doubt it but hey, you might want to learn about playing guitar or training dogs some day - I'm not bad at them things ha :D)

Fred

---

### Post by starcraft.man on 2007-05-26
Yay, glad to have you on the dark side. I'm happy you found everything working great. I uh, haven't used either of those cards, I connect via a plain ethernet line (its my lifeline to reprogram my router and modem) so I can't offer any specific help, except search for NDISwrapper on the forums and google. Hope ya get it working great :).

PS: You don't have to post less once you get set up, I've been perfectly set up for over a few months >.>. You can help other people, talk in cafe and find new tricks/hacks to customize linux. And never say you can't help new people, I wouldn't be helping people today if I hadn't started when I didn't know much and learned more, helping people helps with learning too I think :).

---

### Post by durfff on 2007-05-26
Cheers dude, I'll definitely bear that in mind (but if you DO need help on learning how to play guitar or breeding dogs, you know where to come)

And I wish I could plug straight into an ethernet line (I still don't believe fully in that thing they call "wireless"), but I'm short for cash and paying for a cable by the meter would mean not eating for a while. Well, I say, f*$k that. 

:D

---

### Post by NT4usB on 2007-05-26
> **durfff said:**
> ...(doubt it but hey, you might want to learn about playing guitar or training dogs some day - I'm not bad at them things ha :D) Fred

Working dogs or show dogs?

---

### Post by Dzenhax on 2007-05-26
Now that you're set up check this dude's website out.  It helps get the non-standard stuff running.

[http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia)

Espcially cds and DVDs.

---

### Post by durfff on 2007-06-10
HAHA

Well before having to pick up an NVidia card (even though I'll follow the advice), I guess I can squeeze a lot more out of my old PC...

I'm crrently running on my ubuntu at 1280x800 screen res and everything is going fine - superfast wireless and all ;)

Cheers all

---


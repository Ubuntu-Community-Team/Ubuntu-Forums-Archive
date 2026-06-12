---
title: "Which Linux image: K7 or i686?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by halcyon on 2006-09-15
I have a Athlon 64 X2 3800+ and recently discovered that the default install doesn't support dual-cores, so I have to install a SMP kernel.  However, I'm not sure which architecture is more applicable.  I would guess K7, but I'm just making sure.

---

### Post by Kilz on 2006-09-15
> **halcyon said:**
> I have a Athlon 64 X2 3800+ and recently discovered that the default install doesn't support dual-cores, so I have to install a SMP kernel.  However, I'm not sure which architecture is more applicable.  I would guess K7, but I'm just making sure.

I recommend the amd64 k8 kernel with the amd64 version. You have a corvette, and its like pulling out half the spark plugs running i386.

---

### Post by xyz on 2006-09-15
Yes I'd like to know more about this myself. 
Since yesterday I'm running on kernel 2.6.15-26-686 (as opposed to 386).
I read somewhere that it would make a TREMENDOUS difference but frankly I haven't seen much of it yet!
I didn't spend 3 weeks tuning my box but it's all right, I think.

---

### Post by halcyon on 2006-09-15
I KNEW I was going to get a "why don't you use AMD64 instead?" response haha!

Have you been to the 64-bit processor forums?  I depend on this machine to work, I didn't want to have to deal with all the headaches listed there, and the majority of my programs don't even run 64-bit yet.

So, K7 or i686, which one?

---

### Post by Kilz on 2006-09-15
> **halcyon said:**
> I KNEW I was going to get a "why don't you use AMD64 instead?" response haha!

Have you been to the 64-bit processor forums?  I depend on this machine to work, I didn't want to have to deal with all the headaches listed there, and the majority of my programs don't even run 64-bit yet.

So, K7 or i686, which one?

I live on the 64bit forums. What programs do you need?

---

### Post by halcyon on 2006-09-15
Well alrighty, I'd like to be able to use the 64-bit version so here goes.  So far, Ive been using the following:

- alien
- XnView
- ePDFview
- Xarchiver
- SciTE
- BitTornado
- Audacity
- GnomeBaker
- Kino
- VLC Media Player
- XMMS
- gFTP

and of course everything that comes with Ubuntu already.  It's just that all I know and have read is that 64 bit isn't ready for working use yet, still going through growing pangs, so to speak, so I was hesitant to run it given 32 bit works fine.  However, I'm willing to give it a try on based simply on your greater knowledge of the topic haha.  Lead the way master!

---

### Post by Kilz on 2006-09-15
> **halcyon said:**
> Well alrighty, I'd like to be able to use the 64-bit version so here goes.  So far, Ive been using the following:

- alien
- XnView
- ePDFview
- Xarchiver
- SciTE
- BitTornado
- Audacity
- GnomeBaker
- Kino
- VLC Media Player
- XMMS
- gFTP

and of course everything that comes with Ubuntu already.  It's just that all I know and have read is that 64 bit isn't ready for working use yet, still going through growing pangs, so to speak, so I was hesitant to run it given 32 bit works fine.  However, I'm willing to give it a try on based simply on your greater knowledge of the topic haha.  Lead the way master!


64bit is ready, don't think it isn't. The 64bit section is a constant FUD battle. Peoples perceptions die hard, Breezy was a problem. Dapper is a different world.
I will say there are some things that are not available, but they are rare.  I did a quick check of your list. Everything but XnView is available in synaptic. I don't think it would be that hard to install it though if you have a 32bit .deb file. 32bit applications will run on 64bit, but you might have to add a file or 2. Granted you may have to install some 32bit applications. But those can be counted on your fingers, they also have howto's/scripts to set them up.
Since You have a 32bit setup working fine, and its not upgradeable to a 64bit I suggest leaving it alone and making a 64bit partition if you have room. That way if it isn't to your liking its easy to go back to 32bit.

---

### Post by halcyon on 2006-09-15
Well, consider done and done then!  Thanks for dispelling that particular myth and I'll post in the 64-bit forums should something happen to come up :)

---

### Post by petri on 2006-09-15
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel+386+686") 
Yes it's quite old but I found "... k7 – This kernel is recommended for a computer with a Athlon or newer AMD CPU. New 64 bit AMD cpus can use it as well if you have the 32 bit version of Ubuntu installed. Installing this kernel with may improve performance."

I have an old XP+1800 with k7 and it runs, is it faster than 386? Don't know :) 

The new kernel appears afterwards in Synaptic and is removable, I did it with Breezy Badger 5.10

Should you use **aptitude** instead of **apt-get** I think you might ask aysiu about that. He writes about it at his [website]("http://http://www.psychocats.net/ubuntu/aptitude") 
I think you should. (You know you can PM him about it.)

---


---
title: "wireless trouble:  this isnt serious...."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by jsd1966 on 2007-12-29
Ok.  I have to say this is not a great start to my Ubuntu experience.  Microsoft malware clunks along, but at the very least it works.  So here we all are and after looking around the forum it seems that getting wireless to work in Ubuntu is only slightly more difficult than deciphering the oracle at Delphi -- I must have just looked at about 15 different incantations to exorcise this particular demon -- and from the looks of it none 100% effective, with the haunting returning upon a full moon, etc.  Please.

Folks, please pass it on.  Until this kind of open systems can be used by people with a life, Microsoft is safe.

---

### Post by spiderbatdad on 2007-12-29
My wireless works perfectly and did so "out of the box." All I did was click on the network monitor and enable it. click click done.


IBM T-30 Cisco Aironet Wireless

Linksys Wireless G Access Point

---

### Post by spiff95 on 2007-12-30
Okay, what make/model is your wireless card? If you tried ndiswrapper, are you certain you pointed it at the right driver?

I'm sure you're frustrated, but if you will give the community some detailed info, someone is likely to point you in the right direction. :-)

---

### Post by Dngrsone on 2007-12-30
It's kind of a defeatist attitude, is it not?  At least you tried to look, whereas a good chunk of the people who caused the generation of the multitude of solutions just asked for help without even trying to look for information already out there.

As spiff asked, why not at least give us a chance to help you before you throw in the towel and go running back to Win?

---

### Post by bwtranch on 2007-12-30
Hey bro, I feel your pain. But, if you say that at least it works, you have to ask yourself, for how long? Until it crashes, again? Linux is more trouble to get going in general and I don't think that anybody on the forum would disagree entirely. But, and this is a big  but, it absolutely gives back what you put in and more. The learning curve is rather steep, but there are people willing to help.

And there's a certain amount of satisfaction that goes along with, hey, I did it.

My brother is a top software engineer at IBM and has been in programming all his life. He would tell you that the future IS open source. This guy started out at Rice University using punched cards.

Take Care

---

### Post by jsd1966 on 2007-12-30
Ok.  Let's give a go then.  So, community:

The fellow for whom it "worked out of the box", could you please elaborate on exactly what the "click click click" was clicking -- your comment would be a lot more useful to me then.  If you are referring to the Netwok tab under Administration -- oh, I clicked, man, I clicked.  If not, please expound.

I have a linksys wireless card that had been working fine and forever without a problem under XP Pro.

I do an iwconfig.  It shows me the card as eth2.  The two *wired* netword cards (have not used for years) are shown as eth0 and eth1.  

My first observation is that iwconfig does not show eth2 as having the settings I put in for the wireless card under the network tab.  The ESSID is not set.  The channel numbers is also not set.  I tried setting both of these to their proper values, to no avail.  I try to ping, but I dont get any activity, not even the usual message that ping is at least trying.

Like I said.  I went looking through the threads about this, but you've got to be a CIA analyst to distill something that actually makes sense from them.  I'd appreciate any help, but I'm not holding my
breath.  

The day when Linux can go toe-to-toe with Microsoft is clearly coming and soon, but in my opinion it is just not here yet.  What I find particularly frustrating is that in today's landscape, one would think that wireless networking would be the one thing that people would make sure works seamlessly -- very few people are going to care what Ubuntu is or what it can do if it cannot do wireless completely transparently for 95% of people.

---

### Post by Dngrsone on 2007-12-30
What model Linksys card?  Is it PCMCIA (PC Card) or mini-pci?

---

### Post by jsd1966 on 2007-12-30
pc card

---

### Post by Dngrsone on 2007-12-30
[img]http://xs209.xs.to/xs209/06476/eh.gif[/img]  ... and the model number?

---

### Post by efarrar on 2007-12-31
I agree with the folks here who have cited the defeatist attitude as a primary reason for installation failure. I tried to install Ubuntu a few months back and ran into a tricky problem with my broadcom wireless drivers. After some fitful tries i gave up. 

Yesterday, determined to make it work, I started with a fresh install, *read the forums,* and eventually made things work. Along the way i learned a lot about how Linux works and how to make the OS work. I much preferred this sequence to the standard MS cycle which seems to always involve inscrutable error messages and persistent errors. 

The difference between my two attempts was determination. Ultimately, the job wasn't hard but it took some learning. I'm enough of a geek that even strolling through terminal was fun. it brought back my heady days as a DOS wizard in junior high. Folks need to use the wisdom of those who have gone before, found in these forums, and dive in!

---

### Post by spiff95 on 2008-01-01
Hi JSD,

> **jsd1966 said:**
> Ok.  Let's give a go then.  So, community:

I have a linksys wireless card that had been working fine and forever without a problem under XP Pro.

Yeah, having a native driver will generally make things work easier... :-)


> 

Like I said.  I went looking through the threads about this, but you've got to be a CIA analyst to distill something that actually makes sense from them.  I'd appreciate any help, but I'm not holding my
breath.  

Okay, try this. Go to the ndiswrapper help page: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-4b7c00c6654b2d109b9330c28d9210db329ba573)

Start with the instructions there, before you try to set up the card. I don't know your experience level, so I'm not assuming anything. That said, my exp. level isn't super-great, but I can explain some stuff if the instructions look too cryptic. You can PM or e-mail me if you like. I think you can probably lick this problem without a super bunch of trouble. :-)

---

### Post by eolson on 2008-01-01
Ya just gotta slow down, take a deep breath, read the directions, and everything will work out.  My Wal-Mart special eMachines W4605 works fine.  Broadcom wireless card and all.  Just had to pay attention and load the firmware and drivers.  Finding the driver was the tricky part,  but really wan't that hard.  I understand that Linux is different and change can sometimes be a little stressful,  but it can also be rewarding in many ways.  Just hang in there,  If this dumb ol redneck can do it, you certainly can.

---


---
title: "Help using 3 HDD's and 2 OS's"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by iiDopDop!! on 2007-07-14
I have installed ubuntu successfully and it was really good i loved it but my dad dosn't think its all that good.
i was wondering if there was a way to use my 3 had drives to use ubuntu and windows XP pro sp2.

I have ubuntu on a 40 gig Hdd
and XP pro on an 80 gig Hdd
and another 40 gig Hdd wich we use as a music storage

is there a way i can use both operating systems and all three HDD's without having to unplug one or the other??

i have used all three hard drives at once but it went straight to ubuntu and didnt give me a choice whether to go to windows or ubuntu.

---

### Post by FleetAdmiral74 on 2007-07-14
Once you install XP on another drive (making sure not to erase ubuntu), you have to edit some files to add ubuntu back in. The bootloader you should use is called GRUB. Do a quick search on dual booting, should help.

That gives you a starting point...and remember, even though this info prolly does not help a LOT, its perfectly possibly and many people have this type of setup.

---

### Post by confused57 on 2007-07-14
> **iiDopDop!! said:**
> I have installed ubuntu successfully and it was really good i loved it but my dad dosn't think its all that good.
i was wondering if there was a way to use my 3 had drives to use ubuntu and windows XP pro sp2.

I have ubuntu on a 40 gig Hdd
and XP pro on an 80 gig Hdd
and another 40 gig Hdd wich we use as a music storage

is there a way i can use both operating systems and all three HDD's without having to unplug one or the other??

i have used all three hard drives at once but it went straight to ubuntu and didnt give me a choice whether to go to windows or ubuntu.
See this guide for adding an entry in grub to boot Windows on another hard drive:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
You should be able to have all 3 hard drives connected, Windows would boot by default and you can manually choose to boot Ubuntu in the grub boot menu.

---

### Post by iiDopDop!! on 2007-07-15
Thanks allot for all you help i got it to work fine but it wont read my DVD drive so it dosnt really work that fine.

i have it set up 
Primary Drive 40 gig Ubuntu
Slave Drive 40 gig no OS
Cable select Drive 80 gig windows XP

any help appreciated.

---

### Post by djchandler on 2007-07-15
> **iiDopDop!! said:**
> Thanks allot for all you help i got it to work fine but it wont read my DVD drive so it dosnt really work that fine.

i have it set up 
Primary Drive 40 gig Ubuntu
Slave Drive 40 gig no OS
Cable select Drive 80 gig windows XP

any help appreciated.

The thing about DVDs, especially a burner, is they need to be master on its IDE channel. I would change the two OS hard drives to IDE 0, make your STORAGE-NO OS HD slave on the IDE channel with the DVD drive.

This should work for you.

IDE 0 (1)
Primary Drive 40 gig Ubuntu (GRUB already resides here - it's a no brainer)
Slave Drive 80 gig windows XP

IDE 1 (2)
Master Drive DVD (burner?)
Slave Drive 40 gig no OS

Does your motherboard support SATA? The reason I ask is it adds options beyond 4 internal IDE devices, if you have enough of a power supply.

DJ

PS Getting an external USB box to hold the NO OS drive is yet another option if my first setup idea won't work right, but it should.

PSS Ask your dad if you can have your own computer! If you are mature enough to be changing things around inside anyway, ask if you can maybe get some used parts somewhere locally and build your own box. We have a place here in the Kansas City area called the Surplus Exchange. They have all sorts of re-cycled stuff. Maybe there is a similar operation in your area. The U.S. government subsidizes these operations to help keep hazardous materials out of landfills, as well as reclaim precious metals from obsolete parts.

---

### Post by iiDopDop!! on 2007-07-15
yea i have thought about getting my own computer but i was thinking why not tinker with it while its still the family's one so then when it breaks its my dad who has to get the parts.

And also my dad wanted to know.

---

### Post by regomodo on 2007-07-15
> **djchandler said:**
> The thing about DVDs, especially a burner, is they need to be master on its IDE channel. I would change the two OS hard drives to IDE 0, make your STORAGE-NO OS HD slave on the IDE channel with the DVD drive.

This should work for you.

IDE 0 (1)
Primary Drive 40 gig Ubuntu (GRUB already resides here - it's a no brainer)
Slave Drive 80 gig windows XP

IDE 1 (2)
Master Drive DVD (burner?)
Slave Drive 40 gig no OS

Does your motherboard support SATA? The reason I ask is it adds options beyond 4 internal IDE devices, if you have enough of a power supply.

DJ

PS Getting an external USB box to hold the NO OS drive is yet another option if my first setup idea won't work right, but it should.

PSS Ask your dad if you can have your own computer! If you are mature enough to be changing things around inside anyway, ask if you can maybe get some used parts somewhere locally and build your own box. We have a place here in the Kansas City area called the Surplus Exchange. They have all sorts of re-cycled stuff. Maybe there is a similar operation in your area. The U.S. government subsidizes these operations to help keep hazardous materials out of landfills, as well as reclaim precious metals from obsolete parts.

Wish we could do that. We can't even buy dumped computers from the local tip because of "health and safety". ******* nanny state

---

### Post by djchandler on 2007-07-17
> **iiDopDop!! said:**
> yea i have thought about getting my own computer but i was thinking why not tinker with it while its still the family's one so then when it breaks its my dad who has to get the parts.

And also my dad wanted to know.

Your dad will be more impressed by you solving the problem. As a dad and grandpa, that's how I would see it anyway. You are being very resourceful. I think that will impress him much more besides getting things fixed so everybody is happy (for the moment). Don't you have a birthday or something coming up?

Good luck!
D. J.
:guitar:

---


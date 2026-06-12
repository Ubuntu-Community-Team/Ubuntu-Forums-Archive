---
title: "I really want to use Ubuntu"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by tentel on 2008-03-25
I really do.
Twice before I've made the jump, formatted my hard drive and hit it cold turkey, and both times I've been foiled by my stupid Broadcom card.

I've spent hours working on it and tried many things, but I've always had to go back to Vista.


So the question is, does anyone think there is a chance I'll have better luck with Hardy Heron?



Thanks
-Tim

---

### Post by LowSky on 2008-03-25
What broadcom card? What have you tried already.

Hardy doesnt come out until April 24th, dont use the beta as its unstable.

---

### Post by tentel on 2008-03-25
uh, off the top of my head I think I have the BCM94311.
yeah, that looks right.


I tried using ndiswrapper, and fw-cutter.
I follwed instructions that I found both on this forum and by googling. 
with ndiswrapper in the windows wireless drivers utility, it told me everything installed correctlly, but nothing ever worked.

with fw-cutter in the restricted drivers manager, I could get the light on my card to turn on, signifying it was working, but again, nothing ever worked, and it would only turn on right when I activated the drivers.  If I were to restart, the light would never turn on again.

I eventually decided it wasn't worth the trouble, and Vista really isn't that bad, but I'm just curious if Hardy may have more hardware support since I enjoy tinkering with OSs a little, and I'd rather not do it on the OS that has all my important work.


By the way, I'm using an HP Pavilion DV6000 series laptop.
AMD Turion x2 64-bit
2 GB RAM
NVIDIA GO 6150

And Broadcom wireless of course:)



-Tim

---

### Post by original_jamingrit on 2008-03-25
Broadcom wireless chipsets are finicky creatures.  My buddy's been wrestling with his as well.  For ubuntu, there's tons of step by step howtos, but first we need to know which crad yours is.

open up your terminal and copy and paste in the following:
```
lspci | grep Broadcom
```
It should give you a single line as out put, copy and paste that line into google or the forums search field.  It should give you a link to a website with the info you need.  If you have any more problems, post again.

---

### Post by funrider on 2008-03-25
forget the pain, buy a wireless card which actually works for ubuntu....been there.

---

### Post by grumpylad77 on 2008-03-25
Hey, I have that same Broadcom Card, and my wireless works great using NDISWRAPPER in gutsy gibbon. 
Try this link:
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html]("http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html")

That should work if you follow it step by step.

I know it is for a different computer, but the wireless card is exactly the same.

---

### Post by stchman on 2008-03-25
> **tentel said:**
> I really do.
Twice before I've made the jump, formatted my hard drive and hit it cold turkey, and both times I've been foiled by my stupid Broadcom card.

I've spent hours working on it and tried many things, but I've always had to go back to Vista.


So the question is, does anyone think there is a chance I'll have better luck with Hardy Heron?



Thanks
-Tim

Are you speaking of a wireless card on a laptop?  If so then yes, Broadcom does not support Linux.  You can get an Intel 3945 off ebay for under $20 shipped new.

---

### Post by tentel on 2008-03-25
Oops!

I'm sorry everybody.

I should have clarefied that I don't currentty have Linux on my system.

I'm only running Vista right now.

I was just curious to see if it would be worth it to bother with trying out Ubuntu again.



Sorry for the misunderstanding
-Tim

---

### Post by stchman on 2008-03-25
> **tentel said:**
> Oops!

I'm sorry everybody.

I should have clarefied that I don't currentty have Linux on my system.

I'm only running Vista right now.

I was just curious to see if it would be worth it to bother with trying out Ubuntu again.



Sorry for the misunderstanding
-Tim

YES, install Ubuntu and come over to the side of goodness that is Linux.

---

### Post by jan quark on 2008-03-25
I had to remove my broadcom 4311 wlan card from my laptop ( it is lying somewhere in my cupboard)
it can be a pain, for some it works, for some it does not
the drivers for broadcom are not open it is no joy and as long as the driver are not made open by the manufacturer no release of ubuntu will handle them out of the box

---

### Post by waspbr on 2008-03-25
there's some good news for some broadcom card owners, hardy's repos have the a package called b43-fwcutter that seems to support a great deal of the broadcom cards, unfortunately my hp tx1320us has not been awarded that luck I have a bcm4328 which is not yet supported, so no cake for me, but I still managed to get it working with ndiswrapper,

---

### Post by fela on 2008-03-25
i HATE having to use closed source drivers. :mad:

---

### Post by tentel on 2008-03-25
> **grumpylad77 said:**
> Hey, I have that same Broadcom Card, and my wireless works great using NDISWRAPPER in gutsy gibbon. 
Try this link:
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html]("http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html")

That should work if you follow it step by step.

I know it is for a different computer, but the wireless card is exactly the same.


Thanks!

I'll probobly make myself a nice little partition come April and give Hary Heron a try.
That link will definatly be useful.
I've aready added it to my favorites.



-Tim

---


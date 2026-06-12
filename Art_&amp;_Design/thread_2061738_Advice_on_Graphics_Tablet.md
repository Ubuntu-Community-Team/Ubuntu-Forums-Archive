---
title: "Advice on Graphics Tablet?"
date: 2012-09-23
forum: Art &amp; Design
---

### Post by jingaling on 2012-09-23
Hi guys,

I'm running 12.04 x64 on my machines and I am on the look out for a graphics tablet. To be clear, I'm not looking for a tablet in the form of a Nexus 7 or an iPad, I want a tablet with a stylus that is used for graphic design.

I've been looking at the Wacom CTL 470 (see link below) mainly because it's cheap and there is an option in Ubuntu settings for "Wacom Graphics Tablet" so I assumed they would be compatible.

[http://www.amazon.co.uk/Wacom-ctl470ken-Bamboo-Graphics-Tablet/dp/B005TYVS4Y/ref=dp_return_1?ie=UTF8&n=340831031&s=computers](http://www.amazon.co.uk/Wacom-ctl470ken-Bamboo-Graphics-Tablet/dp/B005TYVS4Y/ref=dp_return_1?ie=UTF8&n=340831031&s=computers)

After some research though, I can see that they may not be all that compatible. I have the option to run it under Windows but I'd really rather not as I prefer Ubuntu.

Can anyone recommend any products please guys? I'm looking to spend no more than £100 ideally.

Thanks all,

Kev

---

### Post by Favux on 2012-09-23
Hi jingaling,

That Bamboo Pen should work out of the box in Quantal.  The Beta2 is due out 9-27-12 along with Gimp 2.8 (I think).  Third generation tablets do require a wacom.ko from input-wacom for Precise.  Not a big deal.

If it was one of the other BambooPTs that had ExpressKeys I'm not sure if the GNOME 3.6 Wacom Graphics Tablet applet in Quantal's System Settings would support them.  But xf86-input-wacom recently had some patches that will support out of sequence ExpressKeys like the BambooPTs' so support for their ExpressKeys should be available soon.  I'm pretty sure I saw the patch for libwacom also so it would be down to whether the applet has code for them yet.

---

### Post by Bucky Ball on 2012-09-23
[I]Thread moved to [B]Art & Design


[/B][/I]Yes, when I researched this a couple of months ago Bamboo seemed to be the go. There's been good development there.

@ Favux: OP is using 12.04, not 12.10. ;)

---

### Post by jingaling on 2012-09-23
I really appreciate the quick replies gents, thanks (sorry for putting it in the wrong category also).

I'll get that then as I fully expect up upgrade to Quantal anyway. I usually do this at Beta 2 stage following feature feeze so it's all good.

Thanks for the assistance guys!

Jing

---

### Post by jingaling on 2012-10-05
Quick update on this guys. I bought the tablet above and it worked completely out of the box flawlessly. I didn't have to do a single thing "Wacomm settings" also picked it up and I was able to do things like change the button associations and to left handed.

If you're after a cheap tablet that works out of the box in Ubuntu then I can't recommend this one enough.

Thanks again for the advice guys.

Jing

---


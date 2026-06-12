---
title: "How do I get display drivers in Ubuntu?"
date: 2013-08-20
forum: Any Other OS
---

### Post by andy23 on 2013-08-20
Hi, I'm new to the site and relatively new to Linux, so forgive me if I'm asking a silly question here.

I have an old PC which identifies itself at atart up as American Megatrends. I've looked at their website and managed to find out it is a M810LR motherboard with a SiS730s chip set (whatever that means!)

My problem is I've just connected the box to a Hanns-G HX191D monitor, which I know should be capable of pretty high resolution. I've used the same monitor with another PC running Windows XP and the resolution is excellent. However I've just installed RRAbuntuon the American Megatrends box and I can't get a vertical resolution of anything above 600 pixells! This is a real problem as the software I want to use needs a higher resolution.

If this was the world of Windows I would be looking to download a driver from somewhere at this point, but with Linux I'm at a bit of a loss. I have a third PC with the same type of monitor running Linux Mint 12 and that had a high resolution option in the display settings right from the beginning, although that one is a much newer motherboard.

Should I be looking for a display driver or do I need a graphics card for this old motherboard?

I hope someone can help as I've been scratching my head over this one all day.

Andy.

---

### Post by Cheesemill on 2013-08-20
*Thread moved to **Other OS/Distro Support**.*

SiS are notoriously bad for their graphics support on Linux, the only drivers available are the ones that you are already using. There may be some workarounds but I would highly recommend getting a graphics card instead (if you can still find one that will fit that motherboard).

---

### Post by lukeiamyourfather on 2013-08-20
I concur with Cheesemill. You'd be better of just getting a different graphics card with better Linux support (assuming the machine doesn't already have one). It's likely AGP slot for the graphics which you can still buy cards for, like $40 for one. Chances are though if you call a local computer shop you might be able to get a used one for free or maybe like $5. Also Craigslist or eBay would likely have some.

---

### Post by andy23 on 2013-08-25
Thanks for the help. I've now tried other versions of Linux on the same machine and I have similar resolution problems, so I'll try to get a different card. Am I right in thinking Nvidia cards are the best supported?

---

### Post by Cheesemill on 2013-08-25
Your biggest problem is going to be actually finding a graphics card with an AGP connector (which is the only graphics expansion slot your motherboard has).

No manufacturers have made AGP cards for some years now, your best bet is probably e-bay or a bricks-and-mortar computer store that sells 2nd hand kit. If you can find an Nvidia card then that's definitely your best option as you will still have the option to use the Nvidia closed-source drivers. Any ATI card that you find with an AGP connector will be one of the models that ATI no longer support so you will be stuck with the open-source radeon driver.

---

### Post by lukeiamyourfather on 2013-08-26
There are still some new AGP cards around like this one from Newegg, more expensive than a used one though (or a free one).

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130452](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130452)

---


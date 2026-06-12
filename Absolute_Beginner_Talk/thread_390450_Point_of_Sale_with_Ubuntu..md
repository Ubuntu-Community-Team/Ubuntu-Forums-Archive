---
title: "Point of Sale with Ubuntu."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Teh Dust on 2007-03-22
I currently work at a old style tool store. We have tons of items and just recently made the jump to put everything into a computer system to make our inventory easier to manage. My boss went out and purchased a HP computer with Windows XP Pro, Quick books Premium and Point of Sale. I am the one who knows the most about technology at the store so if something goes wrong I am the one who has to fix it. It's usably a quick fix but I have noticed that allot of the hardware we are using have Linux drivers for them Available on their websites and every time something goes wrong, I wonder how much easier it would be if the computer was running Ubuntu.

So what I want to know is this. Is there a point of sale program for Ubuntu that can make and print bar codes, keep track of inventory, take credit card payments and work with quick book files? And if not, would the system run more stable under ubuntu using VMware?

---

### Post by seshomaru samma on 2007-03-22
mmm
how about [this ]("http://www.bananapos.com/pos/home.html")?

---

### Post by pcjunkie on 2008-02-24
2005?

Looks like a dead project
Downloads are blocked, No login...

---

### Post by JoshuaRL on 2008-02-24
[http://easypos.sourceforge.net/](http://easypos.sourceforge.net/)
[http://gshop.sourceforge.net/](http://gshop.sourceforge.net/)
[http://www.linuxcanada.com/pos.shtml](http://www.linuxcanada.com/pos.shtml)
[http://www.viewtouch.com/poshome.html](http://www.viewtouch.com/poshome.html)
[http://www.lynuxworks.com/products/bluecat/bluecat-linux-pos.php](http://www.lynuxworks.com/products/bluecat/bluecat-linux-pos.php)

Just a few I found.  Hope you find one, it seems like a cool idea.

---

### Post by crjackson on 2008-02-24
> **Teh Dust said:**
> I currently work at a old style tool store. We have tons of items and just recently made the jump to put everything into a computer system to make our inventory easier to manage. My boss went out and purchased a HP computer with Windows XP Pro, Quick books Premium and Point of Sale. I am the one who knows the most about technology at the store so if something goes wrong I am the one who has to fix it. It's usably a quick fix but I have noticed that allot of the hardware we are using have Linux drivers for them Available on their websites and every time something goes wrong, I wonder how much easier it would be if the computer was running Ubuntu.

So what I want to know is this. Is there a point of sale program for Ubuntu that can make and print bar codes, keep track of inventory, take credit card payments and work with quick book files? And if not, would the system run more stable under ubuntu using VMware?

[http://kde-apps.org/content/show.php?content=17404]("http://kde-apps.org/content/show.php?content=17404")

[http://kde-apps.org/content/show.php?content=19007]("http://kde-apps.org/content/show.php?content=19007")

---

### Post by Presto123 on 2008-02-24
Hrmm...good question that I have been thinking about as well.

---

### Post by FoolsRun on 2008-02-24
After some searching I came across this:
[http://www.openbravo.com/product/pos/get-openbravo-pos/](http://www.openbravo.com/product/pos/get-openbravo-pos/)

It looks like OpenBravo has a pretty extensive ERP package, which has an online demo here: [http://www.openbravo.com/product/demo-center/](http://www.openbravo.com/product/demo-center/)

No demo for the POS, so if you run it I'd actually love to see some screenshots.

---

### Post by theRightNee on 2008-02-24
to answer the stability question

yes, i do believe the system would be more stable under Ubuntu..but the major factor is, will it work as well virtualized? since it is used to keep track of inventory, perhaps virtualization would be too slow, unless the computer has an amazing clock speed...also, hardware may be an issue...as i am sure you know hardware usability is a major issue with Linux, as it is quite a headache to just get basic things running (wireless cards, video cards, etc.)

still, i don't know your system, and if you know that it can handle it, go ahead! (btw...you may want to set up dual monitors tho...if you ever manage to find a replacement program, you'll want to run both a windows virtualized desktop enviroment along with the ubuntu desktop =])
best of luck

---

### Post by jcanini on 2008-02-24
Funny I was just reading about this issue at /. today.
[http://linux.slashdot.org/article.pl?sid=08/02/24/2012230&from=rss](http://linux.slashdot.org/article.pl?sid=08/02/24/2012230&from=rss)

Its an interesting read.

I own a small business and am interested in having a linux pos system as well but so far its seems there is not too much software that is stable and doesnt require some degree of programing knowledge.

I played around with librepos from sourceforge and found it to be quite good but in a business its too risky to use beta software.

Please post back if you find some good alternatives.

---

### Post by FoolsRun on 2008-02-24
I went and downloaded OpenBravoPOS. Here are some screenshots of it. They're pretty self-explanatory of you know POS systems at all.

---

### Post by FoolsRun on 2008-02-24
A few more screenshots of OpenBravoPOS. Again, they pretty much explain themselves.

I was pretty impressed by the polish on this admittedly beta software. I wish I had a reason to play with it further.

You can even give your products little pictures which can be tapped on the sale screen. Neato.

---

### Post by Lefteris Eleftheriou on 2008-06-18
Hi,

We are building an Ubuntu POS system with the following hardware and software:

Tyco Elo Touchsreen
Citizen CBM1000 receipt printer
Weigh scale
Cash drawer
Mag stripe reader
Openbravo POS software

At this point, all of the hardware devices are incompatible with Ubuntu. Do you have any suggestions?

Please let me know.

Thank you,

Lefteris Eleftheriou

---

### Post by meindian523 on 2008-06-18
Try another distribution.:)

---

### Post by JoshuaRL on 2008-06-18
So, what have you found out about their drivers?  Is there anything you've found on Google?

You also might try either Debian or Gentoo.  Ubuntu is based on Debian, and so it would seem pretty familiar.  It's also probably the closest to being a truely universal OS.  So you would have a pretty good chance of getting everything at least covered by VESA type drivers.

Gentoo is a distrobution that compiles almost everything at build time, so it is probably one of the most optimized.  So it might also give you a chance.

Hope that helps.

---


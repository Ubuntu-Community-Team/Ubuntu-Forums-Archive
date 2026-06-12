---
title: "Xgl is cool, but can I run it on a Dell 2350?  How?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by j_m_downing on 2006-06-13
Hi,
  I was initially attracted to Linux because I thought I might be able to run the cool xgl graphics on my Dell 2350 with minimal modifications, instead of having to buy a whole new system for Vista Aero.  (It should have been for a better reason, like security, but I'm afraid it wasn't.)
  But I can't figure out what modifications, if any I need to make.  And I'm having a heck of a time figuring out what video card (if I need an extra one) I should use.  Or if I can run xgl at all.
My general system technical specs are here:
[http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1107033](http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1107033)

More specifically, I have:
1.80 Ghz Pentium 4
256 mg of RAM (I'm updating to 512)
Intel 845GL integrated graphics chip.

I'm going to get a second hard drive (40 gig) for Ubuntu, if that's at all relevant.  I'm running Windows XP now.

The list of video cards that work or don't work is here:
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Intel_Cards](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Intel_Cards)
But only later Intel graphics chips are listed as compatible/incompatible.

I think my Pentium is 32-bit, but I'm not sure.  I also think my PCI card is just plain PCI, and not express, but I'm not sure about that, either.

Does anyone know what kind of video card I could use, or if I can run xgl at all?  My budget is fairly small, and if the necessary card costs above $50 on ebay I'll probably just run plain Ubuntu graphics.

Thanks in advance!
j_m_downing

---

### Post by uzi09 on 2006-06-13
check out the ultimate xgl thread [here](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+aiglx+thread) and see what the ideal configuration seems to be :D

---

### Post by bluevoodoo1 on 2006-06-13
[QUOTE=j_m_downing]More specifically, I have:
1.80 Ghz Pentium 4
256 mg of RAM (I'm updating to 512)
Intel 845GL integrated graphics chip.

I think my Pentium is 32-bit, but I'm not sure.  I also think my PCI card is just plain PCI, and not express, but I'm not sure about that, either.

Does anyone know what kind of video card I could use, or if I can run xgl at all?  My budget is fairly small, and if the necessary card costs above $50 on ebay I'll probably just run plain Ubuntu graphics.[/QUOTE]

My other computer is a Dell 2350, P4 1.8 ghtz, 512 RAM etc. etc. It's 32 bit, and you're correct, it only has a PCI bus. I've run Ubuntu on it without a hitch (but not Xgl/compiz). 

Having a video card will increase all aspects of video. Go for a **Nvidia** card. They have much better driver support for Linux than their rivals.
For my second cimputer, I got a (PCI) eVGA FX5500 online at newegg.com for about $50. It runs Xgl/compiz quite well (for the money of course).

EDIT: Here's a short list of compatible cards. [http://getkororaa.com/releases/xgl/xgl-cards](http://getkororaa.com/releases/xgl/xgl-cards)

EDIT2: If you want to see if Xgl works on your system, you could try the Kororaa Live CD [http://kororaa.org/static.php?page=static060318-181203](http://kororaa.org/static.php?page=static060318-181203)

---

### Post by j_m_downing on 2006-06-13
[QUOTE=uzi09]check out the ultimate xgl thread [here](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+aiglx+thread) and see what the ideal configuration seems to be :D[/QUOTE]

My problem is actually a little more severe than I think I let on: I don't understand video card specs.  I've never had one, except for my little integrated one.  I've tried to figure out what would be compatible with my system, but without any luck.  Is it important that my processor seems to be 32-bit?  Can I run a PCI express card?  What's are the maximum card-based megabytes my system can support?  I've looked for a while trying to answer these questions, but just get more and more lost.
Thanks,
J. Downing

---

### Post by j_m_downing on 2006-06-13
[QUOTE=bluevoodoo1]My other computer is a Dell 2350, P4 1.8 ghtz, 512 RAM etc. etc. It's 32 bit, and you're correct, it only has a PCI bus. I've run Ubuntu on it without a hitch (but not Xgl/compiz). 

Having a video card will increase all aspects of video. Go for a **Nvidia** card. They have much better driver support for Linux than their rivals.
For my second cimputer, I got a (PCI) eVGA FX5500 online at newegg.com for about $50. It runs Xgl/compiz quite well (for the money of course).

EDIT: Here's a short list of compatible cards. [http://getkororaa.com/releases/xgl/xgl-cards](http://getkororaa.com/releases/xgl/xgl-cards)

EDIT2: If you want to see if Xgl works on your system, you could try the Kororaa Live CD [http://kororaa.org/static.php?page=static060318-181203](http://kororaa.org/static.php?page=static060318-181203)[/QUOTE]


Thanks!  Anyone know the maximum specs for an under $50 card for my system?
J Downing

---

### Post by j_m_downing on 2006-06-13
[QUOTE=j_m_downing]Thanks!  Anyone know the maximum specs for an under $50 card for my system?
J Downing[/QUOTE]

I forgot to mention--I've hunted through the Dell forums for support for anything but GeForce, without luck.  And I can't figure out which Geforce might work with my computer--I bought it with the near-minimum specs.
J downing

---

### Post by uzi09 on 2006-06-13
btw, if xgl doesn't work, you can always try AIGLX (more info in the ultimate XGL thread :D). i'm running AIGLX cuz i'm 2 poor to buy a nice vid card, but it works with the integrated card fairly well :D -- course it is still quite buggy :(

---

### Post by Dr. Nick on 2006-06-13
Their are a few different interfaces for video cards

Integrated - What you seem to have

PCI - Older technology but still usually better than some onboard graphics cards if you get a good one

AGP - Few different genrations here. The newest are 8x which should be backwards compatible to the 4x, And then their was 2x which was the first generation I believe. Agp 2x isnt compatible with any other agp generaion

PCI Express  - This is the newest interface, Totally different from PCI above, despite the name being similar.

Wether you have a 32bit or 64 bit processor doesnt really make a differece. The motherboard addon slots is what is important here. The newest 64bit processors motherboard will support pci and agp OR pci express depending on what one you look at. Their may be a select few that support all 3 (pci,agp,pci express). Also I am not aware of any 32bit motherboard that supports pci express.

 It appears you only have PCI and none of the other interfaces, so a PCI card is what you want. If the card is PCI then usually thats all that matters, The motherboard should not limit the amount of video ram the card can have.

Here is a page with many pci nvidia cards.

[http://www.newegg.com/Product/ProductList.asp?N=2010380048+1069609642+1305520548&Submit=ENE&SubCategory=48]("http://www.newegg.com/Product/ProductList.asp?N=2010380048+1069609642+1305520548&Submit=ENE&SubCategory=48")

You can look through their for differnt price ranges and specifications

Your best bet would most likely be one on this page
[http://www.newegg.com/Product/ProductList.asp?N=2010380048+1069609642+1305520548+106790727&Submit=ENE&SubCategory=48]("http://www.newegg.com/Product/ProductList.asp?N=2010380048+1069609642+1305520548+106790727&Submit=ENE&SubCategory=48")

You want to be carefull and avoid some of the older ones as they may not be the best choice for xgl. Also on a card of this age 256mb of memory may be a bit overkill, You are probably fine with a 128 mb one

Many of them fall right around the $50 mark, some just a tad over

---

### Post by j_m_downing on 2006-06-13
[QUOTE=j_m_downing]I forgot to mention--I've hunted through the Dell forums for support for anything but GeForce, without luck.  And I can't figure out which Geforce might work with my computer--I bought it with the near-minimum specs.
J downing[/QUOTE]

I did a newegg search for a 32-bit geforce pci video card, and only came up with this thing:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814121194](http://www.newegg.com/Product/Product.asp?Item=N82E16814121194)
I mean, 16 megabytes?  Can I run anything better?
Thanks,
J Downing

---

### Post by bluevoodoo1 on 2006-06-13
[QUOTE=j_m_downing]I did a newegg search for a 32-bit geforce pci video card, and only came up with this thing:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814121194](http://www.newegg.com/Product/Product.asp?Item=N82E16814121194)
I mean, 16 megabytes?  Can I run anything better?
Thanks,
J Downing[/QUOTE]

That's a PCI-express card, and your system isn't compatible with that, it has to be "PCI," because that's what will fit into your motherboard. Don't worry about the 32/64 bit stuff. That refers more to your processor. Your processor is a 32 bit. Try this search...

[http://www.newegg.com/Product/ProductList.asp?Submit=ENE&N=2010380048+1069609642&Subcategory=48&description=nvidia+pci&srchInDesc=&minPrice=&maxPrice=](http://www.newegg.com/Product/ProductList.asp?Submit=ENE&N=2010380048+1069609642&Subcategory=48&description=nvidia+pci&srchInDesc=&minPrice=&maxPrice=)

---

### Post by Dr. Nick on 2006-06-13
Yeah thats a odd little card, I believe it comes with 16mb of ram and you have to add more yourself, I really dont see a point in getting on of them, even if you could use it lol. I could be wrong though. See the above post plus the end of mine from above for a good search to use

---

### Post by shanepardue on 2006-06-13
[http://castle.pricewatch.com/s/search.asp?s=pci&c=Video+Card&i=37](http://castle.pricewatch.com/s/search.asp?s=pci&c=Video+Card&i=37)

maybe this will help you. lots of choices

---

### Post by j_m_downing on 2006-06-13
64-bit interface cards are OK w/a 32-bit CPU, then?
Also, thank you SO MUCH, everybody, for helping me! 
J Downing

---

### Post by Dr. Nick on 2006-06-13
the interface of the cards is different from the cpu. That 64 bit card should be fine if its pci. If you look at some more expensive cards they will have 256bit interface, none of them are pci though, And you cant tell the bit of a card by looking at it, many 64bit and 128 cards look the same

The larger the bit, the more data that can go thru faster.

I have a 64bit agp an xgl is just fiine

---

### Post by j_m_downing on 2006-06-13
Everybody: thank you, thank you, thank you!
I got it: 
eVGA Geforce FX5200 128-P1-N309-LX Low Profile Video Card [http://www.newegg.com/product/product.asp?item=N82E16814130188](http://www.newegg.com/product/product.asp?item=N82E16814130188)
$46, cheaper brand-new on Newegg than most of the eBay listings of the same thing (gotta love newegg).
Thanks again!
J. Downing

---

### Post by bluevoodoo1 on 2006-06-14
[QUOTE=j_m_downing]Everybody: thank you, thank you, thank you!
I got it: 
eVGA Geforce FX5200 128-P1-N309-LX Low Profile Video Card [http://www.newegg.com/product/product.asp?item=N82E16814130188](http://www.newegg.com/product/product.asp?item=N82E16814130188)
$46, cheaper brand-new on Newegg than most of the eBay listings of the same thing (gotta love newegg).
Thanks again!
J. Downing[/QUOTE]


Looks great. I have the eVGA 5500 and I'm quite happy with it!

---


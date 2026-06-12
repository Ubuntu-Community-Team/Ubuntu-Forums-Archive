---
title: "Help me Choose the Right Motherboard &amp; 64bit Question..."
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-28
Hello ALL !!!

I need your help in this:

I would like to purchase a Motherboard with characteristics:

1. Intel 945 Chipset minimum (because I need the SATA 2 feature)
2. GB LAN (Intel chip?)
3. With Onboard Graphics (Intel chip?)
    (I do NOT wish to spend additional money for a separate Graphics Card) 
4. To Support 64bit (or not)?
-------------------------------------
5. Dual Channel Memory
6. Disable Bit Functionality
7. Audio (Intel chip?)


I definately want the above 1-4!

_For No. 1_:
No comments - I WANT to try it out with my SATA 2 Hard Drives...

_For No. 2_:
I am NOT so good at LAN handling...
...and since I already have an Intel M/B & its LAN works fine in my Ubuntu, I wanted to remain/stay on that...
...at the same time, since I have another Intel M/B, I want them to communicate with each other with NO problem...what do you think?

_For No. 3_:
I want an ONBOARD Graphics Card! I do NOT want to spend/waste additional money - I am too old to play games - so try to suggest an ONBOARD option...

_For No. 4_:
I am concerned about my Ubuntu running on 64bit...
a. Is there going to be a problem?
    I would prefer to choose 64bit, because its NEWER Technology...
    I have also read some threads for Ubuntu running on 64bit compared to 32bit...
    I have read that I can install 32bit Ubuntu on a 64bit machine (although it 
    requires some effort - I would prefer if there was some automated way to do 
    this... perhaps a nice script...)
b. Could I also do the opposite:
    Install an Ubuntu 64bit on a PC designed for 32bit?
    (I know it might sound strange to you, but I do NOT want to be working on TOO 
     many different Systems - Windows, Ubuntu 32bit, Ubuntu 64bit, SuSE - I like to 
     keep my life simple...) 

     At the same time, my current PC is a 32bit one....

     My current 32bit PC & the 64bit PC (I might purchase):
     c. Will they be able to communicate through the LAN (a 64bit PC to a 32bit PC)?
     d. Will there be a problem with communicating through my Router?
         (I mean that:
          My 32bit PC works fine with my Router - does the Router HAVE to support 64bit?
          OR:
          The Router will have NO problem communicating with a 64bit PC?)
          I hope I will NOT end up buying a 64bit Router too...!!!

_For No. 5_:
Well, it is new stuff, so it is nice to keep in pace with new technology...

_For No. 6_:
This is to help with some security issues...
Prevents Buffer Overflow when PC's are attacked...
So, I think that this is a MUST!!!

_For No. 7_:
Since my Ubuntu Audio is working Fine in my Current Intel M/B, I think that I should stick to an Intel Audio solution...

I am in between two Motherboards right now:

1. ASUS P5LD2-VM 
[http://uk.asus.com/products4.aspx?modelmenu=1&model=536&l1=3&l2=11&l3=194](http://uk.asus.com/products4.aspx?modelmenu=1&model=536&l1=3&l2=11&l3=194)

2. GIGABYTE GA-8I945GMF
[http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1910&ModelName=GA-8I945GMF](http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=1910&ModelName=GA-8I945GMF)

What do you think I should pick & why?
Has anybody used any of the above M/B's in Ubuntu?
Did you experience any problems/trouble?

Thanks.

P.S. 1> I was also thinking to purchase an Intel M/B but it is hard to find it on PC shops around my neighborhood...

P.S. 2> At the same time, NOT many alternative Solutions (Motherboards) are available around my neighborhood & according to my ABOVE requirements/specs...

---

### Post by el3ktro on 2006-03-28
I can help you with 4) (I'm AMD-addicted, so I don't know much about Intel ;-) )

Well on a 64bit machine you can instal the 64bit version of Ubuntu and the 32bit version - and there's no effort to do so at all, don't know where you've read that. In fact, going 32bit on a 64bit machine is easier, because on 64bit, some (maybe important) things are missing. The first thing is multimedia support - you'll have problems with many video codecs (divx, quicktime, realplayer, wmv, wma etc.) and you don't have Flash at all. You have to decide if thats important for you.

Besides that, and even if you choose to install 32bit Ubuntu, I'd still recommend you to by a 64bit machine, because - as you said - it's simply newer, and you get more for your money. I'm running an Athlon64 here with 32bit Ubuntu without ANY problems. 64bit CPUs will be faster than their 32bit counterparts, even if you run 32bit software, simply because they're newer & have higher clock speeds. Intalling a 64bit Ubuntu on a 32bit PC is NOT possible though.

If your CPU has 32bit or 64bit has **absolutely nothing** to do with your network. A 32bit PC and a 64bit PC can communicate trough a network just fine, regardless of the router you use, regardless of the network cards you use etc. There's absolutely nothing to worry about here. 32bit/64bit only describe how the CPU - and only the CPU - works, the rest of the system is unaffected (harddisks, network cards, graphics cards etc.)

About 2) I can just repeat the same. It doesn't matter at all which vendor you choose for your network card. An Intel network card will work with an Intel, will work with NVidia, will work with 3Com, will work with D-Link .... it doesn't matter at all.


Tom

---

### Post by dvarsam on 2006-03-29
[QUOTE=el3ktro]
...Well on a 64bit machine you can instal the 64bit version of Ubuntu and the 32bit version - and there is NO effort to do so at all, don't know where you've read that...
[/QUOTE]

If you call this_ NO_ effort, go visit this thread:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Thanks.

---

### Post by IDipSkoalMint on 2006-03-29
Try [this]("http://www.xpcgear.com/msi945gneof.html") motherboard. It supports:

Intel 945 chipset
Dual Channel RAM
PCI-E LAN
Onboard 7.1 audio
Integrated Graphics
Will support Pentium D processors

Only thing: It's a MSI motherboard, not an Intel one

Also, the $116 pricetag doesn't break the bank ;)

---

### Post by el3ktro on 2006-03-29
[QUOTE=dvarsam]If you call this_ NO_ effort, go visit this thread:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Thanks.[/QUOTE]

Well as I understand the original poster he suggested that he has read that it is a lot of effort to install a whole 32bit Ubuntu on a 64bit machine - and this indeed is no effort, because you can install 32bit Ubuntu on a 64bit machine just as you can install it on a 32bit machine. What you mean is 32bit chroot within an 64bit Ubuntu install, but thats something different, and indeed needs a lot of work.

So what I meant, it's no problem and no hassle at all to do a full 32bit install on a 64bit machine.


Tom

---

### Post by dvarsam on 2006-04-01
[QUOTE=IDipSkoalMint]Try [this]("http://www.xpcgear.com/msi945gneof.html") motherboard. It supports:

Intel 945 chipset
Dual Channel RAM
PCI-E LAN
Onboard 7.1 audio
Integrated Graphics
Will support Pentium D processors

Only thing: It's a MSI motherboard, not an Intel one

Also, the $116 pricetag doesn't break the bank ;)[/QUOTE]

Dear "IDipSkoalMint",

                            did you try installing Ubuntu on it?

Cause I bought the "ASUS P5LD2-VM" & I can NOT make the GBit LAN work.

Does your LAN work with NO problem, or did you have to install Drivers to make your Ubuntu LAN work?

Thanks.

---

### Post by dvarsam on 2006-04-01
Edit: IF I can not manage to make my ASUS work, I will exchange for your Mobo - that is why I am asking.

Thanks.

---

### Post by Bartender on 2006-04-01
dvarsam -
Do you have an LGA775 CPU that you want to use in your new board?  Or are you starting over new with CPU and board?
Reason I ask is ASUS just announced their first desktop board that'll run the new energy-efficient Core Duo CPU's.  Other manufacturers are right behind.  AMD & Intel are finally taking serious steps toward energy-efficient CPU's (AMD was already ahead of Intel on this) and in a few years the P4's are gonna seem really archaic and wasteful.

[http://www.asus.com/news_show.aspx?id=2654](http://www.asus.com/news_show.aspx?id=2654)

---

### Post by dvarsam on 2006-04-01
[QUOTE=Bartender]dvarsam -
Do you have an LGA775 CPU that you want to use in your new board?  Or are you starting over new with CPU and board?
Reason I ask is ASUS just announced their first desktop board that'll run the new energy-efficient Core Duo CPU's.  Other manufacturers are right behind.  AMD & Intel are finally taking serious steps toward energy-efficient CPU's (AMD was already ahead of Intel on this) and in a few years the P4's are gonna seem really archaic and wasteful.

[http://www.asus.com/news_show.aspx?id=2654](http://www.asus.com/news_show.aspx?id=2654)[/QUOTE]

What exactly are you suggesting?
How much will it cost?
Is it FULLY compatible with My Ubuntu?

IF it is NOT compatible, right from the START, do NOT suggest this at ALL!

Do NOT make me mess-up with these "disgusting" ".tar.gz" file formats....
I WANT ".DEBS" man!!!

If you are suggesting this as a FULLY compatible to Ubuntu, with NO additional installations, then tell me more about it...

Thanks.

---

### Post by dvarsam on 2006-04-01
[QUOTE=Bartender]
...Do you have an LGA775 CPU that you want to use in your new board?

...Or are you starting over new with CPU and board?

Reason I ask is ASUS just announced their first desktop board that'll run the new energy-efficient Core Duo CPU's.
[http://www.asus.com/news_show.aspx?id=2654](http://www.asus.com/news_show.aspx?id=2654)
[/QUOTE]

I visited the site you are suggesting...
Thanks.
And I understood why you were asking about my CPU...

The Socket used in the site you are suggesting is:
> Socket 479 for Intel® Core™ Duo processor
I have already bought the CPU - a Celeron 3.06GHz (Socket 775).

So, since I have opened it's Box, I can NOT return that & buy something else.
What I CAN return is the Mobo (since its Box was NOT sealed & I did NOT violate any "seals").

Basically, I am stuck with the CPU, but with the Mobo, I could choose anyone I want...

However, since you are mentioning a new Socket, I would have to go Bankrupt to buy such a new technology (& Intel would turn expremely rich...lol)...
I would probably wait for a couple of years for this, for prises to do down, to normal standards...

But, anyway, thanks for your idea...

P.S. Any idea, on a Mobo with:
1. Onboard VGA
2. Chipset Intel 945 (no higher, no lower)
3. LAN Gigabit
4. Socket LGA775 (I am stuck with the CPU now)
5. That works with MY UBUNTU right from a Fresh CD Install?

Do NOT put me in trouble with the ".tar.gz" or other St*pid install methods (like "ndishwrapper" - or what is called...).
"DEB's" man, I WANT ".DEBs"!!!

---

### Post by gary1970 on 2006-04-05
I perfer AMD MSI Boards myself . I  have one in my eMachine that has overclocking capabilties which in turns makes one heck of a gaming machine for me at least . Just to add an Nivida FX6800 which i have found out that has overclocking as well plus added 1gig of ram with it . Point blank it's faster than my Dell Dimension 5150  . I hate to say that after paying $2000 for it . Oh well life goes on as they say .

---


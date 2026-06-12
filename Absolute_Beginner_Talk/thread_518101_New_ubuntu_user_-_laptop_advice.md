---
title: "New ubuntu user - laptop advice"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by arpeggi on 2007-08-05
hey guys.
i'm looking to buy a new laptop in the next few weeks before i start uni in september. for a long time i've been considering making the switch - generally totally fed up with windows!

the laptop i've been looking at is a **compaq **and has the following spec:
# AMD Sempron Processor 3400+
# 1600MHz HyperTransport
# 256KB Cache
# 1GB RAM
# 80GB Hard Drive
# DVD ReWriter MultiDrive
# 15.4" Widesceen Display
# Microsoft Windows Vista Home Premium
# 128MB NVIDIA GeForce Go 6150 Graphics

just wondering if any of you guys had any thoughts about potential problems i could face making the swtich (well dual booting to start with) by looking at the specs. or if anyone here knows of any other better UK deals at the moment - hopefully something around the £300 mark.

thanks guys!

---

### Post by ddrichardson on 2007-08-05
Looks OK - but find out the make and check if there are any problems with the soundcard.

---

### Post by wolfen69 on 2007-08-05
if it has wireless, you may have to tweak a little. but otherwise it looks like it should be fine.

---

### Post by p_quarles on 2007-08-05
I bought a similar Compaq setup recently, and it works great. Is this the V6000 series, by chance?

One word of advice: I don't know if there are different upgrade options in HP's UK store, but I chose the Intel Pro/Wireless 3945 ABG card, and it worked out of the box. The default was an HP card that has a poor track record with Linux. (EDIT: of course, I also chose an Intel processor; don't know if that option is available for the AMB option).

---

### Post by Majorix on 2007-08-05
I wouldn't go with an AMD processor. They have poor Linux support.

---

### Post by equal on 2007-08-05
From all my experience with various computers, I think your experience will be a breeze with that box.

---

### Post by superstylin on 2007-08-05
Are any other vendors besides Dell offering Laptops with Ubuntu?

:O

---

### Post by irish_flu on 2007-08-05
arpeggi-

Check out this website:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

It has user-submitted reviews (by brand---> model) of many laptops, and what sort of experience these folks had putting various flavors of Linux on them.

Of course, if you're buying a newly-released model there might not be anything useful to you (but you can likely get some idea from reviews of a similar model, or of a corresponding HP-branded model).

I wouldn't take that site as gospel regarding what your experience will be like, but it might help....

---

### Post by tprzepiorka on 2007-08-05
> **superstylin said:**
> Are any other vendors besides Dell offering Laptops with Ubuntu?

:O

Yes, [http://system76.com/](http://system76.com/)

Not sure if they ship overseas though...

---

### Post by ugm6hr on 2007-08-05
I think this is almost identical to the one I got (mine is a 5051AWXMi - only spec difference I can see is the MK38 rather than my MK36 processor, and 1GB rather than 512MB).

If you want to see how I got on - go the "Post your xorg" link in my signature.  Essentially - everything that I've tried works, with the exception of the card reader (so far).

EDIT: The link I forgot before [http://www.ebuyer.com/UK/product/126329](http://www.ebuyer.com/UK/product/126329) (£350)

---

### Post by nichipet on 2007-08-05
ZaReason ([http://www.zareason.com](http://www.zareason.com)) ships Ubuntu laptops internationally, from California.

---

### Post by arpeggi on 2007-08-05
wow thanks for all this advice so far!
i wasn't expecting this sort of response for such a topic!

unfortunately for me customisation is totally limited. the (oh so poor) student budget has made me look for the budget laptops at currys and dixons - normally paces i'd never have dreamt i'd be looking!  it's probably an F500 range compaq. although if anyone else has a good suggestion from this list i'd be grateful!  [http://www.dixons.co.uk/martprd/store/dix_page.jsp?page=ProductList&category_oid=-32665&fm=undefined&sm=undefined&tm=undefined&show_all=true&BV_UseBVCookie=Yes](http://www.dixons.co.uk/martprd/store/dix_page.jsp?page=ProductList&category_oid=-32665&fm=undefined&sm=undefined&tm=undefined&show_all=true&BV_UseBVCookie=Yes)

cheers :D

---

### Post by zakalwe_ukuk on 2007-08-05
novatech.co.uk do OS free laptops. You have to select the option at checkout and the price comes down quite a lot without windows on there. The laptops aren't big names but i've seen some good comments about novatech. might be worth checking out.

---

### Post by ayenack on 2007-08-05
How's it going fella, Don't forget that PC World are offering free laptops with Orange Broadband it's £14.99 a month if I remember right might be worth a stroll down to your local PC world for a look. They're not the best laptops in the world but they run WinXP so they should run Ubuntu no Probs.

---

### Post by misfitpierce on 2007-08-05
compaqs usually work quite fine with ubuntu... Mine did when I had it. You may want to check out DELL ubuntu pre-loaded laptops. My friends just got one in and they are speedy fast and no probs whatssoever.

[http://dell.com/open](http://dell.com/open)

---

### Post by ugm6hr on 2007-08-11
Have you seen that Dell UK are now doing Ubuntu laptops (actually cheaper than with Windows too)?

[http://www.dell.co.uk/ubuntu](http://www.dell.co.uk/ubuntu)

---

### Post by arpeggi on 2007-08-13
gah.  :(

 so that currys deal disappeared before i acted quickly. i'm looking for a decent laptop somewhere between £300 and £400.  has anything cropped up with you guys?

---

### Post by fastpakr on 2007-08-13
The specs sound suspiciously like the Compaq F572us model that I've got.  On paper, it's a good unit and I'd be happy with it except for a couple of things:
1) If you ever send it in for warranty repair, they WILL re-flash the original OS image onto the drive, regardless of your wishes or the absolute stupidity of doing so.  They will NOT flex on this.  Be prepared to back up your entire / and /home partition if you have any reason to send it in.
2) Compaq/HP and a couple of others have whitelists of the allowed wireless cards programmed into the BIOS image.  The card shipped with my F572us was a Broadcom based unit and even with the correct driver loaded using ndiswrapper, it's very flaky.  I tried switching it to a Gigabyte card with an Atheros chipset, only to find out that the system refuses to boot with it installed (search for '104-unsupported wireless device').  There are a couple of hacks to work around this, but they are VERY invasive.

It's a good laptop, but the company behind it has made some horrible policy choices.

---

### Post by ugm6hr on 2007-08-13
> **arpeggi said:**
> gah.  :(

 so that currys deal disappeared before i acted quickly. i'm looking for a decent laptop somewhere between £300 and £400.  has anything cropped up with you guys?

Did you read my posts?

[http://www.ebuyer.com/customer/products/index.html?rb=0&product_uid=126329&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&filter_display=both&filter_order=rating_desc&filter_category=&filter_string=&offset=10](http://www.ebuyer.com/customer/products/index.html?rb=0&product_uid=126329&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&filter_display=both&filter_order=rating_desc&filter_category=&filter_string=&offset=10)
This has a review (23 July 2007) that states that Ubuntu and PCLOS LiveCDs run fine, and is very similar to my current machine (5051AWXMi).  For £350, very good value.

[http://www.dell.co.uk/ubuntu](http://www.dell.co.uk/ubuntu)
From £329 for a fully pre-installed Ubuntu machine.  Or more like £380-400 if you want Dual-core (with/without Vista).  Good option for Ubuntu compatibility (and presumably support) - if that's your main priority.

---

### Post by arpeggi on 2007-08-14
that dell looks alright - it's a bit short on a few things though and i'd want a system with vista preinstalled so i could dual boot for some programs required by my course.

for £329 the specs are:

Components
AMD® Athlon™ 64 X2 Mobile Technology TK53
Genuine Windows Vista™ Business - English
15.4" Wide Screen WXGA (1280 x 800) Display with TrueLife™
2048MB 533MHz Dual Channel DDR2 SDRAM [2x1024]
120GB (5400rpm) SATA Hard Drive
ATI Radeon® Xpress 1150 HyperMemory (integrated)
Fixed Internal 8X DVD+/-RW Drive including Software
9 cell Lithium-Ion Battery (85 Whr)

there's also the offer to upgrade the following:

Dell™ Wireless 1490 802.11a/b/g Mini-Card - Europe [add £15.00]	
Dell™ Wireless 1505 Wireless-N Mini-Card - Europe [add £40.00 or £1/month1]

i know linux has problems with wifi - would either of these help?

they're also offering me to swap the vista business for home premium.

what do you guys reckon?

---

### Post by arpeggi on 2007-08-14
or should i look at the better vostro's with the core 2 duo?

---

### Post by p_quarles on 2007-08-14
Avoid Dell's wireless cards. Even they don't use them on their Ubuntu machines.

---

### Post by ugm6hr on 2007-08-14
Which Dell is that?

About wifi - all the Dell wifi cards are Broadcoms (notoriously poorly supported in Linux).

Dell do an Intel 3945 card, which is a better choice (as available in the 6400).

---

### Post by fastpakr on 2007-08-14
From everything I've read, even the Intel 3945 isn't a particularly good choice on the Linux side.  Assuming it's a Mini PCI-E slot, check out the Gigabyte GN-WI01GT.  You can get it for less than $30US and it just plugs in and works (unless you're like me and stuck with a Compaq that won't even boot with it...).  Just sell whatever card comes with it for a few dollars/pounds and put it towards the new card.

---

### Post by arpeggi on 2007-08-14
but they're internal cards..!

---

### Post by p_quarles on 2007-08-14
> **fastpakr said:**
> From everything I've read, even the Intel 3945 isn't a particularly good choice on the Linux side.  Assuming it's a Mini PCI-E slot, check out the Gigabyte GN-WI01GT.  You can get it for less than $30US and it just plugs in and works (unless you're like me and stuck with a Compaq that won't even boot with it...).  Just sell whatever card comes with it for a few dollars/pounds and put it towards the new card.
My internal Intel 3945 worked out of the box without needing to configure a thing. Fully supports WEP, WPA and WPA2. What kinds of problems were people having with it?

---

### Post by fastpakr on 2007-08-14
I'll have to go back and look, but I remember reading a lot of people having to use ndiswrapper or various methods to get them working.  What form factor is your card?

---

### Post by fastpakr on 2007-08-14
> **arpeggi said:**
> but they're internal cards..!

What are you getting at?  Even the internals are easy to swap.

---

### Post by ugm6hr on 2007-08-14
> **fastpakr said:**
> From everything I've read, even the Intel 3945 isn't a particularly good choice on the Linux side.  

Really? That's the card Dell use in their Ubuntu machines - so that is a bit worrying.  And I thought Intel were one of the few component manufacturers that actively support Linux.  It's also the Linux wifi card that other suppliers use for Ubuntu (e.g. [http://efficientpc.co.uk/components/](http://efficientpc.co.uk/components/))

---

### Post by arpeggi on 2007-08-14
gotcha! sorry i don't know that much about hardware upgrades!

there's also this other vostro. it's core 2 duo which i think is  a bit better..

Components
Intel® Core™ 2 Duo T5470 Processor (1.6GHz,800MHz,2MB L2 cache)
14.1" Wide Screen WXGA+ (1440x900) TFT Display with TrueLife™
Matte Jet Black with 2.0 mega pixel camera
2048MB 667MHz Dual Channel DDR2 SDRAM (2x1024)
120GB (5400rpm) SATA Hard Drive
Integrated Intel® Graphic Media Accelerator X3100 with 65 watt AC adapter
Fixed Internal 8X DVD+/-RW Drive including Software
Intel® Pro Wireless 3945 802.11a/b/g Mini-Card - Europe

it's an extra hundred quid though.

---

### Post by fastpakr on 2007-08-14
> **ugm6hr said:**
> Really? That's the card Dell use in their Ubuntu machines - so that is a bit worrying.  And I thought Intel were one of the few component manufacturers that actively support Linux.  It's also the Linux wifi card that other suppliers use for Ubuntu (e.g. [http://efficientpc.co.uk/components/](http://efficientpc.co.uk/components/))

Interesting, I'll go back and do some more reading on this.  If it turns out the Compaq allows that card (doubtful), I might have to try switching to it.  There was definitely some discussion here on this, but maybe it's outdated and the card is now also directly supported like the previous Intel cards.

---

### Post by p_quarles on 2007-08-14
> **fastpakr said:**
> Interesting, I'll go back and do some more reading on this.  If it turns out the Compaq allows that card (doubtful), I might have to try switching to it.  There was definitely some discussion here on this, but maybe it's outdated and the card is now also directly supported like the previous Intel cards.
Mine's on a Compaq, actually, and it was among the options when I was putting it together. 

This is the card I have:
[http://www.intel.com/network/connectivity/products/wireless/prowireless_mobile.htm](http://www.intel.com/network/connectivity/products/wireless/prowireless_mobile.htm)

I noticed, too, that Intel has the Linux driver available for download there, too. Doesn't matter for Ubuntu users, though, as its included in the restricted drivers module.

---

### Post by fastpakr on 2007-08-14
Is your Compaq one of the ones with a whitelist block applied to cards?

---

### Post by p_quarles on 2007-08-14
> **fastpakr said:**
> Is your Compaq one of the ones with a whitelist block applied to cards?
I don't know, but if you'll tell me how to check I'm happy to find out. Is there a way to get this to show up in the BIOS?

It's a customized V6000t, if that helps at all.

---

### Post by amazingtaters on 2007-08-14
> **Majorix said:**
> I wouldn't go with an AMD processor. They have poor Linux support.

My AMD works, I've got a Turion x2 TL-50. But I'm also an AMD fanboy, so I'd never buy an Intel processor unless I had to.

As far as specs on that laptop, its definitely got the power to run ubuntu solidly.

---

### Post by fastpakr on 2007-08-14
I'm pretty sure our laptops are in the same basic series, but I don't know how to tell you to check other than trying out a different card.  You don't have access to another brand card that you could plug in, do you?

---

### Post by fastpakr on 2007-08-14
> **Majorix said:**
> I wouldn't go with an AMD processor. They have poor Linux support.

Based on what?  The 64 bit version of Ubuntu does require a little extra work to get some things going, but that's hardly an AMD issue.  To what are you refering, exactly?

---

### Post by fastpakr on 2007-08-14
> **p_quarles said:**
> I don't know, but if you'll tell me how to check I'm happy to find out. Is there a way to get this to show up in the BIOS?

It's a customized V6000t, if that helps at all.

I just found out that my wife's Thinkpad has a Mini PCI-e 3945, so I'm borrowing that to test on the Compaq tomorrow when it comes in from being repaired (bad power jack straight out of the box).  So far, the only thing Compaq's earned credit for on this laptop is their turnaround time - I shipped the laptop to them on Friday, they got it on Monday, shipped it Tuesday, and I'll have it on Wednesday.  They've recovered a few of the points they lost on the wireless issue and the issue with wasting my hard drive when I sent it in.

---

### Post by p_quarles on 2007-08-14
> **fastpakr said:**
> I just found out that my wife's Thinkpad has a Mini PCI-e 3945, so I'm borrowing that to test on the Compaq tomorrow when it comes in from being repaired (bad power jack straight out of the box).  So far, the only thing Compaq's earned credit for on this laptop is their turnaround time - I shipped the laptop to them on Friday, they got it on Monday, shipped it Tuesday, and I'll have it on Wednesday.  They've recovered a few of the points they lost on the wireless issue and the issue with wasting my hard drive when I sent it in.
Good to know. Of course, my computers usually only break *after *the warranty is up, so we'll see if I ever get to enjoy the quick turnaround time. 

Hope it works for you. It is a really good adapter.

---

### Post by Arthur Archnix on 2007-08-14
HP 530 is a budget laptop that's a dream for ease of use. Check out the support thread...no outstanding issues!!

[here]("http://ubuntuforums.org/showthread.php?t=502833&highlight=hp+530")

---


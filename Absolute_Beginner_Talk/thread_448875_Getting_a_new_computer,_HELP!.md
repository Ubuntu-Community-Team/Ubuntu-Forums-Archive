---
title: "Getting a new computer, HELP!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by JC_510 on 2007-05-19
Im looking at getting a new laptop (didn't post this in the laptop section because im going to be asking alot of noob questions, so thought it would be better placed here!)

Is there anything that I should look out for when getting the laptop for it to run well on Ubuntu? Im planning on doing an XP dual boot, with Ubuntu occupying most of the disk space, and being the primary OS.

I've pretty much decided on the spec *(AMD Dual Core processor 1.6Ghz+, 2GB RAM, 100GB+ HD, 256mb graphics, costing a maximum of £800 GBP)*, but as i'm not very experienced in this (this is the first computer i am buying, i currently use a family PC running XP), I wondered if there are any particular things I should look out for when getting the laptop. Do I get a particular make? Are there certain pieces of hardware to avoid?

My main uses for the computer will be office apps, design apps (GIMP, Inkscape), Firefox, and anything that my planned university course in architecture throws at me!

Again, im not very experienced with computer hardware, and any help at all will be most welcome.

P.S. I recently came across the website of Ubuntu Studio, and it looks pretty cool. Will it work the same as Ubuntu but just with extra apps, or is the operating system different in any major way?

P.P.S. Link to an almost ideal-looking laptop I found: [**Here**]("http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@0960820193.1179605716@@@@&BV_EngineID=ccchaddkmemmffjcflgceggdhhmdgmh.0&sku=169723&tabIndex=1&page=Product")

**Thanks**

---

### Post by Hobo Joe on 2007-05-19
Those specs will run Ubuntu just fine. And yes, Ubuntu Studio will be the same execpt for some added apps and different looks, it's very similar to normal Ubuntu.

---

### Post by JC_510 on 2007-05-19
Cheers Joe.

Sorry, were you referring to the specs on the link that i posted, or the ones that I stated in the post? (I know theyre virtually identical, but i dont know if all of the hardware in the link will be compatible with Ubuntu) :confused:

---

### Post by ugm6hr on 2007-05-19
I have just installed Xubuntu on a new Acer laptop (Aspire 5051), and in general, Acer use Linux compatible hardware, but will not support a Linux-installed laptop at all.  Should be OK with dual boot though.  It's hard to know how compatible any laptop will be without trying it.  

Options: 
1. Go to PC World and try a Live CD out on the laptop.  You could also type lspci into Terminal to find out exactly what hardware the laptop has in it
2. Go to Acer website [www.acer.co.uk](www.acer.co.uk) and go to their support / driver downloads section for the laptop concerned.  Have a look at the drivers available - this will give you a clue as to what hardware chipsets it uses for e.g. ethernet, wireless, modem etc.

Then search on here for any known problems with the various components.
The potential problems are with the 5-in-1 card reader (mine is an ENE device, which is totally incompatible with Linux), modem, and wireless chipset.  From what I've read, NVidia graphics cards are generally Linux-tolerant (but might be worth checking).

---

### Post by JC_510 on 2007-05-19
So Acer works well with dual boots, but not with Linux-only laptops?

Ok, when I receive the Live CD I'll go to PC World, but I know virtually nothing about drivers and hardware in general, so I dont think I'll have any luck on point 2!

Thanks

---

### Post by Hobo Joe on 2007-05-19
> **JC_510 said:**
> Cheers Joe.

Sorry, were you referring to the specs on the link that i posted, or the ones that I stated in the post? (I know theyre virtually identical, but i dont know if all of the hardware in the link will be compatible with Ubuntu) :confused:

The ones you posted, just make sure that the one you buy doesn't have an ATi card. While it's possible to get them working under Linux, it's a big headache. I'm speaking from experience here!

---

### Post by JC_510 on 2007-05-19
Thanks. Sorry, (noob question), whats an ATi card?

---

### Post by ugm6hr on 2007-05-19
ATI card is a Graphics card.  The PC World Acer you have linked to has a NVidia Graphics card, which, as I said, I think should be OK.  ATI and NVidia (and Intel) are different manufacturers of Graphics Cards.

I think you misunderstood me - the laptop will probably work fine with either dual boot or Linux alone, but Acer Customer Service / Warranty will refuse to help if Windows does not remain on the laptop.  i.e. you need to keep Windows for at least as long as the warranty (which you plan to do anyway - and is sensible since you're paying for it).

---

### Post by southernman on 2007-05-19
> Thanks. Sorry, (noob question), whats an ATi card?It's a brand of graphic card that drives your monitor/screen

---

### Post by ruscoe on 2007-05-19
> **JC_510 said:**
> Thanks. Sorry, (noob question), whats an ATi card?
A graphics card. My laptop has an ATI card and, using the standard drivers that come via the Restricted Drivers Manager, Compiz and Beryl will not work.

My particular card is also not friendly to the alternate ATI drivers which do work with Compiz.

I'm told NVIDIA is the way to go for now, although ATI are supposed to be improving their Linux drivers.

---

### Post by JC_510 on 2007-05-21
Ah, I thought so, but wasn't too sure! Thank you all for the help.

Hopefully I'll get the computer within a month's time, and then I'll put Ubuntu on it straight away! (Hopefully the Live CD will have arrived by then).

Another question (sorry): The laptop that I posted in my first post has the  following processor: *AMD Mobile Turion 64 X2 Dual Core TL-52*. Sounds like a stupid question, but as its a 64-bit processor, should I run the 64-bit version of Ubuntu, or does the normal 32-bit version have some benefits? Again, im speaking as a noob here, I'm not even totally sure how 32bit and 64bit work :confused: 

Thanks.

---

### Post by JC_510 on 2007-05-22
UPDATE: I'm downloading the Live CD as I write this (58% - Hopefully will be done within an hour or so!). So I shall soon find out whether or not I'll be running Ubuntu on my new machine, based on my experience with the CD! :D I've got an AMD 64 processor, so I hope I made the right decision in downloading the 64-bit version - seemed self explanatory :confused:

---

### Post by ugm6hr on 2007-05-22
The 64-bit version will indeed run just fine on your AMD Turion.  Although the i386 version would be equally compatible.  

As a beginner, I went for the i386 version, because I believe it's better supported with compatible drivers / software, although technically the 64-bit version should be more efficient.

---

### Post by cotcot on 2007-05-22
I do not see a reason to install Ubuntu Studio. Install the normal ubuntu and add with synaptic what you want. I use kdenlive. This is not included in Studio.

---

### Post by JC_510 on 2007-05-23
Ok, so the i386 version will work the same (or slightly less efficiently), but is better supported in terms of software? If thats the case, I'll run the normal i386 version, and I wont bother with Studio :)

My computer doesn't like the live CD. I went into the BIOS to make it boot from the CD drive, but when i tried to change the 1st boot device to CD it said that it was 'view only'. So im guessing this means i cant use my desktop to test out Ubuntu :confused:

Bit of a pain in the a, guess I'll just have to wait till the laptop arrives! (Unless anyone has any ideas :p)

Thanks

---

### Post by SomethingCronic on 2007-05-23
I would strongly recommend using the i386 cd as opposed to the 64 bit version. A lot of software will need endless tweaking if you choose the 64bit version as it's still quite new (in comparison to 32bit version anyway).

Also, if you have downloaded the 64 bit version and your testing it in a 32bit PC (which I assume you are) then it wont work.

- Mike

---

### Post by JC_510 on 2007-05-23
Ah, ok, thanks for the warnings about the 64-bit version!

No, I am trying to test it in a 64-bit PC (Ive got an AMD athlon 64), but the BIOS wont let me change the boot device. I go into settings, and I get to the bit where it says '1st boot device: HDD-0', but when I go to change it to the CD drive, it says 'view only'.

---

### Post by ugm6hr on 2007-05-23
> **JC_510 said:**
> Ah, ok, thanks for the warnings about the 64-bit version!

No, I am trying to test it in a 64-bit PC (Ive got an AMD athlon 64), but the BIOS wont let me change the boot device. I go into settings, and I get to the bit where it says '1st boot device: HDD-0', but when I go to change it to the CD drive, it says 'view only'.

Really?  There must be a way to boot from CD, because otherwise you couldn't re-install Windows either (which all hardware manufacturers must know is necessary not infrequently!).  Sometimes you have to press a different F-key to get to a temporary boot menu during startup.  The other possibility is that your motherboard has a password set up - so it will not allow BIOS changes - perhaps that's what "View only" means?  Only way to know is to find an instruction manual for the motherboard.

---

### Post by jbrown96 on 2007-05-24
Compatibility wise I think that either choice is good. As the others have said, stick with nVidia because their Linux drivers are much better right now. I couldn't find what type of wireless card is used, but that is a huge problem in Linux. You can get almost any card to work, but certain manufactures (broadcom I know for sure) are difficult to install, especially for people new to Linux. I'm not familiar with the good manufacturers, but you should be able to find out in the forum.

Ubuntu has very good support with most laptops now. On my laptop, all the media and extra keyboard functions work flawlessly with no setup. On another computer, the Flash card reader worked perfectly, but the wireless was a nightmare (broadcom 4311 - STAY AWAY).

I would not recommend 32-bit over 64-bit, without trying both. My laptop is 32-bit but the other is 64-bit. I could not find a way to get the broadcom wireless working with the 32-bit Ubuntu. Firefox (web browser) will not work properly with 64-bit Ubuntu because there are no 64-bit Flash or Java plugins. Firefox is the only program that I have had trouble with in 64-bit Ubuntu; however, this can be avoided by using Swiftfox or a 32-bit version of Firefox. There should be 64-bit Java and Flash sometime this year, so it won't be an issue much longer.
From a hardware standpoint, use 64-bit. Software wise, 32-bit is easier now but that's changing.

---

### Post by JC_510 on 2007-05-24
Yeah, I'm guessing it is password protected. I hit Del for setup, and it brought me to a password screen. I just pressed enter without entering a password, and I got into setup, but I reckon it was a 'view only' setup, where any major changes are prohibited. Hence, 'view only'.

So I guess I'll just have to wait till I receive the laptop. I'll just test both the 32-bit and 64-bit versions on it - the Live CDs arrived today, and I ordered a 32-bit and 64-bit version for this purpose.

---

### Post by SomethingCronic on 2007-05-24
I do agree with jbrown96 in that you can try both CDs and make your own decision, but you won't really notice much difference between the two immediatly, until you try to install something that simply won't work on the 64 bit version.

Your cleary new to Ubuntu, and although it is easier than ever to install, configure and use - it's not perfect. The 64 bit version can put people off Ubuntu because it can give the impression that to use something like 'flash' it so difficult

---


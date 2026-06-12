---
title: "SUCCESS - Skype, 7.04, USB Telbox"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-01-27
I just wanted to post a success here.  A little background:  the USB Telbox (b2k) is a box that hooks into your regular phone line, then to both your regular phone and a USB port on your PC.  The idea is to not need a separate "Skype" phone of some sort.  In my case, I have wanted to use my regular cordless phone to make calls via the regular phone line and via Skpe.

This all requires 3 things:

- usbb2k_api     => a background program that does the major work
- kb2kskype      => like the old SkypeMate, but for Linux
- Skype

There is a sourceforge site for kb2kskype that covers both the api and kb2kskype at
[http://kb2kskype.sourceforge.net/news.html]("http://kb2kskype.sourceforge.net/news.html").

I had followed this, albeit with an older version of both the api and kb2kskype, with an install of Gutsy 7.10, but had really bad choppy audio.  My CPU was being pegged without me doing anything, so I suspected I was out of luck with this PC (an old P3-500, 512mb memory).  I recently acquired a 80 gig drive to use instead of my old 10 gig, so I put a completely fresh install of Ubuntu on it, this time going back to Feisty Fawn 7.04 as everything just seemed slower and I was having problems with 7.10.  So tonight I decided to try the USB Telbox/Skype tthing again.  They had updates for the api and kb2kskype since I had tried last so I got the latest versions.  There are a lot of dependencies that must be met 1st - I just used Synaptic to get them all (there is a link to an Ubuntu how-to in the Skype for Linux forum).

Well, after a LOT of time, it all works great now!  Yep - I can call out on my regular line or use Skype, all on my regular cordless phone.  Audio seems fine now - I suspect this was something in the low-level stuff in the API that was eating the CPU before but doesn't now.

I'm not ready yet to try it in Gutsy.  But I am very happy this works now.

The USB Telbox comes in many flavors and are available at many places - I got mine on EBay for a reasonable price (I don't remember for sure, but I think around $20).  I am on disability, so I needed a way to make long distance phone calls to my family around the country.  SkypeOut was really cheap for a year and now those calls are "free" with my SkypeOut.  When a year is up I'll need to re-up with SkypeOut but it is a LOT cheaper than paying long distance phone rates.  If the person you want to call also has Skype then it's a free call - you don't even need SkypeOut (my folks are in their late 70's and trying to setup and use Skype via a phone conversation with me isn't something I wanted to do, hence why I use SkypeOut).

Oh well - I don't mean to sound like an advertisement for any given product here, and I know there are other free computer-to-computer phone services available.  I just wanted to pass along my success for what I wanted to do.

If anyone has any questions they can reply here, but keep in mind I'm not an expert - just your average Joe who got this working following stuff on the web.:)

---

### Post by deoncarr on 2008-04-20
Hi Gary,

Good to hear someone has had success with this box. I have the same box but am having problems with my audio out. 

I have done a skype test call and the the receiver quality is fine. No probs. When I leave my message however I am getting occasional electronic distortions, very quiet audio and choppy sound playback.

I am using Gutsy on a ATI 780G board.
I am using the latest kb2kskype and usbb2k.

Any chance you can post your ~/.Skype/shared.xml file.

What is the mic volume you are setting in kb2kskype? This is a slider but can you give an indication of the value you are using.

Have you disabled skype to automatically control the sound volume?

Did you ever experience my problem in your latest attempt or did it just work first time this time?

Did you have to do any tweaking to get it to work?

Thanks for your help.

D

---

### Post by deoncarr on 2008-04-21
Hi there.

I think the issues I am having are due to my motherboard. Last night I tested the skype box using my notebook running gutsy. No sound issues.

When running the same telbox on my desktop which has at ati 780g chipset, the mic problems are as described earlier. 

I have read another post with some guy experiencing the same problem with the ati 690g chipset.

thx

D

---

### Post by deoncarr on 2008-04-22
The cause of this problem is a USB power issue. I have tried the box with a powered hub and all my problems went away.

More info below from a mplat forum. I had to view the forum from a cache as the page seems to be down so i have pasted it below

> Oh boy am I having problems! Bought the B2K and set it up (after loads of trouble with cables in the UK) and it worked fine! I was impressed!

Upgraded the machine the box was running on to an MSI RS480M2-IL using the Ati Xpress200P Chipset. Set the box up again and got it working.

Unfortuantly now I hear the other person on the skype call fine, but they hear my voice as distorted! I tested by ringing another account in my house and sure enough the voice being sent is distorted, but I hear everyone else fine. Same phone even!!!

Literally the only thing to have changed is the motherboard! I have also noticed when I plug in the box it detects as a Hi-Speed USB device on a non high speed port. I am not sure how or why becuse I thought they were both USB 2.0. Either way I doubt this is the cause as surely it will run fine @ USB1.1?

Any ideas

admin

26 Posts
	
Posted - Oct 25 2005 :  22:30:20  Show Profile  Reply with Quote
The telbox work fine under USB1.1, We also interested in you said" they hear my voice as distorted", Or you can contact us for this? thanks.
Go to Top of Page

tw19cl

3 Posts
	
Posted - Nov 04 2005 :  02:05:38  Show Profile  Reply with Quote
i am having same problem, i hear the other person fine but they hear a buzz/misquito/fly noise over my voice. i have tryed to turn down the mic (thinking it is over saturating the recording but skypemate keeps increasing the mic volume

any help???

thanks timothy
tw19cl is my skype name so call me and see for your self!!
Go to Top of Page

coalfield

8 Posts
	
Posted - Nov 04 2005 :  02:15:29  Show Profile  Reply with Quote

    quote:Originally posted by tw19cl

    i am having same problem, i hear the other person fine but they hear a buzz/misquito/fly noise over my voice. i have tryed to turn down the mic (thinking it is over saturating the recording but skypemate keeps increasing the mic volume

    any help???

    thanks timothy
    tw19cl is my skype name so call me and see for your self!!



What motherboard is the B2K on?
Go to Top of Page

tw19cl

3 Posts
	
Posted - Nov 04 2005 :  13:30:11  Show Profile  Reply with Quote
i am using a toshiba satelite M40 laptop. using the skypeout from my pc (eg using mic and speakers i get A1 quallity both ways it is only when i use the b2k box i get the distortion. i have tryed 2 phones a corded phone and a 900mhz cordless.. both are the same.

also my system states that i have connected to 1.1USB could this be the problem?? (the ports are USB2)

i will try and use my server to see if it is better..

thanks timothy.
Go to Top of Page

Jack

Belgium
1 Posts
	
Posted - Nov 05 2005 :  05:32:10  Show Profile  Reply with Quote
I had exactly the same problem.
I linked the box to a USB2.0 port (on a USB2.0 PCI card). I had noise when I spoke.
Then I have link the box to a USB1.1 port (standard port on my motherboard) on the same PC. The noise is disappeared.
I think the box is not compatible with USB 2.0.
Go to Top of Page

tw19cl

3 Posts
	
Posted - Nov 05 2005 :  16:00:28  Show Profile  Reply with Quote
well now i have tryed the b2k on my asus motherboard set up and the quality is exelent!
the variables that were changed from not working well to working exelent are:
different computer
computer linked to network via lan not wireless like the laptop was

so to make a conclusion the b2k could be sencitive to different usb ports? (slight variation to the standared) or could just be the delays attributed to the wireless network. but i tests the usb b2k on the laptop via windows audio test function and it also sounded crackly thus the problem mostlikely is the b2k sond card has some incompadibility with different usb hardware (being slight variations from the USB standard)

i hope this makes some sence


thanks timothy

Go to Top of Page

mtudor

5 Posts
	
Posted - Nov 27 2005 :  08:22:54  Show Profile  Reply with Quote
I can confirm a similar problem. Hissing and crackling on the phone. Moved the B2K box from a USB port on the back of my PC to one on the front and voila, no hiss (bar what you might expect with a cordless phone).

So it seems that the USB port might affect the quality of the call - maybe there is a conflict or something with some ports. Worth a try if you are having crackles on your phone.

Cheers,

Mark.
Go to Top of Page

coalfield

8 Posts
	
Posted - Nov 27 2005 :  11:16:42  Show Profile  Reply with Quote
I have fixed it now by.... purchasing a ALI PCI USB Controller card! Cost me £10 on ebay, but has not fixed the problem. It still only detects as USB 1.1, but works fine now. There must be some compatibility issues with the box.. wish is kinda gutting but glad we got to the bottom of it now. Been out of action for about 3 months while i figured it out

If anyone else has this problem please post the motherboard or controller with the problem, we may be able to figure out which / why.

Thanks
Go to Top of Page

mplat

Canada
253 Posts
	
Posted - Nov 28 2005 :  09:01:29  Show Profile  Visit mplat's Homepage  Reply with Quote
For this case, try to use the trial freeware, USBinfo from [http://lpt.usbfireinfo.com/](http://lpt.usbfireinfo.com/)

Optimize Your PC and USB Devices Easily View, Explore and Browse USB Devices and their related devices such as USB Drives Determine whether your USB Controllers, Hubs and Devices are really USB 2.0 or not .

Determine how fast your USB 2.0 Devices really are Measure and compare the performance of your USB Devices View all of yourConnected USB Devices in Topology Tree format and how they are currently configured and connected.

Troubleshoot USB Device and installation problems and determine if your USB Devices are working correctly Easily determine which USB Device is related to what USB Drive Stop USB Devices so they can be safely removed See at a glance all of the USB Devices and Registry Entries that have been installed.

Easily match up which Registry Entries are for which USB Devices and determine which Registry entries are active and that match your USB Devices ?

Also find Registry entries that have incomplete/incorrect information in them or that no longer apply to the USB Device hardware that is currently installed. Review Advanced Technical Information for USB Devices.

Hope this help.
Thanks for your posting.

For your privacy, if you think some questions are not suitable for pubic,please send an email to [email]support@mplat.com[/email]
Go to Top of Page

lshamash

1 Posts
	
Posted - Jan 07 2006 :  08:44:13  Show Profile  Reply with Quote
Hi there,

Have tried the Telbox with 4 different PC's, 2 always work, the two that don't are:
Toshiba M40 satellite (just like tw19cl)

Shuttle XPC

Has anyone tried an external USB hub? Any thoughts from Mplat?

Thanks,
Larry

Go to Top of Page

spe

United Kingdom
10 Posts
	
Posted - Jan 27 2006 :  10:17:13  Show Profile  Reply with Quote
This appears to be a very common problem with V2.0 USB cards. I know of 4 users, all of which suffered from these symtoms to one degree or another.

Ironically, since they are so cheap, I've found that VIA based PCI USB2.0 cards seem to suffer less noise and speech distortion than others. It may come down to power handling on the cards though rather than the chipset itself.

I've even resorted to sending USB cards by post to relatives in Australia who couldn't get past the garbled speech or simple zero functionality using B2K in the various USB sockets on their systems.

Mtudor you are correct, the USB2.0 port in use does make a difference, even on the same controller, which is why I think it may be a power issue.

I didn't try any powered external USB hubs though, good idea Ishamash, thanks.
Go to Top of Page

coalfield

8 Posts
	
Posted - Jan 27 2006 :  14:03:05  Show Profile  Reply with Quote
I must say its a big shame. I really hope they find some way to overcome it without buying PCI USB cards. More money & more hassle :(
Go to Top of Page

mplat

Canada
253 Posts
	
Posted - Jan 28 2006 :  10:27:44  Show Profile  Visit mplat's Homepage  Reply with Quote
When you said big shame, we feel very upset for this word, if you use some USB test software, you will know some computer said support USB 2.0, but not like this.

Thank you for your understanding.
Thanks for your posting.

For your privacy, if you think some questions are not suitable for pubic,please send an email to [email]support@mplat.com[/email]
Go to Top of Page

mplat

Canada
253 Posts
	
Posted - Jan 30 2006 :  08:36:14  Show Profile  Visit mplat's Homepage  Reply with Quote
One partner from Quebec had one solution, we don't test and confirm, this message is only for your reference.
Thank you, Larry.
=============================================
hi, there
I am a reseller in Canada (Quebec). I have bought 5 Telco boxes, and of the 5 2 installations were giving me the outgoing noise problem that is mentioned in the forums. One was a Shuttle PC, the other a Toshiba laptop (as per timothy in the post).

FYI ¨C this is useful info for you ¨C Any reward for this???

I was able to solve the problem, by installing external powered USB hubs¡* And had to incur the expense for same... It works perfectly with the APC USB 2.0 HUB ($30 from Costco) and a Linksys USB Pro-Connect. I believe this confirms that the boxes have some compatibility problems with some ports. Something to do with recognizing it as 2.0 but operating at 1.1. Do you know of any way to solve this problem without having to use a hub? Will there be an updated driver or are there some registry settings that might be made?

Thanks,

Larry
=============================================
Go to Top of Page

coalfield

8 Posts
	
Posted - Jan 30 2006 :  10:13:34  Show Profile  Reply with Quote
Thanks for the info. I remember when I was exploring the problem, i tried a USB 2.0 hub, but the problem was not fixed. The hub was NOT powered though which I am guessing is the key thing here.

I suspect the B2K is drawing quite a large load (which to be fair it likely, its a fairly complex box with no external power). Its probably fine for some chipsets (/controllers), but for others they simply cannot supply the power required for the box to run effectivly.

The obvious fixes are to install a PCI USB card (powered from PCI power, so plenty available), or a powered USB hub (gives extra juice as and when needed).

Hopefully mplat will be able to have a look into this and provide a fix for the B2K version2. I look forward to it!
Go to Top of Page

mtudor

5 Posts
	
Posted - Jan 30 2006 :  10:18:37  Show Profile  Reply with Quote
Funny you should mention that Coalfield - I was thinking the same.

If the ports we're plugging our B2Ks into have a lot of other power hungry devices on them and are not capable of supplying power to them all, that could explain it.

Happy to say my box is working fine now it's in the back of my machine. The only other power drawing device I have attached is a webcam.

I wonder if anyone who is having problems can confirm whether they still exist when all other USB devices are removed?

Just a thought...
Go to Top of Page

coalfield

8 Posts
	
Posted - Jan 30 2006 :  12:42:52  Show Profile  Reply with Quote
Funny thing is i tested the device on al my USB ports, and tried unplugging every other device on the PC. Still did not work. I suspect the RS480 I have has an unusually low current feed to USB, it would not surprise me i think the chipset was dogged with USB issues when it was first released/.
Go to Top of Page

knikander

1 Posts
	
Posted - Feb 03 2006 :  01:34:38  Show Profile  Reply with Quote
Whoever first thought of this power related problem should be given credit! I also couldn't use my b2k due to unacceptable outgoing sound quality, tried everything by without avail. Just like many others with the same problem, I also had a laptop.

I went out yesterday and bought a Typhoon usb high-speed hub with an external power supply. And yes, this fixed the problem! Echo123 worked just fine, made a test call to a friend and I actually experienced some "crumbled" incoming sound at times but this could have been a skype issue... I have to do further testing in the following days. The bottom line is however, go buy an inexpensive hub (with external power) and try it out!

Now I only need to find a solution to my other problem, namely that the hardware wizard pops up when I connect the box to another computer where I originally wanted to install the b2k. Someone posted that a complete reinstall of XP and programs had fixed the problem. Sorry but I am not prepared to go through all that, any other ideas?

Having that said, I am not very convinced of the quality of this device.
Go to Top of Page

spe

United Kingdom
10 Posts
	
Posted - Feb 03 2006 :  04:20:35  Show Profile  Reply with Quote
That person would be Ishamash, thanks again.

Come on Mplat, give us a power in socket on the B2K please. Or bundle the current B2K with dual-head USB cables to draw power from several ports, and maybe also from the PS/2 mouse port if your motherboard still has one.
Go to Top of Page

---

### Post by anewguy on 2008-04-28
Thanks for the info - I'm sure it will help others.  I've always been on a powered USB hub, so I guess that's why I haven't had the same problem.  My biggest problem now seems to be interference from a new neighbor - some piece of electronic equipment the moved in with (I'm in an apartment) has resulted in pulsing "pops" unless I move my phone to a different place than I am used to.

---


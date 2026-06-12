---
title: "Why does Ubuntu Work SO well out of the 'box'?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by zigx on 2006-07-06
I am pretty new to Linux but not THAT new...  i am curious WHY does ubuntu work so well?  How come it can detect hardware and automatically make config decisions that are Correct while other distros and even window cannot?

"Case Study"

I have a dell dimension @ work that i pretty much whore out to testing OSs on and various test cases (i work as a QA Engineer).  Out of the box OS installs i saw this:

Windows XP
-Display was ugly -- needed drivers
-NETWORK (omg) drivers were not installed properly or at all... had to manually put those in
-no sound

Windows 2k
-All worked for the most part
-Display jsut needed to be tweaked on a generic driver

Debian Linux
-did install...
-apt-get gnome and X... went through setup... 
-all windowing was broken

Gentoo
-that was a real PITA and i gave up... so gentoo is not @ fault here
[B]
Ubuntu
100% WORKED... everything out of the box. [/B]


So i guess im just curious... how come ubuntu can support so much so well while like standard Debian (which i thought Ubuntu was built on) could not... 

Is it the quality of Ubuntu's repository of software?  The calibur of ubuntu's core dev team ( :KS ) who have coded in methods of probing and identifying hardware? or... ????  

thanks a lot guys!!

---

### Post by Frank Golden on 2006-07-06
I think it's just a tremendous effort on the part of the developers to make
Ubuntu so compliant. Maybe a little magic also.:-D :mrgreen:
I can mirror your experiences. Install on my Acer Aspire almost everything works out of box, the only real problems were anticipated.
For instance the video card an ATi X1400 needed a simple post setup 
install of proprietary drivers to get full support. I use this machine as a desktop replacement and I have a Creative Soundblaster Audigy 2 NX
external sound card connected by USB. It found and configured card correctly for Alsa. I did have to blacklist my onboard card to avoid
confusing my machine as to what to use in Alsa/XMMS as default. Again 
no big deal.
   This kind of support did not happen "overnight" however.
I have been playing around with Ubuntu since Hoary with varying degrees
of success. On this machine for example I couldn't get Breezy to play
well. When I changed to Dapper flight 6 or 7 I began having good results.
More and more stuff "just worked". When final release time came.
I downloaded and installed with the results detailed above.
It's been interesting to watch this distro evolve.
If the developers aren't careful they just might give XP and M$ a run
for their money. LOL

---

### Post by FredB on 2006-07-06
[quote=zigx]I am pretty new to Linux but not THAT new...  i am curious WHY does ubuntu work so well?  How come it can detect hardware and automatically make config decisions that are Correct while other distros and even window cannot?[/QUOTE]

Philosophy of Ubuntu, maybe ?

> 
"Case Study"

I have a dell dimension @ work that i pretty much whore out to testing OSs on and various test cases (i work as a QA Engineer).  Out of the box OS installs i saw this:

Windows XP
-Display was ugly -- needed drivers
-NETWORK (omg) drivers were not installed properly or at all... had to manually put those in
-no sound

WinXP was released in 2001. So if you computer is younger, it is normal that some part are not detected.

> 
Windows 2k
-All worked for the most part
-Display jsut needed to be tweaked on a generic driver


Strange ! I would have think it will be the opposite between XP and 2k. :mrgreen:

> 
Debian Linux
-did install...
-apt-get gnome and X... went through setup... 
-all windowing was broken

Which version of Debian ?

> 
Gentoo
-that was a real PITA and i gave up... so gentoo is not @ fault here

Gentoo is a dream for long-bearded geeks. Maybe my beard is not that long...
[B]
> 
Ubuntu
100% WORKED... everything out of the box. [/B]

Great :o

> 
So i guess im just curious... how come ubuntu can support so much so well while like standard Debian (which i thought Ubuntu was built on) could not... 

Ubuntu is debian based, but is more advanced on some ways.

> 
Is it the quality of Ubuntu's repository of software?  The calibur of ubuntu's core dev team ( :KS ) who have coded in methods of probing and identifying hardware? or... ????  

thanks a lot guys!!

Maybe the will to show that linux is no more a toy for long bearded geeks.

---

### Post by FredB on 2006-07-06
[quote=Frank Golden]I think it's just a tremendous effort on the part of the developers to make
Ubuntu so compliant. Maybe a little magic also.:-D :mrgreen:[/quote]

Yes. To give linux a true human face ;)

---

### Post by Maggot on 2006-07-06
Ubuntu is the only distro that my Laptop Multimedia keys worked outta the box.

---

### Post by lapsey on 2006-07-06
Ubuntu always features the latest kernel, the most popular libraries and follows the gnome release cycle very closely.

This is not to say that some people don't still have problems with their own hardware but it's good to see that it goes well for others

---

### Post by aysiu on 2006-07-06
I don't think it always works that well. It really depends on what hardware you have.

It worked extremely well on my computer and many other users' computers. But there are also plenty of people here for whom Ubuntu was not impressive and detected virtually nothing.

It all depends...

---

### Post by MaximB on 2006-07-06
the only "driver" problem I had in ubuntu is ATI video card...as usual...
and I've spent a day at this forum to configuare my adsl connection properly , but that wasn't the driver...all good now

---

### Post by zigx on 2006-07-06
thansk for the responses guys!

I guess i am looking for a more technical answer though... 

i mean how come ubuntu can do it but other distros cannot?  It doesnt seem like a butt load of drivers are included with the installation either... unlike windows for example... but maybe i am wrong.

I just am really interested in how things ar ekept in order or what kind of things are implemented to make a distro work well and maybe what ubuntu has done RIGHT where others have gone wrong?



I mean after i installed Dapper i showed my mom and even considered installing it for her... its cake!  :)

---

### Post by crystal on 2006-07-06
I agree that it depends on the hardware. I have three computers in my household, and only mine is able to run the Desktop CD out of the box.

---

### Post by c1ean on 2006-07-06
It doesn't work for everything.  Still, compared to every other distro I've messed with, it's pretty good.

---

### Post by Frank Golden on 2006-07-06
[QUOTE=zigx]thansk for the responses guys!

I guess i am looking for a more technical answer though... 

i mean how come ubuntu can do it but other distros cannot?  It doesnt seem like a butt load of drivers are included with the installation either... unlike windows for example... but maybe i am wrong.

I just am really interested in how things ar ekept in order or what kind of things are implemented to make a distro work well and maybe what ubuntu has done RIGHT where others have gone wrong?



I mean after i installed Dapper i showed my mom and even considered installing it for her... its cake!  :)[/QUOTE]
Am I wrong here but does Ubuntu download some drivers from internet
as it installs? Like based on you individual computers needs.

---

### Post by Road King on 2006-07-06
Totally new newbie today... install seems to have gone okay, display is native 1280 x 1024 60Hz but screen savers, especially plasma, run dog-slow and are jumpy. 

[edit] details deleted and posted in a new thread

I don't know enough about ubuntu, much less Linux to know if this is considered working well out of the box, but I wouldn't be happy with it on Windows or OS-X.

---

### Post by MaximB on 2006-07-06
well the last ubuntu 6.06 dapper got out in 6.06 - it's about a month ago
so it has much better and current support for drivers.
I think it's the most recent linux distrebution to come out.

and for our new newbie Road King - welcome !!!
but could you pose your question in a new thread - so more ppl can help you on this subject.

---

### Post by Road King on 2006-07-06
[QUOTE=MAXDDARK]and for our new newbie Road King - welcome !!!
but could you pose your question in a new thread - so more ppl can help you on this subject.[/QUOTE]

Thanks, and done... moved details of problem to new thread.

---

### Post by Albi on 2006-07-06
Yeah, it depends.  For example, my friend tried the 5.10 LiveCD on his computer, and it wouldn't even graphically boot (kept giving errors about display).  When I installed it, all I had to do was properly install my ATI drivers to properly work with OpenGL and Direct3D

---

### Post by Bugsgalore on 2006-07-06
Well, 

This might be a little off topic....as I don't know nuthin' bout Linux but....Dang until I tried Ubuntu I honestly did not think that Linux could be so "friendly".....

I'm a total linux virgin and have not yet taken the plunge and installed on HD. However, I have to say getting the live CD up and running on my wife's 3 yo homegrown nforce2/AMD XP system was a snap. True, I needed to download NVIDIA drivers and paste some code into the terminal....but hey, I've had to do much worse for Windoze in the past (I use 2K at home and Mac OSX at work). 

The only other distro I've been playing with is "Puppy"  ([www.puppyos.org)](www.puppyos.org)), which I have yet to get running from live CD. 

Ubuntu has really got me thinking about migrating over...there are only a few issues that keep me from taking the plunge immediately. SAS (a statistical analysis program) and some hardware specific software (wife's pocket PC and a ZOOM 4 track audio recorder). 

If I can resolve getting my wifes Toshiba Pocket PC (also 2+ yo) to talk with Ubuntu and figure out the printer drivers I might be able to convince her to make the switch. I'll have to dig out the older homegrown (VIAKT266/AMD Athlon) and see what I can do....

Freedom from the MS empire might just be worth it.....I couldn't even stomach the shift to XP from 2K...there's no way I'm going VISTA at home......

Thank you Ubuntu for opening my eyes!!


Cheers, 

Matt.

---

### Post by zigx on 2006-07-06
so does the support of hardware aspect mean that developers have to hunt down working drivers all across the land and bring them to a central location that ubuntu uses to distribute out?  and how come they pick the Right ones? lol

---

### Post by joelito on 2006-07-06
[quote=zigx]
so does the support of hardware aspect mean that developers have to hunt down working drivers all across the land and bring them to a central location that ubuntu uses to distribute out? and how come they pick the Right ones? lol
[/quote]

Yeah what they do is basically hunt for the drivers that can not be in the kernel and include it as part of the linux-restricted modules package.

As for picking the right drivers, I think it depends on the beta testers to report what works.

---

### Post by confused57 on 2006-07-06
I think the hardware support is commendable...speaking as someone who has built two computers.  Installing XP, first you have install the drivers for the motherboard, drivers for the network card, etc, etc, all supplied on the CD's that came with the component or going to the manufacturers website to download updated drivers.  Guess you can't blame 3rd party software and hardware vendors supporting XP, that's where the money is, for now.  I'll admit XP does have decent driver support builtin to the OS.
In my opinion, Ubuntu works well "out of the box" maybe for most users...wireless, dual-core, maybe SATA, 64-bit, winmodem possibly still have a ways to go for support.
I've installed Ubuntu on 4 quite different computers with no problems.

---

### Post by smegmaster on 2006-07-06
I just reformatted a Dell laptop to dual-boot into Ubuntu and Windows XP. For XP I had to install drivers for the sound card, the ethernet connection, the graphics card (resolution wouldn't go higher than 1024x768), and the wireless PCI card. Everything worked automatically in Ubuntu, though. I told myself that as soon as I found a Linux distro able to automatically recognize my wireless card I'd finally make the full switch, and I'm doing just that right now. :)

---

### Post by zigx on 2006-07-10
thats a lot of work ont he ubuntu team's part.

---

### Post by Slicedbread on 2006-07-10
It does?

---

### Post by zigx on 2006-08-21
It has for me on a LOT of systems.  And its free.

---

### Post by magnoliablossom on 2006-08-21
With my system everything worked out of the box with Ubuntu but my modem and that wasn't that difficult to get working.  With Windows, the video drivers didn't and neither did my sound card, but my modem did.  So I figure it's about tit for tat with Ubuntu just a slight advantage.  The only problems I've had with Ubuntu were my errors which can be blamed on being a Linux noob.

---


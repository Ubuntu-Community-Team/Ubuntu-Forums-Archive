---
title: "Actual ATI linux drivers?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Kamiyay on 2007-04-10
Hey guys, I don't know if anyone has noticed (and I cannot test this because I haven't made the switch to Ubuntu yet. I am a student and have finals in about 4 weeks, so I won't be changing anything major, unless it is unavoidable, until after those are over) anywho, where was I?

I don't know if anyone noticed that ATI now has actual linux drivers. My laptop (which will run Ubuntu later this summer, again after finals) is a Dell Inspiron 9100. It has a ATI Mobility Radeon 9700. I was wondering if the drivers here are good. Are they as much of a pain in the *** as the past?

Thanks

~Kamiyay


Edit: Forgot the link: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by daynah on 2007-04-10
In general, we know. There's big debates over whether to use them in the forums. I think the debates happen in conjunction with the phases over the moon.

Seems to be the people who use nvidia and don't know diddly "yay! We finally have more corporate support!"

And people who used the ATI drivers slowly realize, day by day, that we just got spit on.

I had the ATI card that was the least supported. As in, it would load a gui sometimes, but it would freeze very very often. So... I got an nvidia. I'm happy now.

I suggest you repent before your computer quakes at your knees and you run memtests, harddrive tests, constantly check the heat, and buy a new power supply all because of your driver.

Oh, and you can't use Beryl.

Have a nice day...?

---

### Post by Maestro23 on 2007-04-10
I installed the driver from the ati site for my X1600 w/no problems using the guide at the link below.

ATI wiki: Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Other people have used the Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Kamiyay on 2007-04-10
> **daynah said:**
> In general, we know. There's big debates over whether to use them in the forums. I think the debates happen in conjunction with the phases over the moon.

Seems to be the people who use nvidia and don't know diddly "yay! We finally have more corporate support!"

And people who used the ATI drivers slowly realize, day by day, that we just got spit on.

I had the ATI card that was the least supported. As in, it would load a gui sometimes, but it would freeze very very often. So... I got an nvidia. I'm happy now.

I suggest you repent before your computer quakes at your knees and you run memtests, harddrive tests, constantly check the heat, and buy a new power supply all because of your driver.

Oh, and you can't use Beryl.

Have a nice day...?

Memtets and harddrive tests I can do. Checking the heat also works. New powersupply wont work because it's a laptop. I realize that battery life may suffer too. All things I am willing to test as I will have the time to do so.

Not having Beryl is no problem to me. I don't need the fancy graphics. I am fine working without (and it will probably add a speed increase). The Radeon has 128mb of onboard ram. It doesnt share memory. 

As for previous testing, I got Ubuntu 6.06 to run on a vmware in windows and used the following tutorial: [http://ubuntuforums.org/showthread.php?t=291464&highlight=mobility+9700](http://ubuntuforums.org/showthread.php?t=291464&highlight=mobility+9700) 

(skipping the beryl and xgl part) to get it working. I was just wondering if the  actual linux drivers made a difference.

---

### Post by devnulljp on 2007-04-11
yes, they're still crap though. Go with nvidia if possible.
I've had no end of grief with ati cards. My thinkpad has an ati radeon that I'm stuck with, but we just replaced all the ati cards with nvidias in the lab...they're a waste of money unless you're running win or mac.

---

### Post by mcduck on 2007-04-11
> **daynah said:**
> 
Oh, and you can't use Beryl.

I can't? Great that you told that to me after running Compiz/Beryl for over a year with Ati cards :D

I have 9600XT on my desktop and X1600 on my laptop, both running fine with fglrx drivers, XGL & Beryl.

And making fglrx drivers work took only 2 commands, one to install them and 1 to configure them. You may get better performance & features with nVidia, but Ati is not really even close to being as bad as many people seem to say it is..

---

### Post by WalmartSniperLX on 2007-04-11
Currently Ati is too much into MS. And, to compete with Nvidias UDA (unified driver architecture) they simply took the FireGL code and made adjustments to let it work with radeon cards. Nvidia redesigned the drivers from ground up so they work equally good with all their products. Not to mention the X1K gpus seem to give you the worst price/performance with ati drivers. What I mean by this is the fglrx drivers give you a higher performance percentage with anything older than the X1K than with the X1k; you will lose a lot of your investment if you use an X1K card in linux. II don't know if I was on the right track posting this but I hope it helps you anyways.

---

### Post by msak007 on 2007-04-11
> **mcduck said:**
> I can't? Great that you told that to me after running Compiz/Beryl for over a year with Ati cards :D

I have 9600XT on my desktop and X1600 on my laptop, both running fine with fglrx drivers, XGL & Beryl.

And making fglrx drivers work took only 2 commands, one to install them and 1 to configure them. You may get better performance & features with nVidia, but Ati is not really even close to being as bad as many people seem to say it is..
I think he meant "You can't use Beryl the proper way, using AIGLX instead of XGL". It's doable with XGL, but slow. Yes the drivers are easy to install, but they're going in the wrong direction - this past month the big news was a Catalyst Control Center that is useless at this point instead of focusing on AIGLX support which is what a majority of users want. They've gotten better over the past year, but they're still pretty bad. Here's ATI's official stance on AIGLX, Beryl, and Compiz:

[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907)

To answer the original question posted, if your card is supported by the open source radeon drivers (it should be), opt to use those first. If you notice any lagging or they're slow, then try the proprietary fglrx drivers. The wiki.cchtml.com site linked to earlier works really well, I always use it to install the drivers.

---

### Post by Kamiyay on 2007-04-11
Thank you guys for the many replies. Due to the many responses I will opt to try the drivers. If they suck, then move on to fglrx. The option of replacing the video card is a cool idea.  I have no idea what kind of card it is though, nor what cards would be compatable with my motherboard. Dell does not give me such info.

---

### Post by freebird54 on 2007-04-11
I have never understood the antipathy against the ATI cards here - they always worked for me.  If Beryl is slow on ATI - how incredibly fast must it be on others?  I can spin the cube as almost a blur- while its playing a you tube vid live, and it never seems to drop a frame :)

BTW - this is NOT a powerhouse setup I'm using - and the card is a cheap 9550.  YMMV

---

### Post by devnulljp on 2007-04-13
> **freebird54 said:**
> I have never understood the antipathy against the ATI cards here

Try to do something a little out of the ordinary with the card, that is well-supported on windows, and you'll see the difference. Dual head is a nightmare with ATI, but relatively simple with nvidia (speaking from experience here). Haven't tried beryl, but I could never get gl to work properly on ati cards. A company providing the info necessary for you to use their products would be nice.

---

### Post by freebird54 on 2007-04-13
I understand that they can frustrate the s__t out of people - but they CAN be set up, and they do run well.  My experience with goes back to my first Linux (TAMU - Texas A&M distro) and ATI were one of the few that allowed for Xfree to run at all.  I admit that wasn't that easy a setup either - but again, it WORKED!

We can all hope that now they're in with AMD - who should have some feeling for the 'underdog' if nothing else - that things will improve further.

---

### Post by miggols99 on 2007-04-13
Well in Feisty, my ATI card works out of the box with the (open source?) driver with AIGLX. And fast too. :)

---

### Post by matthekc on 2007-04-13
200m till recently it took monumental effort to work this card.  I personally have not fixed mine yet but i hear it works now.  

I hope amd kicks ati linux support up a notch.  Even if every thing were perfect as soon as the open graphics card project can put out something competitive I'll want one.

As much problem as we have had with graphics cards I'm surprised there is no nsdiswrapper for them.

---

### Post by GSF1200S on 2007-04-13
> **miggols99 said:**
> Well in Feisty, my ATI card works out of the box with the (open source?) driver with AIGLX. And fast too. :)

Ok, I have a Nvidia card, and I had a pain in the ____ trying to get the drivers to work without crashing the Xwindow.. I mean isnt everything relative?

Really.. how GOOD are Nvidia drivers? I mean they may get the job done, but I doubt they work as well with Linux, than the Windows equivalent drivers.. 

Plain and simple, Linux lacks alot of support. If MS offered to pay Nvidia more than Nvidia thought they made off Linux users, than they would probably drop support too. Its all a money game.

---

### Post by eldragon on 2007-04-23
if it works for you, it doesnt mean its will for the rest of the world.

the truth is ati isnt doing much for the linux comunity, and the fact that you have a working card now doesnt guarantee it will work in future releases.

this happened to me, and i was forced out to use the open source ATI drivers, which, at lower quality (but working) does what the fglrx drivers should have. 

aiglx + compiz/beryl + screen resolutions  with higher refresh rates that wont kick me in the retina...

i got lucky since i got an older model (X1xxx will not work).

so, i know i wont be buying another ati card anytime soon (unless of course, support from ati appears).

and im not screaming: open source your drivers!! just a nice binary that wont suck and that works descently is enough for me.

---

### Post by Cervantez on 2007-04-23
The ATI binary linux drivers are unstable and can cause the X server to crash, possibly very often. Try it anyway though, depending on your card, it might work fine.

---

### Post by Arjunus on 2007-04-23
Hi,

I tried to install the Ati drivers for my Radeon 9200 from the package manager. But unfortunately nothing worked. Trying to maually configure them nearly destroyed my pc! I was left with just a command line interface. Thank god my digs mate is a linux pro otherwise I would have been screwed.

My question is, is it the actual drivers that are messed up or is it the way people install them? I am getting a Nvidia Card, I am tired of not have proper graphics on my ubuntu.

---

### Post by matthekc on 2007-04-23
The Ati drivers truely have a history of being broke, certain cards are not supported, certain cards that did wok get broken, and even some supported cards don't work to their potential.

That being said i do believe that amd since buying ati is working to remedy the situation

---

### Post by WHICKS on 2007-04-23
When you want to load up your ubuntu 7.04 and use beryl with the 9XXX series ATI , I would suggest you go to the following link.  I followed his instructions and my 9200 works perfectly, even with beryl and all the eye candy.  The main point is that he changes the drivers during the install.  He uses the open-source ATI driver that comes with Ubuntu plus AIGLX to achieve this; the other way to do this would be to use the closed-source ATI driver together with XGL which seems to be a bit unstable.  It's a painless process and it worked forme!

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

The author goes by the name FALKO, and he has some great linux/ubuntu tutorials out there.
Cheers, W.

---

### Post by matthekc on 2007-04-23
what is going on with the ati open drivers do they need card dumps?  there was an article about amd considering opening some of the specs or drivers.  Is this still a possibility?

---

### Post by eldragon on 2007-04-24
> **matthekc said:**
> what is going on with the ati open drivers do they need card dumps?  there was an article about amd considering opening some of the specs or drivers.  Is this still a possibility?

taken from the freedesktop ati wiki:
> 
Specifications

ATI has a 'developer program'. Specifications of all ATI chips up to the Radeon 9200 were made available to DRI developers under NDA on an individual case basis. Please read carefully the NDA page before you consider applying. 

so there you have it. i dont know how old that info is,and what specs were released....but gives a hint on why some cards work so great and others simply dont.

---

### Post by Arjunus on 2007-04-24
Hi Whicks,

I will give that a try! thanks but I dont have much hope. I already work my GUI a few times trying to load the drivers.

---

### Post by matthekc on 2007-04-28
i came about The irregular Radeon Development Companion which is a attempt to reverse engineer radeon drivers  

[http://tirdc.livejournal.com/](http://tirdc.livejournal.com/)

Quote from site 
Currently Radeon development is going slowly forward. We are looking for developers and users that are able to understand hardware development. So if you got free time and maybe even knowledge of hardware development, feel free to join #dri-devel on irc.freenode.net and look at the source. We are also interessted in porting Renouveau over to R300 (or even to make it vendor independent, so it could be used for Intel and whatever else). This work would be highly appreciated by every developer. It would also be important to check why KMMIO does not work flawless on R300.

---


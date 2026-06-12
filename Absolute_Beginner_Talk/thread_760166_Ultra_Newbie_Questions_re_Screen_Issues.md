---
title: "Ultra Newbie Questions re: Screen Issues"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by GadgetGuru72 on 2008-04-19
Hello everyone-

I am brand new to the world of Linux, and to Ubuntu.  I just installed Ubuntu on my Dell laptop, and I'm having two issues:

(1) The screen is shifted a few millimeters to the left, such that the left-most icons are half hidden.  How do I calibrate the screen?

(2) The resolution of the characters is not very crisp.  The letters "vibrate" a little and appear a little blurry.  How do I fix that?

Thanks in advance.

---

### Post by LaRoza on 2008-04-19
There should be an "auto adjust" or an "auto" button on the monitor to align it.

If it has a weird flicker, it may be that there isn't enough RAM or video capabilities of the computer (or drivers are needed)

How much RAM do you have and what is your video card?

---

### Post by BaffledMollusc on 2008-04-19
I've had similar problems with some LCD screens. If it's the same problem, installing the proprietary driver fixes it. What type of graphics card (or integrated graphics) does your laptop have?

---

### Post by GadgetGuru72 on 2008-04-19
> **LaRoza said:**
> There should be an "auto adjust" or an "auto" button on the monitor to align it.

If it has a weird flicker, it may be that there isn't enough RAM or video capabilities of the computer (or drivers are needed)

How much RAM do you have and what is your video card?

It's a laptop -- there are no buttons on the screen.  I'm not sure how to do an adjustment.

It is a weird flicker.  It has 256MB RAM, and I'm not sure what the video card is.  How would I check?

---

### Post by GadgetGuru72 on 2008-04-19
> **BaffledMollusc said:**
> I've had similar problems with some LCD screens. If it's the same problem, installing the proprietary driver fixes it. What type of graphics card (or integrated graphics) does your laptop have?

What is "the proprietary driver"?

How do I determine what kind of graphics card I have?

---

### Post by LaRoza on 2008-04-19
> **GadgetGuru72 said:**
> It's a laptop -- there are no buttons on the screen.  I'm not sure how to do an adjustment.

It is a weird flicker.  It has 256MB RAM, and I'm not sure what the video card is.  How would I check?

Ubuntu 7.10 or 8.04 need a bit more RAM than that to run well. Assuming you do have a normal resolution, it isn't video drivers.

I recommend getting more RAM, if you have the resources, or using a lighter desktop environment. IceWM or Fluxbox are good bets.

---

### Post by GadgetGuru72 on 2008-04-19
> **LaRoza said:**
> Ubuntu 7.10 or 8.04 need a bit more RAM than that to run well. Assuming you do have a normal resolution, it isn't video drivers.

I recommend getting more RAM, if you have the resources, or using a lighter desktop environment. IceWM or Fluxbox are good bets.

Is there a way to determine if its a resolution issue or a RAM issue without having to spend money on more RAM?  I'd like to avoid that.

Any ideas about the screen calibration issue?

---

### Post by BaffledMollusc on 2008-04-20
> **GadgetGuru72 said:**
> What is "the proprietary driver"?

How do I determine what kind of graphics card I have?

Loosely speaking, there are two types of drivers: open source and proprietary. 

The proprietary drivers are those made by vendors of the graphics card.  They are closed source, and cannot be modified or bug-fixed by the community, although ATI has very recently started to be more helpful in releasing information. 

Open source drivers are drivers written by the community by reverse engineering the behaviour of the graphics card, as well as making use of any information the vendors are prepared to release. Ubuntu uses open source drivers by default.

The proprietary drivers are often a bit faster and contain support for the newest cards that the open source drivers don't yet support.

To determine the type of graphics card you have, you might be able to find it under System->Administration -> Hardware. If not, enter "lspci" in a terminal and post the results.

Also, despite what LaRoza says, I have had two instances of LCDs being badly aligned and no monitor calibration options fixing it. Both cases were fixed by installing a proprietary driver. It was an ATI card in one case and an Intel integrated graphics in the other. I'm not saying this *is* the solution, just that it has solved a similar problem for me in the past.

---

### Post by LaRoza on 2008-04-20
> **GadgetGuru72 said:**
> 

Any ideas about the screen calibration issue?

It is probably the graphics card trying to rewrite the screen, but there is too much information for it to handle well. Use a lighter desktop environment.

---

### Post by GadgetGuru72 on 2008-04-20
> **BaffledMollusc said:**
> To determine the type of graphics card you have, you might be able to find it under System->Administration -> Hardware. If not, enter "lspci" in a terminal and post the results.

Also, despite what LaRoza says, I have had two instances of LCDs being badly aligned and no monitor calibration options fixing it. Both cases were fixed by installing a proprietary driver. It was an ATI card in one case and an Intel integrated graphics in the other.

Ok, thanks.  I'll check it out when I get home and report back.

Also, can you elaborate on what you mean by "enter 'lspci' in a terminal"?  I'm a complete Linux newbie and don't even know what a "terminal" is, or how to get to it.

I installed Ubuntu because I was curious, not because I really knew what I was doing.  ;)

---

### Post by LaRoza on 2008-04-20
> **GadgetGuru72 said:**
> 
Also, can you elaborate on what you mean by "enter 'lspci' in a terminal"?  I'm a complete Linux newbie and don't even know what a "terminal" is, or how to get to it.

I installed Ubuntu because I was curious, not because I really knew what I was doing.  ;)

Applications->Accessories->Terminal

Type the commands given, and press enter. Highlight the results, and double click in your reply (that copies and pastes in Linux)

---

### Post by GadgetGuru72 on 2008-04-20
> **LaRoza said:**
> Applications->Accessories->Terminal

Type the commands given, and press enter. Highlight the results, and double click in your reply (that copies and pastes in Linux)

Ok, thanks!  I'll check it out as soon as I get home and report back with the results.

Thanks a lot for your help.

---

### Post by GadgetGuru72 on 2008-04-20
> **BaffledMollusc said:**
> Loosely speaking, there are two types of drivers: open source and proprietary. 

The proprietary drivers are those made by vendors of the graphics card.  They are closed source, and cannot be modified or bug-fixed by the community, although ATI has very recently started to be more helpful in releasing information. 

Open source drivers are drivers written by the community by reverse engineering the behaviour of the graphics card, as well as making use of any information the vendors are prepared to release. Ubuntu uses open source drivers by default.

The proprietary drivers are often a bit faster and contain support for the newest cards that the open source drivers don't yet support.

To determine the type of graphics card you have, you might be able to find it under System->Administration -> Hardware. If not, enter "lspci" in a terminal and post the results.

Also, despite what LaRoza says, I have had two instances of LCDs being badly aligned and no monitor calibration options fixing it. Both cases were fixed by installing a proprietary driver. It was an ATI card in one case and an Intel integrated graphics in the other. I'm not saying this *is* the solution, just that it has solved a similar problem for me in the past.

Ok, here's what I have:

ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

I found that by using the "lspci" technique you mentioned.

What should I do now?  I have no clue how to find or install a driver in Linux.  Thank you.

---

### Post by BaffledMollusc on 2008-04-20
The easiest way is to go to System->Administration->Restricted Driver Manager (in Ubuntu restricted software is stuff that is not free/open source). You should be able to activate the proprietary ("restricted") driver there.

If that doesn't work, the next easiest thing to do is to install Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and run it from (I think) Applications->Accessories.

All this does is install the ATI driver, but it makes it a lot easier than doing it by hand. Note that it downloads the appropriate driver, which can be tens of megabytes.

I guess I should also suggest that before you go down this route you might want to search the forums for radeon 7500 and see if the proprietary driver has helped other people.

---

### Post by GadgetGuru72 on 2008-04-20
> **BaffledMollusc said:**
> The easiest way is to go to System->Administration->Restricted Driver Manager (in Ubuntu restricted software is stuff that is not free/open source). You should be able to activate the proprietary ("restricted") driver there.

If that doesn't work, the next easiest thing to do is to install Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and run it from (I think) Applications->Accessories.

All this does is install the ATI driver, but it makes it a lot easier than doing it by hand. Note that it downloads the appropriate driver, which can be tens of megabytes.

I guess I should also suggest that before you go down this route you might want to search the forums for radeon 7500 and see if the proprietary driver has helped other people.

The only thing listed under the "restricted driver" section was for the modem.

So, I installed and ran Envy, but it said that the driver is either not supported or Envy's hardware detection failed.

I did a search of the forums for Radeon 7500, but most of the posts were from 2005 and 2006, using a much older version of Ubuntu.

Am I out of luck?  Is there anything else to try?

---

### Post by BaffledMollusc on 2008-04-20
After reading your last post, I did some searching on the Mobility 7500. Apparently the ATI proprietary driver only supports 9500 and later cards; I guess they've discontinued support of their earlier cards. I apologize for suggesting the impossible :(

Unfortunately I have no other ideas, other than possibly trying a different window manager. I've always used the default metacity window manager, and don't know how to install a different one, though. Hopefully someone on the forums will be able to help.

Also bear in mind I have no idea if this will help - I'm just guessing here.

---

### Post by GadgetGuru72 on 2008-04-20
I can't seem to fix this at all.

I downloaded and burned LiveCDs for Kubuntu and Xubuntu, and neither had any effect despite the fact that Xubuntu runs on only 128MB RAM, or so it claims.  I also downloaded and burned a LiveCD of OpenSUSE since it claims to work on old systems.  None of them fixed the screen calibration issue or the shakiness issue.  This is really, really, really frustrating.  

Does anybody else have any ideas?

---

### Post by adk46er on 2008-04-21
When i was 17 i bought my first car-- a stick shift-- without ever having driven a standard (i drove all the way home in 2nd gear). your situation kind of reminds me of that (no offense intended). As a fellow beginner with Linux, I have found that there is a steep learning curve-- and I have some programming background and years of computer experience with DOS, Windows, and.... I'm dating myself.... Apple back when the Apple IIe was THE machine to have. Some unsolicited advice: It's much easier to ask pointed questions and even easier for these folks to help you if understand the basics first (like "terminal"), so I strongly suggest that you read up on the internet and/or get some books from the library on Linux for beginners. i found tons of free info out there, and i know there are other distributions that run well on old machines with small amounts of RAM, so it shouldn't cost you anything but your time... and you'll learn a bunch in the process. Hope i don't sound condescending-- just trying to help (i'm also a teacher so i love it when people read). Don't give up-- you'll catch on quickly. Good luck!

---

### Post by cardinals_fan on 2008-04-21
Well, if you install Openbox you can adjust your screen edges easily.  Plus it'll run faster.  You can follow the excellent guide [here]("http://urukrama.wordpress.com/openbox-guide/").  Before doing this, you should be aware of the facts.  Openbox is lightweight, fast, and configurable, but you need to be openminded in order to learn it.  It requires that you understand how to edit text files and basic use of the terminal.  My advice would be this: stick with the current system (unless it's unusable) until you feel a little more comfortable in Linux.  Than try the guide above.

You might also consider a more lightweight distribution.  Zenwalk is great, as is Vector.

---

### Post by BaffledMollusc on 2008-04-21
> **adk46er said:**
> When i was 17 i bought my first car-- a stick shift-- without ever having driven a standard (i drove all the way home in 2nd gear). your situation kind of reminds me of that (no offense intended). As a fellow beginner with Linux, I have found that there is a steep learning curve-- and I have some programming background and years of computer experience with DOS, Windows, and.... I'm dating myself.... Apple back when the Apple IIe was THE machine to have. Some unsolicited advice: It's much easier to ask pointed questions and even easier for these folks to help you if understand the basics first (like "terminal"), so I strongly suggest that you read up on the internet and/or get some books from the library on Linux for beginners. i found tons of free info out there, and i know there are other distributions that run well on old machines with small amounts of RAM, so it shouldn't cost you anything but your time... and you'll learn a bunch in the process. Hope i don't sound condescending-- just trying to help (i'm also a teacher so i love it when people read). Don't give up-- you'll catch on quickly. Good luck!

Well, this is the absolute beginners forum, so I don't see any problem with people having zero experience with linux. They should feel free to ask anything and not worry about not having any linux background.

---

### Post by BaffledMollusc on 2008-04-21
Okay, I still think it might be a driver problem or an xorg configuration problem.  

Could you find out which driver you're using? To do this, pull up the terminal again, and enter the following:

gedit /etc/X11/xorg.conf

This will fire up a text editor (gedit) and open the file xorg.conf, which sits in the directory /etc/X11.

Could you copy the contents of that file and post it here? Preferably between [code]  tags?

---

### Post by GadgetGuru72 on 2008-04-21
> **BaffledMollusc said:**
> Okay, I still think it might be a driver problem or an xorg configuration problem.  

Could you find out which driver you're using? To do this, pull up the terminal again, and enter the following:

gedit /etc/X11/xorg.conf

This will fire up a text editor (gedit) and open the file xorg.conf, which sits in the directory /etc/X11.

Could you copy the contents of that file and post it here? Preferably between [code]  tags?

Sure, I will follow these direction as soon as possible.  However, I now have additional problems that need to be resolved first.  For some unknown reason, Ubuntu is no longer recognizing my wireless network card.  I think I can get that figured out, but until I do there's little point in figuring out why the screen isn't calibrated or why everything is shaky.  So, I will reply and provide you with the information you indicated as soon as I get these other issues sorted out.

Also, thank you for your comments about this being the "beginners' forum" and my questions being allowed.  I love how people say things like "I don't mean to be condescending" and then proceed to be horribly condescending.  :confused:  The "car" analogy didn't even make sense.  I learned how to drive not by going to the library to get a book on driving, but by actually getting behind the wheel while someone who knew how to drive was sitting next to me.  That's what I'm doing here -- I dove into Linux to experiment with it, and the kind people of this forum are the knowledgeable people who have been willing to help me out.

Anyway, I appreciate your help, and will get back to you shortly.

---

### Post by GadgetGuru72 on 2008-04-21
I wanted to take a minute to say THANK YOU to the people on this forum who were kind enough to offer their knowledge and time to try to help me resolve my problems with Ubuntu.  However, the problems continue to pile up and so I have decided to go back to Windows XP.  I know that may be a horrible thing to admit around here, but it's just more familiar to me and I'm able to troubleshoot better using that OS.

Maybe someday I'll venture back into Linux, but for now it's just too much of a headache.

Thanks again!!

---


---
title: "Hangs trying to install Ubunto 6.06"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-07
I was given an old PC and I am trying to install Ubuntu 6.06 LTS version.  I have formatted both hard drives and I am loading Linux as the only software on the machine. The install keeps hanging up right after the screen where I pick the language.  The PC is very slow and seems to be straining:confused: .  I have a PC with the following specs :

ABIT VA-20 MotherBoard with an AMD Sempron 2600+ CPU and 256MB of RAM using the MB onboard video(UniChrome Pro Graphics).

I have a few simple questions :

1.) I could not find it on Ubunto web site, but I assume you double click the install icon to start the installation?  I did this when trying to install the software and got to pick a language.
2.) Does this processor have enought ump to run Ubuntu?  The first thing I thought I would do would be to add some more RAM but I don't want to spend lots of money.
3.) Are the MB onboard graphics good enought for Ubunto?

This is my first try using Linux and I want to play with it awhile before I build my first Linux machine.

---

### Post by louieb on 2007-02-07
Been using Linux just over 6 months.  Some things I have learned:
Don't have your mother board so don't know.
256mb is enough more is better.
I've install Ubuntu on a P1 its slow and on a P2 400 its what I'm using right now.
Not had any trouble with Linux and any old video card or on board video. Newer 3d cards are sometimes a hassle to set up.
The alternate CD will work where the live CD fails.
Dapper installs where Edgy won't.
Its nice to have a PC to test it on. Can't remember how may times I've broke stuff and reinstalled.
Have fun, Good Luck.

---

### Post by ^rooker on 2007-02-07
...sounds like some process in the background is trying to do something it can't.
<EDIT>
Try using the "system monitor" to see which processes are currently doing something (you should find it under "System/Administration/System Monitor".

But you could also open a terminal shell and type:
"top -d 3"

which will show you infos about running processes ("-d 3"means to update every 3 seconds)
</EDIT>


**About your questions:**
> **rggavubt said:**
> 1.) I could not find it on Ubunto web site, but I assume you double click the install icon to start the installation? I did this when trying to install the software and got to pick a language.
yes.
> **rggavubt said:**
> 2.) Does this processor have enought ump to run Ubuntu? The first thing I thought I would do would be to add some more RAM but I don't want to spend lots of money.
definitely enough. I'm running Ubuntu on a 1 GHz Thinkpad - super smooth! After I upgraded my RAM from 256 to 384, it became even smoother.
I'm doing daily work on that machine - no gaming or video editing. 
> **rggavubt said:**
> 3.) Are the MB onboard graphics good enought for Ubunto?
Depends: 
- if you're a gamer: no - but if you were, you wouldn't have asked that.
- For "normal" (2D) stuff: yes.

---

### Post by ske1fr on 2007-02-07
Have you tried the "noapic nolapic acpi=off" switches on the command line when you start the  CD and load Ubuntu?  These can sometimes make things act more reliably.  If it works then they should then get included in the installed version you run from the hard disk.

If you can't get past those parts of the installation routine, did you download the CD or obtain a pressed copy?  If you downloaded the iso image then it is essential that you check the MD5 sum before burning it and using it.  If you did this and still can't make progress then perhaps the alternative version that installs without a GUI would make more progress.

EDIT: Oh, and if possible, fit  the extra RAM first so if it's a lack of memory issue it's solved.

---

### Post by Bartender on 2007-02-07
Haven't people had troubles with the Unichrome onboard graphics?  Wondering if OP should try "vesa" or whatever command it is for basic video drivers at startup?

---

### Post by xpod on 2007-02-07
I dont think it`s been mentioned but you could try starting the cd up in "safe graphics mode"

I have a machine here with very similar specs and it used to hang on stage 5 of the actual install but just using safe graphics mode seemed to do the job and the install would fly along.

I`ve practically doubled the memory in it now though plus i always use the alternate cd`s for installing anyway:)

---

### Post by rggavubt on 2007-02-07
> **ske1fr said:**
> Have you tried the "noapic nolapic acpi=off" switches on the command line when you start the  CD and load Ubuntu?  These can sometimes make things act more reliably.  If it works then they should then get included in the installed version you run from the hard disk.

If you can't get past those parts of the installation routine, did you download the CD or obtain a pressed copy?  If you downloaded the iso image then it is essential that you check the MD5 sum before burning it and using it.  If you did this and still can't make progress then perhaps the alternative version that installs without a GUI would make more progress.

EDIT: Oh, and if possible, fit  the extra RAM first so if it's a lack of memory issue it's solved.

Where is the command line?  The Cd I made from downloading the image goes to a home screen with a install incon on it......I don't see a command line?

---

### Post by rggavubt on 2007-02-07
> **xpod said:**
> I dont think it`s been mentioned but you could try starting the cd up in "safe graphics mode"

I have a machine here with very similar specs and it used to hang on stage 5 of the actual install but just using safe graphics mode seemed to do the job and the install would fly along.

I`ve practically doubled the memory in it now though plus i always use the alternate cd`s for installing anyway:)

On the main screen, How do you enter safe mode...do you access command line under applications?

---

### Post by xpod on 2007-02-07
You access safe graphics mode as you boot the cd and the command line i think your referring to would be the "terminal" and thats in your applications>accesories menu on the actual desktop.

Just reboot the cd again and choose "safe graphics mode" this time instead of "start\install".
If you cant install ok like that and you`ve tried the other options these guy`s have mentioned then
you will mabey need an alternate cd.

---

### Post by doobit on 2007-02-07
If none of that works, then you should use the alternate install CD. That worked much better for me anyway.

---

### Post by rggavubt on 2007-02-07
> **xpod said:**
> You access safe graphics mode as you boot the cd and the command line i think your referring to would be the "terminal" and thats in your applications>accesories menu on the actual desktop.

Just reboot the cd again and choose "safe graphics mode" this time instead of "start\install".
If you cant install ok like that and you`ve tried the other options these guy`s have mentioned then
you will mabey need an alternate cd.

Thanks....I am trying that now.

---

### Post by rggavubt on 2007-02-07
> **doobit said:**
> If none of that works, then you should use the alternate install CD. That worked much better for me anyway.

I am trying safe graphics now and will try alternate CD next........thanks

---

### Post by rggavubt on 2007-02-07
> **Bartender said:**
> Haven't people had troubles with the Unichrome onboard graphics?  Wondering if OP should try "vesa" or whatever command it is for basic video drivers at startup?

I searched support problems and could not find Unichrome mentioned?

---

### Post by rggavubt on 2007-02-07
> **xpod said:**
> You access safe graphics mode as you boot the cd and the command line i think your referring to would be the "terminal" and thats in your applications>accesories menu on the actual desktop.

Just reboot the cd again and choose "safe graphics mode" this time instead of "start\install".
If you cant install ok like that and you`ve tried the other options these guy`s have mentioned then
you will mabey need an alternate cd.

Tried installing using the safe graphics mode and I hung up at screen 5 of 6.  Tried three times with no luck.  I have ordered some more RAM and will try again after I install it!  I did get much farther along, much faster in the safe mode......thanks

---

### Post by rggavubt on 2007-02-13
> **doobit said:**
> If none of that works, then you should use the alternate install CD. That worked much better for me anyway.

I finally succeeded using the alternate CD,  I am still waiting for my RAM to arrive and couldn't wait until then to install Ubuntu,:)

---

### Post by yme on 2007-02-20
> **rggavubt said:**
> The install keeps hanging up right after the screen where I pick the language.

I had exactly the same problem but with a pretty high spec new laptop. Kept trying and trying and never got past the language screen. 

Then tried the second option when the CD boots 'safe mode' and everything was done and dusted in five minutes. 

It seems there is a problem with the 'install ubuntu' option. Shame as it will put off those new to Linux ...

---

### Post by =CrAzYG33K= on 2007-04-28
> **yme said:**
> I had exactly the same problem but with a pretty high spec new laptop. Kept trying and trying and never got past the language screen. 

Then tried the second option when the CD boots 'safe mode' and everything was done and dusted in five minutes. 

It seems there is a problem with the 'install ubuntu' option. Shame as it will put off those new to Linux ...

Yeah .. Shame .. I too faced some problems with the installer long back and couldn't proceed... :( 
Here's someone else's views on this problem .. 
The solution :
> while installing ubuntu,
1.> Select lang = english , click forward.
2.> dont make any changes to the city , click forward.
3.> dont make changes to the kbd settings let it be us english , click forward
4.> now the partition manager , select manual or guided according to ur choice.
5.> now the setup wont hang further go ahead and follow the steps.

Could there be a small bug in Dapper Drake? :mad:

---


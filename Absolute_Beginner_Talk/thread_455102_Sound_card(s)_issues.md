---
title: "Sound card(s) issues"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-26
I have the Creative Audigy LS2 PCI card in my Shuttle XPC box.  I also have the RealTek AC97 onboard sound.  For some reason, when I go to System-Preference-Sounds, I have to select between SIS SI7012 and six instances of CA0106.  The 7012 is my onboard sound, and the CA0106 is my Creative card.

The first five instances of CA0106 (they appear in the drop down for each of the playback/capture controls) are inoperable.  If I select one of them and hit test, nothing.  If I select one of them and proceed to some application, no sound.

If I select the sixth listing of CA0106, everything works.

If I select the SIS SI7012 option, then, sound works through my onboard Reatek sound card.

I question why this should be so, and how I might fix it.

Furthermore, my system occasionally (as in right now), defaults to the onboard sound card and refuses to be persuaded by any sound preference settings to let go of the onboard card and use the PCI card.

When I am only listening to sounds, this is not that big of a problem, but, when I want to record, it creates headaches, as my little Shuttle (wonder-machine that it is) shipped with an onboard sound setup that has so much inherent system noise that recordings made through that card are not usable.

Again, I question why my Ubuntu setup locks onto that card and won't let go.  What is the fix - anyone?

Also, is there a proper way to enter the path to my sound card in the configuration area of Crossover so that aps that I have installed use the proper sound card.  Crossover is defaulting to the wrong sound card (the onbaord one all the time).  I see where there is an area to enter alternative sound cards, but, when I typed the name of my Creative card in there (I used CA0106), I had no sound with that ap at all, and I see no way to restore the default other than to reinstall the Win Ap.

FWIW I have installed Sonic Foundry's Sound Forge 5 and Steinberg's Wavelab 5.  Both seem to be working, except that I cannot get them to connect with or recognize my sound card or my CD/DVD RW drive.

Different, but, related problems, I think (the CD problem in addition to the sound card problem).  I underlying problem with Crossover is that these aps are not seeing the system in the same manner as they do when natively installed in XP.

If in either of the two wave editing aps mentioned I look at sound card assignments, I see this generic sort of Wine Mixer or something that tells me that Crossover is translating the hardware connections.  Unfortunately, in so far as sound is concerned, it is making a choice that is not  to my liking.

Obviously, this is not an urgent problem, but, if someone can help me with it, I would be most obliged.

Caruso

---

### Post by kyphi on 2007-05-26
Have you tried to disable on-board sound in the BIOS?  I also have a Creative soundcard installed and therefore have no need for any motherboard sound chip.  And Ubuntu works fine with the card.

---

### Post by deadgobby on 2007-05-26
2cd that. You need to go into BIOS and disable the on board sound card.

---

### Post by carusoswi on 2007-05-27
> **deadgobby said:**
> 2cd that. You need to go into BIOS and disable the on board sound card.

Thanks, guys.  I'll try that.  When I first purchased this neat little computer, I came close to returning it because I was so disappointed with the sound card.  Folks at BB offered me a deal on the upgraded sound card, and, for the longest time, I operated with the onboard sound disabled.  Then, during an XP re-install, I decided to try having both enabled, and have been successfully using both in XP for quite a while.  If having both enabled in Ubuntu is causing a problem, I'll just disable it and see how things work that way.  Thanks again for the reply. 

Caruso

---

### Post by carusoswi on 2007-05-27
Ok, disabled the onboard sound - confirmed that by checking sound settings under preferences.  Still, no go.  As previously true, my ap will play sound just fine, and it doesn't seem to matter what setting I use - OSS, AutoDetect, CA0106 (the Creative Audigy card).  The Crossover setting is for Wine Mapper (out/in).  Obviously, out is working, in is not working, and the ap thinks there is either no audio card or something wrong with the setting on the audio card.

It is probably time for me to step away from this for a while - I'm starting to get agravated with it.

Any additional suggestions welcome, though.

Caruso

---

### Post by carusoswi on 2007-05-27
On a somewhat related issue, I cannot get skype to hear me through my microphone.  I know I'm in the right jack (tested the card via XP), but, it seems no mic/sound card setting I use works.  I tried both the onboard (when I had it enabled) and the Audigy PCI card.

Caruso

---

### Post by kyphi on 2007-05-27
This is getting too confusing for me, Caruso.

Let me just list the problems you mentioned:

1.  Sound works in Windows but not in Ubuntu.
2.  Sound works in Ubuntu but not with the sound card (or chip) that you want to use.
3   Sound management programmes used via CrossOver do not work properly.
4.  The microphone for Skype does not work.

That sound management programmes do not work properly via CrossOver or Skype is because there is a problem with your sound setup generally.  Have a look at:

        [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

also check out the RealTek AC97 on that site.

---

### Post by carusoswi on 2007-05-28
> **kyphi said:**
> This is getting too confusing for me, Caruso.

Let me just list the problems you mentioned:

1.  Sound works in Windows but not in Ubuntu.
2.  Sound works in Ubuntu but not with the sound card (or chip) that you want to use.
3   Sound management programmes used via CrossOver do not work properly.
4.  The microphone for Skype does not work.

That sound management programmes do not work properly via CrossOver or Skype is because there is a problem with your sound setup generally.  Have a look at:

        [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

also check out the RealTek AC97 on that site.

You pretty much understand my problems.  Sound (from either card) works correctly in XP.
In Ubuntu, if both cards are enabled, then, Ubuntu seems to randomly switch between them on boot.  One time, the PCI card (Creative Audigy LS 2), another time, the Realtek - no rhyme or reason for this that I can see.

Your item #2 pertains to my desire to run audio editors (Steinberg Wavelab or Sonic Foundry Sound Forge) from Crossover "bottles".  The "wine mapper" that works in Crossover consistently uses the onboard card when both are enabled on the system.  If I disable the onboard sound, wine mapper will playback through the PCI card, but will not capture sound through the mic input.  I have not tried line input on the PCI card with Crossover - I probably should.

Item 3 in your list is related to item 2.

Item 4 - Skype - simply will not take input from my microphone - and, so, will not work.  None of the advanced options to select drivers from those listed works except Default.

Skype also works perfectly in XP.

Now, I realize that neither of my audio editors is supported officially by Crossover, so, frankly, I am surprised that they function at all from within Crossover - they will play back sounds, just will not record properly - onboard sound card capture is noisy (in any OS), and PCI card sound will not record from the mic.

So, those are my problems.  I did check out the site that you mentioned.  It appears that none of the drivers offered for Linux is an exact match for my card.  

I guess I may need to shop for a new card - we'll see.

Anyhow, I remain open for suggestions for anyone who can offer any.  I would be in absolute heaven if I ever got these Win-based editors to work.

BTW, I have had no success in getting Audiacity to record from the mic, either, so, there is, indeed, something wrong with my sound setup.  

Caruso

---

### Post by BobLand on 2007-05-28
Have you looked at the Comprehensive Sound Problem Guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I've had a similar problem but with just one card - Creative Labs SB Audigy LS.  I resolved my problem by commenting out all of the drivers from /etc/modules except the ca0106 driver.  After rebooting sound was 100%.

Bobland

---

### Post by carusoswi on 2007-05-28
Thanks, Bob.  I am going to try that right now.
Caruso

---

### Post by carusoswi on 2007-05-28
> **BobLand said:**
> Have you looked at the Comprehensive Sound Problem Guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I've had a similar problem but with just one card - Creative Labs SB Audigy LS.  I resolved my problem by commenting out all of the drivers from /etc/modules except the ca0106 driver.  After rebooting sound was 100%.

Bobland

Bob:
How do I go about "commenting out" all the extra drivers.
I went to the terminal invoked mixer type screen and could see where mic settings were at zero, but it's hard for me to identify which mic setting is which (I raised them all, but that didn't seem to do the trick).

My CA0106 is listed numerous times with extra numbers (CA0106 (2)).

Sorry I didn't quite understand you the first time around.  Could you help me further, please?

Caruso

---

### Post by carusoswi on 2007-11-25
> **BobLand said:**
> Have you looked at the Comprehensive Sound Problem Guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I've had a similar problem but with just one card - Creative Labs SB Audigy LS.  I resolved my problem by commenting out all of the drivers from /etc/modules except the ca0106 driver.  After rebooting sound was 100%.

Bobland

Bob:
I cannot find the /etc/modules about which you speak.  If I explore /etc I find no directory named 'modules' .  I find modutils, and I can find a file down below the list of directories named modules, but, when I open it, there are only three entries found in a list.  Each consists of just three or four characters.

That can't be right.

Could you please clarify?

Thanks.

Caruso

---


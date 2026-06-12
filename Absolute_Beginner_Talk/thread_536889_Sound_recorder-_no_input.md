---
title: "Sound recorder- no input"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-28
I've been going crazy trying to get my sblive to work.
I've can playback fine but I can't record.
In sound recorder it shows no option for " Record from input "
Also in system>preferences>sound>capture I don't hear anything.

---

### Post by mahiyar on 2007-08-28
Record from input is nothing but settings related to line in. I do not know exactly but just rattling possibilities from the top of my head.
1)Somehow sound capture does not work with both line in and mic cap selected. Deselect one of them and then try.
2)Check to see that the line in is not "crossed" or deselected.
3)Line in or mic volume is sufficiently high.
4)In the "switches" tab, line in capture is selected.

---

### Post by garyed on 2007-08-28
Thanks for the ideas but I've tried all that & still nothing works.
I'm dual booting with XP & have no problems with recording.

---

### Post by cc6000 on 2007-08-29
> **garyed said:**
> Thanks for the ideas but I've tried all that & still nothing works.
I'm dual booting with XP & have no problems with recording.

I have problem with my SB Live! sound card also- unable to use the Mic. I can play but cannot record. After 2 days and countless hours of resetting and setting all the options in various schemes, I came to the conclusion that my sound card's mic is not compatible with Ubuntu.  I think my SB Live! is the "Value" version. Which version do you have?

Let me know if you find any solution to the mic problem. I am reading about how to upgrade or install the latest ALSA driver/mixer software to see if that will get it working.

---

### Post by garyed on 2007-08-29
I have a  Dell with an Sblive 5.1 . that also has digital which I don't need.
I've gone from bad to worse. 
I've played around so much that I somehow made it so the card is not recognized by the alsa mixer at all. Now I can't even playback at all either.

---

### Post by Xebec on 2007-09-01
Unfortunately SBLive! 5.1 support is completely screwed (at least) in Ubuntu. Have been researching this topic for half a year. I can clearly hear the feedback from my mic in my headset, I can use alsamixer to control the volume of the feedback, mute/unmute it, give +20 DB power boost, but nothing can be recorded. My motherboard sound device can record sounds, however they are too weak and distorted to be used with Skype. That is the biggest turn off in Ubuntu for me.

BTW. Sound recording in SBLive! worked in one of Feisty betas, but with one of updates it disappeared. Sound feedback however has always been there.:(

Maybe I should try SUSE

---

### Post by carusoswi on 2007-09-01
> **Xebec said:**
> Unfortunately SBLive! 5.1 support is completely screwed (at least) in Ubuntu. Have been researching this topic for half a year. I can clearly hear the feedback from my mic in my headset, I can use alsamixer to control the volume of the feedback, mute/unmute it, give +20 DB power boost, but nothing can be recorded. My motherboard sound device can record sounds, however they are too weak and distorted to be used with Skype. That is the biggest turn off in Ubuntu for me.

BTW. Sound recording in SBLive! worked in one of Feisty betas, but with one of updates it disappeared. Sound feedback however has always been there.:(

Maybe I should try SUSE

This is also my one big area of disappointment with Ubuntu.  I cannot record anything from any application.  Skype also will not work for me (I hear the nice lady talking, but, she cannot hear me when I speak into my mic).

So, for me, for now, I have to go to XP for Skype and any recording/line in work.

My card is an SB Audigy 2.

It's drivers are loaded, and I can select it in the sound setup dialog, run the tests, but cannot record with it in any fashion.  PCX should be ashamed to have supplied a motherboard with such a poor onboard recording setup (Realtek onboard sound - there's so much scratch and machine noise when recording that nothing is usable - took the first two machines back, but they all suffered from the same poor audio setup - finally, because I wanted the small form factor of that machine, I just purchased the Audigy PCI card and have been using it without problems in XP).

I know we cannot blame Ubuntu for lack of support for our sound cards, but, I wish this could get fixed, or, perhaps there is some other decent sound card out there that would function with Ubuntu.

Caruso

---

### Post by cc6000 on 2007-09-01
> **carusoswi said:**
> This is also my one big area of disappointment with Ubuntu. 

So, for me, for now, I have to go to XP for Skype and any recording/line in work.

I know we cannot blame Ubuntu for lack of support for our sound cards, but, I wish this could get fixed, or, perhaps there is some other decent sound card out there that would function with Ubuntu.

Caruso

It's funny that I am in the same boat. I am unable to use Skype with my SB Live! Value. 

I wish someone can tell me a cheap PCI sound card that will work with Ubuntu that I can get for less than $20.

---

### Post by mahiyar on 2007-09-03
Most intel mobo based sound chip ICH5 works with Ubuntu.

---

### Post by cc6000 on 2007-09-03
> **mahiyar said:**
> Most intel mobo based sound chip ICH5 works with Ubuntu.

Thanks for the info.  I am probably not going to go out any buy a new mobo just for Ubuntu. Is there a cheap PCI card that is widely viewed as "plug and play" for Ubuntu?

---

### Post by MockY on 2007-09-04
> **cc6000 said:**
> Thanks for the info.  I am probably not going to go out any buy a new mobo just for Ubuntu. Is there a cheap PCI card that is widely viewed as "plug and play" for Ubuntu?


I wonder the same

---

### Post by cc6000 on 2007-09-04
> **MockY said:**
> I wonder the same

I was looking at the alsa site and they listed bunch of sound cards and my sound card was officially listed as one of the supported cards but the mic does not work with my copy of the card.

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

I think the problem is due to multiple variations of similar sound card models.  For example, I have 2 sound cards, both are labeled SB Live! and they look completely different. One is from Gateway and one is from Dell.  Even under Windows, I recall I can only use the driver from Gateway and not the official driver from Windows Update.

I think there needs to be a list of sound cards that are confirmed to be 100% compatible with Ubuntu with their exact model number listed somewhere. Then again, I wonder how much of the problem is due to sound card vs mobo/sound card combination.

With the popularity of Ubuntu lately, I am surprised that there is not an official list of sound cards already.

I still have some sound cards available from old PCs that I can try.  Then I am going to start buying cards from places that I am sure I can return and I'll start with the cheapest card.  I may even do a complete clean install of Ubuntu each time just to make sure I keep all the variables constant at the beginning before I start messing with all the controls in alsa.

It looks like it is going to be a hit or miss thing.  I would have been happy using my SB Live! Value without the Mic input and not know it, until I wanted to use Skype.

---

### Post by MockY on 2007-09-05
I ended up buying the cheapest sound card they had at Frys, and I am now very happy. Everythging worked out of the box with no configuration required. Even the sound is better. Before, it sounded like the speaker were broken even though the sound was set on low. Now everything is fixed. Alsa mixer is using: **C-Media PCI CMI8738-MC6**

---

### Post by cc6000 on 2007-09-05
> **MockY said:**
> I ended up buying the cheapest sound card they had at Frys

Can you list the brand and model number?
Thanks.

---

### Post by MockY on 2007-09-06
> **cc6000 said:**
> Can you list the brand and model number?
Thanks.

PPA Int'l 6 Channel PCI 3D

That's everything that is on the box. Like I said, this is extremely cheap stuff but works.

EDIT: 
This is most likely the card I bought (though they list a different chipset than is mentioned by Alsa on my system)

[http://shop2.outpost.com/%7BSXBh0NW6i9RWb+L-UqhQUQ**.node3%7D/product/3484263;jsessionid=SXBh0NW6i9RWb+L-UqhQUQ**.node3?site=sr:SEARCH:MAIN_RSLT_PG](http://shop2.outpost.com/%7BSXBh0NW6i9RWb+L-UqhQUQ**.node3%7D/product/3484263;jsessionid=SXBh0NW6i9RWb+L-UqhQUQ**.node3?site=sr:SEARCH:MAIN_RSLT_PG)

---

### Post by cc6000 on 2007-09-06
> **MockY said:**
> cheap stuff but works.

Thanks!!

---

### Post by Ashrael on 2007-11-20
When i try to test sound recording in system/preferences/sound, i get this error:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.

When i blow in the mic, i hear myself on my speakers, so somehow it's working, but not?
I am not logged in in any chat client, and in soundmixer my mic is muted??? when i switch mute off nothing changes.

I read a lot of posts with the same error, but none of them seams to either aply to me, or work for me...

---

### Post by Ashrael on 2007-11-20
well, i have tried:

1) replacing my ct4760 (emu10k1-sef) for a ct4700 (creative 5507).

SAME PROBLEM, okay, now for something completely different: take it out completely and enabled my onboard soundthingy: same problem: i have sound out, but as soon as i try to record i get this message again in various versions... it seems to be more an ubuntu bug to me,than a real soundcard problem...

anyone??
____________

---

### Post by Franknfurterhotmale on 2007-12-30
I too have the same problem with an Audigy2.
Now I know it's not me or my setup that's the problem, and The Dark Side has won this round.
Ta
Frank

---


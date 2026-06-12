---
title: "[SOLVED] Is there a sound card and sound settings primer somewhere?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by bw44 on 2008-01-08
I would really like to be pointed to a primer on sound cards (for example, I haven't a clue what a PCM  or a "Mixer" is) and also, if one exists, a primer on the Ubuntu/Gnome sound management tools.  As it is I'm lost!

I don't understand the choices in the volume control applet preferences and how they relate to the System>Sound>Preferences settings.  The Help page description of the latter doesn't seem to describe what I'm seeing at all (for Gutsy, anyway); it talks about starting  the Gnome sound server. What is that? The Help page says "Use the General tabbed section of the Sound preference tool to specify..." but my Sound Preferences window doesn't have such a tab.

I have a Dell desktop PC and the sound works OK with the volume applet preference set to "Master" (whatever that is).  On my Compaq laptop when it's set to "Master" I have no control over the volume; I have to set the preference to "PCM."  But when I do that  I lose the functionality of the keyboard buttons for increasing, decreasing and muting the volume (which work fine when I boot into XP)  I don't expect great sound out of a laptop, but I'd like to make the most of it.  

Help anyone?

---

### Post by kyphi on 2008-01-08
Do you really want a primer on sound cards?

Just in case you wanted to know more about ALSA (Advanced Linux Sound Architecture) I might be able to help.

The sound preference tool you can access by going to System (top left of screen), then Preferences and then Sound.  At the bottom of the screen you will see your Default Sound Card listed.  At the top of the screen make sure that the two check boxes are ticked.  You can also select sounds for various functions, either from the provided list or by clicking on 'Select Sound File' if you have created a collection of sound files.

The loudspeaker icon on the top right of your main screen is your volume control.  Move the slider up and down to increase or decrease the volume.  If you right click that icon you can access Preferences.  I use ALSA but some people prefer OSS (Open Sound System).

When you right click on the speaker icon you can access the Volume Control.  If you open the volume control, right click the top bar and from the dropdown menu click on 'On Top' (then that screen will stay on the screen until you close it).

If you move the slider on the volume control (top right of main screen) you will see the Master control move in accord.  If you move it too far down and it locks, just click on the red cross to unlock it.

I keep my PCM set to about 3/4 up (an explanation for PCM is too long, better just to google it).  PC speaker is your computer internal speaker.  Capture controls any device used to capture sound such as a microphone - if ther is a red cross click on the red cross to enable that function.  Switches should only have the Headphone Boost ticked.

Does that clarify the matter for you?

---

### Post by bw44 on 2008-01-09
> **kyphi said:**
> Do you really want a primer on sound cards?

Just in case you wanted to know more about ALSA (Advanced Linux Sound Architecture) I might be able to help.

The sound preference tool you can access by going to System (top left of screen), then Preferences and then Sound.  At the bottom of the screen you will see your Default Sound Card listed.  At the top of the screen make sure that the two check boxes are ticked.  You can also select sounds for various functions, either from the provided list or by clicking on 'Select Sound File' if you have created a collection of sound files.

The loudspeaker icon on the top right of your main screen is your volume control.  Move the slider up and down to increase or decrease the volume.  If you right click that icon you can access Preferences.  I use ALSA but some people prefer OSS (Open Sound System).

When you right click on the speaker icon you can access the Volume Control.  If you open the volume control, right click the top bar and from the dropdown menu click on 'On Top' (then that screen will stay on the screen until you close it).

If you move the slider on the volume control (top right of main screen) you will see the Master control move in accord.  If you move it too far down and it locks, just click on the red cross to unlock it.

I keep my PCM set to about 3/4 up (an explanation for PCM is too long, better just to google it).  PC speaker is your computer internal speaker.  Capture controls any device used to capture sound such as a microphone - if ther is a red cross click on the red cross to enable that function.  Switches should only have the Headphone Boost ticked.

Does that clarify the matter for you?

I really appreciate your post!  After I posted my cry for help I searched with Google and did not come up with a primer on sound cards, but did discover the ALSA site(s) and began to read.  It's a good start, but I haven't gotten very far.

I notice that you're a Dapper user -- I wonder if the sound preferences tool hasn't changed since that release (and since the Help page for it was last updated!).  When I open Sound prefernces, there are three tabs: "Devices" , "Sounds", and "System Beeps"  There is a heading toward the bottom of the first one ("Devices") that's labeled "Default Mixer Tracks" and a box labeled "Device:" where I can select (on my laptop) "HDA Intel (Alsa mixer) or "Conextand CX205551 (Waikki)(OSS Mixer)".  But there aren't  two boxes like you describe at the top of this screen.  So I looked on the next tab "Sounds".  At the top of that screen there are two check boxes (both checked by default) saying "Enable software sound mixing (ESD)" and "Play system sounds".  You didn't mention what the boxes you describe are labeled so I wasn't sure. Below these there is a list of "System Sounds" beside which there is a list of events, and the only ones for which values are shown are "Log out:" and "Log in:"  I'll attach screen shots of these two Sound preferences tabs (but these will be from the machine I'm composing this on so   the mixer device is shown as  Intel 8280IDB-ICH$ (ASA Mixer) rather than simply "HDA Intel (Alsa mixer").

As for the volume control in the upper right of my (gnome) desktop, when I right click and select preferences, a window opens labeled "Volume Control Preferences: and there are two things to be selected: "Select device and track to control."  The first chooses between the HDA Intel (Alsa) mixer  and the Wakiki OSS mixer; the second selects (on my laptop, between "Master"  "PCM", "Mic Bypass", "Capture" and "Digital".  (Which is different from the screen shot below which is from my desktop, which obviously has a different sound card with more capabilities.)

My immediate problem is that when I select"Master" on the Volume Control Preferences, there is no ability to control the speaker volumes: when I use the keyboard buttons to adjust the voume, an indicator opens on the screen showing the voulme changing (or muting)  and the buttons light up, but the actual volume (nil) doesn't change.  To get the volume control to work I have to chose "PCM".  I could also describe the apparent linking to the "Volume control indicators" which appear when I right click the volume control and seelct "Open Volume Control"  (basically, these seem to link to whether I have chosen "Master" or "PCM") but this post is already too long.

 I hope this gives you enough information to offer more help --- I sure need it!

Thanks.

---

### Post by kyphi on 2008-01-09
There are some minor differences in the volume control between Dapper and Gutsy but in principle they both work the same.

I am not at all sure what problem you are having.

You asked about soundcards - your laptop does not have one.  It only has a chip.
You may find some more information at this URL:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

You may also get more of an idea about Alsa by typing the word "alsamixer" into a Terminal (Applications, Accessories, Terminal).  See if all your controls work there.  
Run Alsamixer on full screen and use your directional arrow keys to move about, escape to quit.

I hope that helps a little.

---

### Post by bw44 on 2008-01-09
> **kyphi said:**
> There are some minor differences in the volume control between Dapper and Gutsy but in principle they both work the same.

I am not at all sure what problem you are having.

You asked about soundcards - your laptop does not have one.  It only has a chip.
You may find some more information at this URL:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

You may also get more of an idea about Alsa by typing the word "alsamixer" into a Terminal (Applications, Accessories, Terminal).  See if all your controls work there.  
Run Alsamixer on full screen and use your directional arrow keys to move about, escape to quit.

I hope that helps a little.

Thanks for posting again. I'm not sure what the difference is between a chip and a card, but no matter.  I'll try to be clearer about my question:

When I  run the alsamixer command as you suggested, there are three columns shown: "Master", "PCM" and one which does not seem to do anything, labeled IEC958.  When I move the volume control on the upper right of my screen the volume increases and decreases and the PCM bar column goes up and down in the Alsamixer display. I believe they are "connected" because in the volume control preferences I had to select "PCM" under where it says "Select the device and track to control."  Originally this was set to "Master" but there was no control over volume, though the Master column in the Alsamixer display would move up and down when I changed the volume control setting; volume was at a barely audible level and did not change.  So what's the problem? you ask.  And I agree, with the PCM setting (whatever it is) I get some control over the volume.  

On my desktop Ubuntu machine the volume control in the upper right corner is linked to the "Master" setting and controls the volume.  So what is the difference between "Master" and "PCM"?

The reason I care is that when I run Windows on the laptop the volume control buttons on the keyboard control the volume, the same as the volume control on the taskbar.  In Ubuntu if I select the "Master" setting described above, the keyboard buttons work to control little volume setting images which appear on the screen, but do not control the volume.  My question is WHY?

There also seem to be more controls available to my sound chip running under Windows (Wave, SW Synth and CD Audio all have controls as well as volume)  I'm not touting the merits of Windows here (I'm trying to get off it), but I have the feeling that with my current Ubuntu setup I'm not getting all the functionality from my sound card that I might.

I hope this gives you a better idea of my question.  If not, thanks anyway for having a go at it.

Cheers.

P.S. I had checked the URL you pointed me to and it was one of several that helped me get as far as I did with some kind of volume control.

---

### Post by kyphi on 2008-01-10
Google provides some rather good explanations for PCM (Pulse Code Modulation)  and IEC958 which are much too long to quote here.

My alsamixer shows 34 columns.

The buttons on my keyboard do not alter my chosen sound volume.

Your laptop would have a sound chip on the motherboard whereas your desktop may either have a sound chip on the motherboard or a separate soundcard.

To find out what you have type "asoundconf list" in a terminal or if you want to know more than that, e.g. what sound drivers are installed type "aplay -l".

Coming from Windows it is natural to expect everything to work the same - but it is not so.

I will gladly answer any questions that you have - no worries about that.

---

### Post by bw44 on 2008-01-10
> **kyphi said:**
> Google provides some rather good explanations for PCM (Pulse Code Modulation)  and IEC958 which are much too long to quote here.

My alsamixer shows 34 columns.

The buttons on my keyboard do not alter my chosen sound volume.

Your laptop would have a sound chip on the motherboard whereas your desktop may either have a sound chip on the motherboard or a separate soundcard.

To find out what you have type "asoundconf list" in a terminal or if you want to know more than that, e.g. what sound drivers are installed type "aplay -l".

Coming from Windows it is natural to expect everything to work the same - but it is not so.

I will gladly answer any questions that you have - no worries about that.

I appreciate knowing about the additional commands you mention. 

I think my problem (which I have had so much trouble describing) is a known bug in Gutsy and/or the ALSA driver.  If you are curious you can check it out at [https://bugs.launchpad.net/alsa-driver/+bug/149622](https://bugs.launchpad.net/alsa-driver/+bug/149622).

I don't understand the technical details, but I'm pretty sure this is what I'm experiencing.  At least now I won't keep trying to fix it by adjusting the user-accessible settings!

Thanks again.

---

### Post by bw44 on 2008-01-10
I'm marking this thread SOLVED because no one seems to know of an introduction or tutorial on computer sound hardware and software, and I couldn't find one searching the net.

The specific problem that started me looking for such a primer seems to be an as yet unresolved problem with the specific hardware I'm using and the ALSA  driver (see previous post).

Thanks to kyphi for trying to help.

---


---
title: "Sound not working"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-02
I have a Creative labs SB Audigy LS but the sound will not work.  I have done a search on google for a driver for ubuntu but can't find anything, help would be great, thanks.

---

### Post by ambien on 2007-10-02
I have experienced the same problem with my Creative Labs Live! sound card. Ubuntu comes with ALSA, which should be able to communicate with your sound devices. Check your settings to be sure that ALSA has detected your soundcard correctly (should list it by name). A GREAT way to google search the solution to search ALSA UBUNTU. However, you may have problems next reboot (once you get it working). My system has a nasty habit of reverting to a non-working audio driver after restart. Try hibernate if this happens to you =)

---

### Post by RyanZec on 2007-10-02
when i go to my device manager, the sound card is named like it should be

---

### Post by MrFSL on 2007-10-02
Quite often no sound is a result of a muted channel.

Open a mixer and unhide all the controls. Unmute everything and play around a bit.

---

### Post by RyanZec on 2007-10-02
I turned all channels to be maxed and unmuted still no sound when i try the tests from the sound preferences but got nothing.

---

### Post by Tyke91 on 2007-10-02
have you tried running alsaconf from a terminal?

---

### Post by RyanZec on 2007-10-02
alsaconf comes up as a unknown command.  I tried to do a 

sudo apt-get install alsa

and it says it is the newest version and 

sudo apt-get install alsaconf

is not a valid package

---

### Post by mithbuntu on 2007-10-02
Hello.  First post. First day with Ubuntu and really any linux system at home.

I just wanted to say I am having a similar issues (Creative Labs Sound Blaster Audigy 2 Platinum Pro).  No sound.  My soundcard is detected (along with 2 others on my motherboard) but I can't hear anything.

Also wanted to add that I have unmuted all channels and elevated sound levels to at least 50% on everything.

---

### Post by RyanZec on 2007-10-02
I also tried installing alsa-tools from what i read somewhere else with still no luck.

---

### Post by RyanZec on 2007-10-03
I still can't find any solution from searching on google.

---

### Post by forestpixie on 2007-10-03
might help - but then again might not - have you made sure the analog/digital switch is set correctly if there's one available, dbl clk vol icon - switches

---

### Post by RyanZec on 2007-10-03
everything looks good there.

---

### Post by js_fr on 2007-10-03
If you are sure it's a driver and not a configuration problem, you can try the latest version of ALSA (1.0.15rc3). That resolved the problems I had with a Realtek ALC268 chip and the (older) ALSA version from the Ubuntu repositories.
Sources you can find here: [http://www.alsa-project.org](http://www.alsa-project.org) ... installation instructions e.g. here : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (the article is about HDA Intel sound, but ALSA installation instructions are generic)

---

### Post by mithbuntu on 2007-10-04
Really strange.

I reinstalled ubuntu not long ago and before I updated my packages I was able to hear sound inside ubuntu.  

After the update with the 120 some packages are installed and I reboot my sound card that I'd like to use is no longer the default.

I've tried switching it back, but I can't seem to get it to work.

How do you set the default sound card? I thought I had, but obviously I haven't.

Better yet-- how do i remove the sound cards I dont want to use?

---


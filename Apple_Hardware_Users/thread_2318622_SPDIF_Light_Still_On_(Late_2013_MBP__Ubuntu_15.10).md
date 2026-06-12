---
title: "S/PDIF Light Still On (Late 2013 MBP / Ubuntu 15.10) + Touchegg Help?"
date: 2016-03-27
forum: Apple Hardware Users
---

### Post by chris_miller4 on 2016-03-27
So I have an MBP that I have completely removed OSX and replaced it with Ubuntu and so-far am loving it (an in Web DevOps, so I mostly work in Linux anyways).  The only problems left that I am having are with the S/PDIF Light stuck on regardless what setting is shown in ALSAmixer as muted or not.  ALSA shows 3 interfaces (S/PDIF, S/PDIF 1, and S/PDIF 2) and even after muting all 3 and rebooting, it still is on.  Even switching the interface and muting the S/PDIF there doesn't do anything.  

I then tried to follow the instructions from this post:  [http://ubuntuforums.org/showthread.php?t=2299760&p=13377327#post13377327](http://ubuntuforums.org/showthread.php?t=2299760&p=13377327#post13377327) , but the config files that they point out either don't exist (and do nothing when I create them) or don't have the information in them like the post specifies.

So I'm lost.  Anyone else got any ideas?

I also like the idea of the multi-touch gestures (ala OSX) via the Touchegg app in that post as well, but upon following the post, nothing works.  I can get the config to load, and show the config data that he mentions in the post, but nothing actually works.  The app seems to load correctly, and there aren't any errors, just nothing works.

The last question I have is about the suspend/resume on lid open/close that is mentioned in multiple posts here and there.  Everything seems to work fine on my laptop...  It suspends just fine when I close the lid just fine, and it comes back on when I open the lid.  Is there something that it should be doing better?  Am I missing something?

Thanks a ton for the help!

---

### Post by MikeBraxner on 2016-03-28
@ chris_miller4 ... All the links in the post you referenced work just fine, I double checked, and they do all contain the information specified in the post, though sometimes you actually have to read a bit.

As for the 'lid-open/close' ... if you don't have the 'resume from suspend' error that pestered the hell out of me, count yourself lucky, and leave it at that, you know ... repair ... not broken ... ;-)

Touchegg ... I know that the instructions work just fine under Unity, as well as KDE, though some key-assignments differ. Should you be running Gnome, you'll need to hop through one more hoop. If I remember correctly, you have to allow the desktop to show Icons (or something of the sort), or the desktop becomes the black hole of mouse gestures.

 As for config's not existing or not working ... which config's don't exist? Which one's don't work for you?

---

### Post by chris_miller4 on 2016-03-28
Thanks for the reply...   

I usually pride myself on NOT being the guy who just reads the first line of the instruction and then complains it didn't work because I didn't read all of it.   Guess I failed..  

Here's my issues with the previous post:

**S/PDIF Specific Section:**
[LIST]
[*]The "OLD" way basically says to check the /sys/module/snd_hda_intel/parameters/power_save and make sure the value is "1" (that's the only thing in the file) which it is, though I'm not sure what I'm supposed to do to rc.local (maybe put that command?).
[*]The "Cleaner" method says to put the line (options snd_hda_intel power_save=1) Which I did, but the light is still on.
[*]The part about TLP running doesn't apply as I don't have TLP running on this box.
[*]There was another post elsewhere on the net that talked about running `alsamixer` and highlighting the S/PDIF output on those screens and hitting "m" (mute) which I did as well on both "cards" (HDA Intel HDMI and HDA Intel PCH) which I did, and it doesn't work.  FYI, The HDMI Interface had 3 S/PDIF entries and the PCH had 2.  I muted all 5 and the light is STILL there.
[/LIST]

**Touchegg Config:**
[LIST]
[*]First Note: I am running Unity, not Gnome.
[*]I followed those instructions to download and build Touchegg from source.  Which all worked fine.  I even copied the config example over to the ~/.config/touchegg/touchegg.conf file without problems.  Running the sunclient command "seemed" to work as they didn't throw an error, but there was no output either.  But none of the "other" touchpad commands actually DO anything.  Normal operation is fine, but the multi-finger gestures don't respond.
[*]When I run `touchegg-gce`, I get the nice GUI window, but with nothing in the "details" section (see screenshot 1).  If I press the "Load" button at the top, it loads the info from the profile (screenshot 2).  I press "Save" and it prompts me to restart Touchegg, which I say yes to, and there is no error beyond that, but it doesn't work.  I also added the additional info to the ~/.xprofile to start automatically, but alas, it still doesn't work.
[/LIST]

I guess I'm lucky about the suspend/resume.  Wonder if it's a slight difference in the hardware, oh well.

Thanks for the help!

[B]
Screenshot 1:
[/B][IMG]http://api.cmivxx.com/cmimg/Screenshot%20from%202016-03-28%2011-11-51.png[/IMG]

[B]Screenshot 2:
[/B][IMG]http://api.cmivxx.com/cmimg/Screenshot%20from%202016-03-28%2011-13-29.png[/IMG]

---

### Post by MikeBraxner on 2016-03-28
@chris_miller4 ... My original post was specifically for a MacBook Pro 11.1, i.e. **Retina** ... and it sounds like your using a non-retina one. There will be significant hardware differences between those models, which explains why you don't have to worry about suspend.

SPDIFF ... Again, different model. I have no idea whether the 11.1 required way of handling this applies to your model. You might want to broaden your key-word search to include your model identifier. As for /etc/rc.local ... If you want changes such as the "old way' to take effect at every boot, they need to be instantiated at every boot, hence, you place them into, e.g., rc.local :-)

Touchegg ... While 'Unity reserves to itself gestures with 3 and 4 fingers making impossible to Touchégg make use of them' (touchegg wiki), you can google for a way around this. It's not all that complicated, and I *know* it works, since I used to use it under Unity.

---


---
title: "[SOLVED] Alsamixer question - Continuing the quest to restore functioning sound"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by DoubleR on 2008-02-10
I have been through  [Comprehensive Sound Problem Solutions Guide - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=205449")  and found it to be a good trouble shooting link.  (I killed my sound after removing Amorok from my Ubuntu installation). The driver seems to be loaded but not working so I tried the following to purge packages and reload.

[SIZE=2]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils[/SIZE]
[SIZE=2]sudo apt-get install linux-sound-base alsa-base alsa-utils[/SIZE]
Rebooted and still no sound

Oddly when I run Gnome Alsa Mixer I get the following error message

An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly. (details are listed below)

The ASLA mixer shows two tabs; Analog Device AD 1981B which I guess matches up with the sound card on my laptop which is Intel ICH6 Family and driver Intel8x0.    The other tab is silicon laboratory si3036.8 which I think matches up with the modem chip set. I was expecting to see the tab named as Intel ICH6.

Anyway how do I reinstall alsamixer to restore or correct the configuration file as this seems to be the next step?

.
Details of error message:
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/Silicon_Laboratory_Si3036,8_rev_7-Modem_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/Silicon_Laboratory_Si3036,8_rev_7-Modem_Speaker": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/Silicon_Laboratory_Si3036,8_rev_7-Caller_ID": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/Silicon_Laboratory_Si3036,8_rev_7-Caller_ID": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/Silicon_Laboratory_Si3036,8_rev_7-Off-hook": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/Silicon_Laboratory_Si3036,8_rev_7-Off-hook": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/Silicon_Laboratory_Si3036,8_rev_7": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/Silicon_Laboratory_Si3036,8_rev_7": `,' is an invalid character in key/directory names

---

### Post by BandD on 2008-02-10
I have a the intel ICH6 card as well and had some issues with sound.  I don't really understand all the sound stuff myself.  But I found this page to be very helpful:

[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]
https://help.ubuntu.com/community/HdaIntelSoundHowto[/URL]

as well as this thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=530374]("http://ohioloco.ubuntuforums.org/showthread.php?t=530374")

Good luck my freind!

---

### Post by DoubleR on 2008-02-11
Oh my gosh it is fixed.  I had headphone jack sense turned on in Alsa Mixer.  As soon as I unselected this, BANG sound is working.  Thanks for the links as it led me back to checking settings in preferences again.  Well I learned  more about Linux sorting this out.  Perhaps it was more than one problem along the way and not just this one simple setting change overlooked during months of trouble shooting off and on... and I did not give up and reinstall Ubuntu to fix it.  Its a good day.

---


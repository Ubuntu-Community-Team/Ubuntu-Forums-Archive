---
title: "CD Ripping - Pulling my hair out"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ashughes on 2007-09-26
I have been trying for 6 hours now to get CD ripping with sound juicer to work and I just cannot get it to work.

Sound Juicer is stopping me at every turn.  I have the gstreamer0.8-lame and lame packages installed from Synaptic.

When I go look at the list of profiles in Sound Juicer, my MP3 profile that I set up is not listed.  But if I go into manage my profiles it is there and set to active.

Checking my gnome audio profiles shows it there as well.

The only way I was able to get Sound Juicer to accept mp3 was to hack one of the default profiles that do come up.  But running with that gives me the following error:

Sound Juicer could not extract this CD.  Reason: Could not link pipeline.

One other thing I noticed.  When I click on Edit Profiles, the Edit GNOME Audio Profiles dialog comes up.  When I select a profile to edit and click edit, the Editing profile "blah" comes up but does not respond to click events until I close the previous dialog.

I have not been able to find another decent program to do this either.  I have been using Ubuntu as my main system for about 6 months now and I am about 2 hours from going back to Windows.

Save me!

---

### Post by mcduck on 2007-09-26
Try Grip, it's in the repositories. Pretty much the best ripping app for Linux. If you think it's too slow and your disk has no scratches just disable Paranoia in Grip options. Also if you have Dual-core processor be sure to increase the number of encoding processes in Grip's settings to get even more speed..

You may also want to install Lame, if you haven't got it already.

Check this thread for more info about Grip & how to configure it for best results: [http://ubuntuforums.org/showthread.php?t=183125&highlight=grip+lame]("http://ubuntuforums.org/showthread.php?t=183125&highlight=grip+lame")

---

### Post by ashughes on 2007-09-26
that worked like a charm.  thanks a lot.  Sound Juicer is such a POS!

---


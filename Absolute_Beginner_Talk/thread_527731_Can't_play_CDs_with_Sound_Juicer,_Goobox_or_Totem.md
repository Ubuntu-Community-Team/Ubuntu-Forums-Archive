---
title: "Can't play CDs with Sound Juicer, Goobox or Totem"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by SlithyTove on 2007-08-16
New Feisty install. Asus A8N5X motherboard.

When I try to play a CD with Sound Juicer, the disk tracks are identified correctly but instead of music I get rhythmic noise. Sounds a bit like radio static.

If I try to use Goobox, again the disk tracks are identified correctly, but if I hit the 'play' button, Goobox exits silently. If run from a terminal, I get:

GStreamer-CRITICAL **: gst_element_link_many: assertion `GST_IS_ELEMENT (element_2)' failed
Segmentation fault (core dumped)

Totem won't recognize that there's a CD in the drive.

VLC won't identify the tracks, but plays the CD correctly.

I've tried both the on-board sound 'card', NVidia CK804/RealTek ALC850 Rev 0, and an old Aureal Vortex PCI card. Same results with both.

I've read the multimedia sticky. I've got this stuff installed:

gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

I've searched these forums, googled the net, and can't find an answer. Other people who have a similar problems usually seem just to need the right gstreamer plugin, but I've got those.

I'm out of ideas. Help?

**Update, a few hours later**

This problem seems to be solved. I don't know exactly why. I struggled with it for three days, no change. Then, all of a sudden, about an hour ago, Sound Juicer and Rhythmbox (but not Goobox or Totem) started playing CDs correctly.

I hadn't installed any new software, made any system changes, or even rebooted. The **only** thing I had done was to try to play a DVD in the same drive (didn't work, I don't have decss yet), and then put the audio CD back in. Now it works. Very odd. Also, frustrating for the newbie.
[B]
Update, days later[/B]

Problem NOT solved, unfortunately, although there is a somewhat annoying work-around. See new post below. :(

---

### Post by nonewmsgs on 2007-08-24
well im glad it's working.  no idea here why either.

---

### Post by christianvaldes on 2007-08-24
this is my exact problem
some one please help

---

### Post by SlithyTove on 2007-08-24
My problem in the first message isn't solved. When the PC is re-booted, it comes back: Sound Juicer and RhythmBox just play noise when a CD is played.

Workaround: remove CD, put DVD in drive, attempt to play DVD. THEN put CD back in drive, and CD will be played correctly. Until the PC is rebooted, when the problem happens again.

So there is a work-around, but it's annoying. A few other people seem to have this problem, but it's rare. Maybe hardware related? I'm filing a bug report.

---


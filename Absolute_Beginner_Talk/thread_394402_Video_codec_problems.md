---
title: "Video codec problems"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Krystoll Meth on 2007-03-26
Until now, I've had quite a fun (and sometimes frustrating) time getting along learning about linux.  And, proud to say that through all of this, knowing about Automatix, I've avoided it.  Problem being, now I'm trying to play some downloaded videos and whatnot, but don't know how to get the codecs I need installed.

Best I came up with was results for automatix and "non-free codecs" which all say they are illegal in the US, I know that already.  

How/where do I get/install them?

Canadian BTW, so I'm clear.

---

### Post by crispy_420 on 2007-03-26
If you don't want to mess with Automatix, look into people's sources list they have posted for the appropriate server.

As a side note, I think some of the non-free codecs are not a violation if you own a legal copy of Windows licensed to that PC. I may be wrong though. DVD is not ok no matter what.

---

### Post by machoo02 on 2007-03-26
Check out [this page]("https://help.ubuntu.com/community/RestrictedFormats") for more information on installing some of the non-free codecs.

---

### Post by Krystoll Meth on 2007-03-26
Thanks!  I do actually own a copy of XP (3 to be exact...how sadly dumb I was) so Bill Gates and friends can bit it.  Anyways, thanks for the help!  Anyone else wanting to add more would be great, but this will hopefully suffice.

Other question directed at Crispy, how do I look at other peoples' sources for this and what do I do with them?

---

### Post by crispy_420 on 2007-03-27
Search the forums for dapper sources.list or whatever version you have. Than you can add them them in one of two ways. Manually edit /etc/apt/sources.list or via synaptic.

There are whole discussions on sources.list and even a subforum on the topic here:

[http://www.ubuntuforums.org/forumdisplay.php?f=41](http://www.ubuntuforums.org/forumdisplay.php?f=41)

---

### Post by Krystoll Meth on 2007-03-27
Thanks a lot to both of you!  That stuff helped a lot!!

---

### Post by crispy_420 on 2007-03-27
Good luck. But with sources, I made this mistake, make sure you use only Ubuntu versions that match. Watch out for pure debian sources if you want a stable system.

---

### Post by kahrytan on 2007-03-27
I don't know how many times I say this. Install VideoLAN (VLC). It'll play any video you throw at it. It will even play DVDs with Libdvdcss2 installed.


[SIZE="1"]Note: Libdvdcss2 is shrouded in legal issues. [/SIZE]

---

### Post by houstonbofh on 2007-03-27
I wrote a script for this.  Enable all the stock repositories first.  All the codecs, and other stuff I want.  Edit and use as you see fit.
```

#!/bin/sh
# Ubuntu Update Script (Edgy)
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
#
# Enable the Universe, Multiverse, and Restricted 
# repsoitories.  Uncheck the CD repository.
#
# DHCP Client
# /etc/dchp3/dhclient.conf
# Unhash 'send host-name' and put in system hostname.
#
# NTP Config
# Set the clock to update automatically from
# us.pool.ntp.org
#
# Note: Sudo must be enabled for this to work.
# (Type 'sudo ls' and the passowrd before running
# this script)
#

# Add extra repositories

# Medibuntu
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european flashplugin-nonfree sun-java5-plugin faad ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 liboggflac3 libquicktime0 libsidplay1 libswfdec0.3 libungif4g libwavpack0 libxine-extracodecs libxine-main1 libxvidcore4 libxvmc1 mjpegtools ntp ntp-simple sox vorbis-tools libdvdcss2 w32codecs msttcorefonts ogle-mmx ogle-gui streamtuner streamripper

```

---


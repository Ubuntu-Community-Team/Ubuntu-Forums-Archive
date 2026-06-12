---
title: "Confused... Repository Sources"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by SIobber on 2007-12-14
Okay, so I'm running in Gutsy Ubuntu (7.10) and when I try to click to enable any of the main, universe, restricted or multiverse options, it asks to "Reload" I do so, and then a window titled "Downloading package information" shows up.. It gets to 7 of 9 and then the files fail...Then it says:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

> [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


I looked around on the forums, and people having similar problems weren't using Gutsy, so I didn't know if I could use the same solutions or not... I'm VERY new to Ubuntu (like a few hours now..) and I'm very confused on this subject considering my firefox is working, and I was able to download flashplayer plug-in and install it... I also noticed people asked for the source file to see if there were any errors or anything, so here it is:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

It would be AMAZING if someone could help out! Thank you in advance ^^

---

### Post by overdrank on 2007-12-14
HI and your source's list should look like this 
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy-commercial main

deb http://medibuntu.sos-sts.com/repo/ gutsy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ gutsy free non-free 
```

You can remove the comment # and the 
# Line commented out by installer because it failed to verify:
using this command ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by philinux on 2007-12-14
This can be caused by installing the OS but without an internet connection.

---

### Post by hyper_ch on 2007-12-14
the problem is here:

```

Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

```

Does your internet access work?

---

### Post by SIobber on 2007-12-14
Thanks a ton overdrank! So I when I run that command in terminal, it'll allow me to edit the source.list file? And if I do so, can I just copy the list you posted in?

Oh, and hyper_ch, yes.. For some odd reason the only problems I have with connecting to the internet is when I try connecting to MSN with pidgin and when I try and get files through the Applications>add/remove... Firefox works perfectly, actually, I'm on it right now xD

---

### Post by SIobber on 2007-12-14
Okay, so I copied your code for the source.list and tried running the add/remove applications again and it gave me this:

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/Release.gpg:) Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
[http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/i18n/Translation-en_US.bz2:](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/i18n/Translation-en_US.bz2:) Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/dists/gutsy/Release.gpg:](http://medibuntu.sos-sts.com/repo/dists/gutsy/Release.gpg:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/dists/gutsy/free/i18n/Translation-en_US.bz2:](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/i18n/Translation-en_US.bz2:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/i18n/Translation-en_US.bz2:](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/i18n/Translation-en_US.bz2:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out

I KNOW my network connection is working, becausse I'm using my Gutsy ras we speak to access the internet and do this... The only thing I can think was that I did it wrong.. So here's what I did: I used the "gksudo gedit /etc/apt/sources.list" to open up sources.list, then I deletecd all of the existing code and pasted in yours... Did I do it wrong? This is very fristrating... :(

---

### Post by overdrank on 2007-12-14
HI and you can try and go to system, administration software sources  and change the location of the server. Hopefully that will help.

---

### Post by arochester on 2007-12-14
Try
> sudo apt-get update
then 
> sudo apt-get upgrade 
to get it going

---

### Post by SIobber on 2007-12-14
arochester: I just tried that, and it says it gets 16% and then sits there for a while... And eventually the "connection timed out"... Thank you for the suggestion, is there anything else you can think of?

overdrank: I tried the software sources too, and it started "failing" at like 7 of 35 or something like that... And then it poped up with all of those repository things... Thanks for the suggestion though! I really appreciate all of your help.

Do you think I got  bad copy of Ubuntu? Should I re-download and try to re-install?

---

### Post by t0p on 2007-12-14
There are definitely some repo problems going on.  Up to a few days ago I was using Feisty.  I tried doing an upgrade to Gutsy (as opposed to a reinstallation) and it kept failing because it couldn't download some stuff from the repos.  So I did a reinstallation from CD.  Then, before downloading the updates, I changed the repos I'd use to the UK servers (as I live in the UK).  I had no problems with that.  The solution to your problem could be to change the repos you use.

---

### Post by SIobber on 2007-12-14
Thanks! I'll try that now! So I can use other servers that the U.S. even though I live in the U.S.?

[EDIT] 
OMG! AMAZING!!! Thank you so much t0p! It worked! Well, some still failed, but I'm satisfied for the time being! Thank you again! Thank you all for all of your time and help with this subject! ^^ You guys are awesome!

---

### Post by t0p on 2007-12-14
Glad I could help!

---

### Post by SIobber on 2007-12-14
Alrighty, so I'm super happy the repository sources actually worked, but then I went to the Add/Remove Applications and tried to get aMSN, gstreamer(for the mp3 playback) and then another gstreamer(i think for mpeg) and then I went to lunch, because I was STARVING... I came back to find this "wonderful" little error:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.15-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tk8.4/tk8.4_8.4.15-1ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97RC1+dfsg-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97RC1+dfsg-0ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


By the way, I switched from the U.S.server to the top server on the U.K. list before doing the Add/Remove Applications...

---


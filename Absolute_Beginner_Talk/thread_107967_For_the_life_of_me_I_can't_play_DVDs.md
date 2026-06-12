---
title: "For the life of me I can't play DVDs"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by decypher44 on 2005-12-24
Hi all,

Well, I just installed ubuntu last night and it's my first linux box.  Got a free old HP desktop from a friend who was cleaning up his office.  Sweet deal.  Anyway, I was up until 2am last night reading up, installing packages and all kinds of things.  Completely lost track of time.

So, the one thing I still can't figure out how to do is play DVDs.  I can play CDs, I can read install discs, but no DVD.  I installed the dvdlibrary.css (i think).  I tried to mount.  I tried other things that I can't even recall.  Is there an easy way to do this?  Is there an easy way to find out what I'm doing wrong?

:confused: 

Thanks!

---

### Post by decypher44 on 2005-12-24
Oh, also, when the DVD is in the drive, it has consdtant activity.  Meaning, both the hard drive and the DVD drive lights are going.  Is it just taking a really long time to read?

---

### Post by kingsidy on 2005-12-24
you need to install the libdvdcss2 library to decrypt dvds. install automatix, and you can use that to enable dvd playback. Or you can look for the libdvdcss2 package on the net and install it. after that it should be able to play dvd's. Another suggestion is to intall totem-xine. In the terminal as sudo, type in: apt-get install totem-xine     
Or you can install mplayer or VLC. The default version of totem is not that good at playing dvds as it use the gstreamer backend.

---

### Post by davebgimp on 2005-12-24
All the information you need to set up DVDs should be here:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Also, lots of other good beginner set-up stuff here:

[http://help.ubuntu.com/](http://help.ubuntu.com/)

Personally, I use xine.

---

### Post by GTvulse on 2005-12-24
[QUOTE=decypher44]Hi all,

So, the one thing I still can't figure out how to do is play DVDs.  I can play CDs, I can read install discs, but no DVD.  I installed the dvdlibrary.css (i think).  I tried to mount.  I tried other things that I can't even recall.  Is there an easy way to do this?  Is there an easy way to find out what I'm doing wrong?

[/QUOTE]

Are you sure it is a DVD reader? Older business desktop computers would only have a CD reader, no DVD at all.

---

### Post by decypher44 on 2005-12-24
It's a DVD Rom drive that I had laying around.  I know it still works.  As for Automatix, VLC, xine - got'em.  dvdlibrary2.css - got it.  Any other suggestions?

Thanks.  I really do appreciate the help.

---

### Post by decypher44 on 2005-12-24
So, I tried the site that davebgimp listed and followed th directions.  I tried to open in totem and received the following error:

Failed to find mountpoint for device /dev/hdc in /etc/fstab

What does that mean?

---

### Post by decypher44 on 2005-12-24
Trying to open with beep - error:

Unable to mount the selected volume.:
Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0
Error: could not execute pmount


You know, I am actually very good with Windows.  I can do pretty much anything.  Built many PCs, done a lot of modding (sw and hw), and all kinds of stuff.  Not being able to play a DVD is making me feel so stupid.  But that's how I felt many years ago learning Windows.  I just need to have patience.

---

### Post by Mustard on 2005-12-24
have you installed totem-xine or are you still running totem?

I would agree with your last statement.  Patience is something you will need a lot of as you familiarise yourself with the way things work in linux. :)

I've been using linux since June 2005, and it was a good two months before I started feeling vaguely competent at what I was doing.

---

### Post by GTvulse on 2005-12-24
[QUOTE=decypher44]So, I tried the site that davebgimp listed and followed th directions.  I tried to open in totem and received the following error:

Failed to find mountpoint for device /dev/hdc in /etc/fstab

What does that mean?[/QUOTE]

Out on a limb...

First, does the /etc/fstab line reads like this one?

```

/dev/hdc        /media/cdrom0   auto    user,noauto     0       0

```

(Do notice I changed udf,iso9660 for auto, because it would not recognize my UDF data DVDs otherwise...)

Have you enabled the official backports repository in /etc/apt/sources.list (that can be done by hand or using synaptic, in the latter you have to activate "show disabled repositories" in Settings->Repositories->Settings button)? There are **serious** problems with the pmount version shipped in Breezy's installation CD (and main repository) that are fixed in the backport from Dapper.

---

### Post by decypher44 on 2005-12-24
Wow.  Lots of good info there.  Unfortunately, it's all Greek to me.  :p   I'll try and figure that all out.  Thanks.

---


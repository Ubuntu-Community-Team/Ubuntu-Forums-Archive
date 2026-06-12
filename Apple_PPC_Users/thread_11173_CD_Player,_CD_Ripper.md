---
title: "CD Player, CD Ripper"
date: 2005-01-14
forum: Apple PPC Users
---

### Post by Down8ve on 2005-01-14
I've not found how to configure the default CD player to output sound.  It plays the discs, even finds the online info correctly, but no sound.

The ripper takes forever to rip a cd.  iTunes is light-years faster.

I am aware there are other apps may work, but it would be nice to have the default configs do what they were meant to do.  Any solutions?

DSM

---

### Post by chascon on 2005-01-15
use xmms
mouse over main app window
press cntrl "p"
select "OSS" from bottom output plugin
enable CD Audio Player  [libaudio.so]
configure CD Audio Player  [libaudio.so]
under "device tab" select "Digital Audio extraction"
hit "Ok" and "Apply"

press "eject" on main app window then find "/cdrom"
press "add all files in directory"
hit "close"

hit play

DONE

You'll have to clear the play list to play another CD smoothly:
hit "file -" then "- all"
This clears the play list.

For usb speakers select "use alternate device" under OSS configuration.
name it "/dev/dsp1" under the "Devices tab".

PS- I'm sure that Hoary will support CDs with the default cd player.
If you get any distortion with xmms please report it as a bug.
Get involved:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4301](https://bugzilla.ubuntu.com/show_bug.cgi?id=4301)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4302](https://bugzilla.ubuntu.com/show_bug.cgi?id=4302)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4259](https://bugzilla.ubuntu.com/show_bug.cgi?id=4259)

UPDATE:
To avoid (initial) distortion you can configure OSS's "Prebuffer (Percent)" from 25 to 90.  Similarly, configure Alsa's "Period time" from 50 to 500.  Apparently I did not set these settings high enough.  I thought it was a bug as debian sarge did not have these problems but the xmms settings may be different on debian.  Also, I think Debian sets hdparm by default.  Which brigs to my next fix:
You can also "sudo hdparm -d1 /dev/cdrom".  There is also a way to set this by default.  I'll leave that for someone who has done this to elaborate.  The hdparm is no longer needed with the above two settings with my iMac DV 400mhz with one gig a ram for CD playing.  I still need it for DVD playing (and ogle is best for me.  Learn the "keyboard short cuts" posted at the ogle site as some gui buttons do not work ["stop"]).

---

### Post by jnoreiko on 2005-02-09
[QUOTE=Down8ve]I've not found how to configure the default CD player to output sound.  It plays the discs, even finds the online info correctly, but no sound.

The ripper takes forever to rip a cd.  iTunes is light-years faster.
[/QUOTE]

I'm having exactly the same problem.

What's more, once a track has been ripped (to OGG, with the default ripper), it's complete dross -- it sounds like an audio stream from the net that keeps breaking up.

Has a bug been filed for this?

---

### Post by chascon on 2005-03-02
[QUOTE=][/QUOTE]
 The default CD player sucks balls in linux-ppc in gerneral.  It is fixed in hoary though.
Not about ripped ogg files as I haven't done that in years, but it sounds as if it might be in part the ripping that is at fault.  Perhaps configure settings differently.  The cutting out might simply be a drain on processing power.  Try the hdparm command and anything else that might apply.

---

### Post by farruinn on 2005-03-02
First I'm going to suggest beep-media-player over xmms.  In general it works better and looks better for me.

Second, in hoary you can use grip which is good for ripping/encoding from cds and if you like you could even use it as your cd player.

-Nathan

---

### Post by godsunderstudysdad on 2005-03-06
We have successfully installed Gnome, through FINK, running under X11 We have also installed Ubuntu Gnome and KUbuntu in a seperate partition and are generally impressed, if not amazed, with all of them.
But the CD does not play on any of them. The CD gets read, I can even read the info about it, I can rip it (at slow data transfer rates). I can see the recorder plaaaaying, but no sound. This is a package and application independent problem. 
Forum solutions that I have seen so far don't solve the problem. Anyone have an answer or a clue?

---


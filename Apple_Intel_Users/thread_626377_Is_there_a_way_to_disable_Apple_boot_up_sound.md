---
title: "Is there a way to disable Apple boot up sound?"
date: 2007-11-29
forum: Apple Intel Users
---

### Post by blk97tt on 2007-11-29
I am running only Ubuntu 7.10 on a Intel 1.6 Ghz Core Duo Mini.  Is there a way to disable the Apple "bong" sound heard at boot up?

Thanks

---

### Post by nalencer on 2007-11-29
I sorta doubt it. The sound does get a bit annoying, especially as it plays through the speakers even if you have headphones plugged in. I imagine you *could* do it, but you'd probably have to get into the guts of the BIOS and edit it.

---

### Post by jslmg on 2007-11-29
There is a preference pane add-on called [Scenario]("http://http://macchampion.com/scenario_features.shtml") which may (or may not) have a feature that enables you to mute system audio at log out, bringing it back up after log in. You have to know a little AppleScript, but if you do, you can add a script that will let you do that. This would mute the Apple boot chime without making any significant changes to the system. Try it and see if it works.

BTW, it's a $10 shareware thingy. Also, I've never used it, so I can't vouch for it one way or the other.

---

### Post by jslmg on 2007-11-29
Still looking into this, cuz I might like to do it too.

There is a forum thread at Mac OS X Hints on this:
[http://forums.macosxhints.com/showthread.php?t=70573&highlight=disable+startup+chime](http://forums.macosxhints.com/showthread.php?t=70573&highlight=disable+startup+chime)

One suggestion there is simply to mute the internal speaker using the Apple Midi utility that comes with the OS.

Here's a caveat, though: There may be times when you need that chime. The chime is a reassuring signal that your hardware is working. If you don't hear a chime when you think you should, it means your motherboard or CPU may be shot. This is true when you are trying to troubleshoot, like when your OS won't load. A chime means the problem is in the software, not the hardware.

For that reason, it might be a good idea to tolerate it.

---

### Post by Grey Box on 2007-11-29
I don't hear the chime if I reboot with the sound muted, even if I muted it in Ubuntu. Mine's a Macbook (2nd generation).

---

### Post by jslmg on 2007-11-29
> **Grey Box said:**
> I don't hear the chime if I reboot with the sound muted, even if I muted it in Ubuntu. Mine's a Macbook (2nd generation).

blk97tt could try muting all sound in Ubuntu--Maybe I'll give that a try, too. The issue Mac mini users have--I've had it, as well--is that the chime comes booming, quite shrill, through the internal speakers, even if all other sound after log-in goes through the line-out or headphones. This was not the case with older Macs, like the G3's, though I've seen some disagreement about this. One would want to mute the internal speaker only, assuming one was going to rely on line-out or headphones for all other audio.

The reason for this "chime-through-internal-speaker" issue is explained quite well in the Mac OS X Hints thread I referred to.

---

### Post by Grey Box on 2007-11-29
> The reason for this "chime-through-internal-speaker" issue is explained quite well in the Mac OS X Hints thread I referred to.
Indeed, and it shows how much control over the hardware the EFI has. I bet it can even suppress the little green light on the iSight.

---

### Post by cyberdork33 on 2007-11-29
you could always disconnect the internal speaker :)

---

### Post by volanin on 2007-11-29
The best program I found for that: [**StartupSound.prefPane**]("http://macupdate.com/info.php/id/16425")
From the program's page:

[I]DESCRIPTION:
StartupSound.prefPane is the software which controls the volume of the startup sound of your Macintosh computer. StartupSound.prefPane mute the startup sound without changing the output volume setting. And StartupSound.prefPane limits the startup volume so that it may not become loud even if you make the output volume louder. To set up the startup volume, you select the "Startup Sound" pane added to the "System Preferences."[/I]

It's a MacOSX-only binary though.
:)

---

### Post by xeth_delta on 2007-11-29
Give this program a try to modify the volume of the chime: [http://www.versiontracker.com/dyn/moreinfo/macosx/25458]("http://www.versiontracker.com/dyn/moreinfo/macosx/25458").

It worked on my Macbook, it is called Psst.

Xeth

---

### Post by blk97tt on 2007-11-29
Thanks for the tips.  I don't have OS X installed on the computer so I cant use any of the OS X software mentioned.  I will try muting it in Ubuntu and see what happens.

Thanks

---

### Post by Smutronic on 2007-12-10
Can you post what happened? I haven´t installed mac os either and i don´t know how to disable that boot chime, because all the tools were written for mac os.

---

### Post by Rog-Mahal on 2007-12-10
In my 3rd Gen I took off OSX and single boot Ubuntu and the chime doesn't happen. I don't know if the fact that it's a  little newer has anything to do with it or not.

---

### Post by handy on 2007-12-11
> **xeth_delta said:**
> Give this program a try to modify the volume of the chime: [http://www.versiontracker.com/dyn/moreinfo/macosx/25458]("http://www.versiontracker.com/dyn/moreinfo/macosx/25458").

It worked on my Macbook, it is called Psst.

Xeth

It worked on my current model iMac too.

Thanks for the link :-)

[Edit:]  I just played around with the settings & can get it down really very soft, so it doesn't annoy my wife if I start up the iMac, whilst she is asleep in the next room.

[Edit2:]  The responses at the lowest settings seem to be a little inconsistent on my machine, it will boot with a very soft sound one boot, then no sound the next?  So I've turned the sound level up a bit & will see how that goes.

As far as duel booting is concerned, the system start sound comes in before the rEFIt screen appears, so I would think that using Psst from OS X will work  globally.  (I have rEFIt installed but no bootable Linux as yet, for anyone wondering.)

---


---
title: "upgrade, reinstall, report a bug, or go back to windows?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-12-16
I've asked this question twice so far and got absolutely no response. My thought now is to upgrade to Edgy, but I think a clean install is all that will fix it if I can't get some sort of clue here. A simple upgrade might leave the problem while I don't really want to upgrade yet. Going back to Windows was seriously tongue in cheek but might have got your attention. I have no intention of using Windows as my main OS anytime (soon or otherwise).

Now the problem. After upgdating to Dapper some months ago I had no problem, but then after a few updates the problem appeared. Booting into Ubuntu (I'm on a HP notebook nx6120) at about the stage that it looks for hardware drivers the mute light comes on. Having got into the desktop the volume controls work, I can increase or decrease volume as far as software controls are concerned, but the mute light stays on. The problem is that although I can control volume I can't get ANY sound out of the main speakers.

If I plug in a headset and microphone to the 1.6mm sound points they both work, but a USB headset doesn't get any sound, although it is recognized by Ubuntu.

If I use the Edgy LiveCD I get complete sound.

If I boot into XP (yuck) I get complete sound.

SO it has to be some sort of hardware trip that's happening in Ubuntu.

If someone could tell me where to play with hardware switches within the OS I'd have somewhere to start. If someone could tell me where to get HP help I'd have somewhere to start.

OR should I try reinstalling Dapper, upgrade to Edgy, or something else?

---

### Post by po0f on 2006-12-16
mdsmedia,

Your problem most likely came about due to a kernel upgrade.  Try downgrading it to a previous working version.

You can always upgrade to Edgy as well.  :)

---

### Post by mdsmedia on 2006-12-16
I tried all the available previous versions in GRUB. None of them was any good. Maybe if I'd tried a few months ago that might have worked but wouldn't have solved the problem. Any upgrade would have caused the problem I think.

If I upgrade to Edgy will it leave the problem? Should I clean install Edgy...or Dapper? Will the problem remain?

Is there somewhere in Ubuntu I can switch on/off the mute in hardware?

---

### Post by K.Mandla on 2006-12-16
If you don't trust your desktop controls, try running *alsamixer *from a terminal window. you should get a nifty set of volume controls drawn on the terminal screen. Check to make sure one of those is not muted. 

Other than that, you can set volume levels with the *amixer *command. There are a list of options for amixer [here]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=a/amixer"). Something like *amixer set Master 100,unmute* might do the trick ... or some variation thereof. You have to check what controls you have available with *amixer scontrols* or *amixer controls*.

Upgrading to Edgy might jostle something free, but I have a feeling the quirk will carry over to Edgy, unless it's a hardware problem. And if it works on the live CD and it works in Windows ... it has to be some sort of software setting.

---

### Post by mdsmedia on 2006-12-16
> **K.Mandla said:**
> If you don't trust your desktop controls, try running *alsamixer *from a terminal window. you should get a nifty set of volume controls drawn on the terminal screen. Check to make sure one of those is not muted. 

Other than that, you can set volume levels with the *amixer *command. There are a list of options for amixer [here]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=a/amixer"). Something like *amixer set Master 100,unmute* might do the trick ... or some variation thereof. You have to check what controls you have available with *amixer scontrols* or *amixer controls*.

Upgrading to Edgy might jostle something free, but I have a feeling the quirk will carry over to Edgy, unless it's a hardware problem. And if it works on the live CD and it works in Windows ... it has to be some sort of software setting.Thanks for that K.Mandla. I've tried alsamixer controls in terminal. Yes, a nice set of controls :) No change to the problem, however. 

I'll have a go with the amixer controls. Thanks for that :) Failing that I think just a reinstall  of some sort might be required. The beauty is I "know" it's a software thing, because I have no problem in Windows and the Edgy LiveCD works too. That's why I'm confident it's a software problem and that's why I kept trying here :) I figured if it's a software thing I might find a way to trip it rather than a reinstall. No luck, unfortunately.

---


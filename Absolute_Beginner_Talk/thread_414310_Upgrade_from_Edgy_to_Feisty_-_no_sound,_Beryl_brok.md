---
title: "Upgrade from Edgy to Feisty - no sound, Beryl broken"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2007-04-19
Hi all,

I upgraded to Feisty today against my better judgement, and now Beryl is all sorts of broken.  I've enabled the proprietary ATI driver and I'm using XGL.  When I boot into X, beryl just doesn't take over the window manager.  If I select compiz, or "enable desktop effects" compiz succeeds in wobbling windows and displaying the rotating desktop cube, but window title bars are broken.

Also, sound doesn't work and when I try to play sound in *any* application the app freezes - this includes all media players and the test options in the sound control panel applet.

Any help would be very much appreciated.

Sully

After a bit of thinking I see that beryl isn't starting.  Typing beryl at a command prompt yields this:
Detected xserver                                : XGL

Checking Display :1 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1
sully@sullyslaptop:~$

---

### Post by jsully1 on 2007-04-19
Sound automagically fixed itself on a reboot, but Beryl is still busted :(

---

### Post by Veoeluz on 2007-04-19
Although i do not have a solution to your answer, I have noticed similar instances of sound and visual stuff not working.. I am afraid however, that this thread will be closed by admin.. they have a note about beryl and compiz at the top of this section (newbie section that is..):(

---

### Post by db9s on 2007-04-19
beryl svn guys should be on it. Its nothing new, just run beryl as a "copy" . Advanced beryl options -> rendering path-> copy. This should be a temporary solution for now.

---

### Post by jsully1 on 2007-04-19
So it seems that Ubuntu Beryl does not support Xgl, you need to downgrade the package beryl-core.

Now that that's working though my sound issues are back and I'd say worse.  Some sounds are playing, other programs try to play sounds and immediately crash...

---

### Post by Sef on 2007-04-19
> Now that that's working though my sound issues are back and I'd say worse. Some sounds are playing, other programs try to play sounds and immediately crash...

What specifically is working and what is not working?

---

### Post by mayhemt on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97023](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97023) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				AS per the sound, try this it might help (each time sound is screwed up I run this). I am still lookling for a permanent solution for this.

```
 sudo chmod 666 /dev/snd/*

```
then test using System>Sound>Test
or on commandline gnome-sound-properties

---

### Post by jsully1 on 2007-04-20
Sorry, frustrating day - I usually try to be as specific as possible.

The only sound that plays is my login sound, a wav.  
Going to sound options and testing anything hangs the sound options and Gnome's menus.  I have tried playing some sample even sounds, and also pressing the test button for ALSA and OSS.
Thunderbird also hangs when it plays the new mail sound.  
Gaim doesn't seem to be playing sounds.
XMMS hangs on .wavs and .mp3's.

I have to do a complete restart before things function again - if I just restart x it hangs right after I login.

Where should I start checking?

---


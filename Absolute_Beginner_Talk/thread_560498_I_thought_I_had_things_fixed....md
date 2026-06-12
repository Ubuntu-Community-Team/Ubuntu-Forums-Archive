---
title: "I thought I had things fixed..."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by cmdrkeenkid on 2007-09-26
So, I'm not entirely sure what I'm doing wrong here.

I had another thread ([Gateway MX7515 needs driver support]("http://ubuntuforums.org/showthread.php?t=560099&highlight=gateway+mx7515")) which I thought was solved.

Well, my wireless is working fine and dandy still, but my sound went back out even though last night it was working fine. I'm running into the same problem of it showing music as playing, but no sound comes from my speakers. I tried running through the fix that was linked to me in that thread again, but to no avail.

I restarted the computer after running through all that a couple times last night with no problem, but when I rebooted this morning there was no sound and I have no idea why.

Any suggestions?

---

### Post by kellemes on 2007-09-26
What application are you testing the sound with?
Is it using the correct soundengine? Like OSS or ALSA..
Using ALSA you need to be sure the ALSA-daemon is running and started at boot..

---

### Post by cmdrkeenkid on 2007-09-26
I'm not entirely sure what I did, but after playing around with stuff in the terminal (I suppose that could have ended poorly for me, not entirely knowing what I'm doing) it's playing sound again.

What I was doing previously was trying to get it to play system sounds though the settings as well as mp3 files through Rhythmbox. Both are working now...

I have encountered another set of problems though. When I start up the computer a screen pops up saying something about "Unlock Keyring."

> The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked.

It then is asking for my system password. When I input the password and press okay it continuously comes up with the same prompt. The only way to remedy the problem is to just click deny, and it doesn't come up again.

The second problem is with the Desktop Effects. I had those turned on, with both the wobble effect as well as the workspace on a cube. Now, when I have these turned on the wobble works fine, but I only get one workspace.

Any ideas on this one?

---

### Post by dwhitney67 on 2007-09-26
Concerning the key-ring file, I believe it is used to store the security keys that you use to connect to your wireless access point(s).

If you want those annoying password prompts to stop, the easiest way to to setup a new key-ring file from scratch.  Run this command:

[FONT="Courier New"]$ rm -f ~/.gnome2/keyrings/default.keyring[/FONT]

Then reconnect to your wireless access point, enter the security key, and then when prompted to provide a password for the "new" keyring file, choose a password that you will remember.

As for your second problem, sorry that I cannot help you with that.

---

### Post by wpshooter on 2007-09-26
> **cmdrkeenkid said:**
> I'm not entirely sure what I did, but after playing around with stuff in the terminal (I suppose that could have ended poorly for me, not entirely knowing what I'm doing) it's playing sound again.

What I was doing previously was trying to get it to play system sounds though the settings as well as mp3 files through Rhythmbox. Both are working now...

I have encountered another set of problems though. When I start up the computer a screen pops up saying something about "Unlock Keyring."



It then is asking for my system password. When I input the password and press okay it continuously comes up with the same prompt. The only way to remedy the problem is to just click deny, and it doesn't come up again.

The second problem is with the Desktop Effects. I had those turned on, with both the wobble effect as well as the workspace on a cube. Now, when I have these turned on the wobble works fine, but I only get one workspace.

Any ideas on this one?

Yes, try turning off/uninstall those desktop effects and see if any of your problems go away !!!

---


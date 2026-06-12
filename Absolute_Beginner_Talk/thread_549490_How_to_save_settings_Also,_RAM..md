---
title: "How to save settings? Also, RAM."
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Halifax on 2007-09-12
Okay, I've had it with all the video problems I've had with Ubuntu. I started with Ubuntu, installed KDE, installed tons of codecs, different media players, uninstalled codecs, reinstalled codecs, swam through more configuration screens than I can remember, and I still have to reboot into Windows to watch a DVD or a video file. That, and my 5.1 audio system isn't playing out of the right speakers (the sub doesn't even work unless I plug headphones in first!).

So my question is this: Is there a way to back up the system settings I have and import them later? I'm willing to go through the video setup again, but I like my menu layout and visual theme customizations that I've done and I doubt I'd be able to get them all back to the way they were from defaults because I honestly don't remember HOW I changed some things, and others I remember took a long time to set up. I only want to back up the customizations I've made to KDE, and not anything like programs or codecs, in case those are the problem.

Also, none of the 64-bit flavors of Ubuntu will boot up from the live CDs - could my cheap-*** RAM be the problem? That's the only thing I can imagine, is that my ultra-cheap bargain RAM can't address 64 bits.

---

### Post by bwhitaker on 2007-09-12
Everything should be stored in your home directory.  If you copy the entire /home/username directory it should preserve all of your settings.

Also have you tried installing ubuntu-restricted-extras?

```

sudo apt-get install ubuntu-restricted-extras 

```

---

### Post by ajgreeny on 2007-09-12
Make sure you have the **medibuntu** repos activated in synaptic (google for info) and you should be able to get everything you need.  As far as i know libdvdcss2 is not available anywhere else and is essential for encrypted DVDs.  The repos will also make available many other things needed, eg win32codecs, etc etc.

---

### Post by Halifax on 2007-09-13
Everything already suggested has already been installed and reinstalled. That's why I don't know what the problem is. I think I'm just gonna have to reinstall Kubuntu and try again.

---

### Post by Halifax on 2007-09-13
Reinstalled Kubuntu - didn't fix anything - video files still not working. Haven't tested the speakers yet since it's 2 AM here now. ^__^

---

### Post by hyper_ch on 2007-09-13
Have you tried VLC to watch the videos? VLC is the most astonishing media player I know... out of the box it almost plays everything (the only issue I had so far was a real video with variable bitrate... that wasn't properly played).

Furthermore, you user settings are in your /home/USER folder saved. However system wide settings - such as the video card and stuff - is in /etc contained.

Backup of at least /home and /etc is recommended.

---

### Post by Halifax on 2007-09-13
> **hyper_ch said:**
> Have you tried VLC to watch the videos? VLC is the most astonishing media player I know... out of the box it almost plays everything (the only issue I had so far was a real video with variable bitrate... that wasn't properly played).

Furthermore, you user settings are in your /home/USER folder saved. However system wide settings - such as the video card and stuff - is in /etc contained.

Backup of at least /home and /etc is recommended.

On a fresh reinstall of Kubuntu with codecs installed, VLC gives just a blue screen for video files.

---

### Post by ajgreeny on 2007-09-14
If you have any chance to do so, and assuming Linux Mint KDE version is as good as the gnome version, download that and see if it will play videos etc for you.  The gnome version works on everything I've tried it with, out of the box, no additional codecs or anything.  It's based on ubuntu too, so has a really solid base.  Personally I still prefer ubuntu, actually Kubuntu in my case, or at least ubuntu with kubuntu-desktop added afterwards, though I have yet to try Mint gnome with added KDE desktop as a comparison.

---


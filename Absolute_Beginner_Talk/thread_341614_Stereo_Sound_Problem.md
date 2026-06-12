---
title: "Stereo Sound Problem"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-01-18
Hey guys, I've had Ubuntu Dapper for a couple of months now, and from the very beginning I haven't been able to have stereo sound out of my PC, I have one of those 2.1 stereo speakers from Creative, and my soundcard was included on my Intel Motherboard, but the thing is that I only get sound from the right speaker and some bass from the subwoofer, usually (even when I connect my phone to my speakers) I get sound from both left and right speakers and some sound and full bass from the subwoofer.

I already tried connecting my speakers to the other sound ports on the back (there are just 3, audio in, audio out and mic), but no luck yet. Dunno if there might be something wrong on the motherboard (something not connected properly) or a driver issue.

Ubuntu recognizes the card as the right one, I've checked every single switch in the volume control panel, and the ALSAmixer shows everything as unmuted...

Hope someone can help.

---

### Post by riven0 on 2007-01-18
[This thread says]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+solutions") to try re-installing the entire sound base. It's better to do this from the terminal since you may have to re-install the ubuntu-desktop afterwards. So hit CTRL + ALT + F1 and type this to uninstall:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then re-install it. Also re-install GDM and the Ubuntu-desktop in case they get removed:
> 
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

Then to be true, you can try rebooting and see what happens...

---

### Post by Xummoner on 2007-01-18
Thanks a lot, I hope nothing important gets messed up.

---

### Post by riven0 on 2007-01-18
> **Xummoner said:**
> Thanks a lot, I hope nothing important gets messed up.

:-D That's the beauty of Linux. Uninstall something important and it's always possible to get it back. Not sure if this solution will work, but it's worth a try.

---

### Post by Xummoner on 2007-01-19
Was about to uninstall the ALSA stuff but a lot of other things get uninstalled too, so I'm afraid some important stuff might get hard to recover later, such as nautilus and some other things. Here's what the terminal window shows:

```
david@David-Desktop:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  alsa-base* alsa-utils* gdm* gnome-applets* gnome-control-center*
  gnome-panel* gnome-session* gnome-terminal* linux-sound-base* nautilus*
  ubuntu-base* ubuntu-desktop* ubuntu-minimal*
0 upgraded, 0 newly installed, 13 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 22.6MB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by riven0 on 2007-01-19
Yeah, that's why it is recommended to re-install the Ubuntu-desktop afterwards. In the thread I referred to, a lot of people ended up uninstalling the ubuntu-desktop, (which will uninstall nautilus, etc), when taking out the sound-base and alsa. But there is no harm done; just re-install it afterwards. :)

---

### Post by Xummoner on 2007-01-19
OK, I'm about to do it, but if I uninstall all those things, do I have to restart and enter using recovery or console mode? or will I have the GUI running?... Ah, whatever! I'll just do it right now... Be back in a couple of minutes.

---

### Post by riven0 on 2007-01-19
> **Xummoner said:**
> OK, I'm about to do it, but if I uninstall all those things, do I have to restart and enter using recovery or console mode? or will I have the GUI running?... Ah, whatever! I'll just do it right now... Be back in a couple of minutes.

No, do it through the terminal. Hit CTRL + ALT + F1. That way you don't have to worry about rebooting or going into recovery mode when uninstalling this stuff.

EDIT: Oh yeah, to get back to graphical mode after re-installing everything, hit CTRL + ALT + F7

---

### Post by Xummoner on 2007-01-19
Oh OK, I'll do it right now and tell you the results, thanks guys! :)

---

### Post by Xummoner on 2007-01-19
> **riven0 said:**
> EDIT: Oh yeah, to get back to graphical mode after re-installing everything, hit CTRL + ALT + F7
Hehehe, didn't read that the last time, had to "sudo halt" but everything seems to be working now, but still no Stereo... maybe there's something wrong with the motherboard. I'm gonna check some stuff and let you know.


EDIT**
I'm almost sure there's nothing wrong with the drivers or Ubuntu, I think it's a hardware thing, since when I insert the speakers plug into the back of my PC but not all the way in I get stereo (but low) sound , but if I put it all the way in the sound gets louder but only on the right speaker, I guess the motherboard audio out is messed up, I'll have to take it to repair.

---

### Post by riven0 on 2007-01-19
> **Xummoner said:**
> Hehehe, didn't read that the last time, had to "sudo halt" but everything seems to be working now, but still no Stereo... maybe there's something wrong with the motherboard. I'm gonna check some stuff and let you know.

:( Then I suppose it's not a software problem. Have you checked your BIOS? Maybe something related to your sound card is disabled?

---

### Post by Xummoner on 2007-01-19
As soon as I remember how to get in the BIOS I'll check, I got into the BIOS the same day I installed Ubuntu and now I can't remember how I did it... lol

---


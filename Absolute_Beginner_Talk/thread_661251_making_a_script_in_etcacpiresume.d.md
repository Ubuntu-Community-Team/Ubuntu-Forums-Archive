---
title: "making a script in /etc/acpi/resume.d"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Mular on 2008-01-07
Quick question trying to get my sound to work after I suspend / resume.. 

I guess the thing I want to do is unload the module during suspend and reload it during resume, because its in use by the mixer I am not able to do that. If I suspend and resume, I have no sound. If I do killall mixer_applet2 then do sudo modprobe -r snd_ca0106 and then reload them and click reload on the mixer applet sound works again..

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/122025]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/122025") following hte advice on here, this post actually: 


 Tim Gardner wrote on 2007-06-27: (permalink)

After some experimentation I think a better solution is this:

/etc/acpi/suspend.d/86-lanai-sound.sh:
killall mixer_applet2
modprobe -r snd_hda_intel

/etc/acpi/resume.d/66-lanai-sound.sh:
modprobe snd_hda_intel

This gets the sound module shut down and restored in the right order, and works for both hibernate and suspend. The Gnome mixer applet still annoys you on resume, but I'm not sure how to fix that in a user generic way.


I can't seem to get the scripts to work though.. I don't have the snd_hda_intel so I repalced it with my soundcard snd_ca0106.

I also did chmod +x on both scripts.. They don't seem to run when I suspend =/

Any ideas?

---

### Post by Mular on 2008-01-07
Ok so if I just remove the mixer_applet2 (little sound icon) I can unload and reload the sound modules np, but if that mixer is up and running it gives me this device is in use error..

So figured I would keep the mixer off, since sound works anyway without it. Then I would just add my snd_ca0106 to modules to be unloaded and reloaded in /etc/default/acpi-support but when I tried to suspend I still lost sound..

I have also played around with the scripts and checked and rechecked and they are all in the right place according to the guide but it doesn't seem to do anything?

---


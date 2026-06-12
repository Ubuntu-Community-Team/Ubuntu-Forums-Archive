---
title: "Getting the Mic to work on the Macbook (1st Gen)"
date: 2008-04-02
forum: Apple Intel Users
---

### Post by Viro on 2008-04-02
I'm having difficulties getting the microphone working on my Macbook. I've installed Gutsy and downloaded all the updates. I've followed the [instructions ](https://help.ubuntu.com/community/MacBook#head-a089225bf23ccb59d5bc846e89776ea9890305a3) to get my sound working. 

It still doesn't work. From my investigations, it appears that the system doesn't think that a mic is present. I've gone to System->Sound and hit the test button and that says "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

This leads me to think that there might be some driver/setting I need to set but haven't done. Any help?

---

### Post by cyberdork33 on 2008-04-02
run 'alsamixer' in a terminal to see if there is a Mic channel.

---

### Post by Viro on 2008-04-03
ok, I've run alsamixer and the mic was displayed as MM (i.e. muted). I hit M to unmute it, but then I'm not able to increase the volume. Gnome still thinks that the mic isn't there.

---

### Post by cyberdork33 on 2008-04-03
well i don't know what those changes in the wiki do, but I don't know that they are needed. It may have messed something up in the gnome sound system.

If your Mic is now unmuted, you have to add it to a capture channel (if it is isn't already) and then adjust the level of "capture" for that channel... I know that sounds confusing... I don't have an Ubuntu machine available right now to give better instruction.

You can make sure that all the channels are showing in the gnome sound mixer by using a settings window available in the menu, so you might need to make sure everything is showing there.

---

### Post by Viro on 2008-04-03
The instructions in the wiki are to do with setting the correct volume of the mic. This is already done and the sound volume applet in Gnome shows the microphone as unmuted and at max volume. However, in Alsamixer the microphone's volume is shown as 0 and there is no way of increasing it (Up, W, etc don't work). 

In addition to that, the Gnome's Sound test (System->Sounds->Test input) indicates that there is an error reading from the Mic. This leads me to believe that the system thinks that the mic is not present. If that is the case, is there anything I can do? Any alsa config file to look at?

---

### Post by cyberdork33 on 2008-04-03
> **Viro said:**
> In addition to that, the Gnome's Sound test (System->Sounds->Test input) indicates that there is an error reading from the Mic. This leads me to believe that the system thinks that the mic is not present. If that is the case, is there anything I can do? Any alsa config file to look at?If that is truly the case then ALSA likely need patched as it is not detecting your hardware properly. There is not really a config file for it. Search the forum for one of niccfagn's patches and you can post the output he requests and he might be able to help.

---

### Post by Viro on 2008-04-03
Is that name spelt correctly? I've searched for Niccfagn and found nothing. In fact, searching on google, the only document on the entire internet that contains the phrase Niccfagn is thi thread :D

---

### Post by Viro on 2008-04-03
OK, I've downloaded the latest alsa-driver package from the ALSA project. I've compiled it and installed it successfully. When I do a modprobe snd-hda-intel, I get the following errors in dmesg.

> [106914.216000] snd_hwdep: disagrees about version of symbol snd_info_register
[106914.216000] snd_hwdep: Unknown symbol snd_info_register
[106914.216000] snd_hwdep: disagrees about version of symbol snd_info_create_module_entry
[106914.216000] snd_hwdep: Unknown symbol snd_info_create_module_entry
[106914.216000] snd_hwdep: disagrees about version of symbol snd_info_free_entry
[106914.216000] snd_hwdep: Unknown symbol snd_info_free_entry
[106914.216000] snd_hwdep: disagrees about version of symbol snd_unregister_oss_device
[106914.216000] snd_hwdep: Unknown symbol snd_unregister_oss_device
[106914.216000] snd_hwdep: Unknown symbol snd_verbose_printk
[106914.220000] snd_hwdep: disagrees about version of symbol snd_register_oss_device
[106914.220000] snd_hwdep: Unknown symbol snd_register_oss_device
[106914.220000] snd_hwdep: disagrees about version of symbol snd_ctl_register_ioctl
[106914.220000] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[106914.220000] snd_hwdep: disagrees about version of symbol snd_card_file_add
[106914.220000] snd_hwdep: Unknown symbol snd_card_file_add
[106914.220000] snd_hwdep: disagrees about version of symbol snd_unregister_device
[106914.220000] snd_hwdep: Unknown symbol snd_unregister_device
[106914.220000] snd_hwdep: disagrees about version of symbol snd_device_new
[106914.220000] snd_hwdep: Unknown symbol snd_device_new
[106914.220000] snd_hwdep: disagrees about version of symbol snd_ctl_unregister_ioctl
[106914.220000] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[106914.220000] snd_hwdep: disagrees about version of symbol snd_card_file_remove
[106914.220000] snd_hwdep: Unknown symbol snd_card_file_remove
[106914.220000] snd_hwdep: disagrees about version of symbol snd_register_device_for_dev
[106914.220000] snd_hwdep: Unknown symbol snd_register_device_for_dev


I'm guessing that there is something wrong. I just don't know what it is or how I'd fix it? Will updating the entire alsa package work?

---

### Post by Viro on 2008-04-03
Here's an update on the situation. I came across the bug [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972)

While that's for a different laptop, it applies to the Macbook too. I added the following line to my /etc/modprobe.d/alsa-base file
> options snd-hda-intel model=macbook

My mic works now :)

---

### Post by Viro on 2008-04-03
Incidentally, while my mic works now I have successfully killed my headphones -.-


*sigh*

---

### Post by cyberdork33 on 2008-04-03
yea that was something else that nicfagn was patching (I had too many c's). searching the correct term returns quite a few threads.

---

### Post by Viro on 2008-04-04
I've downloaded alsa 1.0.16, patched it, installed it and rebooted. Nothing has changed.

I wonder if this will be fixed for 8.04?

---

### Post by cyberdork33 on 2008-04-04
> **Viro said:**
> I've downloaded alsa 1.0.16, patched it, installed it and rebooted. Nothing has changed.

I wonder if this will be fixed for 8.04?
If it is not fixed now, then probably no.

Have you tried different values for the modules options?

```
options snd-hda-intel model=macbook
```

try mbp3 and there are some others.

---


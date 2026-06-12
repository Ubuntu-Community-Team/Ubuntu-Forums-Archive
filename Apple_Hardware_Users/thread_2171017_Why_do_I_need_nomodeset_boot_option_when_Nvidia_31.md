---
title: "Why do I need nomodeset boot option when Nvidia 319.49 is installed?"
date: 2013-08-28
forum: Apple Hardware Users
---

### Post by Quackers on 2013-08-28
I didn't need it until I ran boot-repair and set a separate EFI thingamagig for grub.
Now I see the grub menu after the refind menu but it just hangs at an INFO @iw message unless nomodeset is entered as a boot option.

---

### Post by 1/0 on 2013-08-28
Parts of the answer is found [here]("http://ubuntuforums.org/showthread.php?t=1613132").

---

### Post by Quackers on 2013-08-28
Sorry, I don't follow. I've never needed to use the nomodeset boot option on any of a dozen systems previously once the nvidia driver was installed.
In fact, I didn't need it on this system until I used the boot-repair utility.
Am I missing something?

---

### Post by 1/0 on 2013-08-28
Do you have copies of the original configs? If so is there any other differences except nomodeset?

---

### Post by Quackers on 2013-08-28
Which configs? I've got before & after boot script  outputs at [http://paste.ubuntu.com/6037492/]("http://paste.ubuntu.com/6037492/")
and [http://paste.ubuntu.com/6037706/]("http://paste.ubuntu.com/6037706/")

Is that it?

---

### Post by Quackers on 2013-08-28
Problem solved.
Part of the boot-repair was to purge and re-install grub (in a different place) and as a result of this my old /etc/default/grub file, with my edits (i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0) was replaced with a virgin /etc/default/grub.
Nomodeset worked to boot the installetion but the real fix was to re-instate those previous edits to /etc/default grub.
Thanks for your help 1/0

---

### Post by 1/0 on 2013-08-29
Great! Solving these things makes going to sleep much easier

---

### Post by Quackers on 2013-08-29
Indeed! I slept well :-)

---


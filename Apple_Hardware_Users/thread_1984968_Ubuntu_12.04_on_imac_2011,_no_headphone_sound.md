---
title: "Ubuntu 12.04 on imac 2011, no headphone sound"
date: 2012-05-22
forum: Apple Hardware Users
---

### Post by Lunarts on 2012-05-22
Internal speakers sound work if no headphone is connected, after a regular headphone is conected, no sound is avaible at the speakers(as expected) but the headphones also do not emits any sound. It is not a device change volume 'mute' problem.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1003039](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1003039)

If you're having the same issues, please let launchpad folks at the link above know it. There is also more details at the link above.

If you know of fix or partial fix for this issue, let us know.

---

### Post by zZ0nN on 2012-06-18
I'm having the same problem. Have you found a solution?

---

### Post by renws on 2012-06-19
exactly the same problem.

---

### Post by yinnus on 2012-06-19
already posted the exact same issue.  i've tried everything and nothing works.  hasn't worked with any linux distro until i tried fedora 17 the other day.  worked out of the box but i kept getting kernel panics.  too bad

---

### Post by benzodiaz on 2012-06-20
Hi,

I'm trying to figure this out too.  I read over the entire internet and the closest I've come is this patch:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7e5bea19aed376855eb2928c6d3c9ab0b35b5af7#patch1]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7e5bea19aed376855eb2928c6d3c9ab0b35b5af7#patch1")
I didn't try anything with it since it is actually for the 27 inch imacs, but I think it might work anyway.
It would be very nice to see an alsa driver for imac21_5...

If I get it, I'll let you know.

-J

---

### Post by benzodiaz on 2012-06-20
Does anybody know how I can apply the patch explained here:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7e5bea19aed376855eb2928c6d3c9ab0b35b5af7#patch1]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=7e5bea19aed376855eb2928c6d3c9ab0b35b5af7#patch1")

I looked in 
/usr/src/linux-headers-3.2.0-25/sound/pci/hda 
for the file called 
patch_cirrus.c, 
but it's not there.  So, if the file I want to patch isn't even there, what does that mean?

---

### Post by Lunarts on 2012-06-20
There is no need to apply the patch above, because it is already there on your ubuntu, my procedure:

1 - By logic recognized which the lines in green mean the extra fix lines of the patch

2 - using gksudo nautilus, then nautilus search feature, located the  patch_cirrus.c and entered there with full write privileges(due to  gksudo)

3 - using gedit search feature discovered which one of the patch green lines was already there.

After some additional thinking I noticed which one of the patch lines is  close to other lines whose content are exactly used on  /etc/modprobe.d/alsa-base.conf to solve such kind of problems. The alsa  list of supported models for the cirrus codec is not updated yet to  include that(not sure if it will); no matter if you get the list from  your own ubuntu or from the internet. There was no way to know this  model existed without benzodiaz help.

So, open your terminal and:

1 - sudo gedit /etc/modprobe.d/alsa-base.conf

2 - add to end of the file "options snd-hda-intel model=imac27_122"(only the stuff inside the quotes), save and reboot.

This worked for me, the only fix from several and several others I  tried. What a pleasant surprise, the fix was already there since this  year january, it was only hidden.

PS: Thanks a lot for the tip benzodias

---

### Post by zZ0nN on 2012-08-20
I can't seem to get this working on the iMac 2011 21.5".  Adding imac27_122 does not work.

Do the 21.5" and the 27" really have different sound cards?

---


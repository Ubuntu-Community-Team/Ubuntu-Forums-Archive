---
title: "Audio doesn't work"
date: 2010-03-06
forum: Apple Hardware Users
---

### Post by Cossackpride on 2010-03-06
I just started using Ubuntu, and love it. But, I have had an issue with the audio. It just doesnt work.
Ive tried everything on this the site 
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound]("https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound") 
but no luck. Any one have any idea what to do?

I got a mac book pro gen 5,5
and I am running the Extreme Edition Ubuntu "9.10."

---

### Post by viktara on 2010-03-06
When you run gnome-alsamixer does it look the same as in the screenshot on the documentation page?

After unmuting there you still have no sound?

---

### Post by gcndavidmn on 2010-03-07
You are not alone. We are having the same problem here [http://ubuntuforums.org/showthread.php?t=1423422](http://ubuntuforums.org/showthread.php?t=1423422)

Seems to be the new kernel update. No fix yet.

---

### Post by Jason O on 2010-03-08
Install the following packages through synaptic:

linux-image-2.6.31-19-generic 
linux-backports-modules-alsa-2.6.31-19-generic
gnome-alsamixer

- Reboot
- Select the 2.6.31-19 kernel option in grub during boot

You'll probably be running in low graphics mode, don't worry. Just click ok and continue with boot.

Open gnome-alsamixer (Applications >> Sound and Video >> GNOME ALSA Mixer) un-mute everthing and turn up Front Sp.

Sound should now work.

You'll have to reinstall you're Nvidia driver. And if you want to boot into the -19 kernel from now on, install the startupmanager package and run the program then select the -19 kernel from the list.

---


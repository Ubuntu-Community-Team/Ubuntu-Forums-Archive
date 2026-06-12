---
title: "No sound in 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by srathbone on 2007-10-22
Hello,

I am very new to Ubuntu and Linux having come from the Mac world.  I am using a seperate system to experiment with Ubuntu.

Everything was working great until this morning when my sound is not longer working.  I have re-installed the ALSA driver already. 

My sound card is an onboard intel ICH5.  Sound was working great last night and had been since nstallation of 7.10.  THen this morning no sound at all.  I have checked it is not hardware related by booting the 7.04 live CD that I have and sound is working great in that.  Any hints and tips you can give me would be great.

Thank you in advance.

---

### Post by Pumalite on 2007-10-22
I found this (I haven't proved it myself):

[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)

It might help you. I hope so.

---

### Post by TNakos on 2007-10-22
if you have a second audio card you need to disable it in your bios for alsa to work also. check to see in you alsa conf. file that your itel driver is number "hw. 0" in alsa base

---

### Post by srathbone on 2007-10-22
> **Pumalite said:**
> I found this (I haven't proved it myself):

[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)

It might help you. I hope so.

Thank you for the quick reply, I tried this to no success.

any other ideas?

thanks

---

### Post by srathbone on 2007-10-22
> **TNakos said:**
> if you have a second audio card you need to disable it in your bios for alsa to work also. check to see in you alsa conf. file that your itel driver is number "hw. 0" in alsa base

Thanks.

I am sorry but I am really very new to linux, where would I find the alsa.conf file?  can I use nano to edit it?

---


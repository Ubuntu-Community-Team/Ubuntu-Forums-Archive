---
title: "[SOLVED] Ubuntu &amp;amp; Bluetooth &amp;amp; Headset"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by wieman01 on 2006-05-27
Hi Troops, 

I've been trying to install my bluetooth USB dongle for days now, but in vain. I followed this thread: 

[http://wiki.ubuntuusers.de/Bluetooth/Headset](http://wiki.ubuntuusers.de/Bluetooth/Headset)

But at a certain stage - when I try to connect the dongle with my PC (Sony VGN) I get a long list of error messages when running "dmesg". These message look like this:

>> usb 1-1: new full speed USB device using uhci_hcd and address 4
>> snd_bt_sco: disagrees about version of symbol snd_ctl_add
>> snd_bt_sco: Unknown symbol snd_ctl_add
>> snd_bt_sco: disagrees about version of symbol snd_pcm_new
>> ...

Now I suspect that my dongle is not recognized (although I have tried out various ones). I am currently using "Billionton with HCI v2.0" which may be the key issue. However, can anybody confirm that these messages have nothing to do with the Bluetooth packages I have installed or any sort of configuration step that I have missed out? My headset (Logitech HS02-V5) is even detected when searching for it ("hcitool scan").

Like I have said, I did everything that was referred to in the guide (s. above), but before I waste another week in front of my computer, I thought I'd rather ask if somebody else has experienced this and knows the root cause of this problem.

Thanks, guys!

N.B.: The CVS address in the guide has changed: "anonymous@bluetooth-alsa.cvs.sf.net"

---

### Post by wieman01 on 2006-06-02
After a few sleepless nights I am able to answer my own question. Apparently this had to do with the standalone version of ALSA that I had installed. The module "btsco" / "snd_bt_sco" works only with the integrated version of ALSA that comes with the kernel. 

So my suggestion: Rather update your kernel than install the standalone version of ALSA. 

This remark can also be found in the README file of btsco v0.4.

---


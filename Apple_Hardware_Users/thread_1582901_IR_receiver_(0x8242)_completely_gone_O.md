---
title: "IR receiver (0x8242) completely gone? :O"
date: 2010-09-27
forum: Apple Hardware Users
---

### Post by jampe on 2010-09-27
There are a lot of threads on lirc and apple remotes here, I know, but my issue is completely different.

I've been using the apple remote (A1156) with xbmc, and it's been working out great until yesterday, where it just stopped responding out of nowhere.

**gnome-lirc-properties**
When I open the gnome-lirc-properties app, the terminal responds as following:
```

WARNING:root:/usr/share/lirc/remotes: Remote Antec_Veris_Premiere listed twice in imon/lircd.conf.imon-mceusb and imon/lircd.conf.imon-antec-veris.
WARNING:root:/usr/share/lirc/remotes: Remote iMON-PAD listed twice in imon/lircd.conf.imon-pad and imon/lircd.conf.imon-pad.
WARNING:root:/usr/share/lirc/remotes: Remote PVR2000 listed twice in leadtek/lircd.conf.PVR2000 and leadtek/lircd.conf.PVR2000.
WARNING:root:/usr/share/lirc/remotes: Remote Hauppauge listed twice in hauppauge/lircd.conf.hauppauge and hauppauge/lircd.conf.hauppauge.
WARNING:root:/usr/share/lirc/remotes: Remote BESTBUY listed twice in bestbuy/lircd.conf.bestbuy and bestbuy/lircd.conf.bestbuy2.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote Medion_X10 listed twice in atiusb/lircd.conf.atiusb and atiusb/lircd.conf.atiusb.
WARNING:root:/usr/share/lirc/remotes: Remote DVICO_MCE listed twice in dvico/lircd.conf.fusionHDTV and dvico/lircd.conf.fusionHDTV.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC-pulse.conf and generic/NEC-short-pulse.conf.
WARNING:root:/usr/share/lirc/remotes: Remote SONY listed twice in generic/SONY20.conf and generic/SONY12.conf.
WARNING:root:/usr/share/lirc/remotes: Remote NEC listed twice in generic/NEC.conf and generic/NEC-short-pulse.conf.

```

And whenever I press "autodetect" or try to select the correct IR receiver (0x8242), the application hangs and doesn't give me any more information.

**irw**
irw doesn't give me any feedback at all.

**dmesg**
dmesg gives me this on the IR receiver:
```

[    9.971849] apple 0003:05AC:8242.0001: hiddev97,hidraw6: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1/input0

```

**My suspicions**
I think the IR receiver (0x8242) is no longer recognised by lirc, but I haven't been able to figure out why or how to fix it.
In a desperate attempt to correct things, I did try to purge lirc and delete the configuration files before installing it again, but to no avail.

I could really use some help on this.
----------
PC: MacBook Pro 4.1
OS: Ubuntu 10.04 Lucid Lynx
IR remote: Apple A1156
IR receiver: Internal 0x8242

---

### Post by jampe on 2010-10-01
bump?

---

### Post by eti.que on 2011-08-11
Hi jampe,

I'm bumping this thread as I meet quite the same problem.

I own a Mac Mini 4,1 with Natty (installation coming straight from a non-mac computer, just had to reconfigure Xorg, I love the flexibility of Linux!), with the same internal IR receiver.

Basically when I launch gnome-lirc-properties... it doesn't start. It doesn't crash either (I installed HAL), it just somehow hangs.

I can launch it from the command line. After the WARNING you listed in your message, nothing happens. If I hit "ctrl+C", I get the "keyboard interrupt code" and the window appears.

And if I hit "autodetect" I get the same application hanging as you.

If anyone has a clue it would be much welcome !

---

### Post by jampe on 2011-08-11
Oh my, this is an old thread. It started working intermittently when updating to 11.04, although my final solution was to just sell the polished turd and get a better computer for the same amount of money :P

I guess my only useful advice is to try a clean install of 11.04, it definitely started working at that point.

---

### Post by eti.que on 2011-08-11
Ahaha I will certainly try that ;)

Thanks for the heads up.

---


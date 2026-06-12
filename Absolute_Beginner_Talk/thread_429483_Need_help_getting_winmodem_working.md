---
title: "Need help getting winmodem working"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-05-01
I am trying to get my mother board internal modem to work. I can't seem to get scanmodem to produce any useful info.
Tried installing drive for pctel. Got error saying to instal sl-modem. Wvdail does not seem to be sending my username to my isp.
Maybe I'm using the wrong version of sl-modem???
Should I be using another dialer.
I need help here.
Thanks

---

### Post by Kobalt on 2007-05-01
Can you please post the complete output of scanmodem ?
Does the Restricted Drivers Manager have your modem in its list ?

---

### Post by oilchangeguy on 2007-05-01
read this:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by helmut_hed on 2007-05-02
Hi linuxjerk,

I work on the pctel driver and can maybe help you.  Normally you'll get the slmodem message if you don't have a supported pctel modem (not all of them will work).  Try following this HOWTO:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

The first bit gives you an "lspci" command line that will tell you immediately if you have a supported modem.

If you do have a supported modem and the install is failing for you, please let me know.

Regards,
Jeff

---


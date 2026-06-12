---
title: "Caps Lock &amp; Num Lock don't work"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-08-16
I've had this problem since installing Edgy several months ago.  Caps lock doesn't work or even switch it's LED on.  Num Lock LED works but numbers stay locked on.

When I try to alter the keyboard in System>Preferences>Keyboard I get the following error message.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kb

Any ideas please?

---

### Post by chrisN_uk on 2007-08-16
Try reporting it in launchpad and see if they can help. It may already be listed on there. 

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by bugster on 2007-08-17
Thanks chrisN_uk

I reported it here 

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/133049](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/133049) 

yesterday.  Nothing seems to have happened - is there something more I should do? :confused:

---

### Post by bugster on 2007-08-17
I reported it in launchpad yesterday.  Does it take long to get a response ?  I am not complaining about a service where folks are giving time to solve my problem for free.  Just interested in how long it can take.

---

### Post by bugster on 2007-08-19
Haven't heard anything for a couple of days - Is there a site other than launchpad where I could report a bug ??

---


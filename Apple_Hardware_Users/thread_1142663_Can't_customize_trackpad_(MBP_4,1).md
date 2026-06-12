---
title: "Can't customize trackpad (MBP 4,1)"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by berlandb on 2009-04-29
Hello,

I'm on a fresh installation of 9.04 on a Macbook Pro 4,1. The trackpad works out of the box, but I would like to customize it (tap-clicking and 3 finger right clicking are bad defaults).

I tried to follow the instructions on the wiki page[1], but had no success. I would like to hear from fellow Macbook Pro owners what their experiences are. If the wiki instructions worked for you, I would appreciate a little more detailed instructions, if possible.


This is what I tried:

1. add 'blacklist usbhid' to /etc/modprobe.d/blacklist.conf
2. add bcm5974 and usbhid to /etc/modules
3. create file /etc/hal/fdi/policy/11-x11-synaptics.fdi with content from wiki page (which I tried to customize, e.g. swap 2 and 3 finger click)
4. restarted computer

Result: none.

3a. Additional step that I took from the bug report: #update-initramfs -u

Result: Linux didn't load bcm5974 at all after that and I was left without a keyboard.


What am I doing wrong?

Thanks for your help.


[1] [https://help.ubuntu.com/community/MacBookPro4-1/Jaunty#Touchpad%20(bcm5974](https://help.ubuntu.com/community/MacBookPro4-1/Jaunty#Touchpad%20(bcm5974))

---

### Post by __david on 2009-04-29
The instructions on the wiki page will break all input devices. Made the same experience as you. I don’t have a launchpad account and could not change the page …

I’ve attached a fdi file that is working for me (MBP 4,1).

---

### Post by cyberdork33 on 2009-04-29
i'd appreciate someone making the changes or post what the changes should be here so that someone else can make them

---

### Post by berlandb on 2009-05-02
> **__david said:**
> I’ve attached a fdi file that is working for me (MBP 4,1).

Excellent. That works for me, too. Thanks a lot.

---

### Post by berlandb on 2009-05-04
Hi,

like I already said above the configuration is working now. I could disable tap clicking and get 2 finger right clicks.

However, I can't drag with a right click anymore. The effect of a right click is the expected popping up of a context menu, for example. Holding down the button and moving my two fingers over the touchpad will not move the mouse pointer though.

This did work before I dropped that customized configuration into place (with 3 fingers then). Does somebody know what is causing this? Maybe there is something missing in or wrong with the configuration posted above?

Thanks

---


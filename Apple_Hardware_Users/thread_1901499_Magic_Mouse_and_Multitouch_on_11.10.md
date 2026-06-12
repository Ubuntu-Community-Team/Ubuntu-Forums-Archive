---
title: "Magic Mouse and Multitouch on 11.10"
date: 2011-12-28
forum: Apple Hardware Users
---

### Post by vaguely_clear on 2011-12-28
Hi all,

I have been hoping to get my magic mouse working on 11.10. Full disclosure: I'm running AMD64, not on a Mac at the moment.

Here is a link to a thread I opened previously, with a good summary of what I have tried:

[http://ubuntuforums.org/showthread.php?t=1896423]("http://ubuntuforums.org/showthread.php?t=1896423")

I didn't get any response on that thread. :(  Hoping maybe the Apple forum will have something to say about this.

Essentially, I have heard that magic mouse multitouch gestures should be working on 11.10, but I haven't observed anything beyond basic mouse functionality. Does anybody have a magic mouse working with multitouch gestures?

Something that occurred to me recently. My machine doesn't have built-in bluetooth, so I use a USB dongle, and an older one at that. Perhaps this is the issue? Maybe I need to upgrade to a better (newer) dongle?

Any response would be greatly appreciated!

---

### Post by happymellon on 2011-12-29
Are you looking for Touchegg?

[http://www.omgubuntu.co.uk/2011/01/touchgg-allows-you-to-assign-actions-to-multitouch-gestures-in-linux/](http://www.omgubuntu.co.uk/2011/01/touchgg-allows-you-to-assign-actions-to-multitouch-gestures-in-linux/)

It is in the Software Centre, so should be pretty simple, installing it now to see if it helps.

---

### Post by vaguely_clear on 2011-12-30
I have touchegg installed, but I get nothing from gestures on the magic mouse. Don't I need uTouch for basic gesture functionality? Is there a way I can test to see that uTouch is properly installed/working?

---

### Post by vaguely_clear on 2012-01-03
Does anybody have a Magic Mouse connected to a computer with Ubuntu installed? I would be curious to hear whether you have multitouch, even if it's just a "yes" or "no".

I grabbed a new Bluetooth dongle (mine was quite old, may not even be 2.1) but that had no affect.

---

### Post by Wolfador on 2012-01-04
> **vaguely_clear said:**
> Does anybody have a Magic Mouse connected to a computer with Ubuntu installed? I would be curious to hear whether you have multitouch, even if it's just a "yes" or "no".

I grabbed a new Bluetooth dongle (mine was quite old, may not even be 2.1) but that had no affect.


I have a Magic Mouse and Magic Trackpad at home, when I get there later I will try them both out and report back.

---

### Post by Wolfador on 2012-01-04
Was able to test out my Magic Mouse. I was able to left click, right click and scroll but none of the gestures that work on my MacBooks trackpad worked.

---

### Post by debili on 2012-01-16
any news? I'm looking into buying one... these gestures ( [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch) ) should be available?

---

### Post by vaguely_clear on 2012-02-24
> **debili said:**
> any news? I'm looking into buying one... these gestures ( [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch) ) should be available?

Sorry debili, I did not realize any more people had responded to this post!

Thus far, I have not been able to get said gestures to work. I started revisiting the issue today out of curiosity, and made a *small* amount of progress.

I have Touchegg installed from the Ubuntu Software Center, which is a package that should map gestures read from a Magic Mouse. I also have uTouch installed, which Touchegg uses to make it all happen, if I understand correctly. With both packages installed and Touchegg running in the terminal, I got nothing.

There's also this: [https://wiki.ubuntu.com/Multitouch/PyMT](https://wiki.ubuntu.com/Multitouch/PyMT)

I was able to get the PyMT demo working today for the first time, so clearly multitouch input from my Magic Mouse is working. Something must be up with Touchegg or uTouch on my system. I'm going to keep searching.

Anybody have thoughts on what I could be doing wrong?

---

### Post by vaguely_clear on 2012-02-24
> **Wolfador said:**
> Was able to test out my Magic Mouse. I was able to left click, right click and scroll but none of the gestures that work on my MacBooks trackpad worked.

Thanks for checking! I keep hearing that it should just work, so I'm glad to know I'm not crazy.

---

### Post by vaguely_clear on 2012-02-24
Right. Well, I didn't get very much further. I found this:
[https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport)

which is disheartening, as Magic Mouse support is not listed (but Magic Trackpad support is). However, down the page you can find this link:
[ENAC's general list of Linux multitouch devices]("http://lii-enac.fr/en/projects/shareit/multitouch-devices.html")

The ENAC page seems to indicate Magic Mouse support since (kernel, I assume?) 2.6.34:
> Apple MagicMouse. The mouse's back works as a trackpad. Proprietary Bluetooth HID protocol. Linux driver available since 2.6.34 approx.


Am I right in assuming that the Magic Mouse should be supported on 11.10, then?

---


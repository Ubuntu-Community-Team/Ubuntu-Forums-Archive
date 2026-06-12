---
title: "Easily fix your EJECT key!"
date: 2009-05-26
forum: Apple Hardware Users
---

### Post by volanin on 2009-05-26
The eject key has been dead for me since the Intrepid days, and I never found a solution to fix it properly. Today I was navigating through some _[ubuntu bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131818")_, and I finally found a proper solution posted by Martin Filip. To fix it, just create the file */etc/hal/fdi/policy/eject.fdi*, and copy these lines into it:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="button">
      <match key="info.product" string="Apple Computer Apple Internal Keyboard / Trackpad">
        <merge key="input.x11_driver" type="string">evdev</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

Then, restart hal and xorg.
Or alternativelly, restart ubuntu completely.
If it does not work for you at first, try uninstalling the mouseemu package.

Enjoy!

---

### Post by Richardcavell on 2009-05-27
I just tried it on my machine, and it works perfectly.  Thanks for the tip!

I'm running Ubuntu 64-bit 9.04 (Jaunty) on a Macbook 2,1 with a factory DVD reader/CD burner/reader.

Someone ought to make the installer do this kind of thing automatically.

Now, how about fixing the trackpad?...

Richard

---

### Post by volanin on 2009-05-27
Well, it seems we both have 64-bit Jaunty running on our Mabcooks 2,1.
Although it's not the subject of this thread, what's bothering you with the trackpad?

---

### Post by Richardcavell on 2009-06-10
Volanin,

Under Ubuntu my trackpad is very jumpy when trying two-fingered scrolling.  Placing a second finger on the trackpad causes it to generate some scrollticks.

I've posted in another thread about it, and also filed a bug with launchpad.

Richard

---

### Post by billbear on 2009-06-10
Try using both thumbs. As long as two fingers are placed horizontally scrolling is good. You can also scroll with one finger on the right edge of touchpad.

---

### Post by barbaGNU on 2009-06-10
i still use pbbuttonsd and i'm happy!

---


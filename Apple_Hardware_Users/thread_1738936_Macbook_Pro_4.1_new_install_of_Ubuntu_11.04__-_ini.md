---
title: "Macbook Pro 4.1 new install of Ubuntu 11.04  - initiating right click"
date: 2011-04-25
forum: Apple Hardware Users
---

### Post by jeffreylees on 2011-04-25
Hi

I've just installed Ubuntu 11.04 on my Early 2008 Macbook Pro and am trying to initiate some form of right click functionality. A mapped key is fine. Apple's ctrl+click is fine too. I do use a usb or bluetooth mouse quite often, but I really need right click functionality for those times that I just grabbed the laptop and ran with it.

Thoughts? I've browsed the forums, ran into a couple of solutions, but they were a bit older and I could not get them to work properly. Also a hindrance here is my relative unfamiliarity with Linux/Ubuntu.

Thanks

Jeff

---

### Post by Lars Noodén on 2011-04-26
I'm looking for this, too.  Right now I would like to free up the USB port and not have an external mouse.

---

### Post by Stéphane Scot on 2011-04-26
Why can't you use two-fingers on the pad when clicking for right click? That seems much easier to me than setting up an extra button that must be held whilst clicking.

---

### Post by jeffreylees on 2011-04-26
A) I had no idea that you could right click in that fashion... that's all I needed in that regard, tbh. I'm still curious about mapping keys for it, but for curiousity's sake, not functionality's. Thanks a lot!

B) Sometimes my touchpad stops working altogether, and the setting for it vanish from the setting menu. Typically a logoff or reset solves this issue. Any input? I haven't looked this one up yet, so I may find my own answer.

---

### Post by Stéphane Scot on 2011-04-27
A) Not at all a problem; glad that it helped you. Please feel free to mark the thread as [Solved] whenever you're satisfied with responses to the other issues. Mapping keys to things can be done in a number of ways but I'm not sure how to map a key to change the touchpad response.

B)I have that issue on my MBP4,1 sometimes. On mine it is fixable by opening a terminal and removing and reloading the module that runs the touchpad.
```
sudo rmmod bcm5974 && sudo modprobe bcm5974
```


That's obviously just a workaround not a fix, but it works for me.

---

### Post by jeffreylees on 2011-04-30
The touchpad only stops working when it wakes from hibernate/sleep. On initial boot it always works fine. This seems to follow along with the installation guide notes for Maverick which suggest to you a script to set up to reset mouse drivers on wake, or something like that.

However, those instructions were followed and achieved no result in Natty.

Thoughts?

When the touchpad hangs, it hangs immediately upon wake. At the login screen. Every time now that I notice it.

I set up the script below as a script that I can just leave on my desktop and execute upon waking and logging in... but it's still annoying.
sudo rmmod bcm5974 && sudo modprobe bcm5974

---

### Post by jeffreylees on 2011-05-01
I've narrowed the issue to specifically only occurring when the laptop is closed. When it merely sleeps or screensavers due to inactivity, I don't seem to get the issue. Only when I close it and then come back to it, whether in a few seconds or hours.

---

### Post by jeffreylees on 2011-05-08
In addition, I have a separate problem where my keyboard input sometimes stops working momentarily, for maybe 1-5 seconds.

---

### Post by tp21 on 2011-05-26
i confirm having the same behavior with the touchpad on macbook 4,1 and ubuntu 11.04.
touchpad is dead after resume from suspend, and the panel which displays the date ... etc is corrupted.
any ideas?

---

### Post by raumkundschafter on 2011-06-08
i've this touchpad problemo too on a MacBookPro5,3
& 11.04

---


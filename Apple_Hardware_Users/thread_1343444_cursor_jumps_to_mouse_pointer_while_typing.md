---
title: "cursor jumps to mouse pointer while typing"
date: 2009-12-01
forum: Apple Hardware Users
---

### Post by dolphinbrain on 2009-12-01
Hi all,

I am running Ubuntu Karmic on a MBP5,3 and when I type on the keyboard the cursor persistently jumps to the place when the mouse pointer is currently located.

I have read quite a few threads that suggest disabling the touchpad while typing (using syndaemon). While this works and the mouse pointer does not move anymore while I am typing, it doesn't solve the problem that the "typing cursor" will jump the mouse pointer when I brush the touchpad with my palm (even lightly). Consequently, I continue typing within the previous text, which is really annoying. It happens in any typing application so far (thunderbird, gedit, OpenOffice, firefox (while typing this post) etc.).

I also tried to increase the FingerHigh and FingerLow setting in synclient to 120 and 80 respectively (My tapping pressure measured with "synclient -m 10" average about 135-150.) But this did not get rid of the problem either.

This driving me really crazy! Has anyone ever experienced the same thing and found a solution to this problem?

---

### Post by Xog on 2009-12-01
My girlfriend experiences this problem too. But I don't. I told her it's because when she types, she hits the touchpad with her palm and it selects, so I told her to change the angle at which she has my laptop when she uses it. It's solved the issue. Hope this helps.

---

### Post by dolphinbrain on 2009-12-02
Xog, thanks for the reply. It would be something like a last resort, because I find it a bit uncomfortable if you have to type with your palms up in the air.

---

### Post by anionline on 2009-12-02
read this,

[http://miteshj-linux-tips.blogspot.com/2009/09/disabling-macbook-pro-touchpad.html](http://miteshj-linux-tips.blogspot.com/2009/09/disabling-macbook-pro-touchpad.html)


it work for me.

---

### Post by dolphinbrain on 2009-12-03
Thanks, anionline, for your reply. I guess using an external mouse is a viable, but not optimal, solution. I'll try that.

---

### Post by bluefoxox on 2010-01-21
Does anyone else see it as ridiculous that we have to consider disabling the touchpad?  I am seriously considering going back to Windows, it is always soemthing with Linux!

---

### Post by linuxopjemac on 2010-01-22
> Does anyone else see it as ridiculous that we have to consider disabling the touchpad? I am seriously considering going back to Windows, it is always soemthing with Linux!

Take it easy...there is always a solution! ;)

[http://mac.linux.be/content/touch-freeze-automatically-disables-touchpad-while-you-type](http://mac.linux.be/content/touch-freeze-automatically-disables-touchpad-while-you-type)

You can also try to read the wiki:
[https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing](https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing)

---

### Post by bdws1975 on 2010-02-15
> **bluefoxox said:**
> Does anyone else see it as ridiculous that we have to consider disabling the touchpad?  I am seriously considering going back to Windows, it is always soemthing with Linux!

I had the same thing in windows.  It's not a linux issue.

Brett

---

### Post by cpighin on 2010-10-18
:) I had the same problem with my Aspire8530 under Windows7 and Ubuntu10.10.

I was able to solve the issue with Windows7 by decreasing the touch-pad (mouse) sensitivity, but not with Ubuntu and so I opened a bug request here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/646860](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/646860)

Claudio :)

---


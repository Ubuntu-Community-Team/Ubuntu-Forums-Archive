---
title: "Macbook Air External Display,  IS IT POSSIBLE??"
date: 2009-04-07
forum: Apple Hardware Users
---

### Post by benniboi on 2009-04-07
I have Ubuntu 8.10 running just fine on my Macbook Air 1.1, that is, until I want to use a 22" external Lenovo LCD screen which I really need at work. 

I used to run Vista on the Macbook and never had problems with this screen, same with OSX. However I am having all sorts of problems setting this up in Ubuntu. 

I have read numerous posts on various forums and have spent about 5 hours playing around with xrandr to no avail. The Macbook and the LCD do not have a single identical widescreen (16:10) mode and when I select one of the other available modes, it all goes haywire. I have tried adding a new mode for TMDS-1 to match the one on the Macbook but that didn't have any effect either. 

I have even tried running both screens in 1024x768 res and even then it's all over the place. I am amazed that this is so complicated to achieve.

Has anyone actually got this feature working? Is it even possible in Ubuntu to extend the display onto this LCD whose native res is higher? (1680x1050) Even if it can be extended vertically rather than horizontally, that would do.

Any advice would be greatly appreciated. Just would like to know if this is possible or not before making any decisions to revert back to Vista or XP.

Thanks

---

### Post by tgalati4 on 2009-04-07
Go to an Apple store and try an Apple display.  Apple video hardware tends to use strange frequencies.  Try to grab the frequencies while in OSX, then create a custom modline for xorg.conf.

It's not easy, but probably doable.  I have an old Trinitron display that I run at 99 Hz.  Ubuntu would only give 85 Hz. SLED 10 created the appropriate modline, so I grabbed it and now use it in Ubuntu.

Try a Live CD of OpenSUSE and see if you can grab the modlines that show up in xorg.conf.

---

### Post by benniboi on 2009-04-07
Thanks for your suggestions, but after an additional two hours of stuffing around with it I finally managed to get it to work, albeit in vertical mode, but that's fine. Better than nothing. I am not sure what I did different to before but it works now...

But interestingly when I try to maximise VMware running XP to full screen on the Macbook Air itself, Ubuntu promptly shuts down and brings me back to the login screen... Fun never ends...

---

### Post by tgalati4 on 2009-04-07
That's the X server crashing.  Check /var/log for xorg errors.  It may be fixable.

Now you know why Apple keeps a tight fist over hardware and software.

Apple computers and Apple displays tend to work well together.  Just need to shell out more money.

---


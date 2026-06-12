---
title: "14&quot; ibook Screen Resolution"
date: 2006-09-20
forum: Apple PPC Users
---

### Post by meyerfun on 2006-09-20
I just installed ubuntu on a partion on a 14" ibook.  I am unable to view in anything other than 640x480, 60 hz. How can I change the screen resolution.  There are no options in the pref menu other than 60/ 640x480.

Thanks.

jm

---

### Post by meyerfun on 2006-09-26
Okay, I fixed my problem, but I really don't understand what I did.  After pushing buttons many, many times, I read about this command in the postings:

sudo dpkg-reconfigure xserver-xorg

I pretty much pushed through the menus hitting defaults, with an exception (I think, it is all a blurr of finger taps and guesses) of 16 as the preferred depth instead of 24.  I did this because somewhere I saw some reference about the ibook not supporting 24 unless you messed with some other setting.

After I rebooted, I was able to get the different resolutions in my   resolutions pref menu.

I rechecked the xorg file and discovered that some other settings had been added to my Display section.  I even found a better reference to this on a different forum search (how could I have missed it?):

"The problem is that the VertRefresh and HorizSync lines aren't in the xorg config file, you have to add those lines like this:

Section "Monitor"
Identifier "Color LCD"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

If you check your configuration those lines are missing.

Hope this will help you"

The poster is a genius, obviously.

So far, Ubuntu is not easy.

jm

---


---
title: "iBook Video problem"
date: 2006-07-08
forum: Apple PPC Users
---

### Post by timothyt on 2006-07-08
I just received my LiveCD (6.06) and have a serious issue with the video on my clamshell iBook. At first I thought it was just an issue running the LiveCD.

Then I performed an install and I still have the same video problem.

The video display is cut in half. The bottom of the display is 2-3 inches from the top of the LCD, and the top is below the bottom. There is a half inch gap between the top and bottom which cannot be crossed. The cursor stops at this point. To get to the bottom menu bar, I have to scroll to the bottom of the LCD and then the cursor appears at the top of the LCD.

The display was working properly when running OS X (Panther 10.3.9). 

Any help would be greatly appreciated.

---

### Post by Kelvin on 2006-07-10
Hi TimothyT,

What model/year of clamshell iBook are you using? I suspect we need to tweak the x settings, though they worked fine on my graphite 366mHz clamshell.

Let me know and I'll try to help.

Kelvin

---

### Post by timothyt on 2006-07-10
Kelvin
Thanks for responding. 
It is a 466mhz indigo iBook (Released in Sept. of 2000), 576 MB of RAM.

Hope this is enough info to go off of.

Regards,
Tim

---

### Post by digs on 2006-07-10
My screen is off kilter too - occasionally an update would change the degree of how much is pushed off screen. All I needed to do was use the auto adjust button on the monitor - I don't recall the ibook having any such on-monitor buttons for adjustment.

You can try to calculate the correct DisplaySize in your xorg.conf and see if that corrects the screen alignment.

[http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts]("http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts")

---


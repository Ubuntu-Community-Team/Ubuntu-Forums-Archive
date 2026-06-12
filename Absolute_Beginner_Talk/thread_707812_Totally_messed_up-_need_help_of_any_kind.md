---
title: "Totally messed up- need help of any kind"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by cincinnatus13 on 2008-02-25
Well, I went to set my TV out so it would display on my TV. To my surprise, it already was doing so, even without a second screen enabled. So I accidentally resized my comp. to 600x800, nothing happened, and I forgot about it. Well, I restarted and it screwed everything up. It was at 600x800 and when I went to change it, I had no other options to choose except anything smaller than 600x800. I went to enable my restricted drivers but they were already enabled. I tried to shut down and restart repeatedly and now when I go to load Ubuntu, I get to the splash screen and it loads halfway and then I get a black screen with a blinking cursor. I have no idea how to even get back into Ubuntu now.

My specs are: ATI Radeon Xpress 200M video card
Tosh Satellite 1.7Ghz, 1gig ram, etc.
and my native resolution is 1200x800. 

Is there anything I can do?

---

### Post by taurus on 2008-02-25
Wait for it to boot up.  Then, press <Ctrl><Alt>F2 and log in with your username and password.  Now, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, get back to the GUI login screen with <Alt>F7.  Now, restart X again to see if it works with <Ctrl><Alt>Backspace.

---

### Post by cincinnatus13 on 2008-02-25
I tried it without the phigh with no good results. I'll see if I can make this work. Thanks.

---

### Post by cincinnatus13 on 2008-02-25
Well...thank you, because that worked. I at least got back into Ubuntu. I manually selected a monitor for Toshiba and it seems to work but...a couple of my icons are screwed up, Compiz isn't functioning right, and I only have 2 workspaces instead of 4 even though 4 are selected.
Touchpad touch to click is on again as well.
Any solution to the icon problem?

---

### Post by cincinnatus13 on 2008-02-25
Alright....got everything working again but....
I went to edit my xorg file to take out tapping on the touchpad and it is BLANK. Absolutely nothing there. Tried to highlight it, nothing. I have no idea what is going on.

---

### Post by JoshuaRL on 2008-02-25
You mean absolutely nothing is in the xorg.conf file?  If thats it then you probably spelled the path wrong.

Make sure its "etc/X11/xorg.conf".  The capital X in "X11" is important.

---

### Post by taurus on 2008-02-25
> **JoshuaRL said:**
> You mean absolutely nothing is in the xorg.conf file?  If thats it then you probably spelled the path wrong.

Make sure its "etc/X11/xorg.conf".  The capital X in "X11" is important.

I would also include a / in front, /etc/X11/xorg.conf.

---

### Post by JoshuaRL on 2008-02-25
> **taurus said:**
> I would also include a / in front, /etc/X11/xorg.conf.

Aw man!  I hate when I leave out stuff like that.  I'm sorry cincinnatus13.

I guess my brain segfaulted.

---

### Post by cincinnatus13 on 2008-02-26
No, you guys definately helped. Turned out I was putting the lowercase x in there, but, as I was in the editor, I checked the other recently open docs and the real xorg file was sitting right there. I got the touchpad clicking disabled and compiz and everything else seems to work fine. My TV display is a little off but I think I can fix that alright. Thanks again though as it went from a nightmare back to good. :)

---


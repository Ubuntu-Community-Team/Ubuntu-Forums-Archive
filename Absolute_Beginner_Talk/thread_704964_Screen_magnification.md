---
title: "Screen magnification"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by edwardj on 2008-02-22
I successfully installed 7.10 on a Toshiba Portege R100.  The only problem is that the desktop seems to be magnified.  The display's resolution is 1024x768, but the desktop seems to extend well beyond those boundaries--I can't tell how far.  The other thing that makes me think magnification (rather than simply a higher virtual resolution) is that everything--fonts, icons--seems to be too large.  What is nominally 10-point type, for example, looks more like 18 or 20.

Any insight into this would be greatly appreciated.

ed

---

### Post by spiderbatdad on 2008-02-22
try ```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
``` Then enable the restricted graphics driver under System>>Administration>>Restricted Drivers Manager. After a reboot you should be good to go.
You might consider retitling your thread to suggest a problem with display resolution...it might get confused with an accessibility issue as it stands.

---

### Post by edwardj on 2008-02-23
I'll try it.  And I'll be more careful about subject lines.  Many thanks.

ed

---

### Post by edwardj on 2008-02-23
No joy.  I did it twice, the second time getting the message that it "is already the newest version."  From which I infer that it installed correctly.  I rebooted twice, each time getting the magnified screen.

I checked through the accessibility dialogs--as well as I can with 1/4 of a screen ;-) and nothing's turned on.  (The 1/4 screen's a real problem when you're in a shell--the default window's tall enough that you can't actually see what you're typing.)  Maybe the answer's to buy a higher-res monitor, haha.

Any additional ideas gratefully received...

ed

---

### Post by edwardj on 2008-02-23
Whoops.  One more thing: The only driver in the Restricted Drivers Manager is for a modem.

ed

---

### Post by sayakb on 2008-02-23
Try pressing the Windows (Super) key and scrolling down..

---

### Post by edwardj on 2008-02-23
Thanks for the tip.  I tried it using scroll keys and arrow keys, with the window in focus and not.  Couldn't get anything like scrolling behavior on the part of any element of the display.

ed

---


---
title: "GUI acting wierd on Ubuntu Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-20
I opened a file called faq.html from my cd and then i had to open terminal to do something, then when i draged the terminal from center point to the right, the GUI started to act wierdly...

Have a look at this screenshot 

[[IMG]http://img151.imageshack.us/img151/8725/screenshot1gj3.th.png[/IMG]]("http://img151.imageshack.us/img151/8725/screenshot1gj3.png")

Can someone help me figure out whats wrong now..?

---

### Post by Dr Small on 2007-10-20
It looks like the screen messed up. Does it do this often ?
CTRL + ALT + SHIFT + BACKSPACE to restart X.

Dr Small

---

### Post by latheesan on 2007-10-21
yea it does this very often =\

is it because i have ATI Mobility Radeon X300 graphics card? I cant install the restricted driver for it cause i cant another wierd error:

[[IMG]http://img512.imageshack.us/img512/6861/screenshotuh6.th.png[/IMG]]("http://img512.imageshack.us/img512/6861/screenshotuh6.png")

---

### Post by Hobo Joe on 2007-10-21
Use Envy to install your ATi drivers. I have a link in my sig.

---

### Post by latheesan on 2007-10-21
Alright cool, i will try that out. Is that the latest version on your sig?

---

### Post by avik on 2007-10-21
> **latheesan said:**
> yea it does this very often =\

is it because i have ATI Mobility Radeon X300 graphics card? I cant install the restricted driver for it cause i cant another wierd error:


Actually, try this.  Go to System->Administration->Software Sources.  Make sure universe and multiverse are checked.  Then try installing the driver again.

---

### Post by kevin11951 on 2007-10-21
> **avik said:**
> Actually, try this.  Go to System->Administration->Software Sources.  Make sure universe and multiverse are checked.  Then try installing the driver again.

also try changing the server it downloads from, when i installed gutsy NOTHING could download from the main gutsy server.

---

### Post by latheesan on 2007-10-21
to get my internet working, i switched back to Feisty. Im no loger on Gutsy.

So, i installd Envy now, what else do i have to do to get the ATI Drivers installed and get them working?

---

### Post by avik on 2007-10-21
Now that you have the repos enabled, and you can use the internet, have you tried using the restricted drivers manager?

If that still doesn't work, open up Envy and follow the instructions.

---

### Post by latheesan on 2007-10-22
okay i used envy and successfully installed the ati driver

now a new problem has emerged surface.

I cant enable display effects, it keeps saying "The composite extension is not available" :(

---

### Post by latheesan on 2007-10-22
Hobo Joe can you also take a look at this please - [http://ubuntuforums.org/showthread.php?p=3604338](http://ubuntuforums.org/showthread.php?p=3604338)

New problem emerged after Upgrading from 7.04 to 7.10 with Envy + ATI Drivers :(

---


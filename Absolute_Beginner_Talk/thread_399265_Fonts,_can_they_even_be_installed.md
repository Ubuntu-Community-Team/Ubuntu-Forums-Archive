---
title: "Fonts, can they even be installed?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by darkViVi on 2007-04-02
Hi all, I downloaded Ubuntu yesterday. Basically Windows XP is being a pain in the.... yeah you know what... Well, it's because of my PSU overheating..

Anyway, I'm a big big n00b with Linux, and I am also trying to work on my website, to do this I need my fonts installed.
Can anybody PLEASE, do a **detailed** post telling me **exactly** how? Please?
Because I got a zip file with 100 font's I saved just sitting on my desktop right now.

Ok? Thanks a lot. 


*eats popcorn while waiting*
:popcorn:

---

### Post by Warpnow on 2007-04-02
haha, I'm interrested to know this myself.

However, I do know easyubuntu will install some fonts for you.

---

### Post by mills on 2007-04-02
Enable multiverse and install the msttcorefonts package. That includes Arial an Times New Roman.

---

### Post by shirilover on 2007-04-02
Goto System -> Preferences -> Font.
Click the Details... button
Click the Go to font folder button.
Open another file manger(nautilus, thunar, konqueror) and drag-ndrop your fonts into the font folder.

If you wish to extract the fonts directly to the font folder, open the archive and press the extract button.
Choose Other... in the drop down list for Extract to folder,
Browse to *yourhomedirectory*/.fonts and click Open; you may need to right-click and select show hidden files.
click Extract.
You will need to execute ```
fc-cache -f ~/.fonts
``` in order to use the newly installed fonts

---

### Post by darkViVi on 2007-04-02
Haha, yeah a couple and some other stuff, thanks for that tip. Mostly because of the other stuff :P
But I still need my fonts though ;_;;

I opened the "fonts:///" thing but I couldn't copy/move/paste anything there.
*cries*

EDIT: *tries that* Thanks!

EDIT AGAIN: YAY!!!! Thanks so much :D
It worked!!

*bows down and worships you*

Thank you thank you !!!
*goes to work on site*

---

### Post by Lord Illidan on 2007-04-02
Open up nautilus as root with ```
gksudo nautilus /usr/share/fonts/truetype
``` in a terminal.
Then, copy all the ttf files you need over there. Make a directory to store them in and you're good to go..

EDIT, you might need to kill the xserver and relogin for the fonts to be detected in all your apps. Just press CTRL ALT BACKSPACE.

---

### Post by darkViVi on 2007-04-02
> **shirilover said:**
> Goto System -> Preferences -> Font.
Click the Details... button
Click the Go to font folder button.
Open another file manger(nautilus, thunar, konqueror) and drag-ndrop your fonts into the font folder.

If you wish to extract the fonts directly to the font folder, open the archive and press the extract button.
Choose Other... in the drop down list for Extract to folder,
Browse to *yourhomedirectory*/.fonts and click Open; you may need to right-click and select show hidden files.
click Extract.
You will need to execute ```
fc-cache -f ~/.fonts
``` in order to use the newly installed fonts

Thanks so much everyone :)

This solution worked out fine for me, and it wasn't too hard for a n00b either
Haha

However I couldn't find out how to log in as root.. I tried "su" in the terminal but was prompted by a password, well, it's not that important right now and a friend of mine can help me with that later in no time (if he knows the PW)
XD

Thanks again.

---

### Post by david_kt on 2007-04-02
> **darkViVi said:**
> Thanks so much everyone :)

This solution worked out fine for me, and it wasn't too hard for a n00b either
Haha

However I couldn't find out how to log in as root.. I tried "su" in the terminal but was prompted by a password, well, it's not that important right now and a friend of mine can help me with that later in no time (if he knows the PW)
XD

Thanks again.

The password is the first user password, when you install ubuntu.

DK

---

### Post by slayerboy on 2007-04-02
> **darkViVi said:**
> Hi all, I downloaded Ubuntu yesterday. Basically Windows XP is being a pain in the.... yeah you know what... Well, it's because of my PSU overheating..

Sorry if this is off topic, but uhhh....why not just get a new PSU?  Installing Ubuntu really isn't going to solve a hardware issue in 99.999995% of the cases.

---

### Post by miggols99 on 2007-04-02
In KDE you can use the font installer. That works for me :)

---

### Post by Lord Illidan on 2007-04-02
> **slayerboy said:**
> Sorry if this is off topic, but uhhh....why not just get a new PSU?  Installing Ubuntu really isn't going to solve a hardware issue in 99.999995% of the cases.

I concur. While Ubuntu might not be so stressful to your PSU, it will still be better to get a new one.

---


---
title: "Fresh ubuntu install: Simple keyboard issue"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ecmills on 2007-08-07
Okay. I´ve installed ubuntu onto a brand spankin' new Vaio laptop (a VGN-N365EB to be exact)...

And It&#347; got some serious issues with the keyboard. Mainly, the apostrophe and tilde buttons. As you´ve probably noticed in this post, my contractions don´t look normal.

Right now, pressing the apostrophe/quote key once gives me this: it&#347;
Tap it twice during the same word, and I get this: it´s

Neither one&#347;' quite correct, obviously.

(with the tilde key)
once: its
twice: it`s
holding shift once: its

To get a tilde, I have to hold shift and hit the key **twice**: ~

So, how do I fix this?

Also, what font is the equivalent of Arial, or whichever one windows uses as it´s default in I.E. and Firefox? I´d like forums and websites to look the same on this PC they do on my XP-equipped desktop... also running firefox. :)

(Oh, and I booted this thing **once** in Vista before wiping the drive... I know nearly nothing about this OS at the moment, but I´m still far happier this way.) :mrgreen:

A side, unrelated question: Is ¨Linux for dummies" going to be worth the read for a Gnome/KDE (kubuntu) novice? Or am I better off with another book? Any recommendations?

---

### Post by scapalexis888 on 2007-08-07
Maybe Ubuntu detected the wrong keyboard layout? If you are absolutely sure what region your keyboard belongs to, then select it instead of letting Ubuntu detect it. You can do it in System>Prefs>Keyboard

---

### Post by skwishybug on 2007-08-08
> **ecmills said:**
> 
Also, what font is the equivalent of Arial, or whichever one windows uses as it´s default in I.E. and Firefox? I´d like forums and websites to look the same on this PC they do on my XP-equipped desktop... also running firefox. :)

If you like Arial and the other MS TTFonts, open up Synaptic and search for msttcorefonts and install. It will give you the MS True Type Core Fonts (Arial, Comic Sans, Courier, Impact, Times New Roman, etc.)

Also, if you have access to an windows partition/computer, you can copy the true-type fonts from the MS fonts directory (c:\windows\fonts) and drop them into .fonts under your /home folder and be able to use even more than just the core fonts.

>  A side, unrelated question: Is ¨Linux for dummies" going to be worth the read for a Gnome/KDE (kubuntu) novice? Or am I better off with another book? Any recommendations?

I found Ubuntu Linux for Non-Geeks to be very useful both in introducing Linux in general and Ubuntu specifically
[http://www.amazon.com/Ubuntu-Non-Geeks-2nd-Project-Based-Get-Things-Done/dp/1593271522/ref=pd_bbs_1/104-4513191-1885569?ie=UTF8&s=books&qid=1186545771&sr=8-1](http://www.amazon.com/Ubuntu-Non-Geeks-2nd-Project-Based-Get-Things-Done/dp/1593271522/ref=pd_bbs_1/104-4513191-1885569?ie=UTF8&s=books&qid=1186545771&sr=8-1)

---

### Post by ecmills on 2007-08-08
Thanks guys, but I´d already tried the obvious thing: I´ve tried a half-dozen different layout and NOTHING changes.

What exactly would you suggest as the setup?

It&#347; got me down with the standard stuff (105-key and US generic layout)... But obviously, it&#347; a laptop that is missing a lot of keys (it&#347; got 71. I counted). The thing is, your next logical step is then to pick a laptop from the list, and try that.

No matter what keyboard I try, IT WORKS EXACTLY THE SAME. Everything is perfect unless I need a tilde or an apostrophe... :(

---

### Post by fourdigit on 2008-02-21
Bump because I have the same exact problem.

---

### Post by fourdigit on 2008-02-26
Bump because this problem is still driving me insane.

---

### Post by fourdigit on 2008-02-26
Okay I kept fiddling with it and the layout called "Generic 102 key (INTL)" worked for me.

Observe as I use at apostrophe! 

IT'S!!

HAHA!

---

### Post by emuellner on 2008-03-19
I am having the same issue. I have figured out that if I hold down alt while I press it, I can get a normal apostrophe. I have literally gone though and tried every keyboard layout in the options, yet it still isn't working. I have a saitek eclipse keyboard, I have gone through the xorg setup again, and nothing has changed. It's quite frustrating to have to hold down alt every time I want to use and apostrophe. Any suggestions will be greatly appreciated.

---


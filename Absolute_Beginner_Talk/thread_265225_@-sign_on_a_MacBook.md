---
title: "@-sign on a MacBook"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by pan_linux on 2006-09-25
Hello,

I just installed Ubuntu (in Parallels) on my MacBook just to mess with it. How the hell do I get the @-sign in Ubuntu? 

Thanks,
pan

ps: whohoo this is my very first Linux-releated post ever!

---

### Post by anaconda on 2006-09-26
Are all other special characters showing correctly?
I mean do you have the right keyboard layout? In different layouts @can be in different places...

Well anyway here is a gift from me to you
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
feel free to copy-paste them wherever you need..

(Yea.. I know Quick and dirty fix)

---

### Post by aktiwers on 2006-09-26
Isnt it just like on Mac, with the alt and @ botten?
Else maybe this will help?
[http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

---

### Post by el3ktro on 2006-12-05
Hi,

I have the same problem. I've installed Dapper on my girlfriend's iBook G4 - everything was fine. Now I installed Edgy on it (fresh install) - everything's fine, except the @ and € are not working. This is hilarious! My gf is booting Mac OS all the time because of this. I've played around with all the keyboard settings in Gnome (we have a German keyboard) - nothing helps. Any ideas?

Tom

---

### Post by PartisanEntity on 2006-12-05
After installing Dapper on my Asus laptop with a German keyboard I realised that I have to press 'Alt Gr' button (on the right side of the space-bar) to get the @ sign (in my case its on the 'E' key).

---

### Post by Kieranties on 2006-12-05
As far as I can remember (it's been a while since I usd a mac) the @ char gets switched with the " char

Try shift+2 for @

Of course it depends on what keyboard your using.  I'm British-English, think the above change results in the keyboard being interpreted as American-English

---

### Post by snq on 2007-02-10
Okay, sorry for dragging up this old thread, but I had the same problem with my iBook G3 and couldn't find a straightforward answer anywhere on the web. I have an iBook with a Swedish keyboard layout. Normally on a PC keyboard you'd write the @-sign using right-alt + 2. I've never had a mac before so I don't know how it's supposed to be done but I'm guessing it's right-apple + 2?
Anyway, I finally managed to figure out how to get it to work so I figured I'd post here how I did it.

First create a file in your homedir called ".Xmodmap"
Add the following line to it:
**add mod3 = Super_L**
Activate this change by running "xmodmap ~/.Xmodmap"

Next, go to Preferences -> Keyboard -> Layout Options
Under "Third level choosers", select "Press any of Win-keys to choose 3rd level"

And tada, you can now press the right "apple" button together with (in my case) 2 and get the @ that was previously impossible to type :)
Btw I left the keyboard model at the default "Generic 105-key (Intl) PC", changing it to Macintosh broke everything (only numeric keys worked).

The next time you boot up, xmodmap will ask if you want to automatically load .Xmodmap, tell it to do so, and you're good to go.

Hope this helps someone :)

---


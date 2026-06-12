---
title: "Soft/Shortcut Keys"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by flowerstealer on 2007-09-13
Hi

I moved over to Ubuntu last week and have worked most things out by myself (or with help from my bro, and by searching through old threads) but I can't seem to change the soft key function, or work out how to do it. I have an Acer Aspire laptop, and there are four soft/shortcut buttons next to the power button. I used to have them open a web browser, check my e-mails, etc, but now they do nothing. I have gone to System > Preferences > Keyboard Shortcuts, but Ubuntu doesn't seem to register me pushing those buttons. Is there anything I can do to get them working?

Thanks for your time.

---

### Post by Nulifier on 2007-09-13
If you open up a terminal window and type the command:

xev

it will tell you whether or not xserver (which handles all the keyboard input) actually registers those keys if nothing happens when you push those keys when you are running xev, then those keys are not mappable.

The input from xev will be put into the terminal window (mouse input also). If there is input in the window when you push the keys then you need to map those keys to a function.

I found [this page]("http://www.cakey.de/acerhk/") for you which may help (it list aspires as being supported)
you will need to build the driver and I dont know how to use it (i would read the readmes)

Hope this helps

---


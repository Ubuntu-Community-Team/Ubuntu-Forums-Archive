---
title: "A Few Questions"
date: 2008-02-15
forum: Apple PPC Users
---

### Post by Venom_Man on 2008-02-15
I finally got ubuntu 7.04 installed and i have a few questions. First off how do i right click when using an iBook G3. Second how do i delet apps that i have installed, for example screenlets. Lastly where do i add fonts. Thanks any answers would be great.

---

### Post by Twiggy003 on 2008-02-16
RIght click: I think the default is the mac key, or ctrl and click or mac key and click, I can't remember.  

As for apps you've installed, if you've installed them using Synaptic manager, simply right click and select remove.  

Doing a search for fonts on synaptic probably would find the fonts you want.

I hope that's helped a tad.

---

### Post by stream303 on 2008-02-16
Does F11 or F12 work for right click?

Have you considered using a 3rd-party 2 or 3 button mouse?  Life is SO much easier. :)

---

### Post by Venom_Man on 2008-02-16
thanks for the help. i figured out that f12 is right click. when i go  into my usr/lib to try and get something it says that i dont have permisson but im the only urs on it how do i give my self full adim acesses

---

### Post by lluisanunez on 2008-02-16
IN terminal, you prefix your commands with sudo
It then asks for your password

---

### Post by stream303 on 2008-02-26
> **Venom_Man said:**
> Second how do i delet apps that i have installed, for example screenlets. Lastly where do i add fonts.

If you used Synaptic to install screenlets, you can just unmark it, and then apply the action.

or from the commandline

sudo apt-get remove screenlets

Fonts such as with the msttcorefonts if you absolutely must have microsoft fonts, and many find that the Bitstream fonts are very good can also be installed via synaptic or the commandline, ie

sudo apt-get install msttcorefonts

If you have some custom fonts already, you can do a drag-n-drop operation by doing this quickie shortcut:

ALT-F2 to bring up the command window for Running an Application

type
```

fonts:///
(yes, three backslashes)
```

drag your fonts inside the window!

---

### Post by Venom_Man on 2008-03-01
thank you for the help

---


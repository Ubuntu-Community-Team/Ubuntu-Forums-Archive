---
title: "stop firefox from telling me i need plugin"
date: 2006-12-23
forum: Apple PPC Users
---

### Post by Kurbycar32 on 2006-12-23
ok for the time being i give up on trying to get flash and quicktime to work on my ubuntu ppc computer.  i attempted to install gnash last week and totally hosed my OS.  so what i want to do is just have firefox stop telling me that im missing plugins.  i looked in the preferences but didnt see an option for that

---

### Post by kerry_s on 2006-12-23
You can try looking at the about:config settings & see if theres a setting to turn it off, here the available settings list-> [http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries)

Sorry, i don't have time to read it & give you the answer, i'm on my way out.

---

### Post by Kurbycar32 on 2006-12-23
that link is dead but i found what you were talking about. 
[http://kb.mozillazine.org/About:config](http://kb.mozillazine.org/About:config)
the gist is that all firefox options are available by typing about:config in the address bar of firefox.

the problem is that i have no idea which option i need to change and there are many to choose from.  ill keep digging but if someone knows off hand or can point me at a summary of options it would be appreciated

---

### Post by kerry_s on 2006-12-23
I don't think you can, but you might be able to use a extension to put a play button on them which might stop it asking-> [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

---

### Post by Kurbycar32 on 2006-12-24
a valiant effort but that didnt work.

---

### Post by kerry_s on 2006-12-24
It was worth a try. Sorry it didn't work.

---

### Post by Gen2ly on 2007-02-13
I was wondering the same thing too.  Anyone ever find an answer?

---

### Post by BryannMelvin on 2007-02-15
gnuflash? I'm not sure if that is the same thing as I used.

On Dapper...

I installed the gplflash packages from the universe repository...

It works on sites apparently needing <= flash 7

at least no more sites trying to install plugins continuously.

---

### Post by 3rdalbum on 2007-02-16
Right-click (press F12) on the bar that tells you that you need a plugin. From memory, there's an option in the popup menu to turn off those notifications.

---

### Post by Gen2ly on 2007-02-16
**Disable "Install Missing Plugins" from Firefox**

Hey, I found the answer!

A lot of you use PPC computers that don't have flash or what not and this message becomes very irritating.  So I did a little bit of looking about and found out.  Actually I had to look the the bottom of the internet to find out, but I'm happy i did.

Type "about:config" in the address bar.  On the filter line type "plugin.de"  This will eliminate all but one line: "plugin:default_plugin_disabled".  Its bit of irony that disabled is true.  Double click will set if false.  Restart and no more warnings :)

Oh, and on a completly different side note, I was rummaging thru synaptic earlier and found crystalcursors - very sweet!

---

### Post by Gen2ly on 2007-02-18
Read this!

---


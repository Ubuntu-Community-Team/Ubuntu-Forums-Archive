---
title: "(EE) Problem Parsing The Config File"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by leo7068 on 2007-06-09
I shut down my computer, unplugged it, moved it, and booted. Now I can't load my GUI, and get dumped to the terminal on boot. The shown errors are:

```
Parse error on line 6 of section server layout file etc/X11/Xorg.conf " 
-reen0" is not a valid keyword in this section
(EE) Problem parsing the config file
(EE) Error parsing the config file
Fatal server error
No screens found
(ww) xfgcloseconsole:KDSETMODE failed bad file descriptor
(ww) xfgcloseconsole:VT_GETMODE failed bad file descriptor
(ww) xfgcloseconsole:VT_GETSTATE failed bad file descriptor

```

After reading the errors it says:
```
The X server is now disabled... restart GDM...
```

Please help. I have no idea what to type into the terminal to get my GUI back.

---

### Post by Funktown on 2007-06-09
It seems you made a typo!

Search /etc/X11/xorg.conf for "-reen0" and change it to "**screen**0".

If you need help doing that from the terminal, let me know :D

---

### Post by logicalmind on 2007-06-09
Looks like your xwindows configuration file(/etc/X11/xorg.conf) had been changed since the last time you restarted it. Now when xwindows tries to re-read it it fails. What you need to do is post the contents of your xorg.conf file for us so we can help you correct it. 

But chances are you can correct it yourself. Do this from the command line:
1. sudo vi /etc/X11/xorg.conf
2. type "/-reen0" and press enter(without quotes)
3. using the arrows, move the cursor over the "-" preceeding the "reen0"
4. Press "x". (this should delete the "-")
5. Press "i" and type "S" or "c"  depending on what letter is missing(you should now see "Screen0")
6. Press the escape key
7. Type ":"(colon) then type "wq" and reboot.

Should be problem solved.

---

### Post by leo7068 on 2007-06-09
Yes how do I change that? This is my first week trying Xubuntu, and I am having problems enough learning the gui let alone the terminal commands.

---

### Post by logicalmind on 2007-06-09
BTW, if you make a mistake in vi while editing. Just do:
1. Press escape key
2. Type ":" (colon) then type "q!"

And start over. It would be to your benefit to learn a little vi(it's on every unix in the world) or some other text mode editor.

---

### Post by leo7068 on 2007-06-09
Ok i am learning, but this did not solve the issue. When I went to edit the xorg.conf it did not find a -reen0 entry. In fact all lines that referred to screen were spelled correctly. I do not understand how the xorg.conf could be complete and right, but I still can't start my X server GUI.

Maybe this is a result of the ```
00.3% inconsistent contigiency
``` when my scandisk runs? It says something like that.Is there a way to "repair" or simply reinstall my boot? I don't want to loose the many gigs of movies on my drive, but wouldn't mind just reinstalling Xubuntu again.

---

### Post by logicalmind on 2007-06-09
When you say your "scandisk runs" what exactly do you mean? Is that your fsck in linux or something else?

---

### Post by leo7068 on 2007-06-09
It runs automatically before the errors show up and before it tries booting. It changes some numbers from 254 to 256 and some from 453 to 457.

---

### Post by logicalmind on 2007-06-09
> **leo7068 said:**
> It runs automatically before the errors show up and before it tries booting. It changes some numbers from 254 to 256 and some from 453 to 457.

Does it say anything about "inodes"? The linux "scandisk" is called fsck(file system check). It should only run every once in a while on reboot or if it finds an error on the disk when it first tries to mount it. It sounds like you could have a hardware problem. Either a bad disk or bad memory.

---


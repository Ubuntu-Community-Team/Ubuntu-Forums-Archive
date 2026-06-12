---
title: "Help with Envy"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-22
I ran envy to try and get my ATI card to work, but it still wont run beryl! Do I need to uninstall the old driver and try to reinstall it?

Also on startup now when it gets to the select OS screen, it added an option that says 'memtest+86' or something to that effect. What does that mean?

---

### Post by wolfen69 on 2007-07-22
memtest is for checking to see if your memory is good.

---

### Post by mikewhatever on 2007-07-22
What graphics card do you have? Some old cards are simply incapable of running beryl with or without the driver.
Yes, you should have uninstalled the old driver first.
'memtest+86' is a memory testing program. It should have always been there.

---

### Post by w4ett on 2007-07-22
> **ukulele_ninja said:**
> I ran envy to try and get my ATI card to work, but it still wont run beryl! Do I need to uninstall the old driver and try to reinstall it?

Also on startup now when it gets to the select OS screen, it added an option that says 'memtest+86' or something to that effect. What does that mean?

What ATI card are you using?  What problems are you having with your card?

---

### Post by ukulele_ninja on 2007-07-22
I have an ATI Radeon Xpress 200M and when I run Beryl it removes my headers from my windows! I will try to run envy again and remove old driver first. My card was listed on the supported ones on the envy site.

---

### Post by BlahMan_of.Doom on 2007-07-22
No dude. It's fine. You just need to install Emerald.

In terminal type

```
sudo apt-get install emerald emerald-themes
```

EDIT: And then after Beryl & Emerald are installed, type beryl -c emerald --replace. Or at least that works with Compiz Fusion...

---

### Post by ukulele_ninja on 2007-07-22
It wont hurt anything by removing the old one will it? And do i need to restart before i reinstall it?

---

### Post by ukulele_ninja on 2007-07-22
> **BlahMan_of.Doom said:**
> No dude. It's fine. You just need to install Emerald.

In terminal type

```
sudo apt-get install emerald emerald-themes
```

EDIT: And then after Beryl & Emerald are installed, type beryl -c emerald --replace. Or at least that works with Compiz Fusion...

When I ran this, it says invalid option --c

---

### Post by misfitpierce on 2007-07-22
Indeed install beryl and emerald  and make sure graphics are installed correct for ATI by typing 

fglrxinfo 

in terminal... Should give back something about ATI Technologies... If you see anything about MESA driver install failed and try it again by uninstalling old drivers and reinstalling ATI drivers.

---

### Post by BlahMan_of.Doom on 2007-07-22
Well all emerald does is add nice window borders, which Beryl needs to run, unless you change it to Metacity. And yes, do the "fglrxinfo" command. Also, in terminal, type
```
glxinfo | grep direct
``` and paste the output too.

---

### Post by ukulele_ninja on 2007-07-22
Ok its uninstalling my old drivers now, after i reinstall it i will post results. Thanks guys!

---

### Post by BlahMan_of.Doom on 2007-07-22
You don't need to uninstall your drivers. Just post the results =\

---

### Post by mikewhatever on 2007-07-22
Ah, so Beryl did run, but you had no borders!
You card may be supported by envy, but that does not mean it can run beryl. Envy and Beryl are two different projects.

---

### Post by BlahMan_of.Doom on 2007-07-22
I think he knows that. He's just having trouble running Beryl because he doesn't have emerald installed, or his Beryl Window Manager isn't pointing to Metacity.

---

### Post by ukulele_ninja on 2007-07-22
Ive heard several people say they can run beryl fine with m card so i know thats not an issue. One sec let me run those tests you mentioned

---

### Post by ukulele_ninja on 2007-07-22
> **BlahMan_of.Doom said:**
> Well all emerald does is add nice window borders, which Beryl needs to run, unless you change it to Metacity. And yes, do the "fglrxinfo" command. Also, in terminal, type
```
glxinfo | grep direct
``` and paste the output too.

fgrlxinfo says ATI Radeon 

direct rendering- yes

---

### Post by ukulele_ninja on 2007-07-22
> **BlahMan_of.Doom said:**
> No dude. It's fine. You just need to install Emerald.

In terminal type

```
sudo apt-get install emerald emerald-themes
```

EDIT: And then after Beryl & Emerald are installed, type beryl -c emerald --replace. Or at least that works with Compiz Fusion...

When I ran this, it says invalid option --c

---

### Post by BlahMan_of.Doom on 2007-07-22
Okay then type beryl && emerald --replace

---

### Post by ukulele_ninja on 2007-07-22
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by ukulele_ninja on 2007-07-22
Im afraid to try and open it again cuz i dot want it to go into crazy mode...

---

### Post by ukulele_ninja on 2007-07-22
bump** sorry for my impatience but ive been waiting forever and i think im really close!

---


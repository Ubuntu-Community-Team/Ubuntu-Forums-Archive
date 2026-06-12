---
title: "Having some trouble with Firefox"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-12-10
I just switched from Firefox 2 beta 2, to just plain old 2. Well I'm having some trouble now with getting a link to it on my desktop. I have the Firefox folder in my home directory with the .sh link in it, and that seems to be the only way I can get into Firefox. I can't use the terminal, I cant make a link to it, I don't think it would work if I moved it would it?

So that's one problem.

Heres a new one.:rolleyes: 
I can't seem to get the Flash Player plugin working in Firefox. I've done it like 2 or 3 times before and did it the same way each time, which was through Automatix. Well now, when I try to reinstall it back through Automatix 2, it's like I never did it in the first place. Firefox isn't reading it or something...:confused: 


Help?

---

### Post by BarfBag on 2006-12-10
Firefox can be a royal pain.  You should check out Swiftfox.  Haven't tried it myself, but a couple of people have recommended it to me.

I'm pretty sure I'm using version 2.  It came with Edgy.  Or would it not show up in "About Firefox" if it's a beta?

---

### Post by useResa on 2006-12-10
> **voodoonirvana said:**
> 
Heres a new one.:rolleyes: 
I can't seem to get the Flash Player plugin working in Firefox. I've done it like 2 or 3 times before and did it the same way each time, which was through Automatix. Well now, when I try to reinstall it back through Automatix 2, it's like I never did it in the first place. Firefox isn't reading it or something...:confused: 
Help?
I installed the flash player by downloading the file from [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW).
Unpack it and run the install program.
This worked for me.

---

### Post by voodoonirvana on 2006-12-10
> **useResa said:**
> I installed the flash player by downloading the file from [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW).
Unpack it and run the install program.
This worked for me.

Okay I tried getting it through that, and it's telling me that I need to remove xpti.dat from my mozilla directory. I've located that in the terminal, but can't find it through the browser. How would I go about removing this file from here?

---

### Post by useResa on 2006-12-10
> **voodoonirvana said:**
> Okay I tried getting it through that, and it's telling me that I need to remove xpti.dat from my mozilla directory. I've located that in the terminal, but can't find it through the browser. How would I go about removing this file from here?
Go to the directory where the file is located by using the cd command, for example for me this would be ```
cd bla@bla-bla/.mozilla/firefox/xtprsmm3.default/
```

Next remove the file using the rm command```

rm xpti.dat
```

---

### Post by voodoonirvana on 2006-12-10
> **useResa said:**
> Go to the directory where the file is located by using the cd command, for example for me this would be ```
cd bla@bla-bla/.mozilla/firefox/xtprsmm3.default/
```

Next remove the file using the rm command```

rm xpti.dat
```

Okay, well I did that and now they are gone. I had to remove it from the original .mozilla *and* some backup .mozilla.:-k Well I tried installing Flash again but it's telling me the exact same thing. I did another "locate xpti.dat" and it's showing that I removed it, but trying to install tells me that I didn't remove it.

---

### Post by igknighted on 2006-12-10
If you download the flash9 beta from labs.adobe.com all you need to do is place a file in the directory it specifies on the readme.  Very easy install.  I would recommend doing it this way.

---

### Post by voodoonirvana on 2006-12-10
> **igknighted said:**
> If you download the flash9 beta from labs.adobe.com all you need to do is place a file in the directory it specifies on the readme.  Very easy install.  I would recommend doing it this way.

On the site I can only find the Flash 9 update and the Action Script, whatever that is. Where is the actual Flash Player 9?!:confused:

---

### Post by igknighted on 2006-12-10
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

This is the file you want.

---

### Post by voodoonirvana on 2006-12-10
> **igknighted said:**
> [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

This is the file you want.

:) Thankyou! It's now working. 


Now is there someone that can help me with the linking problem please?

---

### Post by igknighted on 2006-12-10
Try making a custom app launcher on your desktop (or GNOME panel), and when it asks for the executable put the whole path to firefox (/home/username/path/executable), then you can click the icon box and select the firefox icon.  This *should* do it for you.

---

### Post by voodoonirvana on 2006-12-10
> **igknighted said:**
> Try making a custom app launcher on your desktop (or GNOME panel), and when it asks for the executable put the whole path to firefox (/home/username/path/executable), then you can click the icon box and select the firefox icon.  This *should* do it for you.

:-D It worked! Thanks everyone. I got both problems fixed. Wow, I wonder where I would be sometimes without this BBS!

---


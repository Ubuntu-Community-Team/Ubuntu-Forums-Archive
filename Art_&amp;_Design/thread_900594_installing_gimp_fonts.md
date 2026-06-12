---
title: "installing gimp fonts"
date: 2008-08-25
forum: Art &amp; Design
---

### Post by jimsonweed on 2008-08-25
I checked around a little and even posted on gimptalk.com and linuxforums.org but either they don't wanna help or it doesn't work. I was told to go into the fonts:/// folder and click and drag the new .ttf font files and and they should work fine. But, for one the new fonts don't show up in the folder, and two they don't show up in gimp. If anyone could help it would be much obliged :(. Sorry forgot to hit the "search if this threads been posted" button.

---

### Post by AJB2K3 on 2008-08-25
Have you tryed using the folder home/name/.fonts
Its a hidden folder and you may also need to create the .fonts folder.
And yes that dot needs to be there.

[COLOR="Red"]BTW try using **search** before posting as theres is a recent discussion on this ![/COLOR]

---

### Post by limasierra on 2008-08-25
Goto ```
/usr/share/fonts/truetype
``` and create a folder (the name doesn't matter, you just need a folder to put your fonts". Then copy your truetype fonts, the ones that end with ".ttf" and paste them into your folder.

---

### Post by jimsonweed on 2008-08-25
yea the .fonts folder is there, not sure how to show hidden files/folders. Sorry again I thought about searching while i was typing the thread out but just forgot to hit the button lol](*,)

---

### Post by Crafty Kisses on 2008-08-25
I just use kfontview, I think that's the easiest way, for me anyways.

---

### Post by AJB2K3 on 2008-08-26
> **jimsonweed said:**
> yea the .fonts folder is there, not sure how to show hidden files/folders. Sorry again I thought about searching while i was typing the thread out but just forgot to hit the button lol](*,)
Press
```
ctrl+h
```
And a load of folders should appear, then make the folder .fonts

---

### Post by sugarwaffle on 2008-08-27
Hi, I just figured this out today.
I got the .zip files from dafont.com...
I extracted the folder and then moved the entire folder into
home/<name>/.gimp-2.4/fonts/

I restarted the gimp and now it works...the fonts appeared in the gimp.

Not sure if this helps, but good luck :).

---

### Post by AJB2K3 on 2008-08-28
Thants ok for gimp but you have prevented the whole system from accessing them.
put them in 
home/<name>/.fonts/
BTW have a look at fontmatrix.

---

### Post by gimphoto on 2008-08-28
AJB2K3,
thanks for your info about fontmatrix.

i think Linux really need some font set standard that same for all distro this will make easier for designer to use it at our design without worried about missing font on other computer, even Hardy Heron not supply Dejavu font complete set only a few of it.

---

### Post by DarkCloud56 on 2009-01-18
ctrl+h opens hidden folders then just drag and drop your fonts into the .fonts folder and then you can open them in GIMP

---

### Post by Sand &amp; Mercury on 2009-01-20
Here is my solution.

Unzip your .ttf fonts somewhere, then start nautilus with administrative privileges: Press alt-f2, type 

[INDENT]gksu nautilus[/INDENT]

Now, grab your .ttf fonts, and navigate to /usr/share/fonts/truetype and paste your fonts in there.

Then you'll need to rebuild your font cache. Open the terminal and type:

[INDENT]sudo fc-cache -f -v[/INDENT]

That will rebuild the list of fonts. If you're running Gimp you may need to restart it before it will see the new fonts.

---

### Post by menschtx on 2009-01-28
I tried your method but couldn't find .fonts in my home/name/.fonts, also they did extract to a location but has a lock on it - what gives?

---

### Post by menschtx on 2009-01-28
I tried ctrl+h in the home folder and didn't find .fonts, what's next?

---

### Post by smartboyathome on 2009-01-29
> **menschtx said:**
> I tried ctrl+h in the home folder and didn't find .fonts, what's next?

create it, then put your fonts in there. I'm guessing you extracted your fonts to /tmp (everything inside /tmp becomes read-only, which gives you the lock).

---

### Post by lyceum on 2009-01-29
I find the best way is to have 2 folders, .fonts & fonts. That way you do not have a slow load time while trying to bring up 1000 fonts. Just move the ones you want to use in and out for what you are working on.

---

### Post by AJB2K3 on 2009-01-30
New tutorial written and added in my signature.
Please bookmark and pass on but please feel free to make any improving suggestions.

---

### Post by Random Avid on 2011-04-08
> **Sand & Mercury said:**
> Here is my solution.

Unzip your .ttf fonts somewhere, then start nautilus with administrative privileges: Press alt-f2, type 
[INDENT]gksu nautilus[/INDENT]Now, grab your .ttf fonts, and navigate to /usr/share/fonts/truetype and paste your fonts in there.

Then you'll need to rebuild your font cache. Open the terminal and type:
[INDENT]sudo fc-cache -f -v[/INDENT]That will rebuild the list of fonts. If you're running Gimp you may need to restart it before it will see the new fonts.


Made an Ubuntu Forums account for the sole purpose of thanking you for that.

As a side note sorry for necroing this thread, but credit where credit is due, I spent 3 hours finding a way to get new Fonts into GIMP.

---


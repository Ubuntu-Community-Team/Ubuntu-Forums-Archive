---
title: "Want to download new fonts"
date: 2008-01-23
forum: Art &amp; Design
---

### Post by famous3warriors on 2008-01-23
I want to download fonts from the web that I want to use in a article that I am designing. How do I go about doing that and doing that properly.  Thanks for your help.  i really do appreciate it.:guitar:

---

### Post by SunnyRabbiera on 2008-01-23
well fortunately for you linux can use ttf (truetype) files, so if you know a decent site with ttf fonts on it you can use it to get what you need.

---

### Post by Paul820 on 2008-01-23
You can just download them. Or do you want to know where to put them?

---

### Post by famous3warriors on 2008-01-23
Yes I would like to know were to put them.

---

### Post by Hairy_Palms on 2008-01-24
open nautilus and type fonts:/// in the address bar, then copy the fonts you want into it :)

---

### Post by c0met on 2008-01-24
Hi Hairy_Palms,

I'm following this thread, too. Thank you! It took me a while to find the Nautilus address bar because this was not my default view.

---

### Post by famous3warriors on 2008-01-24
Ok i will check this out thanks.  Where would I find the Nautilus address bar at and also will I be able to use these fonts in gimp and inkscape.

---

### Post by doorknob60 on 2008-01-24
Click the button

[[IMG]http://img225.imageshack.us/img225/9651/nautilusbarpr5.png[/IMG]](http://imageshack.us)

Also I think the gimp folder is in ~/.gimp-2.40 or something like that and you can stick your fints in there, but gimp might use the system fonts too, same with inkscape.

---

### Post by CarpKing on 2008-01-27
> **doorknob60 said:**
> gimp might use the system fonts too, same with inkscape.

I'm know GIMP does, and I'm pretty sure Inkscape does too.

---

### Post by jan quark on 2008-01-27
have you tried the app

gnome-specimen ( jsut search for it in synaptic)

I stumbled across it and it seems quite useful 
it shows the installed fonts and let you add fonts by drag and drop

---

### Post by AJB2K3 on 2008-01-27
OK This will help with fonts.

In the root of your user folder (home/user)
create the folder
```
.fonts
```
put fonts in that folder.
There is another folder but require sudo cp command but I find just using
```
home/user/.fonts
```does fine

rember .fonts will be a hidden folder and you will need to press CTRL+H to view it.

---

### Post by jan quark on 2008-01-27
I have written a small tutorial on adding fonts in Ubuntu check it out perhaps it will help someone

here the direct link
[http://janquark.fatfreehost.com/gimp8.html](http://janquark.fatfreehost.com/gimp8.html)

---

### Post by AJB2K3 on 2008-01-27
> All fonts in Ubuntu are stored in the directory /usr/share/fonts/
or 
```
/home/user/.fonts
```

You need to add that folder to your guide.

---

### Post by jan quark on 2008-01-27
thank you I wll do that

i have updated the tutorial and added a small credit to AJB2k3

---

### Post by AJB2K3 on 2008-01-28
No probs (nice to be credited) :p:p

---

### Post by pause11 on 2008-02-20
Got a slight problem. I tried adding fonts to the folder by dragging the file to the font folder. But it doesn't seem to want to go into the folder...

Whats wrong with this picture?

---

### Post by nicholim on 2008-02-20
Yeah, the drag and drop method didn'g work for me either.  I had much better luck with: ```
sudo cp /location/of/font.tff /usr/share/fonts/
```
I just opened up OO.o and there my new font was.  It still doesn't show if I go to fonts:// in nautilus.

---

### Post by pause11 on 2008-02-20
Hmm... might be a problem that our technically minded friends need to look at. Or it could be nothing at all:)

---

### Post by AJB2K3 on 2008-02-21
> **pause11 said:**
> Got a slight problem. I tried adding fonts to the folder by dragging the file to the font folder. But it doesn't seem to want to go into the folder...

Whats wrong with this picture?
Which folder?

```
usr/share/fonts
```
or```
 home/user/.font
```?
I always copy/paste the font files into the .fonts folder

---

### Post by SpiderGorilla on 2008-02-21
If you drag fonts into the fonts:/// folder, it'll actually copy them to your /home/username/.fonts folder instead. Check any app that scans that folder for fonts (AbiWord, The GIMP, Inkscape, etc) and you should see that your font has shown up and is ready to use.

---

### Post by ellalan on 2008-02-26
Hi
Go to places>Home Folder.
Then at address bar type    fonts:///
Copy the downloaded font from Desktop and paste at the address bar.
Thats it you are finished with adding a new font.

---


---
title: "Why Can't I Add .ttf Files?"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-07-14
I can cut or copy the downloaded fonts, but I can't paste them into the font directories.

Thanks for any help on this.

---

### Post by Skrewdriver on 2005-07-14
How are you copying them?
What errors are you getting?

---

### Post by polo_step on 2005-07-14
[QUOTE=Skrewdriver]How are you copying them?
What errors are you getting?[/QUOTE]
Just the usual cut and paste from another directory.  The paste option isn't active in the directory to which I'm trying to move the file -- the paste icon's there, just "faded out."

I'm assuming the .ttf files directory is write-protected, or requires higher user levels to write, but I don't know how to undo that.

---

### Post by drummer on 2005-07-14
you could copy the file using the shell by doing:```
sudo cp /foo/font.ttf /font/folder
``` or if you don't like using the shell for all the copying, open nautilus as root with ```
sudo nautilus --no-desktop
```and copy paste into the font folder in the nautilus window opened as root.

---

### Post by doclivingston on 2005-07-14
You can also open "fonts://" in Nautilus, which will let you add fonts as your local user, without having to use (gk)sudo. However, only the user that puts them there will have access to them (they get put in ~/.fonts).

---

### Post by neanderthal // anarchism on 2005-07-15
i actually just did this today for the first time, i went into nautilus and put "fonts:///" and then drag the text file in there, then i restarted the pc and it was all there.

---

### Post by doclivingston on 2005-07-15
Restart your computer? with Linux there is almost nothing you actually have to restart you computer for. The only thing you should have to do when you install new fonts is reload the program you want to use them in.

I just installed a couple of new fonts that I wanted to use in a letter I was writing - all I needed to do was close my word-processor and then start it again.

---

### Post by neanderthal // anarchism on 2005-07-15
[QUOTE=doclivingston]Restart your computer? with Linux there is almost nothing you actually have to restart you computer for. The only thing you should have to do when you install new fonts is reload the program you want to use them in.

I just installed a couple of new fonts that I wanted to use in a letter I was writing - all I needed to do was close my word-processor and then start it again.[/QUOTE]


that works too

---

### Post by polo_step on 2005-07-15
OK, went to comand line and entered:

nautilus fonts:///

...and it brought up the fonts directory.  I clicked "copy" on the icon for the font I had downloaded to desktop and went to the font files directory and could indeed click an active "paste" option, but it didn't seem to actually show up in the directory after that and it doesn't come up in any programs.  I need it -- "fixedsys.tff" -- specifically for FoxFire because of vision problems.

I can't understand why just moving files has to be such a nightmare in Linux. :-|

---

### Post by doclivingston on 2005-07-15
As long as the font file has a ".ttf" file extension it works for me - nautilus doesn't seem recognise files in fonts:// if they do not have a valid font file extension. Alternatively you can move them into the ".fonts" folder under your home directory (which is what putting them in fonts:// should do).

---

### Post by polo_step on 2005-07-15
[QUOTE=doclivingston]As long as the font file has a ".ttf" file extension it works for me - nautilus doesn't seem recognise files in fonts:// if they do not have a valid font file extension. Alternatively you can move them into the ".fonts" folder under your home directory (which is what putting them in fonts:// should do).[/QUOTE]
fonts://     works.

fonts:///     doesn't.

Don't know why.  Don't know the difference in these, nor where the actual directories reside.

Doesn't matter.  Thanks!

---

### Post by doclivingston on 2005-07-15
[QUOTE=polo_step]fonts://     works.

fonts:///     doesn't.[/quote]

Strange, very strange - but it's good to see something works.

[quote=polo_step]
Don't know why.  Don't know the difference in these, nor where the actual directories reside.[/QUOTE]

If case anyone else wants to know: it will be ~/.fonts (is you are doing it as non-root)

---

### Post by polo_step on 2005-07-16
[QUOTE=doclivingston]Strange, very strange - but it's good to see something works.[/QUOTE]
I think I spoke too soon.

It's in there, but as FixedsysTTF, not fixedsys.ttf, and I can't get it to let me rename it, even as sudo.

More freakin' mysteries!

---

### Post by doclivingston on 2005-07-16
I think it won't let you rename the file there, because in "fonts://" it doesn't show the file name - it shows the font name. I think the best way is to rename the file, before you install it. You could go to "~/.fonts" and rename the file there - but you will (probably) need to manually edit the various config files (fonts.*)

These kind of issues are probably why "font://" isn't made obvious. Probably what it should do is to automagically detect the type of file you are trying to drag there and a) complain if it isn't a font or b) ensure it has the right extension (and whatever else) if it is a font. I might be file a bug in bugzilla about this.

---

### Post by polo_step on 2005-07-20
You know, I **still** can't get this to work!

Here's the problem:

Because of vision problems, I need the MS "fixedsys" truetype font.

I can't find it, but I found a slightly tweaked legal clone of it, also called fixedsys.ttf

OK, so far so good.

I finally managed to get the thing into the fonts directory (see above).

The only problem is that the name of the font is not seen as "fixedsys" but rather "fixedsysTTF" which of course won't work, because the host pages that support fixedsys naturally don't support the differently-named fixedsysTTF. If I eliminate the .ttf extension, that won't work either, as something (in Nautilus?) needs to see the extension for it to be in the Fonts directory.  The other TrueType fonts in the directory do not show an appended TTF in the name.

Oh, and I can't rename the font once it's in the directory for some reason.

What on earth is going on here?  Why is the .ttf extension going into the font name?

How can I fix this?

Thanks for ay help.  This is driving me crazy.

---

### Post by doclivingston on 2005-07-20
Hmm... the only way I can think of that happening is if the font calls itself "fixedsysTTF" in the description inside the .ttf file. You said you found a legal clone; if it's on the 'net somewhere, could you post a link? I'll be able to take a better look at it, if I have a copy of the file.

---

### Post by polo_step on 2005-07-20
[http://fixedsys.moviecorner.de/index.php?p=start&l=1](http://fixedsys.moviecorner.de/index.php?p=start&l=1)

For what it's worth, there's no font *named* fixsys on the XP box.  What the font file really is and how its invoked, I don't know.

It's been in Windows forever, though.

I'm just trying to make it an option in Ubuntu.

---

### Post by doclivingston on 2005-07-20
The reason the font name is showing up as "fixedsysTTF" is because that's what the file says it's font family name is. I loaded up FontForge and changed it to "fixedsys", a copy is at [http://www.ids.org.au/~jrl/fixedsys.zip](http://www.ids.org.au/~jrl/fixedsys.zip) if you want it.

Hope this helps

---

### Post by polo_step on 2005-07-20
[QUOTE=doclivingston]I loaded up FontForge and changed it to "fixedsys", a copy is at [http://www.ids.org.au/~jrl/fixedsys.zip](http://www.ids.org.au/~jrl/fixedsys.zip) if you want it.[/QUOTE]
Tried it.

Doesn't work. It won't copy to the fonts directory, just like when I modified the file.

Weird...

I'm going to try something else.  I don't know what yet, but something.

Maybe renaming an installed font that works well enough to "fixedsys," I dunno.

Amazing that this is so hard.  Maybe there's something wrong with that font file.

---


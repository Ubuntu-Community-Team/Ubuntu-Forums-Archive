---
title: "Importing .ai files from illustrator to inkscape?"
date: 2007-05-17
forum: Art &amp; Design
---

### Post by tabithaboof on 2007-05-17
I have a .ai file I am trying to import from Illustrator to inkscape and have installed all the things recommended in this thread

[http://ubuntuforums.org/showthread.php?t=338632&highlight=inkscape](http://ubuntuforums.org/showthread.php?t=338632&highlight=inkscape)

and inkscape doesnt give me any error messages or anything and appears to import the file but the page is empty, like its a new document. Nothing from my picture at all, no layers or anything.

Also I have tried running the python scrip shown in the above link but it will generate a file xxx.ai.svg but inkscape gives me an error message when opening the file saying 

"Failed to load the requested file /home/tabby/Desktop/xxx.ai.svg"

Any ideas what I might be doing wrong?

---

### Post by Dagibit on 2007-05-25
I'm thinking if this file is so advanced (being .ai) that you need a plugin to import it, the Illustrator-exported svg shouldn't be very different- you'll probably lose the same advanced parts. Just export it to svg from illustrator. Or request that Adobe be compatible with Inkscape SVG :/

---

### Post by jorgerosa on 2007-05-25
"import from Illustrator to inkscape" - I had same problem, but because my Adobe Ilustrator was running in windows pc, dont know if this is your case, i solved it (partial) using WMF format. Like i said, dont know if this works for you. This happened to me, when i was developing the iteam gfx [here]("http://ubuntuforums.org/showthread.php?t=427011&highlight=gunbound&page=9")

---

### Post by jgamio on 2007-05-30
I used to export the ai to svg and open in inkscape.

---

### Post by djchandler on 2007-05-31
You can open .ai files with Acrobat Reader 7.x in Windows. I have not tried opening an .ai file with Xpdf yet. I do not know what you will get if you try to copy from Reader and paste into Inkscape.  I will give it a try in Windows, then, if I still get a vector format, try it under Ubuntu. Wish me luck, because I am afraid all I'll get is a bitmap.

---

### Post by bakermiller on 2007-05-31
all i have been able to so until now is to save as .svg in illustrator and open in inkscape. 
Of course all layers, brushes, swatches and styles are lost...but you get the vectors:P

I believe the header of the file created by the python script linked above is wrong or has too much information (it seems to make the file for sodipodi and inkscape). maybe someone with some knows-how can tweek it to output the correct headers. 

here is the link to the little program. i have no idea how to code python, maybe someone else can have a go...

[http://wiki.inkscape.org/wiki/index.php/Tools#ai2svg.py](http://wiki.inkscape.org/wiki/index.php/Tools#ai2svg.py)

---

### Post by djchandler on 2007-06-01
> **djchandler said:**
> You can open .ai files with Acrobat Reader 7.x in Windows. I have not tried opening an .ai file with Xpdf yet. I do not know what you will get if you try to copy from Reader and paste into Inkscape.  I will give it a try in Windows, then, if I still get a vector format, try it under Ubuntu. Wish me luck, because I am afraid all I'll get is a bitmap.

I can open .ai files with xpdf, and they still look ok when zooming in, so the vector info must still be there. No luck copying, though. I can copy in Windows Adobe Reader and paste into InDesign, so that must be because they are using their own private clipboard, not the Windows one. I opened Scribus in Ubuntu, and the paste option was not available. Clipboard must be crippled in Xpdf, probably to keep Adobe off their back. I still need to install Inkscape in Ubuntu. I just got this system back up a couple of days ago after a HD crash.

---

### Post by djchandler on 2007-06-01
> **djchandler said:**
> I can open .ai files with xpdf, and they still look ok when zooming in, so the vector info must still be there. No luck copying, though. I can copy in Windows Adobe Reader and paste into InDesign, so that must be because they are using their own private clipboard, not the Windows one. I opened Scribus in Ubuntu, and the paste option was not available. Clipboard must be crippled in Xpdf, probably to keep Adobe off their back. I still need to install Inkscape in Ubuntu. I just got this system back up a couple of days ago after a HD crash.

Ok, I do not know if this is a help or not. Use Import in Scribus, then choose .EPS, .PS, scroll down the menu to show all files so it will let you see the *.ai files, and I was able to place (that's the Adobe terminology coming out in me) the .ai file on the page. Enlarging and changing aspect ratio was working. Will try cutting and pasting into Inkscape from Scribus. There's no reason I can think of that it shouldn't work.

---

### Post by djchandler on 2007-06-01
> **djchandler said:**
> Ok, I do not know if this is a help or not. Use Import in Scribus, then choose .EPS, .PS, scroll down the menu to show all files so it will let you see the *.ai files, and I was able to place (that's the Adobe terminology coming out in me) the .ai file on the page. Enlarging and changing aspect ratio was working. Will try cutting and pasting into Inkscape from Scribus. There's no reason I can think of that it shouldn't work.

I'm giving up on this one. Inkscape will not paste the .ai file copied from Scribus. It looks as if the data is on the clipboard though, because, just for kicks, I opened Abi Word, and got the text for the postscript description of the object. The data is there, there is just no way to interpret it into a vector drawing in Inkscape. Unlike trying to directly import and getting the Perl error message, it doesn't even show an action was attempted in the history in Inkscape. The Inkscape and Xpdf teams must be going to great lengths to keep from irritating Adobe is the only thing I can say. I go along with some of the previous posters. The best workaround is to save as .svg or .wmf in Illustrator.

---


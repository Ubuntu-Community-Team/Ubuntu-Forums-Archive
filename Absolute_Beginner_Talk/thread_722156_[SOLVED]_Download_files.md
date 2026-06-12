---
title: "[SOLVED] Download files"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by RebelwithoutaClue on 2008-03-12
I wish one of the other threads was a previous posting of my question then I wouldn't feel so totally dumb.

Several sites I've visited, in their installation instructions say something to the effect of...

...just download these files and place them in xyz.

I posted a similar experience in an XMMS2 question.  The answer there wasn't totally satisfactory, as clearly I either failed to understand it or it didn't work.

When I go to the 'download here' site, all I see are links.  If I click on these links they lead either to more links or to a flat page with text on it.

I was told along the lines, 'yes, save these.'  All I have in FFx is 'Save link as'.

There is no save file as option as I would expect.  Consequently, whenever I try to download these plugins or whatever I'm trying to do I just get errors that confirm to me I don't what the hell I'm doing, and generally head back here down-hearted.

This is really annoying because it is obviously something so glaringly simple no-one in Linux land even feels the need to mention it.  I haven't found any pointers to it searching the threads or even through Google.

Please help, this is pants :(

---

### Post by Arthur Archnix on 2008-03-12
Post a link to an example. Generally, if you click on a link and there is something there to download a box will pop up and say "what do you want to do with this file?" and then give you the option of saving it somewhere or opening it if possible.

---

### Post by RebelwithoutaClue on 2008-03-12
Here's one I tried earlier...

[http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/artdisplay-awn/](http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/artdisplay-awn/)

:confused:

---

### Post by kesman on 2008-03-12
I'm not sure if I understood this but here comes:

[http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

in the right side is downloads. Download the tar.bz package, extract it somewhere and run. Isn't awn in the repositories?

EDIT: seems like the tar.bz contains the source, so you need to compile it too.

---

### Post by RebelwithoutaClue on 2008-03-12
The download you refer to is for awn manager.

I was trying to get the rhythmbox plugin.

The instructions say go here

[http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/](http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/)

this is where the links are.

You suggest I may need to compile it,  when referring to the other download, is that the case with this one and if so,

If so, how is it done and why does no-one make reference to it?

---

### Post by Bölvaður on 2008-03-12
Yes Avant-Window-Navigator is in the repositories.


> **RebelwithoutaClue said:**
> [http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/artdisplay-awn/](http://avant-window-navigator.googlecode.com/svn/trunk/plugins/Rhythmbox/artdisplay-awn/)

It seems to me that it contains python scripts which you would have to download and then use as plugin for rythmbox.

So it looks like to me that you just need to download these files and place them on your... desktop (is the best place imo) and then place them in the directory that is talked about in the guide you are following.

[Edit] you do not have to compile

---

### Post by RebelwithoutaClue on 2008-03-12
I see this when I click down...

# -*- Mode: python; coding: utf-8; tab-width: 8; indent-tabs-mode: t; -*- 
#
# Copyright (C) 2006 - Gareth Murphy, Martin Szulecki
#

If I try to save higher up all I get is FFx giving me the option to save link as and if I do I get an htm.

If I highlight all of the python text and right-mouse click all I get is Copy or Search options.

There doesn't seem to be a way to turn either the link or the text into a program.

:confused::confused::confused:

My guess is that this is so wildly obvious to anyone who knows Linux from a lamp post that  perhaps the kind and knowledgable respondants can't see the issue that I'm struggling with.

There just isn't anything program-like there when I get directed to download something.  If I have to compile it, so be it, I will have to go and find out how to do that but I wish I wish the intstructions were more explicit.

---

### Post by Arthur Archnix on 2008-03-12
If you're using firefox do this:

>edit  >preferences  >click on content  >under file types, click on manage

A box pops up. Click on the very first item listed. If the "Remove Action" button is greyed out so you can't choose it, then press the down arrow to the next item. Continue down the list and every time it gives you the option of removing the action, do so. Close firefox, restart, and go back to that link. This time it should ask you what you want to do. Instead of opening, choose save.

If that doesn't fix the issue then something more difficult is going on. Could be a firewall issue. Could be a hosts issue.

---

### Post by forrestcupp on 2008-03-12
It's because you are trying to download scripts.  Scripts are text files and text files are always automatically displayed in your browser and not downloaded.  To download these scripts, you just need to right-click on the link and choose 'Save Link As...", then tell it what directory to save them in.

You're not doing anything wrong.

---

### Post by Achtung on 2008-03-12
Open the link to the python script you want, say the "amazon cover art search" which is the first link, with the py file extension. It will display as a full page of text in your browser. 
Click File/Save page as. Save the .py file to a known location.

---

### Post by RebelwithoutaClue on 2008-03-12
OK, firstly, thanks everyone for sparing the time to answer.

Arthur - I went through all that you suggested, none of the file types offered Remove as an option.

forrest - I had already tried that and ended with Firefox saving the web pages, so I had awn-menu.htm or some such similar - I've deleted them since.

The fact that they were scripts should really have tipped me off though.  Gnnnn.

I'm guessing this is a safety action on the part of Firefox, though feel free to correct my guess if anyone knows better.

Achtung - you certainly did spill the beans, when I did what you suggested I did at least end up with the files as they were, I think, intended to be.

I saved them all to my desktop and created the sub folders there before moving them to the correct directory in .gnome2.

The upshot is that the plug-in doesn't work, I still get the default Rhythmbox icon on awn, but that's a battle for another day.

Thanks to anyone I haven't mentioned above who threw their two-penneth into the ring also.  So in short, I now know what to do with the script files.  So I'll mark the thread solved.

Is there a reason why the files aren't packaged up and extract into the correct folder?

---

### Post by forrestcupp on 2008-03-12
> **RebelwithoutaClue said:**
> 
forrest - I had already tried that and ended with Firefox saving the web pages, so I had awn-menu.htm or some such similar - I've deleted them since.
Your problem was that you tried to save a link that was to another menu, i.e. artdisplay-awn/
If it has a '/' at the end of the link, it means there is another sub-menu.  You needed to click that link which would bring you to a menu of the actual files.  On those links to the files, like AmazonCoverArtSearch.py, which is a python file, you can right-click->Save Link As and it will work.  I tried it and it worked for me.

You can do it either way, but I like my way better.  The reason is that if you want to download a script that is very big, you have to wait a long time for it to load into your browser, then save it.  I've had problems doing that with a large file before.  I'd rather just download it straight to my hard drive.

---

### Post by RebelwithoutaClue on 2008-03-12
I think your way sounds more sensible.

Thanks for taking the time to explain it.  It would still mean I have to to each file to save it though.

It does seem long-winded though to have download each file individually.  Is there a utility or  some comand I should know about that would have enabled me to download all of the files listed?

My Win brain was telling me that the the scripts were in text form as a virus measure, but then reading the comments about nasty people hiding rm commands I guess I have something new to worry about now!

Thanks again

\\g

---

### Post by Achtung on 2008-03-12
> **forrestcupp said:**
>  The reason is that if you want to download a script that is very big, you have to wait a long time for it to load into your browser, then save it.  I've had problems doing that with a large file before.  I'd rather just download it straight to my hard drive.
Well if you know the source is reliable, it's no biggie. But I find it's comforting to look through a script for suspicious commands and whatnot before downloading it and running it.

---


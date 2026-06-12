---
title: "problem installing desklet"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Kilrain on 2007-03-12
I'm trying to install the "RSSTicker" desklet @ [http://www.gdesklets.de/?q=desklet/view/131](http://www.gdesklets.de/?q=desklet/view/131).  I downloaded and extracted the necessary control to usr/lib/gdesklets/Controls, but when I attempt to install the desklet itself through the gdesklets shell it gives me the following error: 

The supplied file could not be opened as a package. It is either corrupted or not of the correct file type.

Am I doing something completely wrong, or is there another way to install the desklet?  Thanks.

---

### Post by Kobalt on 2007-03-12
It's been quite a while since I didn't try Gdesklets, but back then I think all I had to do to start a desklet was to double-click on it... have you tried that ?

---

### Post by Kilrain on 2007-03-12
Double-clicking just brought up the gdesklets shell, but I stumbled upon a fix: apparently I wasn't supposed to extract the folder the download came in before installing it.

---

### Post by Kilrain on 2007-03-12
Hmm...I have the desklet up and running now, but the feeds won't display, and I'm getting an odd-looking error:

len() of unsized object                                                              
/home/me/.gdesklets/Displays/RSSTicker/rssticker.display

and under this it highlights what i assume is a line of the desklet's coding:

>  97  if(story_index >= len(news.items)):

---


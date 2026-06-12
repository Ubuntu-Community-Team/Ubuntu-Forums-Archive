---
title: "Out of Memory running .exe in Wine"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by LordFlashHeart on 2007-09-21
I am trying to run a  program via wine and it gives me a not enough memory error.
I have 1 gig of ram and 200 gig hard drive, what could be the problem?

---

### Post by Daveth on 2007-09-21
might be something along these lines;

5. Registry editing in Wine. Run the command below and it'll pop-up a Wine version of regedit.

Code:
wine regedit.exe
Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D. Right click in the pane to make New > String Value for each of the following key pairs:

Code:
OffscreenRenderingMode	fbo
	UseGLSL					enabled
	VideoMemorySize		256
Make sure you have 256MB of video memory and GLSL support before enabling. Set whatever is needed for your card, but note w/o GLSL Oblivion won't run. I use a Nvidia 6800 GS with 256MB of RAM, and it gets it done.

Taken from [http://ubuntuforums.org/showthread.php?t=349764&highlight=wine+memory](http://ubuntuforums.org/showthread.php?t=349764&highlight=wine+memory)

I have a recollection that the default memory settings are very low and as it is told to use amounts it does, even though you may have a lot available.

---


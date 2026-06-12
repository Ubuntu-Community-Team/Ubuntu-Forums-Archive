---
title: "Animation Software Ideas"
date: 2009-06-05
forum: Art &amp; Design
---

### Post by Ac1ds0ld13r on 2009-06-05
Hey everyone. I just DLed KToon and pretty much hate it. 

Does anyone know of any other options for 2D animation?
Also, any reason my Wacom Tablet would not work?

Any help would be greatly appreciated.

---

### Post by rylleman on 2009-06-05
There's Synfig for vector animation or Pencil for traditional drawn animation.
And there's also a few non free alternatives, Anime Studio and Plastic Animation Paper.

---

### Post by Favux on 2009-06-05
Hi Ac1ds0ld13r,

What do you mean "Also, any reason my Wacom Tablet would not work?"?  What Wacom tablet do you have?

---

### Post by Ac1ds0ld13r on 2009-06-05
> **Favux said:**
> Hi Ac1ds0ld13r,

What do you mean "Also, any reason my Wacom Tablet would not work?"?  What Wacom tablet do you have?

It's acting like its not there. Just refuses to see it. Its the Bamboo Fun. 


> **rylleman said:**
> There's Synfig for vector animation or Pencil for traditional drawn animation.
And there's also a few non free alternatives, Anime Studio and Plastic Animation Paper.

Thanks. :) I'll check them out.

---

### Post by Favux on 2009-06-05
Hi Ac1ds0ld13r,

Oh, OK.  The problem is the default Jaunty 10-wacom.fdi is not parsing the Wacom device names properly.  You can see this if you type in a terminal:
```
xsetwacom list
```
It should return stylus, eraser, cursor, and pad.  If it is blank then "wacomcpl" won't work.  To see what names it is returning use:
```
xinput --list
```
One way to deal with it is to rename everything.  Another is to use a new 10-wacom.fdi we developed.  I posted it in Loic2's thread "Re: Wacom tablets in Ubuntu guide/howto" in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Then once wacomcpl works you can set things up.  For some instructions on wacomcpl see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And then in Loic2's thread (first link above) shatterblast shows how he set up his Bamboo in post #188.

Hope this helps.

---

### Post by hessiess on 2009-06-05
Blender, works perfetly for both 3D and 2D (2D is a subset of 3D after all ;) ) and is extreamly fast to work with, being mainly keyboard driven.

---

### Post by Ac1ds0ld13r on 2009-06-05
Favux:

That did the trick. :) thanks.


hessiess:

Yeah I'm struggling to get familiar with the Blender UI, but I'm slowly getting the hang of it. God bless tuts and the people who write them. :)

Thanks.

---


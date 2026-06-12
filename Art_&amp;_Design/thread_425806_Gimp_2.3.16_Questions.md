---
title: "Gimp 2.3.16 Questions"
date: 2007-04-27
forum: Art &amp; Design
---

### Post by episodic on 2007-04-27
Ok, coming from photoshop and windows, this is kind of hard to get use to.

The one thing driving me mad now is this.

I want to make a selection and simply paste it as a new layer. I for the life of me can't figure this out in gimp. In photoshop I just made a selection and pressed control + j. Thanks for this.


Also in photoshop you could select the highlights of the image by pressing control alt ~

How can you do this in the gimp.



Also, the crossprocessing scriptfu in the repository doesn't work in gimp 2.3.16 - anyone know of a good cross processing tutorial for gimp.

Is there not an equivelent to the little two boxes in photoshop that defaults to 'white' and 'black' in the toolbar. I don't know where to click to change colors.



Finally, how do I get into 'lab' mode.

Thanks so much.

---

### Post by CarpKing on 2007-04-28
> **episodic said:**
> Ok, coming from photoshop and windows, this is kind of hard to get use to.

The one thing driving me mad now is this.

I want to make a selection and simply paste it as a new layer. I for the life of me can't figure this out in gimp. In photoshop I just made a selection and pressed control + j. Thanks for this.


Also in photoshop you could select the highlights of the image by pressing control alt ~

How can you do this in the gimp.



Also, the crossprocessing scriptfu in the repository doesn't work in gimp 2.3.16 - anyone know of a good cross processing tutorial for gimp.

Is there not an equivelent to the little two boxes in photoshop that defaults to 'white' and 'black' in the toolbar. I don't know where to click to change colors.



Finally, how do I get into 'lab' mode.

Thanks so much.

Selection to new layer- Select an area, then Shift+Ctrl+L (Select->Float Selection) then Shif+Ctrl+N (Layer->New Layer, "New Layer" button in Layers Dialog).  

Don't know about the highlights thing, but several tools and effects have options to affect highlights.  

Don't know much about script-fu.

For the color boxes, you'll want the Colors tab.  I'm not sure if it's there by default (if you haven't figured it out yet, you can move all sorts of parts of the interface around), but if it isn't, click the little triangle on the top right of one of the dialogs (e.g. "Tool Options") and go to Add Tab->Colors.  You can also add little boxes to the bottom of the Toolbox with File->Preferences->Toolbox->Show Foreground and Background Color.  

If you mean the LAB colorspace, GIMP doesn't support that yet.  It should be possible once GEGL is integrated, a process which will begin after the next stable release (2.4).  It could be awhile though.  

In any case, good luck in your endeavors.

---

### Post by stadt on 2007-04-29
If you need LAB now (and not in an unforseeable future) give Krita (which is Part of KOffice, which uses KDE and QT, so a lot will be installed) a try. BTW. usage should be too much more common for Photoshop users.

Have a look here to see/read what you can expect from Krita

[http://www.koffice.org/krita/](http://www.koffice.org/krita/)

---


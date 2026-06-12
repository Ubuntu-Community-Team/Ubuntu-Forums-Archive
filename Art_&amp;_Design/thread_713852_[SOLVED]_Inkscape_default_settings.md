---
title: "[SOLVED] Inkscape default settings"
date: 2008-03-03
forum: Art &amp; Design
---

### Post by Kevbert on 2008-03-03
Hi.  I'm running the excellent Inkscape drawing package (v0.45) under Ubuntu Gutsy.  Is it possible to set up a default page on starting the application that is landscape and zoom is set to 1:1 ?

---

### Post by feenicks on 2008-03-03
I found the inkscape wiki, but it doesn't look like it does what you want.
[http://wiki.inkscape.org/wiki/index.php/PreferencesDialog](http://wiki.inkscape.org/wiki/index.php/PreferencesDialog)

I use inkscape too and love it for its simplicity and price :)
But it ain't Illustrator and it ain't Freehand, so you just have to make do.

I'm playing with the portable version right now on Windows XP. The keyboard shortcuts to do what you want are shift+ctrl+d, alt+L, ctrl+w (to close the dialog), then 1.  Get fast with shortcuts and who cares about the defaults.

---

### Post by Kevbert on 2008-03-03
Thanks for the reply.  Maybe it will be a future option...

---

### Post by badmedic on 2008-03-03
There should be a way to do what you want by replacing the file "default.svg" in this directory: /usr/share/inkscape/templates

However since the file is protected and I am a bit of a newb I am not 100% sure! :)

---

### Post by Kevbert on 2008-03-04
> **badmedic said:**
> There should be a way to do what you want by replacing the file "default.svg" in this directory: /usr/share/inkscape/templates

However since the file is protected and I am a bit of a newb I am not 100% sure! :)

Thanks badmedic.

To set both zoom and page orientation you need to use the following in terminal:
  sudo gedit /usr/share/inkscape/templates/default.svg
Next go to the line
width="744.09448819" and change it for the height value of 1052.3622047 and
replace the height value.  So you now have 
   width="1052.3622047"
   height="744.09448819">
Now go down to inkscape:zoom="0.35" and replace it with zoom="1.00"
I'm not sure what the cx and cy values do.
Save the file.
Now when you open Inkscape the default page will be landscape.

---

### Post by mutz on 2008-06-15
> Thanks badmedic.

To set both zoom and page orientation you need to use the following in terminal:
sudo gedit /usr/share/inkscape/templates/default.svg
Next go to the line
width="744.09448819" and change it for the height value of 1052.3622047 and
replace the height value. So you now have
width="1052.3622047"
height="744.09448819">
Now go down to inkscape:zoom="0.35" and replace it with zoom="1.00"
I'm not sure what the cx and cy values do.
Save the file.
Now when you open Inkscape the default page will be landscape.

Just a quick addition for those who don't want to edit svg code directly...
For a more user-friendly way of doing this, simply

```

sudo inkscape /usr/share/inkscape/templates/default.svg 
```
to open the aforementioned /usr/share/inkscape/templates/default.svg in inkscape and then edit the document properties to whatever you want as a default template. Remember to simply save as the same file - renaming will just create some other file that won't be a default.

Thanks all for the info - always forget where the defaults are :)

---


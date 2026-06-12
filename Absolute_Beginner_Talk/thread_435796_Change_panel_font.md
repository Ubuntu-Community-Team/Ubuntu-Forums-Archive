---
title: "Change panel font?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-05-07
Is it possible to change the font on the panel?

Is it possible to turn of the confirm dialog for the trash can?

Thanks for any answers:)

---

### Post by rai4shu2 on 2007-05-07
The "Application Font" changes the Gnome panel font. I don't think you can turn off that trash dialog.

---

### Post by justleen on 2007-05-07
i think i only get a conformation question when emptying my trash... (and i can live with that..). 
You could make a script, and place it in .gnome2/nautilus-scripts (or some other convients lace)to empty it?
something like ```
 #!/bin/sh
rm -rf /home/username/.Trash/ 

```
that will delete everything, nu questions asked..

---

### Post by _sAm_ on 2007-05-07
Thanks for your help. I have been using google and found this exellent guide: [http://www.netscape.com/viewstory/2007/04/24/how-to-disable-warning-message-when-emptying-tash-in-ubuntu/?url=http%3A%2F%2Fwww.watchingthenet.com%2Fhow-to-disable-warning-message-when-emptying-tash-in-ubuntu.html&frame=true](http://www.netscape.com/viewstory/2007/04/24/how-to-disable-warning-message-when-emptying-tash-in-ubuntu/?url=http%3A%2F%2Fwww.watchingthenet.com%2Fhow-to-disable-warning-message-when-emptying-tash-in-ubuntu.html&frame=true)

I also changed the font, but it also changed the font in all my other applications like FF, and was terrible - so now "Sense" is back :)

---

### Post by eldepeche on 2007-05-07
You can change the trash confirm behavior in the gconf editor. I don't know if the icon shows up by default in Ubuntu, but if you run "gconf-editor &" in a terminal, it will open up. Then, navigate to apps/nautilus/preferences and look for "confirm_trash". Uncheck the box next to it, and it will never ask you to confirm again.

---

### Post by rai4shu2 on 2007-05-07
The "confirm_trash" is for verifying sending to trash, not for emptying the trash.

---


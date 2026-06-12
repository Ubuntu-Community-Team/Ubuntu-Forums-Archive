---
title: "How to make OpenOffice NOT open sh scripts?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-04-30
Hi,

I'm running Feisty and for some reasons (I don't know what I did...if I ever did anything) each time I try to run an sh script file OpenOffice starts and the script is displayed in the Word processor :confused: I remember that before double clicking a script file would make a dialog pop up asking if I want to display the script (would start Text editor, not OOffice) or if I want to run the script in the terminal etc. Now if I right click any sh script the default "Open" behavious is to open the script in OOffice Word processor...

Anyone know how I can revert to the old behaviour? I guess it has something to do with file association maybe but I have no idea how to change that.

Thanks

---

### Post by Pobega on 2007-04-30
Right click it and edit it's properties. You must have changed the default command to open the file, possibly by opening one with OOo.

It's in the properties somewhere, I don't have Nautilus right now so I can't really check for you.

---

### Post by Metacarpal on 2007-04-30
You can right-click any file and select Properties, as Pobega said.  The option is in a tab labeled "Open With" (how's that for user-friendly?), and you can select the default application using a radio button, or use the Add button to select an application not already on the list.  You can also Remove an app from the list, which I'm guessing you'll want to do.

---

### Post by kilou on 2007-04-30
Thanks for your help! I finally found what caused the problem (although I don't really understand why). I had used ln -sf /bin/bash /bin/sh before because some sh scripts were not correctly interpreted with dash (the default for Feisty I think). After that those scripts worked but for some reasons some scripts were opened with OOffice. I removed the symlink with ln -sf /bin/dash /bin/sh (restoring Feisty default) and now double clicking on a script ask me if I want to run it or open it in the text editor.

Thanks!

---

### Post by kilou on 2007-05-01
Well I still have the problem of association of sh files to OOffice :( Basically now if I double click the file a dialog ask me if I want to run the script or display it. If I click display it starts OOffice! I'd prefer to open script in Text editor but I can't find how to change the association. When I right click a script file I can choose "Open with application..." (I don't have "Open with..." but it's probably the same). Then I can choose which application to start but it doesn't get stored for the next time. There is no option to add/remove associated programs too :confused: 

Is there a way to change the association with a terminal command?

---


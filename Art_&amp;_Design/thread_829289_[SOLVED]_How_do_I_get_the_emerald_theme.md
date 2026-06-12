---
title: "[SOLVED] How do I get the emerald theme?"
date: 2008-06-14
forum: Art &amp; Design
---

### Post by L337_K3y5 on 2008-06-14
I'm in the Compiz Fusion window, I believe, and I can't find where the emerald theme switcher is.  Here is a picture of my window decorator plugin:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-3.png[/IMG]
I read the wiki on that part of the window decorator, but it assumes the button, or whatever it is, is there, I only see the options above it.  Here is the link to the wiki I'm looking at:  [http://wiki.compiz-fusion.org/Plugins/Decoration]("http://wiki.compiz-fusion.org/Plugins/Decoration")  :confused::confused::confused:
I guess that Compiz Fusion came on Hardy, and I'm using the x86_AMD64 edition.

---

### Post by X_CheshireCat_x on 2008-06-14
i would search for the "emerald theme manager" through the synaptic package manager... this allows you to choose your theme...

to swap between the different types of window decoration you may need to enter:

"emerald --replace"

into the terminal.... they look soo nice! although when i close the terminal i loose my window decorations... which im trying to work out now! hope its works for you though...

hope this helps you

---

### Post by Genius314 on 2008-06-14
Put *emerald --replace* in the "Command" box. Also, make sure Emerald is installed first.

You may need to restart Compiz to see the changes, but I'm not sure.

---

### Post by X_CheshireCat_x on 2008-06-14
this page is quite useful:

[http://ubuntuforums.org/showthread.php?t=809695&highlight=emerald](http://ubuntuforums.org/showthread.php?t=809695&highlight=emerald)

this is the part which i was missing (getting the window decorations to appear when the terminal is closed and to re-decorate when i logged out an in again) is as follows:

"To enable Emerald on login, go to System > Preferences > Sessions. Click the Add button, and type in "Emerald" for Name and "emerald --replace" for Command. Click OK and close the Sessions window. The next time you sign in, Emerald will be running." (directly pasted from the guide)

this does the replace command every time you log in :) although is yo want to switch the decoration while you are logged in you will have to enter the "emerald --replace" command in the terminal

hope this helps

---


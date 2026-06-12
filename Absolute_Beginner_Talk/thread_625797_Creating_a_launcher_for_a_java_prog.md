---
title: "Creating a launcher for a java prog"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by mikedmoon on 2007-11-28
Sorry if this is wicked simple, but....

I'm running TED (Torrent Episode Downloader). Works fine. I like it a lot. However in order for it to run I need to open terminal, go to the folder when I extracted the tar and type in java -jar ted.jar. Launches fine. But I need to keep the terminal window open. If I close it, the program closes. So my question is two fold:

1) How do I create a launcher for it.
2) Does it actually need a term window open.

Thanks in advance.

---

### Post by nc_jed on 2007-11-28
> **mikedmoon said:**
> Sorry if this is wicked simple, but....

I'm running TED (Torrent Episode Downloader). Works fine. I like it a lot. However in order for it to run I need to open terminal, go to the folder when I extracted the tar and type in java -jar ted.jar. Launches fine. But I need to keep the terminal window open. If I close it, the program closes. So my question is two fold:

1) How do I create a launcher for it.
2) Does it actually need a term window open.

Thanks in advance.

Try a few simple tweaks:
java -jar **~/path/to/ted/**ted.jar **&**

*1) How do I create a launcher for it.*
Right-click top bar (in Gnome), select "Create launcher" (or equivalent sounding option).
Input string above.
Assign icon.
Try with and without the 'Run in terminal' option.  You shouldn't need to, but if your experience suggests otherwise, do it.

Sorry this post is so vague, I'm at work on Win XP.  No Ubuntu for me til 6...

Jed

---

### Post by nc_jed on 2007-11-28
> **nc_jed said:**
> Try a few simple tweaks:
java -jar **~/path/to/ted/**ted.jar **&**

*1) How do I create a launcher for it.*
Right-click top bar (in Gnome), select "Create launcher" (or equivalent sounding option).
Input string above.
Assign icon.
Try with and without the 'Run in terminal' option.  You shouldn't need to, but if your experience suggests otherwise, do it.

Sorry this post is so vague, I'm at work on Win XP.  No Ubuntu for me til 6...

Jed

At home in front of Ubuntu, so here is some clarification.
- Right click panel in empty spot.
- Choose 'Add to Panel...'
- Click 'Custom Application Launcher...'
- Test between 'Application' (should work) and 'Application in Terminal'
- 'Name', enter the name displayed on hover of the icon,
- 'Command':
[INDENT]- If you chose 'Application' above, enter: java -jar **~/path/to/ted/**ted.jar[/INDENT]
[INDENT]- If you chose 'Application in Terminal' above, enter java -jar **~/path/to/ted/**ted.jar **&**[/INDENT]
- Click 'No icon' box to assign icon.  Look in /usr/share/pixmaps or ~/.ted (a guess at the installation directory).

Note, this assumes you want an icon on the panel above.  If you want it on the Menu instead, right-click the 'Applications' menu, select 'Edit Menus', navigate to the place you want the icon added, and follow roughly the same instructions to add it to the menu (using 'New Item').

---


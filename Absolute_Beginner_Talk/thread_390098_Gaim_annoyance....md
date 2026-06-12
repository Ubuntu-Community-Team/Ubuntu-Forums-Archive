---
title: "Gaim annoyance..."
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by dj9866 on 2007-03-21
Running Ubuntu 6.10.  Using Gaim for IMing.  When minimizing buddylist to the task bar, a series of decreasing-in-size boxs representing the window is painted across the screen until minimized.  

Can this action be modified?  Would prefer that it snaps down like other windows.

Suggestions are greatly appreciated.

---

### Post by Kobalt on 2007-03-21
It should snap down like other windows actually... Have you tried reinstalling Gaim through Synaptic ?

---

### Post by dj9866 on 2007-03-21
I have reinstalled gaim under Synaptic and Automatix (different versions).  The result is the same.  However, gaim is not the only window that performs in this manner.  They all do.  It's just that the gaim window seems to generate more of the rectangles than the other apps.

Is this the norm for the windows minimizing operation?  I can't remember at this point, how the windows functioned in the beginning.  My preference is that the window 'snaps' from open to minimized without tracing the rectangles in the path from the open window to the task bar.

Can this be done?

---

### Post by mcduck on 2007-03-21
It's a feature of Gnome. Somebody must have thought that it looks nice :rolleyes: 

Anyway, it can be disabled with Configuration Editor:

1. press Alt-F2 and run 'gconf-editor'
2. Browse to apps/panel/global and disable 'enable_animations'

If you aren't using Compiz/Beryl you might want to remove this animation completely:

3. go to apps/metacity/general and enable 'reduced_resources'
4. finally go to desktop/gnome/interface and enable 'accessibility'. This is needed as 'reduced_resources' disables showing window content while moving windows, enabling accessibility re-enables showing the content.

---

### Post by dj9866 on 2007-03-22
That has me squared away.  Thanks, mcduck.

---


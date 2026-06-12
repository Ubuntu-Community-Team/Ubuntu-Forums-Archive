---
title: "New media player in Firefox"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2006-01-12
So I've brought this up before, but couldn't get the problem fixed. Basically, it looks like XMMS is my defualt movie player in firefox and it causes the browser to randomly close whenever I go to a page with video (wmv for example) files. How do I change to a different embedded video player for firefox? Or maybe firefox suddenly closing is another problem.

---

### Post by Dr. Nick on 2006-01-12
type ```
about:plugins
``` into the FF address bar. It lists all plugins, if you see the plugin you believe is causing crashes then remove the files listed

---

### Post by TheAnonymousx on 2006-01-12
[QUOTE=Dr. Nick]type ```
about:plugins
``` into the FF address bar. It lists all plugins, if you see the plugin you believe is causing crashes then remove the files listed[/QUOTE]

Ah okay. Well, I guess the obvious question is "how to remove those files" other than just removing the package with dpkg --purge *name*
Second, I don't even see XMMS in there. Looks like it WANTS to use mplayer for playing my video files but is still attempting to load XMMS.
More Suggestions?

---

### Post by Dr. Nick on 2006-01-12
Hmm not sure why it would want to load xmms, But if you need to remove any of them plugins, Just note the file name and then search your hard drive for the file and delete them using nautilus or the terminal, or however you choose

---


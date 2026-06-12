---
title: "Wine Installation Won't Work?!"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by gregmcavity on 2006-10-22
I went to synaptic package manager and I downloaded and installed Wine. After that I went to run it and it's not there?
I went to Applications and I couldn't find it?
I went through every catagory?
It's not there, what do I do?

---

### Post by CatKiller on 2006-10-22
You won't have Wine on the menu. There's no graphical aspect to Wine on its own. Open a terminal and type ```
wine *nameoftheWindowsexecutableyouwanttorun*.exe
``` to have Wine run your executable. Or, right-click on an executable in the file manager and select "Open with Wine Windows Emulator".

Before either of these, though, you'll probably want to type **winecfg** into a Terminal window to set up your pretend Windows environment.

Welcome to the community.

---


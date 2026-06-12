---
title: "?Corrupt localstore.rdf in Firefox, won't show toolbar bookmarks"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Zeedok on 2007-08-21
Having trouble with my ubuntu copy of firefox (thanks to google bookmarks synchronizer I suspect).

My toolbar bookmarks will not be displayed in my main browser window. I have reimported and deleted the old bookmarks, and declared a new folder 'The ToolBar Bookmarks Folder' and nothing thus far has worked. On my windows copy, a complete reinstallation fixed the problem, though a reinstall via synaptic did not do the trick in ubuntu.

I found this page:
[http://kb.mozillazine.org/Toolbar_customizations_reset_on_startup](http://kb.mozillazine.org/Toolbar_customizations_reset_on_startup)

and tried starting firefox in safe mode. I could make the changes, but they were not saved! I tried deleting the localstore.rdf file in profiles (that page suggests it may be the problem) but I can't work out how give myself 'deleting rights'.

Can anyone suggest anything else to try? Would a complete uninstall in Synaptic, followed by a reinstall work?

---

### Post by sumguy231 on 2007-08-21
> and tried starting firefox in safe mode. I could make the changes, but they were not saved! I tried deleting the localstore.rdf file in profiles (that page suggests it may be the problem) but I can't work out how give myself 'deleting rights'.
If you don't have proper permissions to write to/delete your profile folder, then that's probably what's causing the problem. Firefox probably can't write to localstore.rdf since it's running with your permissions. Who is listed as the owner of the folder? (You can type 'ls -l' in the terminal while in the folder to find out) If it's not you, type 'sudo chown -R <your username here> <profile folder>' to fix it.

> Would a complete uninstall in Synaptic, followed by a reinstall work?
Probably not, since the problem lies with your profile folder.

---


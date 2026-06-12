---
title: "Basic Archive Manager Question"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by jwwjr on 2006-08-21
Hello Topic Administrator,

I'm happy to say I've successfully installed Unbuntu 6.06, I am now Windows free in my home!

I'm have an embarrassing question regarding downloading and installing a .tar using Arhvive Manager.

I'm trying to get the latest stable build of XaraLX (this is version 0.7, it is not offered in any repository I can find.)  Xara offers a .tar on their site here -

[http://www.xaraxtreme.org/download.html](http://www.xaraxtreme.org/download.html)


I've been able to successfully download this tar to Unbuntu 6.06, extract it to the tmp directory with Archive Manager, and run the program by finding it in tmp and double clicking.

However, I'd like to save it to usr/bin, as in tmp it is gone when I log off.  Archive Manager though, will not let me, advising I don't have permissions.  I've looked for a way to be root in Ubuntu to extract the tar to usr/bin where it would be permanent and create an icon in the menus, but can't find it.

Any help would be greatly appreciated.

Sincerely,

jwwjr

---

### Post by aysiu on 2006-08-21
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by jwwjr on 2006-08-21
Hello Aysiu,

Thank you very much, that worked, and I was able to extract the .tar to usr/bin.  I'll obviously remember gksudo nautilus for the future.  I'm determined to be rid of Windows for good, no matter what it takes.  

Archive manager extracted the entire XaraLX tar folder to usr/bin, instead of just the executable, I guess this is OK in terms of not creating a problem with the hierarchy of mostly executables only showing in usr/bin (not folders that contain executables, binaries, etc.) and that entire folder within usr/bin will not impede updates for that app in the future if they appear in the repositories.  

In any event, I clicked the executable for XaraLX in usr/bin, and it launched.  If I can figure out how to add it to the drop down menu with the other "Graphics" software, I will have succeeded completely.  I'm not techncially trained, but I really like Linux.

Thank you,

jwwjr

---

### Post by aysiu on 2006-08-21
Just for cleanliness' sake, I would put the untarred XaraLX folder into /usr/local/bin or /opt instead of /usr/bin. Then, you can always symlink it back to /usr/bin by doing ```
sudo ln -s /usr/local/bin/XaraLX/xaralx /usr/bin/xaralx
``` or middle-click-dragging the executable to /usr/bin and selecting **link here**.

To get it into the Graphics menu, just right-click on the Applications menu, select **Edit menus** and add a new entry in the Graphics section with the executable's name ```
xaralx
``` for example... or whatever it really is.

---

### Post by jwwjr on 2006-08-21
Hello aysiu,

Thank you again, I figured out the menu edit, including adding an icon, and associating it to the location in the file system.  I tried it and it all worked.

Thank you very much for the suggestion on the file system locations.  I prefer consistently sticking to the appropriate conventions, once I understand what the file system is trying to do in Linux.  I love this software.  I'm in marketing, and I want to figure a way to evangelize Unbuntu in my area.  It is just so much more powerful and flexible than XP or Vista.

Thank you again for your kind help.

jwwjr

---

### Post by aysiu on 2006-08-21
There's actually no real convention. You can stick it wherever you want. I like using /usr/local/bin because it's otherwise empty. Glad it worked out for you.

---


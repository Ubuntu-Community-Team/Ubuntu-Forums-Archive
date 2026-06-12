---
title: "can't configure printer"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-07-25
Hey guys and gals.  I was trying to configure a new printer tonight on a smb network.  I  was able to add a printer on the same network about a month ago.  Tonight, when I was trying to configure this printer i clicked on the "printer" icon that was under system tools on the applications menu.  When I click on the icon there is a brief pause then nothing.  I don't remember my printer configuration icon being in the system tools menu but that's where it is now.  Can anyone tell me what to do?  Also the printer that i added about a month ago is working fine!  I would just like to add this other printer.  Can someone tell me what to do to correct this problem?

Okay I noticed that I have another icon under administration.  The icon under administration works correctly.    I don't know why there's another icon under the system tools that does absolutely noththing at all!  Does anyone else have this icon under "system tools"?  Does anyone know what it does? And why it's there?  I'm puzzled by this...

---

### Post by Pragmatist on 2007-07-26
> **bradmayne said:**
> ....Tonight, when I was trying to configure this printer i clicked on the "printer" icon that was under system tools on the applications menu.  When I click on the icon there is a brief pause then nothing....Can someone tell me what to do to correct this problem?....The icon under administration works correctly.    

So you solved this problem?

---

### Post by bradmayne on 2007-07-26
well yes and no.  I can't figure out why there is a printer icon under system tools.  However i did confugre the other printer i have.

---

### Post by Pragmatist on 2007-07-26
Mine is, and has always been, at: 
System-->Administration  

So I'm not sure why you have it in two places.  What is the command that is executed?  You can find this out by using a menu editor like alacarte.  In alacarte, you can double-click an entry and it will show you the properties, which includes the execute command.  For System-->Administration-->Printing  the command is "gnome-cups-manager"  There are also checkboxes so you can deselect an entry and it won't appear in the menus.

---


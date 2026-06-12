---
title: "[SOLVED] Wine uninstaller fails."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by saptarshi.roy on 2008-02-07
There is a particular application from a wine installation which I would like to remove. I've tried everything from typing 'uninstaller' in a terminal, to running uninstall programs directly via wine but with no success. 
The program as a whole fails to uninstall. I keep running the uninstaller but it keeps on getting installed again and again. The program which I am trying to uninstall is my ISP's dialer application.
Could someone please give me the entire command to delete that application with the path, please?
I would like to make a clean uninstall.
Any hints would be highly appreciated.

---

### Post by randy78 on 2008-02-08
I had the same problem and here's what worked for me:

I went to  the wine C: drive >Program Files, sent the offending program's main folder to the trash, went into the WINDOWS folder>clicked on Regedit.exe...
Once regedit opened up, I went to HKEY_Current_User>Software, and searched for the offending program.

Then I just right clicked on the main program folder and clicked delete.

After that, I right clicked on my main Ubuntu menu, clicked Edit Menus, clicked Wine in the left panel, expanded it and unchecked the box next to the offending program.

That should do it for ya ;)

---

### Post by saptarshi.roy on 2008-02-08
Thanks for your timly response Randy78. But this is something strange. I browsed the C:\ drive\Program Files but could not locate it, it must have been deleted. What's more intriguing is the fact that the stubborn aplication was not found in the registry editor. I didn't do anything. Why did this happen?

---

### Post by randy78 on 2008-02-08
You're welcome :popcorn:

Then it has been uninstalled...

Wine holds the programs in the Wine menu for some reason, so you can just edit the menu to remove them ;)

---

### Post by saptarshi.roy on 2008-02-08
Thanks a ton Randy. I appreciate your assistance. Issue resolved.

---

### Post by randy78 on 2008-02-08
Glad to help :)

---


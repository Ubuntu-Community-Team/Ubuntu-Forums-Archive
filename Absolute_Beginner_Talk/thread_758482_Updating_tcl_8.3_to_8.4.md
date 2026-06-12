---
title: "Updating tcl 8.3 to 8.4"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Pasty-Flawss on 2008-04-18
I downloaded TCL 8.3 and now i need 8.4 but i cant install because i have to delete all previous versions.. but i cant workout where they are?

thanks in advance :)

---

### Post by Trail on 2008-04-18
What is "TCL"? I am assuming something NOT found in the repositories, else the update would have been automatic.

So, first place to look, is the README or INSTALL file that should be included that program.

That said, did you compile it yourself? If you followed the "./configure && make && sudo make install" procedure, you can try going to the directory where you compiled it and try to "sudo make uninstall" it.

Otherwise, if you used a custom script for installing (for example, install.sh) check to see if an uninstalling one is provided as well.

I think the provider of the software has to have some way to automatically uninstall the software, since he requires you to do that before installing a new version.

Really lacking info here. As said, check the README first.

---


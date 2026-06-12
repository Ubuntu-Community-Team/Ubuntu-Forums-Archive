---
title: "Installing ndiswrapper from desktop"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by sanderella on 2007-05-21
Ok, I'm just a lillte old lady, getting older. I thought I had cracked Ubuntu, but no. 
I have no internet connection at the moment, so how can I install ndiwrapper? I put it onto my desktop from a floppy. What do I type in the terminal to install it from there? Thanks

---

### Post by foresth on 2007-05-21
If it is a .deb package, type "sudo dpkg -i ndiswrapper*.deb".

---

### Post by ThinkBuntu on 2007-05-21
No need for the terminal here.

If it's a .deb package, double-click it, and select the "Install" button. It'll prompt you for your password, and you're done! If there are unresolved dependencies, it'll tell you them in bold, red text. Install these first if this is the case.

---

### Post by ThinkBuntu on 2007-05-21
If it's a .tar.gz file, or .tgz, right click it and select "extract here." Open the new folder, and follow the instructions in the plain text file named "INSTALL," or possibly, "README" if there's no "INSTALL." This will walk you through the install. You'll probably want to look at the README as well.

---


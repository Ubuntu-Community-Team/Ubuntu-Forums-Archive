---
title: "How to install a .sh file"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Balzy59 on 2007-11-25
My file is "thinkorswim_intaller.sh". How do I go about installing this file. Any help would be appreciated.

---

### Post by skymera on 2007-11-25
sudo sh thinkorswim_intaller.sh

---

### Post by Balzy59 on 2007-11-25
Where do I type "sudo sh thinkorswim_intaller.sh". Do I open up terminal and type into that?

---

### Post by riven0 on 2007-11-25
> **Balzy59 said:**
> Where do I type "sudo sh thinkorswim_intaller.sh". Do I open up terminal and type into that?

Yeah, go to Applications >> Accessories >> Terminal and copy and past the command. Make sure you're in the folder with file. If it's on the desktop, then type these commands first:

**cd Desktop**

then: **ls -a**

You should get a list of whatever is on your desktop. If the sh file is in a folder called thinkorswim, type: **cd thinkorswim**

Finally, install the file. Either: **sudo sh thinkorswim_installer.sh** or **sudo sh ./thinkorswim_installer.sh**

---

### Post by Balzy59 on 2007-11-25
Thank You!

---

### Post by PeterJS on 2007-11-25
It's also worth noting, as it hasn't been explicitly stated but you don't install .sh (shell scripts) files, but run them. The fact that this specific shell script installs something doesn't say anything about shell scripts as a whole. All a shell script is a series of commands that are automatically run by the computer to preform some function.

---


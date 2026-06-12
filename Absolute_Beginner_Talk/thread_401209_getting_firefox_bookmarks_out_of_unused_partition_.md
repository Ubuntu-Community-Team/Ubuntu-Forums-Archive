---
title: "getting firefox bookmarks out of unused partition [Resolved]"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2007-04-04
I'm running the disk from a deceased computer in a usb case. from the livecd i don't have permission to look in or move .mozilla from home. I need the bookmarks that I understand are inside. how do I give myself permission? why don't I have permission anyway? thanks.

---

### Post by charles.g.moore on 2007-04-04
> **leetrefz said:**
> I'm running the disk from a deceased computer in a usb case. from the livecd i don't have permission to look in or move .mozilla from home. I need the bookmarks that I understand are inside. how do I give myself permission? why don't I have permission anyway? thanks.

Just to make sure...
You have tried to move it using the sudo command from the CLI, or are you trying it through the GUI?

---

### Post by Kobalt on 2007-04-04
You need to [mount]("https://help.ubuntu.com/community/Mount") the HD you're trying to read in order to access the files I think.

---

### Post by aysiu on 2007-04-04
You don't have permission?

Press Alt-F2 and use one of these commands.

Ubuntu: ```
gksudo nautilus
``` Kubuntu ```
kdesu konqueror
``` Xubuntu ```
gksudo thunar
``` and then copy over the .mozilla folder from the old drive.

---

### Post by leetrefz on 2007-04-05
got it, thanks.

could only paste it within the same nautilus window, not to another one i clicked open.

---


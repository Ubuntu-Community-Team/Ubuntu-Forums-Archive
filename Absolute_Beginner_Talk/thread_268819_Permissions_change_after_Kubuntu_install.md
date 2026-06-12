---
title: "Permissions change after Kubuntu install"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by alcamus on 2006-09-30
I recently added the Kubuntu desktop to my Ubuntu install with sudo apt-get install kubuntu-desktop. Everything about the install is fine except now when I log into Gnome, I no longer have access to the root folder; all I can see when I click the filesystem icon that allows me to view my Linux directories are the /home and /media folders. I'm pretty sure a user permission setting has changed, but I have no idea how to get back to the original settings. Maybe KDE wants to protect me from myself, but I'd rather live a little bit dangerously.

Any idea how to restore the original Gnome permissions?

(I've searched for this everywhere and must not be using the right terms or something. I keep coming up blank.)

---

### Post by alcamus on 2006-09-30
After poking around some more, I've discovered that the file permissions haven't changed, the files are somehow rendered invisible. How do I restore them to the original setting, so that everything is visible on clicking the Filesystem icon?

Any help would be greatly appreciated.

---

### Post by alcamus on 2006-09-30
Wow. I feel like a dork. After poking around even further, I found the .hidden file, edited it and now everything is back to normal. Sorry for the static.

---


---
title: "Unremovable entry in firefox extensions"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by cremnob on 2006-07-25
I tried installing an extension and I guess it messed up. Now I have an entry that I can't seem to remove from the extensions window. How do i remove it?

---

### Post by not_yet on 2006-07-25
if it won't uninstall from the extensions window, have a look in .mozilla, which is in your home folder

something like  /home/Your_name_here/.mozilla/firefox/isvvlhth.default/extensions

look inside each folder to find the extension you need to get rid of

---

### Post by cremnob on 2006-07-25
Hmm I cant seem to find it. I only have a Desktop, EasyUbuntu, Examples in the Home folder under my name.

---

### Post by aysiu on 2006-07-25
What's the extension and what happens when you try to remove it?

---

### Post by jordilin on 2006-07-25
You can always redo your firefox profile and begin again. Follow these steps:
cd ~
tar -czvf firefoxbackup.tgz .mozilla/firefox (It does a backup of your firefox profile)
rm -rf ~/.mozilla/firefox/xxxx.default where xxxx are random characters
firefox -ProfileManager and create a new profile

---

### Post by cremnob on 2006-07-25
Sorry i'm a real noob. Where exactly am I using those steps?

---

### Post by aysiu on 2006-07-25
It's even easier than that, actually. Paste this one command into the terminal: ```
mv ~/.mozilla ~/.mozilla.backup
``` And then restart Firefox.

See my signature for *where* to paste the command.

---

### Post by Aurdal on 2006-07-25
> **cremnob said:**
> Hmm I cant seem to find it. I only have a Desktop, EasyUbuntu, Examples in the Home folder under my name.

It's a hidden folder to go to it you can either hit ctrl + L ant type ".mozilla" after the last "/" or the easier way, hit ctrl + H to show hidden files and folders. :)

---


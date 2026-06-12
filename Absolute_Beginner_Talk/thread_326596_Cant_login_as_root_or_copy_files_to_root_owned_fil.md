---
title: "Cant login as root or copy files to root owned files"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by bonedog73 on 2006-12-27
I'm trying to copy some new cursors into the use/share/icons folder, but (copy) is greyed out. The owner is root, yet I am unable to login as root. I supposedly have admin rights but... I changed the root password in user settings but still unable to login.

How do I copy these files?

---

### Post by taurus on 2006-12-27
Applications -> Accessories -> Terminal
```
sudo cp **filename** /usr/share/icons
(and use the same password that you login in with...)
```

---

### Post by nhandler on 2006-12-27
Here is another option that doesn't use the terminal.:

Enable viewing of hidden files: View->Show Hidden Files (Ctrl+H)
Navigate to /home/YOURNAME/.gnome2/nautilus-scripts
Right click->Create Document->Empty Document     Name it anything you want. I called mine Root Nautilus

Paste the following code in the document:
```
#!/bin/sh

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

```

Save the document and close the window. Right click the document, and select Properties. Then go to the Permissions tab. Check the 'allow executing file as program' box and close the window. Now, go to the folder that has the cursors you want to copy. Copy them. Now, go to the /usr/share/icons folder. Right click in some empty space. Select scripts->Root Nautilus (or whatever you called the script). This should prompt you for your root password. Next, it should launch a new file browser that is opened to /usr/share/icons. In this file browser, you are the Root user, so you have write access. Simply go to edit->paste to paste the cursors.

---

### Post by bonedog73 on 2006-12-27
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo cp **filename** /usr/share/icons
(and use the same password that you login in with...)
```

Thanks that worked great, I was just reading about sudo too. lol

I'm new to Ubuntu, not sure why there is such a nice simple theme manager, and nothing for cursors at all. Oh well work in progress..

---


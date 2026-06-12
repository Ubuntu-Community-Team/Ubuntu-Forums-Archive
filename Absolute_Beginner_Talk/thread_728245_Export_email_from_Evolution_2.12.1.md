---
title: "Export email from Evolution 2.12.1"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-03-18
Hello Ubunteros!

In Evolution 2.12.1 I created a Folder called "Received MAil" Within this folder are sub folders into which I drag and drop my email.

Is there a way I can export my "received folder" so as to save all it's contents for backup purposes?

Thank you.

---

### Post by gobbles414 on 2008-03-18
> **suomalainen said:**
> Hello Ubunteros!

In Evolution 2.12.1 I created a Folder called "Received MAil" Within this folder are sub folders into which I drag and drop my email.

Is there a way I can export my "received folder" so as to save all it's contents for backup purposes?

Thank you.

In recent versions of Evolution, there's a *Backup Settings* option in the *File menu*. In addition to your settings, this wizard actually exports your emails/contacts/calendars/tasks as well. All of these go into a compressed archive, which you can save in just about any location you choose. Obviously, you'll use *File => Restore Settings* in Evolution to restore your data directly from the backup archive. Don't extract first. This procedure works great if you plan to continue using Evolution. However, I'm not sure if other email programs can import from this kind of archive or not.

An alternate backup method is to simply copy the contents of your *.evolution* folder. The *.evolution* folder is hidden in your home folder. You can view hidden files/folders in Ubuntu by going *View => Show Hidden Files*. To restore you backup, just replace the contents of any existing .evolution folder with the one you've copied.

Do either of these help?

---

### Post by suomalainen on 2008-03-18
Thank you! I think copying the contents of the " .evolution" folder will work easiest for me!

However, when I copy it to the place where I want it I don't want it maintained as a HIDDEN FOLDER and I can't change the status of that feature for one reason or other.

The Ownder is stated as being "root" followed by "You are not the owner, so you can't change these permissions" BUt I am the owner?

Little confused now.

Any suggestions?

Thanks for your great advice!

---

### Post by gobbles414 on 2008-03-18
> **suomalainen said:**
> Thank you! I think copying the contents of the " .evolution" folder will work easiest for me!

However, when I copy it to the place where I want it I don't want it maintained as a HIDDEN FOLDER and I can't change the status of that feature for one reason or other.

The Ownder is stated as being "root" followed by "You are not the owner, so you can't change these permissions" BUt I am the owner?

Little confused now.

Any suggestions?

Thanks for your great advice!

Sorry, I guess that my original answer wasn't very clear. Create a new folder on your desktop. Call it *email_backups* or whatever you want -- the name doesn't matter. Then go into your home folder and enable the viewing of hidden files/folders. Double-Click **into** the .evolution folder. Copy all of the items that you see there. That is, copy all of the **contents** of the .evolution folder. Now, go inside the folder that's on your desktop and paste. Now, return to your home folder and make sure that the viewing of hidden files/folders has been disabled. These instructions have worked flawlessly for me many times -- no permission issues.

To recover your backups, double-click into the folder that's on your desktop and copy everything. Then go to your home folder and enable the viewing of hidden files/folders. Now, go *into* the .evolution folder and paste. The current contents of the .evolution folder will be overwritten by your backups. You shouldn't encounter any permission issues here either. If you do encounter permission problems, right-click on the .evolution folder and choose *Properties => Permissions* (I think). There's an option to apply the folder's permissions to all of the contents.

When you start Evolution, your backups will be fully restored.

---


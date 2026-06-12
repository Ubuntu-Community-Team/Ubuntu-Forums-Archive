---
title: "backing up files on external drive"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by chelseachelsea on 2007-10-07
I'm trying to back up files onto an external drive and keep getting the message "You do not have permissions to access this drive"

I have files already on that drive from another computer and can copy and read them.  So...why can't I paste TO this drive?

---

### Post by ryanVickers on 2007-10-07
What filesystem is it?  NTFS?

And if you go "gksudo nautilus" in the terminal and **then** view the drive, it should be ok (unless it's ntfs, then you need to install ntfs-config (I think))

---

### Post by chelseachelsea on 2007-10-07
sorry, I got the message wrong.  It states "you do not have permission to writie to this folder.'

Of course, I can't write at all to the drive in any folder nor create a new folder.  The File - create folder and Edit - paste commands are not active for the external drive in file browser.

Yet I can access, read, and copy any file or folder FROM the external drive.

Just can't get anything TO it.

---

### Post by ryanVickers on 2007-10-07
I repeat:
> **ryanVickers said:**
> What filesystem is it?  NTFS?

And if you go "gksudo nautilus" in the terminal and **then** view the drive, it should be ok (unless it's ntfs, then you need to install ntfs-config (I think))
:p

---


---
title: "Editing Config files"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by mulder_edu on 2006-08-07
How do I edit configuration files in Ubuntu?
I don't have Root permissions to do it the easy way, and I don't know how to do it from the terminal.

Can someone tell me how to edit files from the terminal?  I know you have to use the sudo command, but what commands do you use to actually edit the file?

David Mulder.:-k

---

### Post by aysiu on 2006-08-07
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by davebgimp on 2006-08-07
> **mulder_edu said:**
> How do I edit configuration files in Ubuntu?
I don't have Root permissions to do it the easy way, and I don't know how to do it from the terminal.

Can someone tell me how to edit files from the terminal?  I know you have to use the sudo command, but what commands do you use to actually edit the file?

David Mulder.:-k

Well, first identify the file you need to edit it and back it up.
**sudo cp filname filename_backup**

Then, launch the file in a text editor. You have a few choices. Vi, Vim, Gedit (Gnome), Kate (KDE) and others. Assuming you're on Gnome, you could do:
**sudo gedit filename**

---

### Post by aysiu on 2006-08-07
If you do ```
sudo nano -B *filename*
``` you'll create a backup copy *and* be able to edit the file.

---

### Post by mulder_edu on 2006-08-07
Thank you. That did the trick.

David Mulder.

---


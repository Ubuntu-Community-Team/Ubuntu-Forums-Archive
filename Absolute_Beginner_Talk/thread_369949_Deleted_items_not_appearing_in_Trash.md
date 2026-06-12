---
title: "Deleted items not appearing in Trash"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by badbobbybarnes on 2007-02-25
Hi

I'm having a problem when moving items to Trash (6.06 and 6.10): they disappear as though deleted but do not appear in the Trash window, but they ARE in the hidden /user/,Trash folder. Here's the link to my post yesterday in the Desktop Environments section,  with replies:

[http://www.ubuntuforums.org/showthread.php?t=368791]("http://www.ubuntuforums.org/showthread.php?t=368791")

Can anyone help please?

---

### Post by tribble222 on 2007-02-25
I'm not sure what you mean by "they disappear as though deleted but do not appear in the Trash window, but they ARE in the hidden /user/,Trash folder"?  Do you mean you can't see them in nautilus but you can see them in the terminal with ls command?  The first thing I would do is check the permissions of your .Trash directory and make sure that it is owned by you and writeable by you.  I.E. ,run:

sudo chown yourusernamehere /home/yourusernamehere/.Trash
sudo chmod 755 /home/yourusernamehere/.Trash

Then try to send something to the trash and see if it appears in there.

---

### Post by badbobbybarnes on 2007-02-26
I mean that I CAN see deleted files in the hidden /home/yourusernamehere/.Trash folder in Nautilus, but the Trash applet on the desktop taskbar shows as empty ("No Items in Trash" it says, when clearly there are if you look in the hidden .Trash folder via Nautilus). I've tried your above commands but I'm afraid it made no difference.

---

### Post by tribble222 on 2007-02-26
If you click the trash icon on the taskbar does it open up the Trash folder, and can you see anything in the folder it opens up?  If the folder the trash icon opens up is empty, then perhaps it is looking for trash in the wrong folder?

---

### Post by badbobbybarnes on 2007-02-26
The trash icon opens up an empty Nautilus window, location "trash:", not "/home/myusername/.Trash". There are no hidden files in it. Any ideas how/if I can change it to point to the latter?

---

### Post by alienexplorers on 2007-02-26
On my system running Ubuntu 6.10.1 when I open the trash file by using the panel icon it goes to a file listed as "Trash".  It does not show the page location as username/.Trash.  All of my trash is found in the trash bin labeled "Trash".  Note no dot before the word Trash.  Did you check the configuration editor to make sure everything is enabled correctly:
command                nautilus "%s"
enabled                   check mark in box
needs terminal         unchecked

Other than this I have no idea why you can not see your trash in the .trash folder.

---

### Post by badbobbybarnes on 2007-03-15
I think the problem may be that I can't get a UUID for /dev/hdb2, my ext3 boot partition. Device Manager shows this as an LVM2 raid member. When I installed Ubuntu I used a default install - nothing fancy when partitioning the 2 hard drives. Anyone got a clue what's going on please?

---


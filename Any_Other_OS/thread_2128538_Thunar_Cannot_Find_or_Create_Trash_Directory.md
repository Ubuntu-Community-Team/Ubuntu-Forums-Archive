---
title: "Thunar: Cannot Find or Create Trash Directory"
date: 2013-03-23
forum: Any Other OS
---

### Post by Virtuality314 on 2013-03-23
Hey guys

I am building a custom Ubuntu Distro using Ubuntu Builder and Ubuntu Mini Remix. I have installed Thunar as the file manager. However, in the LiveCD, the live-user cannot delete a file (however, you can delete a folder). The root user can delete anything. Also, I have installed gvfs, and gvfs-trash which gives me the exact same erro when used from command line. There is an intact Trash folder under /.local/share with the sub-folders of 'info' 'files' and 'expunged' and the user has the ability to read and write to this folder. I have also tried setting permissions for the Trash folder under /root/.local/share but it has not worked.

Is there any solution for this?

---

### Post by ManamiVixen on 2013-03-23
in thunar, can you put into the address bar and go to trash:///?

---

### Post by Virtuality314 on 2013-03-23
Thanks for the quick reply, and yes I can. 

Annoyingly, I can actually delete folders, just not files.

EDIT: I have found a temporary solution - to delete a file, I can place it inside a folder, and then delete that folder.
Double Edit: I actually installed my custom distro in a VirtualBox, and everything seems to work.

---


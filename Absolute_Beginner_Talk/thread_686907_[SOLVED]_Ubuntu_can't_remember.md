---
title: "[SOLVED] Ubuntu can't remember?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Robert Ashley on 2008-02-03
I am trying to get access to a Shared folder on the desktop of Ubuntu Linux 7.04, from an Imac over a LAN through a DHCP Router. Access is not available for ??? reason. (Another problem)
The Shared folder has been created, and appears on the desktop.
If I right click on the folder, and then left click on "properties", a window opens with 5 tabs at the window top.
The third tab is labeled "Permissions".
Clicking on this tab, shows the owner (me), a small window labeled "Folder Access", where I have selected "Create and delete files", another small window labeled "File Access", where I select "Read and write".
My question is "Why is the last (Read and write) selection not remembered?
I have clicked on the bottom "Apply permissions to enclosed files" button, but next time I bring up this Properties window, the previous selections are not shown. They are blank!
Is this selection really forgotten, or by design not displayed?

---

### Post by p_quarles on 2008-02-03
This isn't an Ubuntu-specific issue. Different filesystems handle permissions differently, and many simply don't use the permission system that Linux uses. In these cases, you will need to handle the permissions via the filesystem table (/etc/fstab) rather than on the filesystem itself.

What type of partition is the shared folder?

---

### Post by spiderbatdad on 2008-02-03
most likely the permissions are being controlled by your smb.conf. You'll need to do some reading on setting up a samba share and editing smb.conf.

---

### Post by Robert Ashley on 2008-02-04
The Shared Folder is located on the main desktop. I assume it is in the same partition as Ubuntu itself.
Thanks for your prompt reply.

---


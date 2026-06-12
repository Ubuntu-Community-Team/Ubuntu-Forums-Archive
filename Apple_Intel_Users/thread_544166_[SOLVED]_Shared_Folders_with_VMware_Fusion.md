---
title: "[SOLVED] Shared Folders with VMware Fusion"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by Resn8tor on 2007-09-06
I have a MacBook Pro SR C2D, one of the new ones.  I've got VMware Fusion installed and have created a VM and loaded ubuntu.  I installed VMware Tools and set up the VM to access a shared folder using the VMware Tools.  So far so good.

I think I should be able to see the shared folder at /mnt/hgfs, but nothing is there.

Any ideas what I need to do to make this work?

R8

It turned out I needed to make one other change to the Fusion settings.

---

### Post by lynng on 2007-10-08
Care to share your solution?  I've not been able to get shared folders working, despite having it enabled in the virtual machine settings.

---

### Post by Resn8tor on 2007-10-08
Do you have shared folders enabled under "Settings/Shared Folders" itself, as well as under the share entry?  In my case, I have "Enabled at power on" checked on Shared Folders, and "Enabled" checked on the entry for the share itself.

---


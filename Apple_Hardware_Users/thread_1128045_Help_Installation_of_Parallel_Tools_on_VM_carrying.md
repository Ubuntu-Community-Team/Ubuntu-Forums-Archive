---
title: "Help: Installation of Parallel Tools on VM carrying Ubuntu 8.10"
date: 2009-04-17
forum: Apple Hardware Users
---

### Post by decidedlyno9 on 2009-04-17
Hello

Please allow me to make my apologies if there is already an answer posted somewhere in these forums, but my frustration with Parallels support has led me to try my luck here.

I have successfully installed Ubuntu 8.10 on a VM (Parallels 3 Build 5636, MacBook Pro 2.33 GHz 2 GB RAM) however, when I follow the instructions to install Parallel Tools (the Parallel Tools CD image has been mounted on the Ubuntu desktop) using this command: sudo sh /cdrom/parallels-tools.run I receive this message: "Verifying archive integrity... All good. Uncompressing Parallels Tools for Linux..... You are about the start installing Parallels Tools" (there is some further text at this point regarding saving and data loss) then it asks: Continue ? [Yes/No]: I input "Yes", then the message follows "Found xorg version 1.5.2, Installation for xorg.1.5 not found."

If anyone could help I would be most grateful.

---

### Post by cyberdork33 on 2009-04-17
> **decidedlyno9 said:**
> Hello

Please allow me to make my apologies if there is already an answer posted somewhere in these forums, but my frustration with Parallels support has led me to try my luck here.

I have successfully installed Ubuntu 8.10 on a VM (Parallels 3 Build 5636, MacBook Pro 2.33 GHz 2 GB RAM) however, when I follow the instructions to install Parallel Tools (the Parallel Tools CD image has been mounted on the Ubuntu desktop) using this command: sudo sh /cdrom/parallels-tools.run I receive this message: "Verifying archive integrity... All good. Uncompressing Parallels Tools for Linux..... You are about the start installing Parallels Tools" (there is some further text at this point regarding saving and data loss) then it asks: Continue ? [Yes/No]: I input "Yes", then the message follows "Found xorg version 1.5.2, Installation for xorg.1.5 not found."

If anyone could help I would be most grateful.

Make sure to update Parallels as much as you can... It sounds like the tools still don't support Intrepid.

Parallels 4.0 works fine though.

You could also just try using VirtualBox. It is free.

---


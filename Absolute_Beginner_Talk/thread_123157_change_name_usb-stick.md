---
title: "change name usb-stick"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by maxdevis on 2006-01-29
how can i change the name of my icon of my usb-stick that appears on my desktop?

---

### Post by el3ktro on 2006-01-29
You have to rename the partition on the USB stick. You can do this with the mkfs.vfat tool and give a parameter like "-n new_name". This will re-format the USB stick so be sure to copy important data off of it first.

Tom

---

### Post by mgmiller on 2006-01-29
I really hate this answer:
Plug the stick into any Windows XP machine and in MyComputer right click the sticks icon and select properties and just rename it.  This preserves everything on the stick and does not reformat it.  The new name will be used by Windows, OS/X and Linux.

I wish there was a way to do this so easily in Linux, but so far I haven't found it yet.  I have used the same technique to rename an external USB hard drive.  

I have been hoping Dapper would have this capability, but the Disks applet in System Administration only provides a GUI for renaming that wipes the contents of the drive you are renaming.  This applet can also be installed in Breezy.

---

### Post by benplaut on 2006-01-29
i think if you open nautilus as root, you can do that, but i'm not sure

---

### Post by el3ktro on 2006-01-29
Where's the problem with my solution? A USB stick is (usually) not a long-term archiving solution, so there shouldn't be a problem by reformatting it quickly. But your suggestion would of course also work.

Tom

---

### Post by cybergus on 2008-02-06
I'm only a noob, but this is about as simple as I've found...
You'll need to install "mtools" - just search for it in Synaptic.

In terminal, type "mount" and check the line that mounts your usb stick or drive. Mine mounts to /dev/sdb.... etc

now type:  sudo mlabel -i /dev/sdb ::your-label-name-here

...note the double colon. Obviously you'll change the /dev/sdb to whatever your mount information says in terminal.

Clear as mud?

---


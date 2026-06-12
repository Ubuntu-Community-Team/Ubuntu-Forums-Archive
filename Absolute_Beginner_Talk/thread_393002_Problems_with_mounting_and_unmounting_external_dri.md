---
title: "Problems with mounting and unmounting external drive"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-03-25
Hello, phenomenal guys of UbuntuForums!

I am having problems to automatically mount an external firewire drive with ntfs-3g. Edgy wasn't giving this problem. If I mount manually then in the context menu of the drive it appears only "safely remove" and not "unmount". If I press "safely remove" I get the following error message

Unfortunately, the device system:/media/sdb1 (/dev/sdb1) named 'Store' and currently mounted at /media/store could not be unmounted. Unmounting failed due to the following error:
Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL

Any idea on how to solve this problem?

Cheers

Cippa

---

### Post by eljalill on 2007-03-25
I am not sure whether that will solve it, but you could try to manually unmount it with the "umount" command in a terminal.

---

### Post by Stoff on 2007-05-16
There is a hidden item .Trash-username on your external drive. Delete it and umount the drive manually. This should do it.

So far I am not aware of another workaround.

---

### Post by iamkitzune on 2008-02-04
Assuming KDE (I never had this problem in gnome)

Right click on the icon when it is loaded and go to properties.
Select mount automatically.

Unmount/remove which ever method you want. Just make sure your data
is safe before removing the device. The screen should show the removal
of the device. I have mine set to show unmounted devices so it came back.

When you put it back in it should come up mounted giving you the option 
to open new window.... etc.

In my case it was now able to safely remove the device with out errors.

And no I did not have any issues before hand of it mounting the device.
This action only changed the way it behaved for un-mounting.

---


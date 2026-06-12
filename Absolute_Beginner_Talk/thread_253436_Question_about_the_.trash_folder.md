---
title: "Question about the .trash folder"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-09-08
Short version: Where does it live?

Long version: I've noticed that when I have my USB drive plugged in, sometimes if I trash a file, it'll appear in /media/myUSBdrive/.trash  Or maybe it's when I delete files out of my trash folder, they appear in in a new trash folder in the USB drive.  I'm not sure which, haven't done much experimentation.

Obviously, this is not a life-or-death problem, but it's made me curious.  Anyone have any insight on this?

---

### Post by kingbilly on 2006-09-08
Short answer:  Your .trash folder lives in /home/username/.trash
If you are browsing in nautilus you will have to show hidden files and folders to see it.

Long answer(not really): I'm guessing that the usb device has some firmware/hardware/softwhere (not sure what to call it) technology to save things you delete in it's own trash directory, just like the trash bin on ubuntu or recycle bin on windows.  This is probably for the same reason, to restore a file or files you might have not wanted to delete.

---

### Post by argie on 2006-09-08
Just to add, when I delete stuff using root on my USB drive they go to <usbdrive>/.Trash-root 

Don't ask why I do stuff like that.

---

### Post by HAARP on 2006-09-08
That's simple. Any devices get's it's own trash folder, because else it would take ages to delete something. The data would need to be transferred from the usb-stick/other drive to the drive hosting your home(/.Trash) folder first!

---

### Post by noynac on 2006-09-13
I accidentally deleted some photos that were on a compact flash card in a USB CF reader. I was surprised because these files did not show up in the trash icon on the desktop. I looked at the hidden trash directory  on the CF card and all of my deleted photos were in that directory. Why didn't the deleted photos show up when I clicked on the trash icon. 

BTW, I did of search of how to configure trash but couldn't find anything.

noynac

---

### Post by bluefrog on 2006-09-18
launch nautilus
open preferences > behaviour
check add a delete menu (near the bottom of the window
when deleting things, right click on them and select delete (bypass trash)
no more .trash stuff

no gui. ok, command line --> rm .trash

James

---


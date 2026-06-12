---
title: "A:\ drive problem"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-12-16
i installed ubuntu but i cant save to a floppy. it doesnt recognize the drive. can anyone help me out.

---

### Post by bscbrit on 2005-12-16
Have you mounted the floppy after putting the disk into it?  Try

sudo mount /media/floppy

and see if that helps.  You may not need 'sudo', but try it anyway.

---

### Post by bscbrit on 2005-12-16
Don't forget to 'umount /media/floppy' before you remove your disk, otherwise you may lose your data!

---

### Post by Mustard on 2005-12-16
Just out of curiousity, what do you get for output when you do this in terminal

```
cat /etc/group | grep floppy
```

That should show what users are part of the group floppy.  I have read in another thread somewhere that it can help to add the user 'hal' to the group floppy.

The solutions suggested above by bscbrit should be fine, but if you still encounter problems, you might be able to try this angle.

---

### Post by bscbrit on 2005-12-16
Mustard, thanks for the info - that's a new one for me.  I gather that hal should recognise that a new disk has been put in the drive and remount it accordingly?  Does it also do immediate 'umount' s to ensure that data is written to disk straight away?

---

### Post by Mustard on 2005-12-16
[QUOTE=bscbrit]Mustard, thanks for the info - that's a new one for me.  I gather that hal should recognise that a new disk has been put in the drive and remount it accordingly?  Does it also do immediate 'umount' s to ensure that data is written to disk straight away?[/QUOTE]

I believe it will automount the floppy (from what I have read), but as for unmounting I think you would still need to do that manually.  On gnome of course you can right click on the floppy drive icon and choose unmount.

I was having trouble with CD's and USB drives not automounting in Breezy, so that was a solution that I tried for those (with some success).  I don't often use my floppy drive, but floppies were also mentioned in this particular thread.

-edit-

Well, I just tried it and it didn't automount the floppy..hehehe..so I guess it might have been that it is supposed to automount the **floppy drive** at boot up perhaps. :)

-edit2-

This is the thread anyway...
[http://www.ubuntuforums.org/showthread.php?t=77141](http://www.ubuntuforums.org/showthread.php?t=77141)

-edit3-
I started fiddling around with it afterwards and then remembered that I had changed some options in my configuration editor to not display internal drives.  This could be related to why I have been having problems. :)

---

### Post by wylfing on 2005-12-16
[QUOTE=bscbrit]You may not need 'sudo', but try it anyway.[/QUOTE]

Nope, you don't need 'sudo'. Just mount it.

Incidentally, this is (AFAIK) due to the fact that most PC floppy drives have no hardware input notification. This means that Ubuntu has no way of knowing you've inserted a disk, and so doesn't automount it. People who have newer USB floppies have full functionality, because those drives know when a disk is inserted.

So the only possible solution to this is to mount the thing on the command line. Once it's mounted, however, you can unmount it from within Gnome by right-clicking the floppy icon and choosing Unmount volume. 

**NOTE: As pointed out above, you must unmount the floppy before ejecting it!**

---

### Post by Delkster on 2005-12-16
You don't necessarily need the command line for mounting a floppy. You can also go to Locations -> Computer and open the floppy drive icon there when the disk is inserted. That should mount the floppy and place an icon onto the desktop for accessing its contents.

As others have pointed out, when you're finished using the floppy, remember to right-click on the floppy icon on the desktop (or the Computer location) and select 'Unmount' before removing the floppy from the drive. That'll ensure that everything you stored on the floppy actually gets written there.

---

### Post by grim918 on 2005-12-17
thank you i got it working.

---


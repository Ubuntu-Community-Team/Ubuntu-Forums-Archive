---
title: "properly deleting stuff - delete key?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by oysterpog on 2007-11-06
gday all!!

firstly i'm pretty new to linux so please treat me like a total noob.

if i hit the 'delete' key to delete files from my internal (boot) drive, it sends said file to the garbage bin and i can empty the trash and its all good.

however, when doing the same thing on either of my external drives (one is a 500GB SATA (EXT3) the other is a 200GB IDE (NTFS), both mounted via usb adaptors) the file just disappears. it doesn't go into the trash, it doesn't ask for confirmation to delete, and the 'free space' listed at the bottom left of the file browser doesn't update. ejecting/unmounting, restarting does nothing to change this.

even more weird, if i do this and then hit 'properties' of said drive, it counts up the files and displays the proper updated figure in 'contents' but the pi graph down the bottom doesn't update, neither does the free space figure.

this doesn't occur when right-clicking and hitting 'delete', nor when i send it to the trash first, only when i actually hit the 'delete' key.

any ideas on this?

many thanks in advance for your wisdom!

jonas

ps: got the ntfsprogs to try and run a check/repair, to no avail.

---

### Post by ohzopants on 2007-11-06
That's sort of a known-issue.

You should look for hidden directories called ".Trash-yourusername" in the root directories of these drives.  This happens to me all the time on my usb flashdrive, I always have to go empty that directoy manually.  I think it's a gnome bug with external volumes in general.

Hope this helps.

---

### Post by jordanmthomas on 2007-11-06
If you navigate to an external drive (in the file browser) and press <Ctrl-h> in it you should see a directory called .Trash-yourname or .trash-yourname.  In this directory resides the trash.

Not sure why it doesn't show up in your trash, but at least you can get to it.  To permanently delete something, press shift + delete on it.

---

### Post by rsambuca on 2007-11-06
I am not sure about the external ext3 drive, but I know for all ntfs drives, if you delete a file it goes to a folder called .trash-<yourusername>.  If you browse the drive, go to the top menubar in Nautilus (the file browser), and select "View -> Show Hidden Files".

To permanently delete the files and free up the space, you can just delete the folder.  The next time you delete something on that drive it will reappear.

---

### Post by oysterpog on 2007-11-07
you guys rule. many thanks,

rock the gold tooth!!

---

### Post by ro314 on 2007-12-09
In Nautilus go to: Edit -> Preferences -> Behavior and activate
"Include a delete command that bypasses trash"

Then pressing Shift+Delete will permanently delete your files.

---

### Post by mcduck on 2007-12-09
> **ro314 said:**
> In Nautilus go to: Edit -> Preferences -> Behavior and activate
"Include a delete command that bypasses trash"

Then pressing Shift+Delete will permanently delete your files.

You don't need to enable that to use Shift-Delete. It works by default. That option adds the delete to right-click menu.. :)

---


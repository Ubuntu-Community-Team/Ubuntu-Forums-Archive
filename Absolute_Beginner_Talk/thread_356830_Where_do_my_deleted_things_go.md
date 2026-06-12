---
title: "Where do my deleted things go?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Kittens on 2007-02-08
I feel like a gigantic idiot asking this, but where do my deleted files go? They don't show up in the trash bin. Did they just disappear?

---

### Post by NewOldTimer on 2007-02-08
check show hidden files under veiw

---

### Post by Kittens on 2007-02-08
So, I'm assuming that it went into the folder named Trash? When I delete that it just disappears too! Where did it go! It didn't go into the trash folder on the taskbar. Was it deleted permanently?

---

### Post by taurus on 2007-02-08
Into black hole.

---

### Post by NT4usB on 2007-02-08
I was poking around shared folders on my MythTV box from XP and found many 'deleted' files.
Crabwalked over to the Linux box, updatedb and searched for them. They were no where to be found. 
I could play them on the XP box and after dragging them to the XP box and back to the pvr, I could find them on the Mythbox.
No idea where they were hiding that locate couldn't find them...

Similar thing on NTFS formatted external USB drives. Plug them into a Linux box and 'deleted' files show up big as life and some even play.

aaah, the mysteries of Linux...

ed: spelling

---

### Post by Kittens on 2007-02-08
So....were the files I wanted to delete...deleted? Thereby freeing up memory because they don't exist anymore? Maybe?

---

### Post by Adrenal on 2007-02-08
Deleting files frees up hard drive space, not memory. And if your files are not in the trash, or their original location, then there is a very good chance that they have been deleted.

Additionally, if you want to bypass the trash can, in Nautilus go to preferences/Behaviour and, at the bottom, check the box that says "include a delete command that bypasses trash". This will add an entry called "delete" to your right click menu which, when used, will delete your files permanently. Basically, they don't hit trash at all, they are just gone(use with caution, recovering files on ext3 is hard)

---

### Post by nalioth on 2007-02-08
Assuming you are using the nautilus context menu when you delete something, those files are gone forever.  "Move to Trash" from the nautilus context menu -er- moves the files to the Trash which can be found in a terminal by running 
```

ls .Trash

```

If you are using the terminal to delete with the command "rm", the files are gone forever.





Actually 'forever' can be as soon as you pay a data recovery specialist lots of money . . .

---

### Post by Kittens on 2007-02-08
Oh, ok. Thank you very much! I have the answer I was looking for!

Love the fast responses from this community.  ^_^

---

### Post by jml on 2007-02-08
This message thread raises a question in my mind.  In Windows, deleting a file actually only deletes the reference to the file in the File Allocation Table, so the OS now "sees" that area on the disc as open and available for writing new data.  Special utilities are capable of "undeleting" the date by bypassing the File Allocation Table in their search for the data as long as nothing has been written to that area of the disc yet.  That's why if you want to really "wipe" a drive in Windows, you need a program that actually writes over the entire area of the disc you want to securely erase.

What actually happens in Linux?  Is there an equivalent of the File Allocation Table in Linux?  For example, the journaling system in either ext3, or ReiserFS?  Or, does deleting a file in Linux actually remove it from the hard disc?  I tried to look this up in a few Linux resources, but did not find anything.

Joe

---

### Post by finer recliner on 2007-02-09
^ also interested in Linux file recovery on ext3 (just to satisfy my own curiosity)

---


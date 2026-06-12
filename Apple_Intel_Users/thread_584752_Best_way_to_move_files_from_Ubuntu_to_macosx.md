---
title: "Best way to move files from Ubuntu to macosx"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-21
This is more of a housekeeping thing than anything but I'm trying to move a music album (folder of mp3 files) from Gutsy over to the Mac OS X system on my MacBook (C2D).
From Ubuntu, I can easily get into /mnt/sda2/macosx/Users/paul/music/ (but only as root).
However, I cannot, even as root, move (mv) the music folder from Gutsy to this directory tree. The error I get says that the new folder cannot be created as this (the Mac side) is a read-only file system.
How can I get around this?
Thanks
Paul

---

### Post by cyberdork33 on 2007-10-21
> **PaulFXH said:**
> This is more of a housekeeping thing than anything but I'm trying to move a music album (folder of mp3 files) from Gutsy over to the Mac OS X system on my MacBook (C2D).
From Ubuntu, I can easily get into /mnt/sda2/macosx/Users/paul/music/ (but only as root).
However, I cannot, even as root, move (mv) the music folder from Gutsy to this directory tree. The error I get says that the new folder cannot be created as this (the Mac side) is a read-only file system.
How can I get around this?
Thanks
Paul
did you disable journaling in OSX?

---

### Post by PaulFXH on 2007-10-21
No, I did not.
This would eliminate my difficulty?
If so, what counter-problems might be caused in OS X in your experience?
Thanks
Paul

---

### Post by cyberdork33 on 2007-10-21
> **PaulFXH said:**
> No, I did not.
This would eliminate my difficulty?
If so, what counter-problems might be caused in OS X in your experience?
Thanks
Paul

The kernel code only allows for write if journaling is disabled. I do not know of any huge implications of this, rather than, you do not have the benefits of journaling. 
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

### Post by PaulFXH on 2007-10-21
OK, thanks. I'm gonna try this
As I regrettably don't actually use OS X very much up to this, there's really very little to lose.

---

### Post by PaulFXH on 2007-10-22
OK, I disabled journaling on my OS X partition and now I can copy my music folder from Ubuntu over to OS X. So, that's great.
However, there's still a problem. Before disabling journaling in OS X, I had to open Rhythmbox (from Ubuntu) as root to enable it to "see" the music files stored in OS X.
However, now with journaling disabled, this situation has not changed. Only opening Rhythmbox as root from Ubuntu allows me to play the music stored  on the OS X partition. 
OK, it's not a major disaster but it would be nice if there was a way around it.

---

### Post by cyberdork33 on 2007-10-22
Linux reads permissions on your OSX files. Those files are likely owned by another "users" (at least to the system the users are different). You can start up OSX and change the permissions on the files you want, (read privs to ALL) then you should be able to access them. 

There is more complicated method which involves tricking the systems into seeing the users as the same. (editting user id's), but is not recommended. There are some threads about sharing home directories if you are interested.

---

### Post by PaulFXH on 2007-10-25
Don't seem to be able to manage what you're recommending here to make my music files in OS X accessible from Ubuntu without having to access them as root.
In OS X, the My Music folder already had Read&Write privileges for the owner (paul -- that's me). The group ownership (also paul) had privileges for nothing so I changed that to Read.
However, this made no difference to how I could access the music files from Ubuntu. I still could only reach them as root.
Any more clues on how to do this?
Thanks
Paul

---

### Post by cyberdork33 on 2007-10-25
> **PaulFXH said:**
> Don't seem to be able to manage what you're recommending here to make my music files in OS X accessible from Ubuntu without having to access them as root.
In OS X, the My Music folder already had Read&Write privileges for the owner (paul -- that's me). The group ownership (also paul) had privileges for nothing so I changed that to Read.
However, this made no difference to how I could access the music files from Ubuntu. I still could only reach them as root.
Any more clues on how to do this?
Thanks
Paul
you need to give read privs to ALL, not just group. The group IDs are in the same situation between systems as the user IDs.

---

### Post by PaulFXH on 2007-10-26
OK, thanks for that and I've got it now. OS X music files are now fully readable as user from Ubuntu.
However, what you refer to as ALL, is actually called OTHERS in OS X on my computer. This where I got confused.
But, all's well that ends well.
Thanks for your help once again.
Paul

---

### Post by cyberdork33 on 2007-10-26
> **PaulFXH said:**
> OK, thanks for that and I've got it now. OS X music files are now fully readable as user from Ubuntu.
However, what you refer to as ALL, is actually called OTHERS in OS X on my computer. This where I got confused.
But, all's well that ends well.
Thanks for your help once again.
Paul
Sorry, I literally meant all the available options.

---


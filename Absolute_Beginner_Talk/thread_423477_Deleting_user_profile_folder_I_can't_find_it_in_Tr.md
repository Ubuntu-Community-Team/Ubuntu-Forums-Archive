---
title: "Deleting user profile folder: I can't find it in Trash?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-25
Okay, here's the gist. A few days ago, one of my user profiles became corrupted. Anyways, i've just moved the corrupted user profile folder from /home into the Trash can. 

Any idea how to truly delete it? I can't find the folder in none of the .user-trash folders.

---

### Post by stmiller on 2007-04-26
open a terminal and

$ cd .Trash

then type

$ ls -a

this will tell you if any files are in there, including hidden files/folders. If something is there, to delete everything type

$ rm -Rf *.*

(warning: this cannot be reversed!)

---

### Post by BaffledMollusc on 2007-04-26
Edit: Oops, double post.

---

### Post by BaffledMollusc on 2007-04-26
> **Lucifiel said:**
> Okay, here's the gist. A few days ago, one of my user profiles became corrupted. Anyways, i've just moved the corrupted user profile folder from /home into the Trash can. 

Any idea how to truly delete it? I can't find the folder in none of the .user-trash folders.

Not quite sure what you're asking. If you've deleted it using the file manager it's in the trash can, which means it's deleted. If you want you can always empty the trash can which means it's gone forever (right click on the trash icon and choose "empty trash").

If you want to delete something without sending it to the trash you can always remove the file from the command line with "rm filename". That deletes the file completely, bypassing the trash.

---

### Post by Lucifiel on 2007-04-28
> **stmiller said:**
> open a terminal and

$ cd .Trash

then type

$ ls -a

this will tell you if any files are in there, including hidden files/folders. If something is there, to delete everything type

$ rm -Rf *.*

(warning: this cannot be reversed!)

Thank you but that doesn't work for this issue. The folder simply doesn't show in Trash. 

As a test, I tried this:

Using Alt + F2: gksudo Nautilus, I opened up Nautilus and I actually tried creating a folder called Testing123 under "/home". Then, I deleted it. Guess what? That folder didn't land in the Trash folder. I even used gksudo Konqueror and gksudo Nautilus to look at "trash:/" but the folder was not there. 

The question is: where the heck did it go to? :confused: 

Does this mean I'll need to log into my root account?

---

### Post by Lucifiel on 2007-04-28
> **BaffledMollusc said:**
> Not quite sure what you're asking. If you've deleted it using the file manager it's in the trash can, which means it's deleted. If you want you can always empty the trash can which means it's gone forever (right click on the trash icon and choose "empty trash").

If you want to delete something without sending it to the trash you can always remove the file from the command line with "rm filename". That deletes the file completely, bypassing the trash.

Errr, actually I do know how to use the Trash can. ^^;; And I do know where files go to, after they're deleted. :)

Thank you for the command! :) That's something new, indeed for I didn't know you could delete a file and bypass the Trash folder. :)

---


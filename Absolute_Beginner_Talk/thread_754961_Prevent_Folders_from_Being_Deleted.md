---
title: "Prevent Folders from Being Deleted"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-04-14
I Seem to have accidentally moved and deleted my Pictures folder.  Nothing too much in there that was THAT important, but there could have been.  If it had been my Documents folder I would have been in a pickle.

So Question....

What steps do I need to take to prevent a particular folder from being deleted.  How do I protect them and still be able to write, modify, and delete items from within that folder?

---

### Post by ajgreeny on 2008-04-14
The only way I can think of, though there may be other more practical ways, is to make the important folder "Access Only" in the permissions tab of Properties when you right click it.  You can always change it if you need to to write to it, but at least you won't be able to delete it.

There may well be other possibilities that I do not know of, but you will need to wait for other replies for them to be made known.

---

### Post by OZFive on 2008-04-14
That is a work around on it but it would make instant use of the folder kind of difficult.

---

### Post by nhandler on 2008-04-14
Another idea is to setup a cron job to copy ~/Documents to ~/.Documents daily (or as needed). This would keep two copies of all your important documents. Since the second copy would be in a hidden folder, you wouldn't see them unless you needed to restore a file. An even better approach, would be to use hard links. I won't go into the details, but hard links would save you hd space.

By using this approach, you could easily restore the folder and all of your documents if you ever accidentally deleted them.

---

### Post by OZFive on 2008-04-15
I think I see what you mean here.   

So make a Link to the Picture Folder and hide the original. 

Use the link for adding pics and items to the folder

And if I delete the Link Pictures folder (not the original) the items I moved to the link folder will still be in the hidden Pictures folder?

Also the items in the Link folder will be links, copies of the originals saving me drive space.


Is that correct?

---

### Post by GoCool on 2008-04-15
Yes.

Case scenario 
-----------------
I have a machine which is used especially only for playing music, this is for my Meditation Center.

I created two logins one for administrative purposes and another for just daily usage.

I put all the music in a folder called Music and made a link to it.

And that link folder I moved it to the "daily usage" music folder and gave just read access to it (No write and no execute)

I now ask any one using the machine to use the login for daily usage. And it saved many a times when they accidently press the delete key. And since I have just given it read access, it just pops up an error message, so even the link directory is safe.

---

### Post by ajgreeny on 2008-04-15
Clever!!  I must remember that one for any such times and situations.

---


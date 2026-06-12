---
title: "permissions to delete links"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by DVD-R on 2008-01-10
Hi,
I created a few links to folders on the desktop.
A couple of them, I then wanted to delete.
But the only option in the rightclick was to send to trash.
So I did.

then I went to empty trash and got an error that the particular links were seen as parent objects and I did not have permission to delete.

I went inot the terminal as gksudo nautilus and looked for these files, but the file manager does not show the .Trash folder under my username 
/home/user/.Trash I believe is where its supposed to be, but it does not appear.
This business of not having full permissions is a little silly for me.
I there a way for me to log in with full permissions?

Or else, these files will forever be in the trash folder :confused:
Big thanks

---

### Post by jken146 on 2008-01-10
Press Ctrl+H to see hidden files (those whose names begin with a dot).

---

### Post by DVD-R on 2008-01-10
AH!
Thanks :)
Sorry for the dumb questions.
Is there a good book that has all of this stuff?
Or are there so many GUI versions that no book could be made?

Thanks again!

---

### Post by Blutack on 2008-01-10
There are many books, wiki's and blogs all of which will help.
The Ubuntu Linux Bible is good.
To remove the files start a terminal and type:
> gksu nautilus
then browse to your home folder and remove offending files!

---


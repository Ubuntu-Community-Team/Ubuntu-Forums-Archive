---
title: "How do I remove a file?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Mykewl on 2006-04-19
Hi,
I need to remove a file but the "move to trash" is grayed out.
How do I do this?
Thanks
Mykewl

---

### Post by cgjones on 2006-04-19
```
sudo rm -f *filename*
```

Just make sure that you don't need the file.

---

### Post by taurus on 2006-04-19
If you want to delete a file, you can also do that from a terminal or a command prompt.
```

rm filename
-or-
sudo rm filename (if it's a system file)

```

---

### Post by Mykewl on 2006-04-19
Thanks for the reply :)
I must be using the wrong filename.
It is in file system > opt >firefox.
Got there when i tried to update to firefox 1.5.02,
after which I used the install script in the forums.
I used /filesystem/opt/firefox when trying to remove
as per your instructions.

---

### Post by outofnicks on 2006-04-20
A great way to avoid typos in paths and filenames is to drag & drop the file icon into the terminal window after entering the rm command, or after whatever command(s) being used--the full path is printed in the terminal.

---

### Post by vavoem on 2006-04-20
you might not have the right permissions to remove the file.

If you type sudo rm -r filename 
you will be asked for a  password that'll be your one.

Be carefull you don't want to be throwing the wrong thing away.

Another tip as concerned to typo's 
If you type the first (few) letters of a filename and hit Tab it wil automagicly type the rest for you.

That's how powerfull the terminal is. :mrgreen:

---


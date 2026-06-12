---
title: "Sort by modified date"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-05-03
I'm looking for a command to sort all files in a directory by date/time modified.  

It would be helpful if I can also view modified dates of all files in children directories as well.  

Any suggestions?

---

### Post by Cypher on 2007-05-03
```

ls -ltr

```
-l = Long List
-t = Sort by modification time
-r = Reverse

This will show the most recently modified files at the bottom of the listing. Remove the "-r" if you want them on top..

P.S. "man ls" is your friend..:)

---

### Post by starcraft.man on 2007-05-03
Just right click on the white background of your nautilus window, select "arrange items" then select "by modification date".

To see the dates, go to the menu at the top of the file browser. View > View as List, or click Ctrl + 2.

Have a nice day :)

Edit: Oh... you wanted the command, *slaps head* oh well, my way if you wanna browse with Nautilus.

---

### Post by chymo on 2007-05-03
> **starcraft.man said:**
> Just right click on the white background of your nautilus window, select "arrange items" then select "by modification date".

To see the dates, go to the menu at the top of the file browser. View > View as List, or click Ctrl + 2.

Have a nice day :)

X server is not installed...

---

### Post by starcraft.man on 2007-05-03
Hehe my bad, I glanced over command :p

Listen to cypher :)

---

### Post by jfinkels on 2007-05-03
You can go through subdirectories recursively with -R, so it will look like this ```
ls -ltR
``` Add the -r if you want to reverse the order. You're going to get a lot of listings if you do the -R (recursively list all sub-directories), so you may want to put the output into a file, like this ```
ls -ltR > somefile
```

---

### Post by chymo on 2007-05-03
> **Cypher said:**
> ```

ls -ltr

```
-l = Long List
-t = Sort by modification time
-r = Reverse

This will show the most recently modified files at the bottom of the listing. Remove the "-r" if you want them on top..

P.S. "man ls" is your friend..:)

Thanks, this tells me the owner/group of the file... but it does not tell me who was the last user to modify the file.  Any thoughts on that?

---

### Post by jfinkels on 2007-05-03
> **chymo said:**
> Thanks, this tells me the owner/group of the file... but it does not tell me who was the last user to modify the file.  Any thoughts on that?
Hmm you can view the author...
```
ls -ltR --author
```

Take a look at the man page for ls ```
man ls
```

---

### Post by chymo on 2007-05-03
Thanks,

I'm getting:


-rw-rw-r--  1 userx userx userx 12073 2007-05-03 10:40 index.html


using: ls -ltr --author

However, the file was not modified by userx at 10:40, it was modified by another user... This is why I'm confused.

---

### Post by jfinkels on 2007-05-03
> **chymo said:**
> Thanks,

I'm getting:


-rw-rw-r--  1 userx userx userx 12073 2007-05-03 10:40 index.html


using: ls -ltr --author

However, the file was not modified by userx at 10:40, it was modified by another user... This is why I'm confused.

Yeah, the author is the one who created the file, not necessarily the last one to modify the file. Unfortunately, I'm not sure how to determine the last user to modify a file...sorry.

---

### Post by chymo on 2007-05-03
I got it!

ls -ltr > worked!

Thanks!

---


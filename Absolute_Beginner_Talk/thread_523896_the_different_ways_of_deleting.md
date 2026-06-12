---
title: "the different ways of deleting"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-12
can anyone tell me all the ways you can remove file, like the commands and all that which is used in terminal, thanks and is terminal and shell the same thing? when someone tells you to open/edit shell, is it the same as going to applications>accessories>terminal?

---

### Post by Blutack on 2007-08-12
To delete a file normally use
rm /path/to/file
to delete a directory use
rm -Rf /path/to/directory

Normally a shell is the same thing as the terminal.  However, they may be referring to a virtual terminal - hit control, alt and f1 to access a virtual terminal and log in.  This is only normally necessary for changing X-server stuff (graphics drivers etc).

---

### Post by nixclusive on 2007-08-12
Yes, the terminal and shell are the same thing by implementation. When someone tells you to open/edit shell, it *is* the same as going to applications>accessories>terminal.

The following command can be used to delete files:```
rm -iv <filename>
```

The following command can be used to delete a directory/folder:```
rm -iv -r <directory-name>
```

Regards :-)

---

### Post by rax_m on 2007-08-12
And it's probably worth noting that deleting via a terminal command does NOT put the items into your trash can... in other words once you hit enter, it's gone.

---


---
title: "setting up wireless card"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by RexConnix on 2008-03-03
Ok i am using the how to install by adampyre but having trouble with the ndiswrapper command

keeps coming up with could'nt create /etc/ndiswrapper: permission denied at /usr/sbin/ndiswrapper line 186

Do i need to be logged in as root ?

---

### Post by unutbu on 2008-03-03
You need to execute the command as root.
Simply put the word sudo in front of the ndiswrapper command.

For example,
```

sudo ndiswrapper -i filename

```

PS. In ubuntu, you never log in as root. Instead, you preface commands with 'sudo' whenever you want to invoke the powers of root.

---

### Post by RexConnix on 2008-03-03
Ok thanks for that it worked but i have now a new problem.  it comes up with could'nt find PRISMICB in "."

---

### Post by unutbu on 2008-03-03
"." is the current directory.
Apparently, PRISMICB is not in the current directory.
Perhaps the file you want is called PRISMICB.inf?
if so try

```

sudo ndiswrapper -i PRISMICB.inf

```

Unlike Windows, Ubuntu never ignores the file extension. Also note that file names are case-sensitive. 

Doing 
```

ls -l

```

will show what is in the current directory. If you PRISMICB.* should be there, you'll get to see what Ubuntu thinks the file name is.

Of course, if the driver is in some other directory, you have to give the full path name.

---

### Post by RexConnix on 2008-03-03
Cool thanks for that all working now.  Cheers

---


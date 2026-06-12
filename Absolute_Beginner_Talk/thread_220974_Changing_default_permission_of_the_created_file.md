---
title: "Changing default permission of the created file"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-07-22
The default permission of the new created file on my computer is 600,rw-------. It's means only me, the file owner, can access the file. It isn't convenient for me. Can I change it?

---

### Post by zxee on 2006-07-22
> **NeoRc said:**
> The default permission of the new created file on my computer is 600,rw-------. It's means only me, the file owner, can access the file. It isn't convenient for me. Can I change it?

Sure you can do anything in linux :).
Take a look at the man page for chmod i.e man chmod
sudo chmod 644 (the file you want to change) would, for example let everyone have read access to that file.

---

### Post by cwaldbieser on 2006-07-22
> **NeoRc said:**
> The default permission of the new created file on my computer is 600,rw-------. It's means only me, the file owner, can access the file. It isn't convenient for me. Can I change it?

The umask command works for files created by most shell tools.  You could set it in your ~/.bashrc.

---

### Post by Omnios on 2006-07-22
In the /home section with you as owner you can right click the file and choose properties and permitions to graphicly change the permitions.

---

### Post by aysiu on 2006-07-22
If changing the ~/.bashrc file works, I'd really like to know, because in the meantime I've been recommending [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9).

---

### Post by NeoRc on 2006-07-22
Maybe my question is inexplicit, I'm sorry about that. But I don't mean how to change the permission of an existed file, I mean can I change the default permission from 600 to 644? Thus, when I create a new file again, I can get a file with permission 644.

---

### Post by aysiu on 2006-07-22
> **NeoRc said:**
> Maybe my question is inexplicit, I'm sorry about that. But I don't mean how to change the permission of an existed file, I mean can I change the default permission from 600 to 644? Thus, when I create a new file again, I can get a file with permission 644.
See posts #3 and #5.

---

### Post by NeoRc on 2006-07-22
How to use the umask command in ~/.bashrc. Can someone show an example for that?

---

### Post by taurus on 2006-07-22
In ~/.bashrc

```

umask=022

```
Then rehash it so the new change will be in effect...

```

source ~/.bashrc

```

---

### Post by aysiu on 2006-07-22
~/.bashrc is a big file. Where do you put the *umask=022* parameter?

---

### Post by taurus on 2006-07-22
A big file!!!  Actually, you can put it anywhere in there...  Usually, I add my personal stuff, aliases and what not, at the end so I can keep track of things...

---

### Post by aysiu on 2006-07-22
Good to know--so it can just be tacked on to the end of the file?

---

### Post by taurus on 2006-07-22
> **aysiu said:**
> Good to know--so it can just be tacked on to the end of the file?
Yes, sir.

---

### Post by NeoRc on 2006-07-22
I checked out the ~/.bashrc, but cannot find the *umask* parameter.

---

### Post by aysiu on 2006-07-22
> **NeoRc said:**
> I checked out the ~/.bashrc, but cannot find the *umask* parameter.
There is none. You add it.

---

### Post by NeoRc on 2006-07-22
OK, now it works fine. I have a another question, what does the 022 mean?

---

### Post by aysiu on 2006-07-22
```
SYNOPSIS

umask [-S] [mode]
DESCRIPTION

umask sets the file mode creation mask of the invoking process to the given mode. You can specify the mode in any of the formats recognized by chmod; see chmod for more information.

The file mode creation mask (often called the umask) determines the default permissions for any file created by the process. For example, a file created by the create command has the permissions specified by the umask unless the create command specifies explicit permissions.

Calling umask without a mode argument displays the current umask.
Options

-S 

    displays the umask in a symbolic form:

        u=perms,g=perms,o=perms

    giving user, group and other permissions. Permissions are specified as combinations of the letters r (read), w (write) and x (execute).

DIAGNOSTICS

Possible exit status values are:

0 

    Successful completion.
1 

    Failure due to an invalid command line argument, or invalid mode.

```

---

### Post by NeoRc on 2006-07-22
OK, I got it. Thx for all the replies.

---

### Post by NeoRc on 2006-07-23
It's me again, and I found another problem.

Now when I create a file use *touch file_name*, the default permission has been changed to 644. It's great. But when I create some file in the file manager(nautilus), the default is still 600. Can I change it?

---

### Post by steve.horsley on 2006-07-23
A wild guess - you may need to log out and back in again so that Gnome can re-read the file during its startup.

Incidentally, for those who don't get it, the way that the umask is applied to newly created files is that any 1s in the umask force the corresponding bit it the file to 0. Confusing, huh?

---


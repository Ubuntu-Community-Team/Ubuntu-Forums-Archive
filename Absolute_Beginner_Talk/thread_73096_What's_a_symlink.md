---
title: "What's a symlink?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by jipke on 2005-10-08
Probably a simple question ... but what does a symlink exaclty do? 

Is it 'just' a windows shortcut equivalent? How does it differ from a launcher (on the desktop)? And where are the symlinks stored from the programs that I start from terminal?

Thanks!

---

### Post by mpat on 2005-10-08
A symlink (symbolic link) is a reference to another location inside your file system.

For example when you link to folder you can change (cd) "into" that symlink and are actually in the folder the symlink references to. When you open/execute a symlink to a file, actually the file the symlinks references to is opened (and modified when you save it)/executed.
When you delete a symlink, the file/directory that symlinks points to will *not* be deleted.

Compared to Windows' shortcuts a symlink is something directly stored inside the file system. A shortcut under Windows actually is a file with the .lnk-extension and inside the file there is the information stored to which location that shortcut should point to. When you open a .lnk-file inside a text editor you will see some binary stuff. But I guess some Windows software will recognize that the "file" is actually a shortcut and will read the shortcut information and open the location referenced to.

**But be carefull** when you have samba installed and a symlinked directory inside a share. When you are deleting from Windows Explorer, I think Windows goes thru the sub directories and will delete from bottom to top so first the folder's (actually the symlinked folder's) content and then the folder itself (symlink) is deleted!

There is another thing: hardlinks. A hardlink is a file that uses the same "space" on a drive than another file does. So a file allocates some space, say 100 MB, on the harddisk, a hardlinked file will exactly use the same 100 MB.
When you delete a hardlink the space will still be used by the original file and other hardlinks. Only when the last file that allocates that space will be deleted then the space will be freed.

Note that symlinks can point from one partition to another, even a network location, but hardlinks only work inside the same partition.


I hope this explanation is not too complicated. I can remember when I started with LINUX I also did not get this symlink/hardlink stuff... ;-)

---

### Post by transactionlogfiller on 2005-10-08
A launcher is a lot more like a Windows shortcut, in that it is a file in it's own right - it just runs a command, and if you move the file the launcher points to, the launcher breaks. 

I have links to some programs (like firefox) in my /usr/bin/ directory. Is that what you mean when you say programs you run from the terminal?

---

### Post by jipke on 2005-10-08
Thanks for the replies.

[QUOTE=transactionlogfiller]
I have links to some programs (like firefox) in my /usr/bin/ directory. Is that what you mean when you say programs you run from the terminal?[/QUOTE]

Yes, that's what I mean. When I, for example, type "gaim" in a terminal, gaim will start because there is a 'gaim-symlink' in the /usr/bin directory (which points to the executable 'gaim')?

And if this is correct:

How do I add/create a symlink for a program which is not symlinked in the /usr/bin directory, and therefore I cannot start from a terminal just typing <program> (e.g. gaim).

---

### Post by mpat on 2005-10-08
```
ln -s <destination> <name for link>
```

e.g.

```
ln -s /opt/foobar/bin/start /usr/bin/foobar
```

So when you type in "foobar", actually "/opt/foobar/bin/start" will be executed.

If you leave out "name for link" then the symlink will be placed in the current directory named by the file that it will point to, so here: "start".

You can recognize a symlink in the directory listing by typing

```
ln -l
```

Symlinks are shown like (with a **->**):
```

lrwxrwxrwx    1 root root   28 2005-09-28 22:09 initrd.img.old -> boot/initrd.img-2.6.12-9-686
```

---

### Post by Neilwebster on 2006-09-20
Hi,

How would I go about removing a symbolic link?

I've put one in that is freezing everything on boot.

Cheers

Neil

---

### Post by christhemonkey on 2006-09-20
Remove them like you would a normal file.
```
sudo rm /boot/yoursymlinkfile 
```
or just delete them through the file browser.

---


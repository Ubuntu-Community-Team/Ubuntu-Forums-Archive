---
title: "help me install tar file pls"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-12
I extracted the tar file to my desktop then typed tar -zxvf pspvc-install-0.2.1/ and this is what happens:

rain@the-cube:~/Desktop$ tar -zxvf pspvc-install-0.2.1/
tar: pspvc-install-0.2.1/: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can anyone help me?

---

### Post by Maestro23 on 2007-02-12
If you have already extracted it, there is no need to use tar on it.  That is a directory.

cd <directory>

ls

---

### Post by LotsOfPhil on 2007-02-12
The command you mention "tar -zxvf pspvc-install-0.2.1/" is to undo the archive pspvc-install-0.2.1/
The problem is that it is a directory, not an archive. Go into the directory and see what's in there.

cd pspvc-install-0.2.1/
ls

---

### Post by Ceta on 2007-02-12
There's a install.sh file, and a folder called archive that contains some tar folders.  Now what?

---

### Post by Ceta on 2007-02-12
Okay, nevermind, I figured it out.  It installed and when i type pspvc the program opens. But how do I get it into my applications drop down menu so I dont have go to a terminal to open it?

---

### Post by igknighted on 2007-02-12
> **Ceta said:**
> Okay, nevermind, I figured it out.  It installed and when i type pspvc the program opens. But how do I get it into my applications drop down menu so I dont have go to a terminal to open it?

I am using Fedora so I can't promise its the same, but this is how I would do it: System -> Preferences -> MenuLayout (mine has a MorePreferences step in between, but I doubt you would have that).  From here it is very easy.  I don't know if Ubuntu uses the same tool or not, I think the menu editor might be in Applications -> Accessories in Ubuntu, but don't quote me on that.

---

### Post by Ceta on 2007-02-12
I went to System -> Preferences -> MenuLayout and found it there.  It worked. Thanks!

---

### Post by tonyr1988 on 2007-02-12
Glad everything's working for you...just as a quickie shortcut: you can access the same menu editor by right-clicking "Applications" and choosing Edit Menus. You shouldn't need to edit your menus often enough to need a shortcut, but it doesn't hurt to have one. :P

---


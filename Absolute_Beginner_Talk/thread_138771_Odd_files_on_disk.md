---
title: "Odd files on disk?"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by kel on 2006-03-02
hi, I'm new to linux so I've been reading through the Terminal for Beginners guide posted on this site, its ace btw and a its been a huge help sorting out some file issues so a big thanks to Kyral for that.

Anyway, I've noticed that when using the ls command on the Desktop and other home folders, that some files are showing up that aren't there. For example, on my Desktop I only have one file called "junk", but if i use ls through terminal it reports this:

junk   junk~   new file~

This also happens in other folders. I've used the file browser and enabled hidden files but the files~ don't show up.

So, just out of curiosity, what are the mysterious files~ (with the wiggle at the end) :D

Cheers.

---

### Post by gord on 2006-03-02
the files with the 'wiggles' "~" are created by Gedit when you save a file, they are backups of the file so if you make a mistake then you can rectify it with the backup.

---

### Post by Q4U on 2006-03-02
It's... junk :D

Sometimes old versions of modified files are automatically saved - e.g. by text editors etc - with a wiggle suffix after being modified.

Just a safety feature, so you can always go back and reverse the changes).

---

### Post by engla on 2006-03-02
gedit and emacs both create these.
Any other editors that do it?

---

### Post by kel on 2006-03-02
Cheers guys.

I can understand them being useful if the original file is still on the disk, but I had a few of these for files that I'd removed, I'll just have to get used to it I suppose.

thanks again.

---

### Post by Q4U on 2006-03-02
You don't have to get used to it.

You can:
1. instead of passing rm - v example.file, you can pass rm -v example.file example.file~
2. reconfigure your application so that not to do this (although I consider it a bad idea)

Q4U

---


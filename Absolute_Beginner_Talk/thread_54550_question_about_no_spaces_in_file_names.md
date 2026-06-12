---
title: "question about no spaces in file names"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by tkteo on 2005-08-05
This is not an Ubuntu-specific question so I will ask it here.

While working in the Windows 98/2000/XP world, I somehow developed the habit of not inserting any spaces in file and folder names, although Windows apparently allows it. For example, Windows' default location for installation of software is /Program Files/ instead of /ProgramFiles/

Now I use programs like TeX (typesetting) and R (statistics). These applications recommend strongly against installing in folders and naming files with spaces inside, which like I stated is fine by me.

But I am curious. Why, from a non-Windows perspective, is "filename.ext" okay while "file name.ext" is not?

btw I heard that Windows vista will rename /My Documents/ to /Documents, etc. Good! No spaces in between! (well, for when I am dualbooting anyway).

---

### Post by Ampersand on 2005-08-05
When using a command line, a space is interpreted as the end of the filename. You can use spaces, but when using a command line, you need to either put the path in quotes (cd "~/my folder") or put a backslash before the space (cd ~/my\ folder). This could cause problems for scripts.

---

### Post by doclivingston on 2005-08-05
Using space in file name should work fine with most things, but there are some apps (and a lot of "weekend hack" scripts) that don't like it.

I've heard that the whole reason that MS used "My Documents" and "Program Files" was to force developers to fix their applications to deal with spaces in filename/paths.

---

### Post by Spano on 2006-02-16
Let me jump in on this.  Since a lot of my audio/video files were collected while I was using windows there are many spaces in my file names. "The Cramps - Can't Hardly Stand It" for example.  The seem to play fine in all the linux media apps I've used.
As I collect new files should I label them "Madonna_-_Like_A_Virgin"?
What do the experienced have to say?

---

### Post by theturner on 2006-02-16
As long as you don't use the command line or scripts, having spaces is fine.

I have a lot of spaces in my file names, but only for stuff in my home folder. When I install software to /opt, for example, I never put spaces in the file names there.

---

### Post by TeeAhr1 on 2006-02-16
Whitespace, as I understand it, is interpreted by the shell as the end of a name or command.  Thus, the command **gedit this file.txt** is read as "open the file named *this*, then open the file named *file.txt*."  Of course, this applies to commands as well.  (Note to wiser sages than I: is this accurate?)

I also got into the habit, very young, of never putting whitespace in names; I use underscores or dashes.  Learning basic computing skills on an Apple Deuce will do that to you ;)

---


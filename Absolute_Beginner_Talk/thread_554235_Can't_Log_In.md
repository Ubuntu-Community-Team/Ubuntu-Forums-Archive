---
title: "Can't Log In"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by starbright on 2007-09-18
Hi everyone,

well I finally got my Xubuntu working and things were going great, until two days ago :(. I was copying some files, and I realized that my disk space was low, so then I decided to delete some of the files, but they wouldn't go into the garabage can, and wouldn't delete. Some message poped up about not finding a file.  Then I rebooted my computer and tried to delete my files again, same message ( I don't remember the message as I was going to write it out but now I can't because...) Now today I tried to log in and when I did I got a message saying:

GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.

I can't log in at all! Is there any way to log in or delete some files?? Can I somehow fix this problem without loosing any files???? Is there any way possible to get into the computer at all??? I don't want to re-install everything as I finally have everything working the way I want it to.

HELP PLEASE!!!!

Xubuntu 7.04

---

### Post by Fidelio on 2007-09-18
Bump.
Help him out guys. This looks like an easy fix for someone who knows what they're doing. Not me, unfotunately.

---

### Post by DezSP on 2007-09-18
You might be pleased or slightly annoyed that this issue is set to be fixed for Gustsy. Anyway, when you get to the login prompt, press CTRL+ALT+F1 (or boot in recovery mode) to reach a terminal. Log in, and you'll be able to delete files with the rm command.

If you're unfamiliar with terminal commands:

Note that your password won't come up with asterisks. This is normal, just type it in and press enter

rm a-file.txt removes a file (immediately)
rm -rf directory/ removes an entire folder
cd directory/ switches to the specified folder
ls lists the contents of the current folder
~ is your home folder.

Don't run rm as root unless you know what you're doing!

---

### Post by starbright on 2007-09-20
Okay well...let's just say things didn't go as I wanted them to go.

I got into the terminal and such and wanted to delete a folder, so I entered 

rm -rf directory/

like DezSp had mentioned. Now for some reason that had not worked and I thought from the angle I was looking at the screen (probably not a good choice) looked like there was a space between 'directory' and the '/' so I put a space and it started to delete everything in my home folder. I mean in the end I was able to log in again since I had lot's of disk space, I just lost all of my files in my home directory and my bookmarks, and things like that. Good thing I had a back-up CD of all of my old 'important' files, so I just lost a few, but they are easy to find again. At least I still have all of my programs which I had installed.

So I don't know a real solution to the problem I had, since well, I deleted everything. :lolflag:

---


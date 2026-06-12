---
title: "Symlink / move directory"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-07-01
Hi everyone

I got Football Manager installed under wine, it works well!

Initially i wanted to install it to an external USB drive to save space, but it wouldnt install unless i put it in the home directory.

is there anyway to move the entire directory to the external drive now, and then make a link? (i know there is, im just curious on how to do it)

cheers

drowner

---

### Post by drowner on 2007-07-01
I think i've worked it out ;)

I want to move /home/drowner/.wine/drive_c/Program\ Files/ to /media/EXTERNAL/Program\ Files/

Some questions: 

1. Would the correct command be:

ln -s /home/drowner/.wine/drive_c/Program\ Files /media/EXTERNAL/Program\ Files\  ?

2. Can I then delete the contents of the original folder?

3. How do I undo the soft link if I ever change my mind?

---

### Post by drowner on 2007-07-01
So, i've tried it, and its not working. It wont make the link.

Any suggestions from anyone?

---

### Post by drowner on 2007-07-01
I'm getting an 'operation not permitted' error when i try and do it, or try and copy the files across. I don't know why.

---

### Post by lakris61 on 2007-07-01
I may be that wine has issues with symlinks, or that You don't "own" the directory on the EXTERNAL drive.
Have You tried it like this:
1. Make sure You have the correct permissions to the external media. Otherwise do this as root,
2. cd /home/drowner/.wine/drive_c
3. mv "Program Files" /media/EXTERNAL
4. ln -s "/media/EXTERNAL/Program Files" .
5. chown -R drowner.drowner "/media/EXTERNAL/Program Files"

You can remove the link and then move the folder back if it doesn't work.

---


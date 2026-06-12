---
title: "Another noob question, and some recommendations"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Antidisestablishmentarian on 2008-02-19
I am new to Ubuntu and Linux in general, and I have a questions and a problematic issue that I need help with. I would also like people's opinion on:
1. Whenever I try to use the sudo tool, I enter a line, and press enter. It says, [sudo]: password for ****. However, it doesn't let me type. If I press enter again, it lets me, but after a few seconds, even if I type the correct password, it says, that the password is incorrect. What do I do?
2. How do I unzip zip files and open rar files? I tried installing unrar, but I need to use sudo, and I have the problem above.
3. Can I have an opinion on which people like more, Gnome or KDE?
4. What is a good 3D first person shooter game for Linux?
Thanks!

---

### Post by neurostu on 2008-02-19
1. when you are typing in the password it doesn't display the text you type (or astrixes) this is so someone can't see how many letters you are typing, its a security feature.

2. try tar -xvzf <archivename.tar.gz> or open it using the GUI

3. I prefer Gnome, can't give you a good reason why though, I guess I'm just used to it

4. Enemy Territory is a free online 1st person shooter, kinda like counter strike

---

### Post by Hobo Joe on 2008-02-19
1. It won't show typed text, no matter what you type, nothing will appear. Just be sure to type carefully.

2. The default unpacking tool can open .zip files, and I think it can open .rar files as well, although I'm not sure.

3. I prefer Gnome.

---

### Post by S15_88 on 2008-02-19
the sudo issue i've never experienced so can't help you there...

in linux instead of "zipped" stuff there's tar balls that can be extracted.
to make a tarball:
tar czf filename.tgz text.txt c-program.c

to untar that:
tar xvzf filename.tgz

go with GNOME it's cleaner lighter i find KDE to be just a little toooo much, u can switch between the two if you want to get a feel for each.

first person 3d shooter game: open arena, i love that game haha it's awesome

---

### Post by Antidisestablishmentarian on 2008-02-19
Thanks! The sudo thing is working now. Also, thanks for your opinions!

---

### Post by jcanini on 2008-02-19
1.See above

2. "try tar -xvzf <archivename.tar.gz> or open it using the GUI"
      *man tar* - will give you a bit more info on the tar command 

3. Gnome has a simpler and more uniform layout, KDE is more customisable, I prefer KDE because of the K applications.

4. Open Arena is based on Quake and I have found it runs well.

Have fun.

---


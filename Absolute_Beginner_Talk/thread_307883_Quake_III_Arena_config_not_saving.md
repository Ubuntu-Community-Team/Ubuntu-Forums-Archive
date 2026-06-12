---
title: "Quake III Arena config not saving"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-11-27
Hi all - changes I make in Quake III Arena are not saved the next time I open the game. In Windows these are saved to a file called config.cfg. My guess is that a similar thing happens, but in Ubuntu I don't have automatic rights do just edit a text file the way I could in Windows.

Is this what is happening, and if so, how do I go about changing it?

Cheers

---

### Post by azkehmm on 2006-11-27
Without being an expert, I'd say that you'd either need to install the game inside your /home folder. This is where you have write privileges. Otherwise you might be able to create a launcher and start quake with a "sudo." I can't figure out how to do that right now though, but I'll look into it.

---

### Post by tribaal on 2006-11-27
Launching quake with sudo (as root) is not really a good idea. You shouldn't use sudo except when you really need it - to tweak system settings.

Make sure you have write access to the directory (or file) you're trying to write to. You might want to grant access to that file to you username using the sudo prefix this time, however :)

- trib'

---

### Post by daschmidty on 2007-05-27
it makes a directory ".q3a" in your home..chown this to yourself and it will work

---


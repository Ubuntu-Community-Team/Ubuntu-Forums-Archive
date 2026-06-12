---
title: "Starting/Stopping X-server"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-28
The GUI installed and has worked properly on my install from the beginning, however I'd like to start playing with it and I'm trying to figure out how to properly shut down the GUI.

I've found several commands on google that do not work and one in the man pages which also does not work "gdm-stop".

I found one suggestion to use ps and just kill the process, but I can't imagine that is a good way to close the GUI (plus there are alot of processes that appear to be 'X' or have 'gnome' in the name, and I dont know what order to kill them in)

Ctrl+Alt+backspace is also mentioned alot, but that only logs your account out, and doesn't appear to completely shut down the GUI.

---

### Post by white on 2006-09-28
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

That should do it, works with mine. :)

---

### Post by someonedumb on 2006-09-28
As I stated in my question "gdm-stop" does not work.


> someone@someone-desktop:~$ sudo gdm-stop
Password:
sudo: gdm-stop: command not found
someone@someone-desktop

---

### Post by someonedumb on 2006-09-28
Did you edit your post or did I just loose at reading comprehension o.O

---

### Post by white on 2006-09-28
Sorry, I edited it to the correct one. Was working on something, the post is correct now. :mad:

---

### Post by someonedumb on 2006-09-28
That works great, thanks :)

---


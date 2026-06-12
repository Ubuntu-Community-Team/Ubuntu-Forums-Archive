---
title: "That infamous delete everything code- does it ask for a password?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2008-03-05
So that code that's so horrible and deletes everying "RM -f / something.  I don't know what it is exactly.

My question is does it ask for a password?  Say my computer was in the library and I went up to get a book, could somebody run this command and delete my whole computer?

---

### Post by nutz on 2008-03-05
Yes, because you have to prefix that command with sudo. Otherwise it doesn't have the permission to do its dirty deed.

---

### Post by wieman01 on 2008-03-05
Unless you log in as root which by all means you should avoid. Apart from this, you are safe.

---

### Post by lswest on 2008-03-05
also, if you have a terminal open and have just run a sudo command, chances are, it won't ask for a password, however, you can play with the sudoers file so that it asks for a password every time...but, if you're planning on leaving your laptop unattended and you know of people who would know these kinds of tricks...just lock the screen before you go :P i have it bound to ctrl+esc for those times when i just don't trust anyone around ;)

---

### Post by hyper_ch on 2008-03-05
it will not ask for a password if you ahve given it not too long ago in the same terminal session. It will still be cached then and you will still be allowed to run that command.

---

### Post by mcduck on 2008-03-05
Depending on in which directory the command is run it can delete all your own files without asking for a password. (Of course anybody could do the same by just drag&dropping your files into trash and then emptying it..)

If the commad is prefixed with "sudo" it will ask for password and then happily delete eveything, both system files and your own files..

If you leave your computer unattended, lock it or log out.

---


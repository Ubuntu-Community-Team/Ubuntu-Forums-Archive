---
title: "i had an accident"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by GILBERTO15 on 2007-01-13
Yesterday i on xubuntu 6.10 on my ibook i was looking through file manager and i couldn't acess this file so i went to properties to enable the use "gil" to read and write so i shutdown the computer. i wake up the next day with this at after loggin in                      URL=http://img179.imageshack.us/my.php?image=mvc009sdi9.jpg][IMG]http://img179.imageshack.us/img179/8468/mvc009sdi9.th.jpg[/IMG][/URL]

"User's $HOME/.dmrc file is being ignored.  This
prevents the default session and language from being 
saved.  File should be owned by user and have 644 
permissions. User's $HOME directory must be owned
by user and not writable by otyher users."


i cant enter any session exept the terminal is there a command i can enter?

---

### Post by riven0 on 2007-01-13
Alright, when you get to the terminal try this:

> sudo chmod 644 /.dmrc


And see if that works at all....

I would say to do **sudo chmod a+x /.dmrc**, but I think that would give all users access to that file, right?

---

### Post by bodhi.zazen on 2007-01-13
sudo chmod 644 .dmrc
	sudo chown username .dmrc
	sudo chmod 755 /home/username
	sudo chown username /home/username

	OR, if that fails:

	sudo chown  username /home/userfolder 
	sudo chmod 755 /home/userfolder
	sudo rm -rf /home/userfolder/.dmrc

where username is your log in name and user folder is you home folder (also login name)

---

### Post by GILBERTO15 on 2007-01-13
its still showing the error

---

### Post by bodhi.zazen on 2007-01-13
What did you do ?

---

### Post by GILBERTO15 on 2007-01-13
when i type sudo chmod 644 .dmrc it show "chmod: cannot acess `.dmrc ': No such file or directory"

---

### Post by Rhubarb on 2007-01-13
Yeah I've had the same problem with my Xubuntu install - couldn't work it out so I just re-installed it.

---

### Post by riven0 on 2007-01-13
Make sure you're in the right directory. Type
> 
cd && ls -a

---

### Post by GILBERTO15 on 2007-01-13
i can login in back to xcfe session but there is nothing except a baby blue screen?

---

### Post by GILBERTO15 on 2007-01-13
did i lose everything all i see a baby blue screen after i login in the xcfe session

---


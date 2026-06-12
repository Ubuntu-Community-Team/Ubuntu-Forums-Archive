---
title: "Grsync backup of multiple folders"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by JBA2337 on 2008-04-13
I would like to use Grsync to backup files from my computer. I would like to backup the following directories (folders) in the same Grsync session:

/home/
/var/
/user/local/
/etc/

In Grsync, am I limited to backing up only one directory at a time, or is there a way to put multiple directories on the source line, so that I can back all of them up at the same time?

Thank You!

JBA2337

---

### Post by Het Irv on 2008-04-14
Using Grsync, I don't know.  But I do know of a program that is built to do what you want.  See QuickStart in my Sig.  I know that this doesn't exactly answer the question you are asking.

---

### Post by bbrozo on 2008-05-17
Grsync is just a front end gui for rsync. Create separate sessions for each directory you want to backup and then click the Simulation button for each one. The window that pops up will show the actual rsync command that will be run for the session. Copy the rsync commands for each session into a file (e.g. - a shell script) and just run the shell script to backup multiple directories all at once. Do a "man rsync" to see all of the options available to you beyond the grsync front-end gui.

---


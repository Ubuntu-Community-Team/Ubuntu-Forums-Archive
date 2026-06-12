---
title: "Can't copy and paste within my home directory"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by gcsmit on 2007-01-21
Hallo

I've been trying to get to grips with security in Ubuntu. I was under the impression that if I own a directory e.g.  "/home/myname", then anything under that directory belongs to me. I installed a Windows  program (Acemoney) under wine. I wanted to copy a file to  the "/home/myname/.wine/drive_c/Program Files/AceMoney" directory but got the error message "You do not have permission to write to this folder."

This is a bit of a sticking point. How do do I become the owner of this folder so I can write to it?

---

### Post by moshuptrail on 2007-01-21
I bet those directories are owned by root for some reason - possibly how wine was installed, but wouldn't know about that.

What I do know is how to check:
Open a terminal, then 
$ cd .wine/drive_c
$ ls -l

this will give a listing of all the files and directories on drive_c with ownership

to fix (and beware, I know little about wine so this could screw up wine)
$ cd
$ chown -R myname:myname .wine

where myname is your username

---

### Post by gcsmit on 2007-01-21
Thank you very much. It all worked like magic, except that I had to add the sudo command.

---


---
title: "Shell to Shell ??"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by raggit on 2007-02-08
Ok, it's been a while since I've been in the forum but, I do still need it at times.
I'm currently trying to connect to my webhosts shell using my terminal.  I know
there is someway to do it with the command line and an IP, username & pass etc etc.
I can't for the life of me remember what to ask google so I thought my 
best bet was to ask here.  Thanks guys

---

### Post by kebes on 2007-02-08
You're probably thinking of [ssh]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1"). Assuming that the remote server "blah.com" is running an SSH server, and you have an account "bob" on that server, on a commandline you can go:

ssh [email]bob@blah.com[/email]

It will ask you for the password. Once done, you will be logged in to a shell under username "bob" on that server. You can then issue whatever shell commands you want. If you want to transfer files, you can also use "scp" (secure copy), or "sftp" (file transfer over ssh), or "rsync" (which has an ssh option built into it).


Hope that helps.

---


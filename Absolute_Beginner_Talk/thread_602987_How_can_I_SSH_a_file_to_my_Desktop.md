---
title: "How can I SSH a file to my Desktop?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by kidKazam on 2007-11-04
Once I ssh to [email]user@server.com[/email] I can see my files and directories no problem. I can even copy and move files within my directories at server.com. The problem I'm having is copying a file from the server and pasting on my own computer in my home/user or home/user/Desktop folder. I think i might want to use scp? but I couldn't find a clear guide on doing what I need to do.  Thanks for any help

---

### Post by nrfool on 2007-11-04
Hi, there are two ways you might want to take:
1. cd ~/Desktop, then ssh to the server, then start sftp and use get command
2. Install and use gFTP, that will provide a gui way to do it,

---

### Post by Dr Small on 2007-11-04
```
man scp
```

---

### Post by Mawy on 2007-11-05
I looked at a few ways to do this and found this to be the easiest for me

Places > Connect to Server

Service type: SSH

filled in the information and works great! Creates an icon on the desktop just like ftp or other shares.

Cheers,
Mawy

---

### Post by lisc998 on 2007-11-05
To send a file to the remote host

scp <file> account@<remote host>:/var/tmp/<file> 

To copy a file off a remote host

scp account@<remote host>:/var/tmp/<file> .

And various combinations of the above.

---


---
title: "copy files on remote server (ssh)"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-12-23
I connect to remote server like this:

ssh -X st11@razor.... 
and then i write in my password.

The question is:

How do I copy files from my computer to that remote server?

---

### Post by p_quarles on 2007-12-23
SSH servers come with two file transfer applications built in: scp and sftp. Since you're using X forwarding, I'm guessing you want a graphical application, and the easiest thing is to use an FTP client that supports sftp. Filezilla does this, and I believe that gFTP does as well. The Firefox extension FireFTP can also be used.

---

### Post by baysl on 2007-12-23
I have gFTP installed. Can you help me connect...

Host: razor.fe....
Port: ?
User: st11
Pass: ....

This error accoured:

Looking up razor.fe.uni-lj.si
Trying razor.fe.uni-lj.si:21
Cannot connect to razor.fe.uni-lj.si: Connection refused

---

### Post by p_quarles on 2007-12-23
You need to set it to use the sftp protocol -- based on the error message you got, it's still set in normal ftp. I don't have that program on my machine, so I can't give you exact instructions, but look in the settings menus.

I do have FileZilla, though, so install that if you can't find the right setting.

---

### Post by baysl on 2007-12-23
It worked with SSH2.

Thanks for help!

---


---
title: "how to talk to debian web server"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Larry Grant on 2006-03-02
I administer a remote Debian / Apache web server which does not have X-Windows installed.  Currently I work with it from a Windows desktop using putty for a terminal emulator, and WinSCP for file transfer.  I have password authentication disabled on the remote web server, so I use private key authentication with Pageant running on my Windows desktop.

I would like to move from my Windows desktop to my Ubuntu desktop.  I want to leave the remote web server as-is (no X-Windows; password authentication disabled) and still be able to access a terminal shell on the remote server as well as transfer files using a GUI.

I'm thinking I would use ssh for a terminal emulater and Firefox for file transfer, but I'm not quite sure how to proceed, as far as setting up the private key, installing an "agent" (like Pageant), and getting Firefox to talk "scp".

Thanks!

---

### Post by Pragmatist on 2006-03-05
**ssh** can do everything.  You can read about it with ```
man ssh
```
check out the man pages for the other programs at the end of the ssh man page.  For example, reading the man page for **scp**

You can use **gftp** [http://www.gftp.org](http://www.gftp.org) for a graphical file transfer program. It also supports Secure Shell file transfers. You can install it via ```
sudo synaptic
``` just do a search in synaptic for **gftp**

---

### Post by az on 2006-03-05
Nautilus is a great ftp client.

Go - location:  [ftp://usrename:yourpassword@ftp.example.com](ftp://usrename:yourpassword@ftp.example.com)

---

### Post by Lary Grant on 2006-03-16
Yes, that worked great!  I didn't realize that Nautilus could do that, thanks.

---


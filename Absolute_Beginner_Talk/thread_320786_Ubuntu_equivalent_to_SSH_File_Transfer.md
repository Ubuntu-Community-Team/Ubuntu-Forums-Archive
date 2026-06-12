---
title: "Ubuntu equivalent to SSH File Transfer"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by suki on 2006-12-17
Is there an Ubuntu equivalent to [SSH File Transfer]("http://www.ssh.com/support/documentation/online/ssh/winhelp/32/file_transfer-3.html")?

I need to tranfer a load of information from a school server to my computer. Which means I'll have the address of the remote host computer and DNS address of the remote host. Then I'll be able to connect.

---

### Post by reiatzu on 2006-12-17
Use an FTPd or SCP.

---

### Post by scxtt on 2006-12-17
you can use scp (secure copy) or sftp (secure FTP) to connect to any host running (open)ssh ...

:> scp <file> <user_name>@<remote ip>:/<file>
:> sftp <file> <user_name>@<remote ip>:/<file>

---

### Post by compwiz18 on 2006-12-17
if you want a GTK program: gftp

---

### Post by bsell on 2006-12-17
> **suki said:**
> Is there an Ubuntu equivalent to [SSH File Transfer]("http://www.ssh.com/support/documentation/online/ssh/winhelp/32/file_transfer-3.html")?

I need to tranfer a load of information from a school server to my computer. Which means I'll have the address of the remote host computer and DNS address of the remote host. Then I'll be able to connect.

sftp <*username*>@<*IP address*> -log in
get <*filename*>-copy to directory (specify path)

---

### Post by Rippey on 2006-12-17
make sure you have a ssh client
open Nautilus
in location type: ssh://user@ip:port
when asked enter password

---

### Post by compwiz18 on 2006-12-17
> **Rippey said:**
> make sure you have a ssh client
open Nautilus
in location type: ssh://user@ip:port
when asked enter password
Or click the Places menu on the Gnome panel, and choose connect to server, choose SSH from the list.

---

### Post by scxtt on 2006-12-18
**fish** in konqueror is cool too

:p

---

### Post by steve.horsley on 2006-12-18
> **Rippey said:**
> make sure you have a ssh client
open Nautilus
in location type: ssh://user@ip:port
when asked enter password

This is fine, but it only works after you have connected to the server at least once using a command-line SSH. This is because the first time you ever connect, SSH gives you a message asking if you are sure this is the right server. If you answer "yes", that server gets entered into the known hosts list, and the queston never gets asked again. Nautilus doesn't seem to handle the case where the server is not known.

That said, nautilus is my preferred SFTP client.

---

### Post by az on 2006-12-18
> **steve.horsley said:**
>  Nautilus doesn't seem to handle the case where the server is not known.


Works fine for me...

---

### Post by steve.horsley on 2006-12-18
I take that back then. I just tried it (on Edgy), and got a popup window with the question. I admit it's been a while since I tried this (I'm in the habit of opening a command-line ssh first), so it could have been fixed for a while. Thanks, Azz.

---

### Post by Xappe on 2006-12-18
I find nautilus SFTP quite slow. So I suggest gftp for larger files...

---


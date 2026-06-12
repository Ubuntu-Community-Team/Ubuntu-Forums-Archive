---
title: "Simple Home FTP Server"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-01-16
I am really confused about the whole FTP process.

Basically I want to share some documents (large pdfs, VERY large adobe indesign files, etc) with some colleagues.

The only way right now is to use something like mailbigfile breaking the document into chuncks with something like rar.

I was wondering if I can use my computer to set up a VERY simple ftp server.

I don't understand the process, what programs I need, or even what a ftp server constitutes, security isn't a big issue. I just want my colleagues to be able to download very large files straight of my computer.

Help would be appreciated.

(running Gutsy)

---

### Post by amo-ej1 on 2008-01-16
well install and ftp daemon (e.g. proftpd), add a user that will own the files, set a password for this user and copy the files to that users home directory. There's nothing more to it. 

But you could also consider setting up a http daemon (installing apache2) so they can download the files using their browser ?

---

### Post by abhiroopb on 2008-01-16
Thanks,

is there a guide anywhere? And I would like it to be accessible using http.

---


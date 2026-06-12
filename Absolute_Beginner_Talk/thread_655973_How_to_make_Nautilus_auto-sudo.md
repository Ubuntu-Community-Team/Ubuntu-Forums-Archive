---
title: "How to make Nautilus auto-sudo?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-02
Two questions:

1. How can I make it so whenever I open up Nautilus, "sudo nautilus" is run as opposed to just "nautilus"?

2. I've set up an SSH server. On my Windows comp I'm using SSH Secure Shell to access my Ubuntu comp. Within the SSH Secure File Transfer (graphical FTP client) I'm unable to manipulate root permission folders/files; is there a way to change this in that program or within my Ubuntu server? 

THanks for the  help

---

### Post by kpkeerthi on 2008-01-02
> 
1. How can I make it so whenever I open up Nautilus, "sudo nautilus" is run as opposed to just "nautilus"?

You may want to **Create Laucher** by right-clicking on your desktop and type **gksudo nautilus** for **Command**.

---

### Post by iansane on 2008-01-02
oops uh yeah what he said. How do I delete a reply I didn't mean to submit?

---

### Post by zero-9376 on 2008-01-02
you may want to install the package nautilus-gksu which will add an option to the right click menu of nautilus to allow you to open a file/folder as administrator (root)

for the second issue, perhaps there is an option in your SFTP client to issue commands on login? if so maybe you can sudo -s to become root. alternatively you can enable the root account but that is not recommended. if you provide the name of your SFTP clients someone may be able to give you more specific help.

---

### Post by ~LoKe on 2008-01-02
> **iansane said:**
> oops uh yeah what he said. How do I delete a reply I didn't mean to submit?

Users can't delete their own posts, as far as I know.  All you can do it edit it and type "oops" or something, so people skip over it.

---

### Post by SOULRiDER on 2008-01-02
> **inktri said:**
> 
1. How can I make it so whenever I open up Nautilus, "sudo nautilus" is run as opposed to just "nautilus"?


Please, allow me to point out that unless you have a genuine reason to do this you REALLY shouldn't.

---

### Post by inktri on 2008-01-02
with gksu nautilus, iis there a way to have "Open as Administrator" always run upon double clicking a thumbnail?

---

### Post by Chayak on 2008-01-02
There are reasons you don't have write access to a lot of the system directories.  It's to keep you from killing your system with an accidental deletion or such.  Anything outside of /home is the system and if you don't know what you're doing it's not a place to be mucking around.

If you do insist on having it, keep good backups of your home directory, you'll probably need them.

---

### Post by zero-9376 on 2008-01-02
> **inktri said:**
> with gksu nautilus, iis there a way to have "Open as Administrator" always run upon double clicking a thumbnail?

not that i am aware of although once you are running nautilus as admin (open any folder as administrator) if you open a document/image/music you will be opening it as the administrator.

---

### Post by SOULRiDER on 2008-01-02
> **inktri said:**
> with gksu nautilus, iis there a way to have "Open as Administrator" always run upon double clicking a thumbnail?

Everything should be opened as root, which is a security risk.

---

### Post by bill_greene on 2008-01-02
> **zero-9376 said:**
> you may want to install the package nautilus-gksu which will add an option to the right click menu of nautilus to allow you to open a file/folder as administrator (root)

for the second issue, perhaps there is an option in your SFTP client to issue commands on login? if so maybe you can sudo -s to become root. alternatively you can enable the root account but that is not recommended. if you provide the name of your SFTP clients someone may be able to give you more specific help.

Thanks for the info about the package nautilus-gksu . Just what I was looking for :wink:

---

### Post by SOULRiDER on 2008-01-02
Its always useful to know about these packages. I like the one called nautilus-open-terminal (at least thats the name in the ArchLinux repos) It lets you open a terminal anywhere, it can be really useful!

---


---
title: "puTTY assistance needed"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2006-11-19
Hey, it's me again! New Ubuntu user stuck with 5.04 until my Dapper CDs come in by snail mail.

When I was operating off of Windows, the editor I used for editing my website ( camp.virtualventures.ca/~ksavich ) was puTTY. I had to access with a port  . . . 22, I think. Is there an alternative to puTTY for Linux, or a way to do this via a terminal?

---

### Post by David_T on 2006-11-19
Ya, that would be ssh.  (uses port 22)

From a terminal, just type ssh username@hostname.

---

### Post by Halfling Rogue on 2006-11-19
> **David_T said:**
> Ya, that would be ssh.  (uses port 22)

From a terminal, just type ssh username@hostname.


Awesome! You can use terminal to ftp stuff to a website server too, right?

---

### Post by David_T on 2006-11-19
> **Halfling Rogue said:**
> Awesome! You can use terminal to ftp stuff to a website server too, right?

If you just want to copy things to a website server, you can use the ftp command (type ``man ftp'' for info), or you could also use scp, which is a way to copy files via ssh.

---

### Post by Halfling Rogue on 2006-11-19
> **David_T said:**
> If you just want to copy things to a website server, you can use the ftp command (type ``man ftp'' for info), or you could also use scp, which is a way to copy files via ssh.

So . . . the command would be "ftp [filepath] camp.virtualventures.ca ssh"? Or "ftp [filepath] camp.virtualventures.ca 22"?

---


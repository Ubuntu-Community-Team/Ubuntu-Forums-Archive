---
title: "how to install new fonts when the file system is read only?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Bhante Santi on 2006-04-10
I just learnt that because the fonts folder is in the file system directory it's normally read only, so how can i paste new fonts into it?

A few minutes ago I learnt how to open an application with root privileges so that I can edit a file in the file system directory, but I can't do this to add fonts or can I? Is there not an easier way? Adding fonts is a very common thing and it doesn't need to be so secure does it?

Thanks, Bhante Santi.

---

### Post by hw-tph on 2006-04-10
Create a directory called  .fonts in your home directory and copy the fonts there. Either run **fc-cache -v** or log out and then in again to make the fonts available to your applications.


Håkan

---

### Post by Bhante Santi on 2006-04-10
[QUOTE=hw-tph]Create a directory called  .fonts in your home directory and copy the fonts there. Either run **fc-cache -v** or log out and then in again to make the fonts available to your applications.


Håkan[/QUOTE]

Thankyou very much.

---


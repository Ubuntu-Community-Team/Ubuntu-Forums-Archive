---
title: "Cannot open shared files"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by digTro on 2006-04-02
I'm trying to open a PDF file from a windows shared folder, but I'm getting a warning saying "Can't display location. Now, if I copy the file into my Home folder, I'm able to open it. Am I missing something? :confused:

---

### Post by catlett on 2006-04-02
Are you typing a command to open the file or are you just double clicking on it? Do you mean you can't open it when it is in the original location but if you copy it to /home you can open it?

---

### Post by adamkane on 2006-04-02
Many applications can't browse a samba share and open a file. 

That is Nautilus can see the file on the share, but the pdf reader can't access the share. 

If you want to open files on shares, then you need to mount the share. The mounted location will be:

/media/sharename/document.pdf 

which is easy to browse, rather than this, which is a network share:

smb://192.168.0.x/sharename/document.pdf

and is difficult to browse for most applications.

---

### Post by digTro on 2006-04-03
I was not using the command to open the file. I double clicked it. I will try mounting the share folder when I go home (I use Ubuntu at home). Thanks for your patience!!

---


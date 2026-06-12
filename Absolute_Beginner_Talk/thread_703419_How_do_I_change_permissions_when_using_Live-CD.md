---
title: "How do I change permissions when using Live-CD?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by jonw-999 on 2008-02-21
Apologies for the 'dumb newbie' question, but is it possible to change the permissions just by using the GUI, without having to use the command line, when you are running off of a Live-CD?

Explanation:  My Windows computer crashed, and I'm trying to use an Ubuntu Live-CD as a 'rescue disk' to transfer some files from the internal hard-drive to an external, USB hard-drive.  But in order to do that, I need to make the external drive writeable, and of course, I want to be sure that the internal hard-drive stays Read-only.

I don't have enough experience with Linux to feel comfortable mucking around with command lines -- especially as Root -- unless I really, really have to. The last thing that I want is to accidentally overwrite the files that I'm trying to save!

Thanx in advance,   jonw.

---

### Post by freelinuxhelp on 2008-02-21
You can change permissions by right-clicking the file and going to properties.
I don't think you can use the Linux style permissions on an NTFS filesystem though.

You can mount a hard drive read only.
sudo mount -r -t filesystem /path/to/device /path/to/directory

---

### Post by louieb on 2008-02-21
Just a suggestion get a [Knoppix Linux]("http://www.knoppix.net/") live CD.  For copying stuff off to an external drive its the easiest I've found. Just right click on the desktop icon for that partition. There are options to mount it read only or read/write.

---

### Post by jonw-999 on 2008-02-21
Thanks for the reply.    I understand that I can get to 'permissions' by right-clicking, etc.

But the problem is that the external hard-drive belongs to 'root' and so it won't let me change the permissions.   So I guess my question is:  How do I make myself 'root' from within the graphical interface, without having to get involved in command-line syntax?

Or, if that's not possible, can I go into a terminal mode just long enough to make myself 'root', and then go back to the GUI to do the actual changing of permissions?

TNX again.

---

### Post by freelinuxhelp on 2008-02-21
Sorry I didn't get your meaning right off. I don't think you can get a blanket root permission for the GUI when using the Live CD.
You could drop to a terminal, run sudo nautilus
that would give you a file manager with root priviliges.

---

### Post by jonw-999 on 2008-02-21
OK,  running  " sudo nautilus "    seems to have solved my problem!!

Thanks for the advice.

---

### Post by freelinuxhelp on 2008-02-21
You're welcome. :-)
Please mark the thread solved so that other users can find solutions easier.

---


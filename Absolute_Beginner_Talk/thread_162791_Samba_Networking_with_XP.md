---
title: "Samba Networking with XP"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-04-19
Hello

I finally got it so that I can see my linux box and the shared folder on it from my xp computer. I am trying to transfer music over but when I paste in the files from windows into the shared folder in ubuntu, I get a no permission or in use error. On the properties of the shared folder I have "read only" unchecked.

Any suggestions????

---

### Post by johnny2211 on 2006-04-19
I don't know how to set it up in the graphical interface, but...

Go to "/etc/samba" and edit smb.conf file. At the end you should see a section describing your shared folders. Verify that read only option is set to no.

The other reason could be the folder permisions on the file system itself, just go to that folder and set the permissions. In the console you can do it like this:

chmod 777 -R name_of_folder

It is probably one of those two.

---

### Post by rubrboots on 2006-04-19
Thanx johny2211

It was the folder permissions=D>

---


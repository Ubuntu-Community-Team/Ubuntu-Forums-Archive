---
title: "VSFTPD user?"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-27
How would I go about adding a new user to VSFTPD do that I could upload stuff to the server from college?

Thanks

---

### Post by Jimmey on 2006-01-27
I didn't know where else to ask, as the #vsftpd is always empty, lol.

---

### Post by BenTyreman on 2006-01-27
The easiest way for me was to add a new user to the system. I then fired up /etc/passwd, found the new user, and changed the default shell from /bin/bash to /bin/false. This should prevent the user account from doing anything, except being used for authentication by VSFTD.

---

### Post by Jimmey on 2006-01-28
Oh, so, if I went onto the server from another computer, and chose to enter with a username and password, and used the username and password of this computer, would that allow me to upload stuff?

---

### Post by BenTyreman on 2006-01-28
I think there's a few settings that need to be changed in the configuration file. Off the top of my head, you need to set local users. I also enabled a list of people allowed to ftp and enabled chroot, which locks them into their home directory.

---


---
title: "gcc and sudo root"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by linuxnoob43 on 2006-07-31
Hi there,

Just managed to installed Ubuntu, as a n00b can someone please help me with getting gcc....apparently i need this to compile applications into installers, specifically i'm looking to install the mp3 player xmms.

Also, can someone please help me switch to the root user, it asks for a pwd then it says sorry, access denied or something. I don't recall setting up a root user account password....:confused:

---

### Post by Titus A Duxass on 2006-07-31
Search the wiki for information about root and sudo.
For gcc, you need to get build-essential.

---

### Post by T700 on 2006-07-31
See my sig for the link "Where's Root".  Short answer:  There is no root account by default in Ubuntu.  To access things as root, you preface the command with "sudo" for non-graphical apps or "gksudo" for the graphical ones.  The password is your normal, log on one.

Paul

---

### Post by zappafrank on 2006-07-31
there's no root account by default, but you can aquire superuser privileges with sudo, providing your normal users' password.

for installing xmms try: 



sudo apt-get install xmms

---


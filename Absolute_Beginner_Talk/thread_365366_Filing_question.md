---
title: "Filing question"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by paker on 2007-02-19
Will someone kindly guide me how filing works in Ubuntu from ex-Windows user's perspective? When I view a pdf file, it gets downloaded to desktop. Do all files go to desktop?

I want to store 2006 tax documents in a separate folder. Desktop or JohnDoe (my user name)? What do I keep in "my user name?"  What is File Systems? Thanks.

---

### Post by kanha on 2007-02-19
check your firefox preferences (edit----->preferences)
on main tab check the box
ask me before download
or you can set default download folder in same windows
check out

---

### Post by IYY on 2007-02-19
Ultimately, the way your organize your files is up to you. A common way of doing it is this:

1. The desktop, like a real-world desktop, is used for files you are currently working on, or that have been recently downloaded. Once you are done working on the files, you can move them to a storage location. By default, all files get downloaded to the desktop.

2. The home folder itself contains directories for various categories. I created directories called Documents, Images, Music and Programs. You can place your files there for storage.

3. The filesystem is for system files that effect all users and should be edited by the administrator only. Configuration files reside in the /etc directory, program executables reside in /usr/bin, icons usable by all users are stored in /usr/share/icons, etc. 

4. The /media directory is used to mount media like floppy disks, CD-ROMs, other hard disks, iPods and so on.

5. The /tmp directory is for temporary files. It gets cleared once the system reboots, so don't put anything important there. When in Firefox you select 'Open' instead of 'Download', the file is downloaded to /tmp. I use /tmp to do quick tests when writing shell scripts, but many users never touch it by themselves and leave it for programs to use it.

---

### Post by paker on 2007-02-19
Many thanks.

---


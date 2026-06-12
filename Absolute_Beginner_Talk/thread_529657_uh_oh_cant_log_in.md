---
title: "uh oh cant log in"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by rutilajw on 2007-08-19
so its a stupid mistake but i accidentally mounted an .iso file to my home folder therefore overwriting everything else and now i cant log in because of some kind of file missing error or something.

basically im wondering if there is a way to undo what i just did through logging into the terminal and some kind of command line stuff.

thanks.

---

### Post by Happy_Man on 2007-08-19
....no. You will have to reinstall from a CD.

---

### Post by jamvegan on 2007-08-19
If all you did was *mount* the file to your home folder, then it would not have actually over*written* anything.  It's just hiding it.  How did you mount it?  If you didn't add it to /etc/fstab, then rebooting should fix the problem.

---

### Post by rutilajw on 2007-08-19
sudo mount -t iso9660 -o loop /path/to/file.iso /path/to/mountpoint

that is the code that i used

EDIT: fixed. no idea how it worked, but just rebooting fixed everything.  so strange, i checked for hidden files before i posted this problem and there were none, my /home was completely gone. i restarted x and i couldnt get back in. but just rebooting and everythings back to normal.

---

### Post by sumguy231 on 2007-08-19
To explain, mounting the .iso didn't actually touch your hard drive, it just changed which drive got to be your home directory. But rebooting undoes that, since it checks a file which tells it where to mount things.

---


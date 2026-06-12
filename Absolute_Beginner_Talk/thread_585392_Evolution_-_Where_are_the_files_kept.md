---
title: "Evolution - Where are the files kept?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by hodad on 2007-10-21
I am planning to upgrade to 7.10, and want to save my email, in order to restore later.  I know how to back up the files (from other posts), but don't know where they are kept.  I thought they were in /var/mail, but they aren't.

Anyone know where they got to??

Thanks

---

### Post by Pumalite on 2007-10-21
At the Terminal:
locate evolution

---

### Post by BackwardsDown on 2007-10-21
I dont have ubuntu installed at the moment so I can't check but they need to be somewhere like:

/home/_user_/.evolution/

or in the .gnome folder:
/home/_user_/.gnome/evolution/
/home/_user_/.gnome/apps/evolution/
/home/_user_/.gnome/somethingelse :)

---

### Post by sas on 2007-10-21
The mail is in .evolution/mail (note the leading .), press ctrl + h  in the file manager to see all hidden files.

---


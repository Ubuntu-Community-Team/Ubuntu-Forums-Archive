---
title: "Softlinks"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by xtek on 2006-10-14
Argh I feel like a dork for asking this, but is there a way to remove a softlink that links 2 directories.

I was trying to setup a mail server and had to follow 2 different howto's and somewhere I linked the folder /var/www to show the contents of /usr/share/phpmyadmin. I need to remove that link so that the default page that is loaded when going to my url will not be the login for phpmyadmin.

---

### Post by kidders on 2006-10-14
Hi there,

Just delete it :-)

```
rm /var/www
```

**Edit:** Deleting /var/www will break your web server ... remember to do an **mkdir /var/www** afterwards.

---

### Post by xtek on 2006-10-14
Won't that remove the directory or the contents there of?  I will still need access to the /var/www dir when I finally get squirrelmail working.

---

### Post by kidders on 2006-10-14
If /var/www is a symlink, deleting it just removes the symlink, not the directory it's linked to.

**Edit:** Chances are you have will have needed to delete the /var/www directory to create the symlink in the first place :-(

Hope that helps.

---

### Post by IYY on 2006-10-14
No, it won't remove the parent directory. For example,

```
ilya@muddy:~$ ln -s /tmp/
ilya@muddy:~$ rm tmp

```

---


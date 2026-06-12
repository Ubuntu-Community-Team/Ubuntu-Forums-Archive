---
title: "apache group to create file"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2007-06-26
im thinking this is a rather basic question regarding file permissions.

im writing a php script that outputs some svg to a new file.
however im getting errors that i cannot create files.

i read this has to do with the config of apache and its permissions.
where can i look to find the permissions of apache and/or change them?

apache does not have an entry under system -> admin -> users & groups


thanks!

---

### Post by az on 2007-06-26
> **xolot1 said:**
> im thinking this is a rather basic question regarding file permissions.

im writing a php script that outputs some svg to a new file.
however im getting errors that i cannot create files.

i read this has to do with the config of apache and its permissions.
where can i look to find the permissions of apache and/or change them?

apache does not have an entry under system -> admin -> users & groups


thanks!

The web server uses the www-data user.  If you want php to write to a directory, the directory has to be writeable by that user/group.  Do not chown all of /var/www to www-data, since that is a security risk, just the folder you need.

---


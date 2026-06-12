---
title: "[SOLVED] mysql question"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Repus on 2007-09-25
[LIST]
[*]I have mysql running.
[*]There are several dbs that are active. gallery, joomla, drupal, several others
[*]I have had little direct input to their creation or maintenance.( it has all been through various install scripts etc.)
[*]I now would like to install wordpress but I cant because I dont actually know anything about my mysql install. eg a user who has access to it. how to set up a db .
[/LIST]
please advise.

---

### Post by hyper_ch on 2007-09-25
Install phpMyAdmin - it's in the repos - that's a simple tool to administrate your mysql dbs/users from a webinterface.

---

### Post by Repus on 2007-09-25
Thanks for the response.

I installed phpmyadmin. First thing it does is ask for username and password. Mine does not work and there are no other users on the system.  So Im sorta back where I was, Only now I have a web interface.

Any ideas?


EDIT:
wait username root grants access. thanks for the phpmyadmin recommendation.

---

### Post by hyper_ch on 2007-09-25
well, upon instalaltion of mysql-server did you also set a root password? If not run this:

```

sudo mysqladmin -u root password yourrootsqlpassword

```

That will add yourrootsqlpassword to the userlist and then you can connect to mysql server through phpMyAdmin with "root" and "yourrootsqlpassword".

---


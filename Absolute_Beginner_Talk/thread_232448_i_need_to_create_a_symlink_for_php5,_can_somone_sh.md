---
title: "i need to create a symlink for php5, can somone show mw how?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Hawkowl on 2006-08-08
I have found that there i no reference to php in my mods-enabled or mods available folders inside apache2.

Php seems to be installed..(iit has a folder in /etc :)

But really i don't know.

I have tried to install a phpbb2  web forum, but it doesn't work. it says this 
```

error 404
the requested URL /Ballistic/phpBB2/install/install.php was not found on this server.
```

could someone please walk me through a symlink for php?

all help appreciated.

---

### Post by mlind on 2006-08-09
Is php5 module currently enabled?
```

sudo a2enmod php5

```

---


---
title: "How to RunAs another user"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-02-02
I'm running under my main ubuntu user account. For security's sake, I've offloaded some of my documents to another user account, whose group I will eventually be removing my main account from.

Until then, I find it annoying to have to chown and chgrp every file I create in nautilus from my main account to this other account.

Is there any command that lets me run terminal or nautilus as if it were by this other user? Sort of like how "sudo bash" lets you do things as root, or "gksu nautilus"

---

### Post by spiderbatdad on 2008-02-02
sudo su should do it.

---

### Post by pteri498 on 2008-02-02
Close, but that's not exactly what I'm going for.

I'm not looking to run as root, I'm looking to run as a different user that I've called "webadmin"

So far my best luck has been ssh'ing to myself, but then I lack the faculty of nautilus.

---

### Post by spiderbatdad on 2008-02-02
then you will have to switch user and log in under the other account.

---

### Post by Zack McCool on 2008-02-02
> **pteri498 said:**
> Close, but that's not exactly what I'm going for.

I'm not looking to run as root, I'm looking to run as a different user that I've called "webadmin"

So far my best luck has been ssh'ing to myself, but then I lack the faculty of nautilus.

su is what you want.

```

su - webadmin
[enter password]

```

su is "switch user", the dash means use the login shell (sets everything up as you were fully logged in as webadmin), then the account name.

You could also do a sudo -u weblogin nautilus to run nautilus as weblogin.

Or, even gksu -u weblogin nautilus

Pick your poison...   ;)

---

### Post by pteri498 on 2008-02-02
> **Zack McCool said:**
> su is what you want.
You could also do a sudo -u weblogin nautilus to run nautilus as weblogin.

Or, even gksu -u weblogin nautilus

Pick your poison...   ;)

Oooh, so close!

```

$ sudo -u webadmin nautilus
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.

```

Don't know exactly what's wrong there.
BUT, I can use su - webadmin successfully, so that's a great step forward. Thanks!

---

### Post by spiderbatdad on 2008-02-02
take a look at ```
man su
```

---


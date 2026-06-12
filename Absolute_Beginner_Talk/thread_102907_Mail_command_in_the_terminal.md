---
title: "Mail command in the terminal"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by grte on 2005-12-13
Okay, apparently there's a mail command in the terminal, that you can use to send the results of something to an address.

However, checking on the mail command, I get:

```
mail
bash: mail: command not found
```

What am I missing, here?

---

### Post by Mustard on 2005-12-13
I know of mutt and pine (both are installed via synaptic), but I wouldn't know how to use them to send mail via the internet.  I use them for reading messages that the system sends to my local user mail address.

---

### Post by thezerogroup on 2005-12-14
I love pine, it is by far my favorite email client.

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=grte]Okay, apparently there's a mail command in the terminal, that you can use to send the results of something to an address.

However, checking on the mail command, I get:

```
mail
bash: mail: command not found
```

What am I missing, here?[/QUOTE]
The "mail" program is part of the "mailx" package on my system:
```

$ type mail
mail is /usr/bin/mail
$ dpkg -S '/usr/bin/mail'
mailx: /usr/bin/mail

```

---


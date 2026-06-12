---
title: "Where does the hostname go in the /etc/hosts file?"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by chopper81 on 2006-08-09
I am trying to ad my host name back to my system. The error that I get upon start up says that I should add the hostname to the file /etc/hosts. I just dont know where to ad it at.
chopper81

---

### Post by dusu on 2006-08-09
The first line of my /etc/hosts file reads :
127.0.0.1 localhost.localdomain localhost NAME

where NAME is the name of my machine.

I hope it helps

---

### Post by chopper81 on 2006-08-09
I was missing that. I tried to put the hostname in there but it said that I did not have permission. Ant idea how I would get that permission?

---

### Post by dusu on 2006-08-09
don't forget to edit the file with a sudo command. Let's say you're using emacs, then type : sudo emacs /etc/hosts

---

### Post by chopper81 on 2006-08-09
I tried that and it did not work eithor. Thank you for your time. Back to the books and code I guess. Good day.
Chopper81

---

### Post by huygens on 2006-08-10
> **chopper81 said:**
> I tried that and it did not work eithor. Thank you for your time. Back to the books and code I guess.

Perhaps, did you check if the file wasn't read-only? I do not know how to force the save with emacs, but you could try to follow this (the dollar sign only represent what is called the shell prompt, it just indicates the beginning of a new line, do not enter it when typing the commands):```
$ sudo chmod u+w /etc/hosts
$ sudo emacs /etc/hosts
*    And once you're done editing under emacs, and you exited from emacs:*
$ sudo chmod u-w /etc/hosts
```Hope this help,
Huygens

---

### Post by MrHorus on 2006-08-10
> **chopper81 said:**
> I just dont know where to ad it at.
chopper81

It's a LOT easier to use the hostname command :)

```
hostname <hostname>
```

---


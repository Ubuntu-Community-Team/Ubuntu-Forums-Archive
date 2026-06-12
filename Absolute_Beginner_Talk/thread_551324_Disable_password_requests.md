---
title: "Disable password requests?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by hiloguy on 2007-09-15
Is there a way in Feisty to disable the password requirements?  Nobody else uses my computers, so it's just a nuisance to have to enter my password every time I open the lid or go into any admin tasks.  Not a big deal, but if there's a way, I'd go for it.

And yes, I have read the other postings on this topic, but I have no issues with security.  I don't lock cars, either.  The computer on which I'm learning Linux has nothing on it anyone would want to "steal."

So as I said, if it's an easy fix, Ill go for it.  If not, it's just fine the way it is.

Aloha!

---

### Post by alienexplorers on 2007-09-15
Go to system>administration>security and select auto login.

---

### Post by jordanmthomas on 2007-09-15
Look up information about editing /etc/sudoers (visudo)
```
sudo visudo
```
If you read the file, it should make itself obvious.  If it doesn't, find this section:
```

# Same thing without a password
[COLOR="Red"]#[/COLOR] %wheel	ALL=(ALL) NOPASSWD: SETENV: ALL

``` and take out the hash mark I've colored red.

and you can set up gdm to not require a password to log in.
system --> administration --> login window (somewhere in there)

**edit** forgot to mention the obligatory DON'T DO THIS IT'S INSECURE nonsense that always seems to flood these types of threads.  (Security isn't only about stealing information, though and your computer could become a zombie used to attack other people, so there are valid concerns.  I'm not here to preach though.)

---


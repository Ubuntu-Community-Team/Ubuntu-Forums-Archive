---
title: "Error Message after Log-In"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-11-03
I installed Beryl yesterday and it works a dream. I finally get all the transparency my little heart desires.

But after I log-in, I get the following error message. I can just click ok and everything seems to work fine. Fortunately the best way to learn about an OS, is by solving errors, so here goes.

> USER's $Home/.dmrc file is being ignored. This presents the default-session and language from being saved. 
File should be owned by user and have 644 permissions. Users $Home directory must be owned by User and not writable for other users.    

This message appears after I have entered my password before my desktop loads. 

Currently as I said, I do not find any hindrance from this after clicking it away but I might get confronted by other errors later on.

---

### Post by mtron on 2006-11-03
try from a terminal:

```
sudo chmod 664 /home/*username*/.dmrc
```

if this does not help there might be a wrong file ownership. Try correcting it with:

```
sudo chown *username:groupname* /home/*username*/.dmrc
```

if you didn't change it ubuntu uses the same user/groupname.

---

### Post by Belgatom on 2006-11-03
Tried both lines above without succes. 

Even tried the first line with 644 instead of the 664 you wrote because the error spoke of 644. But that didn't work either.

In the Gui the permissions look like this:

[IMG]http://users.telenet.be/belgatom/ubuntu/Screenshot.png[/IMG]

---

### Post by Belgatom on 2006-11-06
Lil' update:

Had a look round on the forum and found [this]("http://ubuntuforums.org/showthread.php?t=72988") thread. Executed the advise in the terminal:

> chmod 700 ~

And hey presto, solution.

Little question afterwards so I can learn something:

What does the .dmrc file actually do?

What could have caused this?

What does chmod 700 ~ actually do?

What does the "~" refer to?

---

### Post by Tamil on 2006-11-06
> **Belgatom said:**
> What does chmod 700 ~ actually do?

 Modifies permission to home directory with read, write & execute permission for user & nothing for group and others.

See [http://www-128.ibm.com/developerworks/aix/library/au-speakingunix4/index.html](http://www-128.ibm.com/developerworks/aix/library/au-speakingunix4/index.html)

> What does the "~" refer to?Your home directory.

---


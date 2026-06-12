---
title: "[SOLVED] simple chmod question"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-06-30
Hi,

I am very new to Linux (a couple of weeks) and although I have browsed through some chmod documentation, I still cannot figure out how to do the following simple thing..

Suppose I have three users in my machine: user1, user2, user3

How can I make the contents of a folder in user1, available (read,write and execute) to user3 only (so user2would no be entitled)?

I am particularly interested in how to do this *without* using sudo or root but just logged in as user1 and from the terminal because I want to replicate it when using my University's account.

thanks,

---

### Post by hyper_ch on 2007-06-30
well, the files have three premissions: owner, group, world...

you can't put two users as owner but you can put two users into the same group.

So the simplest would be to change the group ownership of that file to the group user2 is in and make it rwx.

e.g. assume user2 has also a group named "user2" then you could do this:

Changing the group
```

sudo chown -R jdrodrig:user2 /path/to/dir

```

Making it rwx for user2 group:
```

sudo chmod -R 0775 /path/to/dir

```

---

### Post by jdrodrig on 2007-06-30
thanks for the quick reply...but is there anyway to do this without sudo? I want to also do it in a computer that has user1 (jdrodrig) and user2 among hundreds of users and of course I do not have sudo or root privileges.

---

### Post by annda on 2007-06-30
> **jdrodrig said:**
> 
I am particularly interested in how to do this *without* using sudo or root but just logged in as user1 and from the terminal because I want to replicate it when using my University's account,

you HAVE to have root privileges to change ownership of files (the simple way) or modify user groups (the right way).

---


---
title: "User File Structure Edit"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by zitro62 on 2008-03-25
I've got SAMBA up and running just the way i want, but I noticed that every new user has a shortcut to Examples...

So my questions:
 how can i remove that shortcut from all new users AND is it possible to add my own files so that every new user would have a pre-determined file structure with a few actual files

I say actual files because the examples folder is a shortcut. id like my users to actually "own" the files...

I'm new to linux users and all... so i hope i was clear

thanks!

---

### Post by feanil on 2008-03-25
take a look at
```
man useradd
```

the -m option is what you want to read.  Essentially there is a skeleton directory that is used to create the home directory.  If you remove the symlink from that directory then new users will not have that symlink anymore.

---

### Post by drubin on 2008-03-25
> the -m option is what you want to read. Essentially there is a skeleton directory that is used to create the home directory. If you remove the symlink from that directory then new users will not have that symlink anymore.

Nice to know, My question is where did my "Documents" "Desktop" "Videos" "Templetes" "Music"..... Folders come from??

Not to steal the thread but is related

---

### Post by feanil on 2008-03-25
I think that is something that happens when you add users through the users-admin interface that Ubuntu uses.  I did a command-line useradd -m and it did not produce those directories for me.  It did produce the symlink since that is in my skel directory.

---

### Post by drubin on 2008-03-25
> Re: User File Structure Edit
I think that is something that happens when you add users through the users-admin interface that Ubuntu uses. I did a command-line useradd -m and it did not produce those directories for me. It did produce the symlink since that is in my skel directory.

I mean this isn't really the bigest deal, but while we were on the topic. :) thanks for clearing that up

---

### Post by feanil on 2008-03-25
Hmm, I'm curious about that as well, when I created a user with the GUI it did not create those folders either. They were created when I first logged in as the new user.  I wonder how this can be prevented.

---


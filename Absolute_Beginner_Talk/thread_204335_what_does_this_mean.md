---
title: "what does this mean?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-06-26
i get this message on start up "User's $Home/.dmrc file is being ignored. this prevents the default session and language from being saved. file should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by others"
how do i fix this? would this make me have to re-enter my (dns) numbers in networking as i have to do every time i re-start? thank you.

---

### Post by taurus on 2006-06-26
Hold down <Ctrl><Atl>F2.  Log in to a console and type
```

sudo chown <your loging name> .dmrc
sudo chmod 600 .dmrc

```
Now, see if you can log into a window manager again...

---

### Post by abu-fatu on 2006-06-26
i am able to log in into gnome. and everything works save for me having to re-enter my dns numbers to get on line.

---


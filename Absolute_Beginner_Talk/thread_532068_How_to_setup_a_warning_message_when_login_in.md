---
title: "How to setup a warning message when login in"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mtime2457 on 2007-08-22
Can someone tell me how to setup a warning message when someone logs onto to a server?

---

### Post by asmoore82 on 2007-08-22
graphically or remote ssh login?

---

### Post by mtime2457 on 2007-08-22
remote ssh login

---

### Post by asmoore82 on 2007-08-22
I'm sure there is a better way but a quick hack would be to
edit that person's $HOME/.bashrc file and add something like this to the end of it...

```

#.bashrc

...

echo "Welcome to $HOSTNAME"
cat << ENDMOTD

Do not cause mischief and
Please keep your Password a Secret!

ENDMOTD

# End of File
```

---

### Post by Dr Small on 2007-08-22
What kind of warning message?
You can use motd and issue.net for a server message and a banner.

Dr Small

---

### Post by mtime2457 on 2007-08-22
Sorry I just needed to walk away and come back.  I just needed to  edit the /etc/motd file.....  But when I checked I couldn't find it.  Thanks for all the replies.....

---


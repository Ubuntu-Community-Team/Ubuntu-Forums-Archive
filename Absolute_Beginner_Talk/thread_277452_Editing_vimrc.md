---
title: "Editing vimrc"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by navneeth on 2006-10-14
Hi,
 I want to enable syntax highlighting through vim. I can "uncomment" the line 'syntax on' in the etc/vimrc file, but it happens to be a Read Only file, and so, I'm not able to save it. How do I save the file? Any help would be appreciated.

---

### Post by taurus on 2006-10-14
Are you talking about /etc/vim/vimrc?  Then do

```
gksudo gedit /etc/vim/vimrc
```

---

### Post by navneeth on 2006-10-14
Yes, that's the one I was talking about. Thanks. :)

Btw, this popped-up after I typed that...
```
(gedit:6928): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Something to worry about?

Also, the prompt's missing.:confused:

---

### Post by taurus on 2006-10-14
That is just a warning.  Don't worry about it!!!  Once you are done and saved your work, you will get your prompt back.  Otherwise, do

```
gksudo gedit /etc/vim/vimrc &
```

---

### Post by junglepeanut on 2006-10-14
I edited 

.vimrc 

in my home folder to enable syntax highlighting with

:syntax enable

---


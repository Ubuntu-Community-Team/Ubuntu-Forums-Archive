---
title: "File Permissions"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-19
Hello,

I am trying to change the file permissions on the file 'own.sty' to allow me to edit it.
This is what I did:

bernard@bernard-desktop:/usr/share/texmf/tex/latex$ chmod ugo+rwx own.sty

chmod: changing permissions of `own.sty': Operation not permitted
bernard@bernard-desktop:/usr/share/texmf/tex/latex$ 

How can I rectify that please.

Thanks


Bern

---

### Post by Inxsible on 2007-11-19
that file is not in your home directory. So you need to sudo it```
sudo chmod ugo+rwx own.sty
```

---

### Post by duruttye on 2007-11-19
Well, I'm not sure what that file is, and modify it, ONLY IF U KNOW what you are doing.

Try to add the sudo command at the beginning of that command, that will give you root permissions.

Only if you know what you are doing.
Hope it helps.

---

### Post by bern1939 on 2007-11-19
Thanks to you both. That works fine.
Out of interest the file is one I wrote myself to contain various commands that are
used in drafting documents in Latex.

Thanks again


Bern

---


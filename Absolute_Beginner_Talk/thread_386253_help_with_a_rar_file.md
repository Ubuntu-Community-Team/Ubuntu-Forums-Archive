---
title: "help with a rar file"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-16
guys i downloaded theme but its a file i cant open .. can you tell me what this file is.. 

.cgwdtheme

what package/software should i download ?

---

### Post by diepruis on 2007-03-16
If it's a rar file install unrar-free and read the docs for it. Skimming the man page will tell you what you need to do.

```

sudo aptitude update && sudo aptitude install unrar-free
man unrar

```

EDIT: Forgot to add, you have to copy and paste those commands in the Terminal.

---

### Post by HunkieChan on 2007-03-16
im not sure if its a rar file but thats the extension..

---

### Post by Kateikyoushi on 2007-03-16
You need the universe repos to install it, and you can search for programs in synaptic.

---

### Post by jbayone on 2007-03-16
the archive manager handles most compressed files, so you should just be able to double-click on the file.

nevermind, sorry

---

### Post by HunkieChan on 2007-03-16
thanks bro..

---

### Post by diepruis on 2007-03-16
> **HunkieChan said:**
> im not sure if its a rar file but thats the extension..

Linux doesn't use extensions to identify files, it uses the file header.

You can check the real file type by using the "file" command in the terminal.

The file manager should show the file type as well.

---

### Post by HunkieChan on 2007-03-16
> **jbayone said:**
> the archive manager handles most compressed files, so you should just be able to double-click on the file.

nevermind, sorry

it doesnt.. im not that stuppid wink wink

---


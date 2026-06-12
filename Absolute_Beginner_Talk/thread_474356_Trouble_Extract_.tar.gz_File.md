---
title: "Trouble Extract .tar.gz File"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by chantzzzzz on 2007-06-15
I'm currently trying to extract a .tar.gz file in Ubuntu FF, but I've hit a snag. Whenever I try to do anything, the box icon turns into a .txt icon, and I cannot use the archive manager on it, nor can I open it in the text pad, nor can I run the program or run it in the terminal. It's blank. This has happened a few times, and I would really appreciate knowing how to fix this. Thanks!

---

### Post by kevdog on 2007-06-15
At command prompt first make sure you are in the directory where the .tar.gz file is located.

Then 

tar -zxvf *filename*

That should extract the file in the current directory

---

### Post by chantzzzzz on 2007-06-15
gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

That's all I get. Any ideas?

---

### Post by kevdog on 2007-06-15
Is this with all tar.gz files or just one in particular.  It seems from the error message you are giving me that the file you are trying to unzip is prematurely truncated.  Try redownloading it, or try with a different .tar.gz file so we can eliminate possibilities of what is causing the problem.

---

### Post by chantzzzzz on 2007-06-15
> **kevdog said:**
> Is this with all tar.gz files or just one in particular.  It seems from the error message you are giving me that the file you are trying to unzip is prematurely truncated.  Try redownloading it, or try with a different .tar.gz file so we can eliminate possibilities of what is causing the problem.

For some reason, it worked when I didn't save the file then open it, but rather opened it right through the firefox download manager. But upon configuring, I get this:

checking for libgnome-2.0 libgnomeui-2.0 libpanelapplet-2.0 gconf-2.0... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package libpanelapplet-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libpanelapplet-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libpanelapplet-2.0' found Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (libgnome-2.0 libgnomeui-2.0 libpanelapplet-2.0 gconf-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them

I've got those packages, so what's the deal here?

---

### Post by kevdog on 2007-06-15
Just a shot in the dark, but try extracting as before after updating your system:

sudo aptitude update && sudo aptitude upgrade

---

### Post by chantzzzzz on 2007-06-15
> **kevdog said:**
> Just a shot in the dark, but try extracting as before after updating your system:

sudo aptitude update && sudo aptitude upgrade

Updated it today and just now and I still get the same thing

---


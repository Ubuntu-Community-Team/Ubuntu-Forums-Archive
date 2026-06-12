---
title: "trouble compiling netatalk and nfs from source"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by spandau on 2008-02-18
Hi, really new here, trying to figure out how to install things on Feisty using the command line, but it's not going well. I have been trying to install NFS and netatalk by unzipping the tarballs and then doing "./configure" as it says to do in the READMEs, It runs a series of checks and then eventually ends at:

"checking for C compiler default output... configure: error: C compiler cannot create executables"

or 

"checking for C compiler default output file name... 
configure: error: C compiler cannot create executables"

I have no idea what to do from here. Can anyone help? Thanks!

---

### Post by paultag on 2008-02-18
did you install a compiler?

Install package gcc and / or g++
```

sudo aptitude install gcc g++

```
and you will need to install more packages and headers for the dependences of the application. ( if it requires libnotify, you will need to install libnotify-dev as well )

Cheers,
Tag

---

### Post by spandau on 2008-02-18
I had thought that the compiler was already installed, but regardless I ran the code you said to. But I'm still getting the same message from trying to install nfs...

---

### Post by paultag on 2008-02-18
sorry bout that,

I found this thread, that seems pretty good:
[http://ubuntuforums.org/archive/index.php/t-37434.html](http://ubuntuforums.org/archive/index.php/t-37434.html)

let me know,

Cheers,
Tag

---


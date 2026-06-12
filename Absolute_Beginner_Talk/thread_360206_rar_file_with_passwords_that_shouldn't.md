---
title: "rar file with passwords that shouldn't"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-02-12
every once in a while i'll download a rar file and try to unrar it and it will prompt me for a password.  These same file my windows using friends open and aren't asked for passwords.  The files i'm d/ling are not supposed to have passwords.  I am using file-roller.  Usually, rar file don't give me trouble, but once in a while, i won't be able to open them because i don't have the password that doesn't exist.  Ayone have any ideas about this?

---

### Post by azazel00 on 2007-02-12
Use "unrar"
```
sudo aptitude install rar unrar
```

Then
```
unrar e file.rar
```

Hope this helps. I've run into the same problem with file-roller, and unrar seems to be the solution.

---

### Post by RaiSuli on 2007-02-12
I've encountered this a couple of times with corrupt or damaged rar files. If there are par files available, you should get around this problem by installing "par2" and "parchive" with the synaptic package manager. Par files can repair damaged rar archives.

---

### Post by omac on 2007-04-10
Just had the exact same problem as xboxbman.

Simple solution:  Install IZArc (izarc) under wine.  If you already have wine, just run the setup program (right click - open with wine windows emulator) and so far, it works perfectly.  It extracted the multiple part rar files, where under the one in Ubuntu (not sure if it was Ark or File Manager), it kept asking for the password.  The password had a special character, so maybe it had to do with the bug related to that.

And if you don't have Wine, I suggest getting it through Automatix.  :)

---

### Post by compiledkernel on 2007-04-10
Open a terminal 

sudo apt-get install wine 


Alot easier than installing A-X to get it done for you. Refer to official docs for how to use wine 

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---


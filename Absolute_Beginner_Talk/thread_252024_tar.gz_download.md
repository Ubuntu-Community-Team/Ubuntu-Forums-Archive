---
title: "tar.gz download"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-09-06
My short-term memory must be completely gone today.  I can't get a tar.gz file to open in a specific directory.  I'm following a howto that tells me to download a source file and provides me a link.  At the link I choose a mirror and click download.  Then I get to the 'Opening xxxxxx.tar.gz' window. I open it with Archive manager and extract it into the directory I created, but I cannot access it from the terminal, even after I do a cd xxxxx. I get:

gary@Faith:~$ cd gnomad_install
gary@Faith:~/gnomad_install$ tar -zxvf libmtp-0.0.16.tar.gz
tar: libmtp-0.0.16.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
gary@Faith:~/gnomad_install$

 What am I doing wrong, please?

---

### Post by benfindlay on 2006-09-06
> I open it with Archive manager and extract it into the directory I created

if you've already extracted it, then theres no reason to type ```
tar -zxvf libmtp-0.0.16.tar.gz
```

Just go straight to
```
./configure
make
make install
```

---

### Post by Tomosaur on 2006-09-06
When you download a file, I find it much simpler to save it to disk rather than open it straight away. Firefox by default saves to your Desktop, while Opera saves to your home folder. I am unsure of other browsers.
Anyway, once you've saved your file, open up a terminal. CD to the directory the .tar.gz file is, and type:
```

tar -zxvf libmtp-0.0.16.tar.gz

```
This will create a directory called libmtp-0.0.16.tar.gz which you can then enter and compile or whatever you need to do with it.

---

### Post by Guns90 on 2006-09-06
Thanks guys, that worked.

---


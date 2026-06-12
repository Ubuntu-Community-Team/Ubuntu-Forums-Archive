---
title: "What files should I save?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Zoltarp on 2008-03-20
I really messed up my Ubuntu 7.10 install. I am now using the LiveCd and am now copying my data to a server. I got my files what else can I copy to save time recovering my settings apps etc after I do a fresh install? Thanks in advance.

Bruce

---

### Post by Bruce M. on 2008-03-20
> **Zoltarp said:**
> I really messed up my Ubuntu 7.10 install. I am now using the LiveCd and am now copying my data to a server. I got my files what else can I copy to save time recovering my settings apps etc after I do a fresh install? Thanks in advance.

Bruce

Hi Bruce,

Check my signature for QuickStart ... the link is to the thread, you can get the file there.

It does backup and restore very nicely ... and a whole lot more.

Bruce (is that an echo?)

---

### Post by Bruce M. on 2008-03-20
I misread your post.

Grab everything in your **/home** folder

That's where your programs are.

EDIT: Make sure you get all the hidden files too.

---

### Post by nick_h on 2008-03-20
In addition to /home you might want to save the packages you have installed.  Save a list of the installed packages with:
```
dpkg --get-selections > file
```
and backup the directory /var/cache/apt/archives

If you have modified any files in /etc then make a backup of them as well.

---

### Post by Zoltarp on 2008-03-20
Ok thanks guys....


and Yes that was an Echo... :)

---


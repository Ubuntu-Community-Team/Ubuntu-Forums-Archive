---
title: "chmod Command"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-29
I'm trying to learn the basic commands and unfortunately can't understand all I get with the "man <command>".  For chmod, is there a form of the command which will give you the present permissions, before changing them?  Also I don't understand what this means (from man chmod):  The first digit selects the set user ID (4) and set group ID (2).

Thanks for help.

Buck

---

### Post by taurus on 2006-11-29
```
ls -la
```
will tell you the present permissions of all files in current directory...

---

### Post by bodhi.zazen on 2006-11-29
[Linux Files and File Permissions](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by Buck2348 on 2006-11-29
Thanks very much to both of you.  One answer seems always to bring up another question.  In a directory listing, long format (ls -l), what does the "Links" entry for each file mean?  Thanks again.

Buck

---

### Post by Peepsalot on 2006-11-29
> **Buck2348 said:**
> Thanks very much to both of you.  One answer seems always to bring up another question.  In a directory listing, long format (ls -l), what does the "Links" entry for each file mean?  Thanks again.

Buck
What do you mean the links entry for each file?  Where does it say "Links"?

It is possible to have "symbolic links", which are similar to shortcuts in windows.  But not every file has a symbolic link.
For more info:
```
man ln
```
Or just google for "symbolic links"

---

### Post by CatKiller on 2006-11-29
I believe it is the number of [hard links]("http://en.wikipedia.org/wiki/Hard_links") to that file, or the number of subdirectories for a directory.

---

### Post by Peepsalot on 2006-11-29
Oh, yeah I see the column you mean now.  Never noticed it before.  Yeah it would make sense because every directory has a "." file which links to the current directory, and a ".." file which links to the parent directory.  So all directories have at least 2 links to them(the (hard?) link which is the directory name, and the "." (symbolic?) link), and more if it contains subdirectories.

I think this includes the sum of both hard and symbolic links.

---

### Post by Buck2348 on 2006-11-30
Thanks a bunch, just what I wanted to know, though now that I do know it seems I should have been able to figure it out myself.  :???:  BTW, I just mentioned in another post that my buttons and such in this reply box aren't working.  I had to insert that smiley manually.  :)

---

### Post by Peepsalot on 2006-11-30
> **Buck2348 said:**
> Thanks a bunch, just what I wanted to know, though now that I do know it seems I should have been able to figure it out myself.  :???:  BTW, I just mentioned in another post that my buttons and such in this reply box aren't working.  I had to insert that smiley manually.  :)
Hmm, I couldn't find your other post.  What browser are you running?  Can you see if it is throwing a javascript error?

---

### Post by Buck2348 on 2006-11-30
Thanks for the reply.  I'm running Swiftfox.  Your post gave me the clue I needed.  I installed NoScript in the browser recently and it was blocking the functions I mentioned.  Thank you very much!  :-D 

Buck

---

### Post by anaconda on 2006-11-30
> **Buck2348 said:**
> Also I don't understand what this means (from man chmod):  The first digit selects the set user ID (4) and set group ID (2).

Thanks for help.

Buck

There is an easier way to use chmod.. examples:
```
chmod a+rwx file1
chmod u+r file2
chmod g+rw file3
```
the first would give all users read,write, and execute rights for file1
second gives user (you) read rights for file2
third gives group read, write rights to file3 (not sure about the "g".. newer needed it..)

---


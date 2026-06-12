---
title: "sudo: deb:command not found"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by h4450 on 2007-12-28
sudo

---

### Post by philinux on 2007-12-28
you would normally run

sudo anycommand

Not just sudo on its own it means nothing

---

### Post by xeth_delta on 2007-12-28
Excuse me, can you be more explicit about the problem you are having? The error message you wrote on the thread title means that sudo could not find a command called deb, there is not such a command. What are you trying to do on your computer?

---

### Post by tech9 on 2007-12-28
> **xeth_delta said:**
> Excuse me, can you be more explicit about the problem you are having? The error message you wrote on the thread title means that sudo could not find a command called deb, there is not such a command. What are you trying to do on your computer?

big + 1

---

### Post by xeth_delta on 2007-12-28
> **tech9 said:**
> big + 1

Thanks tech9.
H4450, does this have anything to do with the thread you opened some time ago: [http://ubuntuforums.org/showthread.php?t=638737]("http://ubuntuforums.org/showthread.php?t=638737")?

---

### Post by tech9 on 2007-12-28
> **xeth_delta said:**
> Thanks tech9.
H4450, does this have anything to do with the thread you opened some time ago: [http://ubuntuforums.org/showthread.php?t=638737](http://ubuntuforums.org/showthread.php?t=638737)?

:)

---

### Post by h4450 on 2007-12-28
Sorry,I  didn't mean to post.

Some more details about my problem

I was trying to  Enabling Extra Repositories

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 

followed the steps for Adding the Universe and Multiverse Repositories,

but still have an issues with package installation?


Thank you all for a such a quick respond !!![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by xeth_delta on 2007-12-28
> **h4450 said:**
> Sorry,I  didn't mean to post.

Some more details about my problem

I was trying to  Enabling Extra Repositories

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 

followed the steps for Adding the Universe and Multiverse Repositories,

but still have an issues with package installation?


Thank you all for a such a quick respond !!![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

Did you run **sudo apt-get update** after the modifications to the file?

---

### Post by SOULRiDER on 2007-12-28
You didnt just type
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe  in the terminal did you?
You need to add those lines to your sourceslist file.

To do such thing press alt + f2 and type
```
gksu gedit /etc/apt/sources.list
```
and add those two lines at the end, then save and run this command
```
sudo aptitude update
```

---


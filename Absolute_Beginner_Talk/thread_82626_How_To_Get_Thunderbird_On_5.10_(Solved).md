---
title: "How To Get Thunderbird On 5.10? (Solved)"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by Breezy Badger on 2005-10-26
Hello,

I want to get Thunderbird as my mail client instead of using evolution.  I went to add aplications and it listed thunderbird but it says it is not in the archive and will not let me add it.

This may be a noob question, or not I am not sure.  Anyone know how to do, I am guessing its very easy.

thanks,

Badger

---

### Post by Kyral on 2005-10-26
Look for "mozilla-thunderbird"

---

### Post by Manny C on 2005-10-26
```
 sudo apt-get update 
```
Then
```
 sudo apt-get install mozilla-thunderbird 
```

---

### Post by Breezy Badger on 2005-10-26
thanks for the help, this is what I get

```
XXXX@XXXX:~$ sudo apt-get update
Reading package lists... Done
XXXX@XXXX:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate

```

---

### Post by fannymites on 2005-10-26
Do you have any repositories enabled in /etc/apt/sources.list?

---

### Post by aysiu on 2005-10-26
[QUOTE=fannymites]Do you have any repositories enabled in /etc/apt/sources.list?[/QUOTE] Yes, please post your /etc/apt/sources.list here.

---

### Post by Breezy Badger on 2005-10-26
My bad fellas, it was the repositories.  I should have known better, silly me.  I added new repositories and it is all fixed up now.

thanks

Badger

---


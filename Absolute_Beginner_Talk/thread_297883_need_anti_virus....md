---
title: "need anti virus..."
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-11
I'm running xubuntu on my computer and i need anti virus,  I try to install clam anti virus though the terminal but it says its not avaible some one help please!

---

### Post by professor_chaos on 2006-11-11
clamav is in the universe repository and to install you can type

```
sudo apt-get install clamav
```

---

### Post by strabes on 2006-11-11
can you paste your /etc/apt/sources.list and the exact error?

---

### Post by wieman01 on 2006-11-11
You have tried this?
> sudo apt-get install clamav
But you are online, right?

---

### Post by lordvolo on 2006-11-11
i have tryed sudo apt-get install clamav and still doesnt work

---

### Post by professor_chaos on 2006-11-11
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

add universe.
then if it still doesn't work, post your error/message that you get.

---

### Post by lordvolo on 2006-11-11
error message:
Reading package lists... Done
Building dependency tree... Done
Package clamav is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package clamav has no installation candidate

---

### Post by tuxcantfly on 2006-11-11
are your repositories set up correctly? have you enabled universe in /etc/apt/sources.list?

---

### Post by lordvolo on 2006-11-11
you talking to a total newb i have no idea what your saying

---

### Post by CatKiller on 2006-11-11
> **lordvolo said:**
> you talking to a total newb i have no idea what your saying

Then read the link professor_chaos posted.

---

### Post by Omnios on 2006-11-11
If I remember properly when I used to use clam I installed fresh clam for updates and the clam demon which seemed to run the anti virus but that was a very long time ago.

---

### Post by lordvolo on 2006-11-11
thanks to you all it worked!!

---

### Post by bodhi.zazen on 2006-11-12
> **lordvolo said:**
> I'm running xubuntu on my computer and i need anti virus,  I try to install clam anti virus though the terminal but it says its not avaible some one help please!

I am surprised no mentioned it, but, you probable DO NOT need antivirus software with Linux.

---

### Post by wieman01 on 2006-11-12
> **bodhi.zazen said:**
> I am surprised no mentioned it, but, you probable DO NOT need antivirus software with Linux.
Unless... you are sharing files with Windows machines. Just to round this up.

---

### Post by jonesyp on 2006-11-12
Can I suggest AVG?  There is an excellant tutorial on this forum

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

It works perfectly for me.

Best wishes

---


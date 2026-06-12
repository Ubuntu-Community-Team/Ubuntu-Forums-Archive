---
title: "installing package"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by next on 2005-06-21
Newb here---->


ok so i had to install libncurses5-dev, but when i tried 
apt-get install libncurses5-dev it said package could not be found.     

so i downloaded it on my other computer burned it to a cd and then went back to the other copmuter with linux.

i typed   dpkg -i libncurses5-dev    

and it said requested operation requires superuser privlleges. 


help please---------hope you understand

---

### Post by aamir on 2005-06-21
type: 

```
sudo dpkg -i packagename
```

---

### Post by Leif on 2005-06-21
Type "sudo dpkg -i libncurses5-dev " instead, and then your normal password. Sudo is how you do stuff that requires admin privileges. Are you doing things this way because your ubuntu computer doesn't have internet access ?

---

### Post by next on 2005-06-21
"Are you doing things this way because your ubuntu computer doesn't have internet access ?"

yes i need this to set up ndiswrapper

---

### Post by next on 2005-06-21
ok i tried that, now its saying that it cant find it, how do i put the location of the file?

---

### Post by next on 2005-06-21
exact words are "cannot access archive: no such file or directory"

---

### Post by TeeJay on 2005-06-21
[QUOTE=next]exact words are "cannot access archive: no such file or directory"[/QUOTE]

I always do a " sudo dpkg -i " then drag and drop the debian package in the terminal so as to get the correct location & spelling.

---

### Post by az on 2005-06-21
Whoa!

Why do you need ncurses-dev to get ndiswrapper running?

1-  ndiswrapper is already included.  the module is already installed and all you need to do is install ndiswrapper-utils from the cd.

2-  If you want to compile a newer version, all you need are the kernel-headers.  Again it is all on the cd.  Install build-essential and linux-headers-2.6.10-5-386.

---


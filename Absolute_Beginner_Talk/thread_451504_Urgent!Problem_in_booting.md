---
title: "Urgent!Problem in booting?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-05-22
While starting Ubuntu me getting error file missing "apt-get" install it by typing: apt-get install apt but after i type this the same msg reappears help...

---

### Post by icechen1 on 2007-05-22
try entering ''exit'' it will probably continue to boot,this happened to me before when i modify my partitions.

---

### Post by ThinkBuntu on 2007-05-22
Does it take you to a text-only login (Init 3)? Please let us know a little more.

---

### Post by Dark Star on 2007-05-22
@ice .. I tried typing exit but after the restart same thing happens....

@TB ... Ammm??????? Yep after the Ubuntu load screen ends it takes me to a text screen..

---

### Post by Dark Star on 2007-05-22
Help plz ... Soon :(...

---

### Post by Sparkster185 on 2007-05-22
If you're missing apt-get, I don't see how you could install it using "apt-get install apt".  That just doesn't make sense.

Perhaps you could install it via some other package management system?  Like aptitute (this might be apt, I'm not sure) or dpkg?

If you type "which dpkg" that will tell you if it's installed.  Try searching for a URL that contains the apt package, and do a wget on the url, then dpkg the package.

EDIT:  Search for the dpkg file, not the apt package.

---

### Post by ThinkBuntu on 2007-05-22
Login. If "sudo apt-get install apt" doesn't work, and "sudo aptitude install apt" also doesn't, I recommend you manually install apt. What is your architecture (i386? 64? PPC?)? Let me know, and I'll provide you with a pretty safe solution, assuming you have dpkg installed (you should).

---

### Post by Dark Star on 2007-05-22
i386 / Plz tell me soon Regards

---

### Post by ThinkBuntu on 2007-05-22
> **Dark Star said:**
> i386 / Plz tell me soon Regards
Here you go. After logging in, enter these two commands (leave out the $, that indicates a shell):
```
$ wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb
$ sudo dpkg apt_0.6.46.4ubuntu10_i386.deb
```

---

### Post by Dark Star on 2007-05-22
> **ThinkBuntu said:**
> Here you go. After logging in, enter these two commands (leave out the $, that indicates a shell):
```
$ wget http://ubuntu.mirrors.tds.net/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb
$ sudo dpkg apt_0.6.46.4ubuntu10_i386.deb
```

Not working. I even did not reach to the log in scree a DOS type screen appears stating the same error and I could not reach the log in screen:(

---

### Post by Dark Star on 2007-05-22
Help plz....

---


---
title: "trying to install rpm"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-10-01
when trying to run the following command, I keep getting the same error message:  

andy@ubuntu:/usr/local/mmc$ sudo apt-get install rpm build-essential
Reading package lists... Done
Building dependency tree... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate

I am trying to install a fortran compiler, and the 
sudo apt-get install rpm build-essential 
line was the first step...unfortunately I cant get past this point.

Thanks

---

### Post by meng on 2006-10-01
I doubt that those instructions you have are for an ubuntu or other deb-based system. You will need the package build-essential though, and therefore type:

sudo apt-get install build-essential

this will download and install the build-essential package (the command you used tries to download and install two packages, one named rpm and one named build-essential).

---

### Post by oscar78 on 2006-10-01
Ok, I just tried to get build-essential, and it gives me essentially the same error message:

andy@ubuntu:/usr/local$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essential
andy@ubuntu:/usr/local$

---

### Post by meng on 2006-10-01
Hmm that's strange, do you have any repositories enabled? If you don't know what I mean, then just post the output of this command:
cat /etc/apt/sources.list

---

### Post by oscar78 on 2006-10-01
hmm, not sure about the repositories

andy@ubuntu:/usr/local$ cat /etc/apt/sources.list
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
andy@ubuntu:/usr/local$

---

### Post by meng on 2006-10-01
There's your problem then. Your only repository at the moment is the repository for Automatix. Now we could speculate as to why this is (even though that doesn't help directly, but I'm going to speculate anyway). I bet that you (or someone professing to help you) REPLACED the contents of that file with the Automatix repository instead of APPENDING the repository to the file (it's as simple as using ">" instead of ">>").

Okay, now that I've vented, you need to update your sources.list. I recommend doing this:
1) Go to [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
2) Highlight and copy the suggested repo list for Dapper.
3) Run from terminal: gksudo gedit /etc/apt/sources.list, and paste into the file. You can keep the Automatix repository if you want to (if you really, really, really want to...)
4) Save/exit
5) From terminal, run: sudo apt-get update
6) Now run:
sudo apt-get install rpm build-essential
(yes you can include rpm if you want to, I looked into it and it should be okay).

---


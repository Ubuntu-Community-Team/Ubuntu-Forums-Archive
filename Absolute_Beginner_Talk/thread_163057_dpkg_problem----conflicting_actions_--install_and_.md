---
title: "dpkg problem----conflicting actions --install and --install. What do I do with it?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by lg3 on 2006-04-20
I am following the steps outlined on some previous threads and the User Guide, but running into the problem below---see output>>>>

~/Desktop$ sudo dpkg -iitrade_0_4_coca_2006-03-19.tar.gz
Password:
dpkg: conflicting actions --install and --install

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

What does this mean conflicting actions? and what do I do next?

Thank you.

---

### Post by meborc on 2006-04-20
hmm... i see a typo

**sudo dpkg -i itrade_0_4_coca_2006-03-19.tar.gz**

should be the right command... mark the space between **-i** and the filename

---

### Post by htinn on 2006-04-20
iTrade isn't a package you can install. It's a python program. To do that, simply extract it (using Archive Manager) and run the itrade.py file.

In a terminal you could run it this way:

python itrade.py

---

### Post by meborc on 2006-04-20
hehe... i must be going blind :mrgreen: i only saw dpkg... and i didn't even notice the end of the file... so my previous post is useless...

:oops: hiding

---

### Post by lg3 on 2006-04-20
Thanks for your pointing out the Python situation and help.

---

### Post by lg3 on 2006-04-20
Okay did that an extracted it, then I cd'd to that directory and tried to run. Here is the output:
leroy@user2:~/Desktop$ cd /home/leroy/iTrade/itrade
leroy@user2:~/iTrade/itrade$ python itrade.py
iTrade(alpha) - 0.4 Coca - FINAL
User Configuration : usrdata/usrconfig.txt
Traceback (most recent call last):
  File "itrade.py", line 67, in ?
    import itrade_wxmain
  File "/home/leroy/iTrade/itrade/itrade_wxmain.py", line 61, in ?
    import itrade_wxversion
  File "/home/leroy/iTrade/itrade/itrade_wxversion.py", line 64, in ?
    import wxversion
ImportError: No module named wxversion

What does that mean?

---

### Post by htinn on 2006-04-20
Meh. It probably won't work anyway. It requires the ANSI version of wxPython (and Ubuntu uses unicode).

---

### Post by lg3 on 2006-04-20
Thanks. move along, move along nothing to see here.  :)

---


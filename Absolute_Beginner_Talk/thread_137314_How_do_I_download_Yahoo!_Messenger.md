---
title: "How do I download Yahoo! Messenger?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by ILoveTheDark7962 on 2006-02-27
I feel like such a n00b asking this, but I can't download Yahoo! Messenger, and i have no clue how to do it. First, I don't know which one to use.

**RedHat Linux**

   1. Save the appropriate file to your machine:
      RedHat 6.x
      RedHat 7.x
      RedHat 8.0
      RedHat 9
   2. Log in as root and type: rpm -i <filename> with the appropriate filename depending on your version to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.

**Debian Linux**

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.

**FreeBSD Installation**

   1. Save the file to your machine.
   2. Log in as root and type: pkg_add fbsd4.ymessenger.tgz to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.

Which one does Ubuntu go into? and what does it mean, log in as root? or am I off altogether? I'm so confused.... Somebody please help!!!:confused:

---

### Post by stuporglue on 2006-02-27
> 
Debian
1. Save the file to your machine.
2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
3. Run /usr/bin/ymessenger from X Window to launch the application.

Ubuntu is based on Debian. 

root: Whenever instructions want you to do something as root, just type "sudo " then the command they gave...ie: 

sudo dpkg -i ymessenger_1.0.4_1_i386.deb 

You can use the menu editor SMEG to add a launcher for messenger, instead of running /usr/bin/ymessenger, if you want.

---

### Post by souteneur3190 on 2006-02-27
u do realize the gaim also has yahoo instant messanger too..... right?

---

### Post by xhie on 2006-02-27
theres always gaim as well, dunno, I just like it better. Something about not having to install any aol / yahoo software.

---

### Post by cstudent on 2006-02-27
The Yahoo messenger for Linux is out-dated. I wouldn't recommend using it. You can do exactly the same stuff with Gaim. Yahoo messenger for Linux doesn't have voice chat capabilities, Gaim doesn't either. I've heard that Google may be porting their Google Talk to Linux, which may give voice chat. But for now, Gaim is probably your best choice and it's installed by default. Plus you can also chat with friends who use other services like MSN as well.

---

### Post by ILoveTheDark7962 on 2006-02-27
Thanks a lot! I wasn't aware gaim was already on here...

---


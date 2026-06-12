---
title: "apt-get mysql not working. here is my error msg. !"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-19
any idea what the problem my be? i am running flight-4. thx!




poipu@ubuntu1:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mysql-server: Depends: mysql-client (>= 4.0.24-10ubuntu2)
E: Broken packages

---

### Post by amoser on 2006-02-19
Sounds like the package that you need is not in Dapper's repos yet.  This is to be expected speaking Dapper is the devolpment version of Ubuntu right now.  I think that if you are a beginner you should use Breezy Badger, the stable version of Ubuntu.

~Alan

---

### Post by bbqbaker on 2006-02-19
what is the developer version?

basically i am using flight4 dapper because there is no other ubuntu version right now that can be installed on my dell 3100. is this right? it has something to do with the usb and hard drive not being able to recognize it....

since its not in the repositories, can it still be installed manually?


thanks.

---

### Post by amoser on 2006-02-20
you could always go to mysql.com and see if there is somewhere you can get the Ubuntu package for it.  I didn't know about the Dell thing, you could always try the Breezy Badger Live CD, and see if it works, I think Breezy should work on your Dell.

~Alan

---


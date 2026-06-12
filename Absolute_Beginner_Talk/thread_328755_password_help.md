---
title: "password help"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2006-12-31
As you see I am running Ubuntu 6.10 on my laptop. It is working fine, crosses fingers.

I have a hard drive from a second laptop running Ubuntu also. I do not know the login or the password for the installation on this second hard drive. I have it installed on my laptop thru the USB using an adapter.

I can see all the files and can access the ones that are not password protected.

My question is: how do I find out what the login name and password for the Ubuntu account installed on the second drive? Also if possible, there are some folders and files locked, how would I unlock those folders and files?

Thanks in advance

---

### Post by rbhigday on 2006-12-31
While waiting for an answer I looked in help files and found the lost password page and now know how to get a lost password. 

Now I was thinking I should be able to find the username/userid somewhere in files for configuration of network or something else and would like to know the name of a file or more than one that would have a record of the username and is readable.

---

### Post by tommytom on 2006-12-31
I'm not sure about finding logins or passwords, didn't you install ubuntu originally on that lap top? 

With regards to the locked files-

Can you see them with ```
sudo ls /dev/foo/foo
```

 "foo" is your directorys, you can find the path to the external HD by typing ```
 mount
```

If you can see the have you tryed to chmod them? read this link to find out how
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---


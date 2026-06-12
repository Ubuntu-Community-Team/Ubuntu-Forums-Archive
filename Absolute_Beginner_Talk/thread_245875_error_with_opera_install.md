---
title: "error with opera install"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by rrp on 2006-08-28
I can download opera but cant open it without getting a error wrong archetecture message.

---

### Post by catlett on 2006-08-28
The Dapper commercial repository has opera in it. Just add the to your list and you can install it with apt-get or synaptic.
First open the list by entering this in the terminal ```
sudo gedit /etc/apt/sources.list
```
Add this to the end of the file
```
#dapper-commercial repository
deb http://archive.canonical.com/ubuntu dapper-commercial main
```
Save the file and close it.
Now enter these 2 commands in the terminal. The first updates your apt cache, this will add the commercial repos packages. The other will install Opera.
```
sudo apt-get update
```
```
sudo apt-get install opera
```

The only issue is, Opera doesn't have a 64-bit version. Are you running the 64bit version of Ubuntu or just the regular 32bit installation (a.k.a. i386)? If you have the 64bit then Opera will not install with any method.

---

### Post by nrwilk on 2006-08-28
It sounds like you downloaded a file which is supposed to install Opera on a chip which is incompatable with the chip in your system.

We need a little more information.  What is the name of the file you downloaded, and what type of chip is in your system?

---

### Post by rrp on 2006-08-28
yes i am running a 64 bit. thanks anyway.

---


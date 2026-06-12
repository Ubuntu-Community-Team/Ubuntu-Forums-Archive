---
title: "DKPG and Download Management Error"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Dennis Shipman on 2007-07-30
How do I resolve the error message below and, more importantly, determine what software may be causing it? I am new to this linux generally, and Ubuntu particularly. I am using Ubuntu 7.04 (Feisty Fawn) AMD64. 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report."

Also when I try to download and install Automatix2, I get an error saying "only one software management tool is allowed to run at the same time

Please close other application e.g., 'Update manager,' 'aptitude' or Synaptic first"

None of those applications are running, unless they are running in the background. And I suspect that the former is causing the latter. Please help. Thanks for your prompt response.

---

### Post by forestpixie on 2007-07-30
open a terminal and do

sudo dpkg --configure -a

enter password when asked

---

### Post by davidjmayo on 2007-07-30
Hi Dennis

first do what it says in the error message. you need to go into a terminal from Applications==>accessories==>Terminal

now type in

**sudo dpkg --configure -a**

and hit enter. When it asks for a password this is your user login password

when it's finished you should be good to continue
If you get an error message post back the error message

---

### Post by Dennis Shipman on 2007-07-31
Thank you.

> **forestpixie said:**
> open a terminal and do

sudo dpkg --configure -a

enter password when asked

---

### Post by Dennis Shipman on 2007-07-31
Thank you.

> **forestpixie said:**
> open a terminal and do

sudo dpkg --configure -a

enter password when asked

> **davidjmayo said:**
> Hi Dennis

first do what it says in the error message. you need to go into a terminal from Applications==>accessories==>Terminal

now type in

**sudo dpkg --configure -a**

and hit enter. When it asks for a password this is your user login password

when it's finished you should be good to continue
If you get an error message post back the error message

---


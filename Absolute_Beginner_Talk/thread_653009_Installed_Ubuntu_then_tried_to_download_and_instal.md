---
title: "Installed Ubuntu then tried to download and install updates. Help!!"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by banjo13 on 2007-12-29
Hi I'm totally new to Linux/Ubuntu. After installing Ubuntu 7.10 I decided to download the latest updates using software sources and installing them using synaptic package manager ( I think) All this done in accordance with a book on Ubuntu. When I restarted my PC I get the username and password screen, then a blue screen with a couple of icons on it and thats all, no toolbar or anything else. Like i said I'm totally new to computers and Linux, Please help. Thank you.

---

### Post by overdrank on 2007-12-29
> **banjo13 said:**
> Hi I'm totally new to Linux/Ubuntu. After installing Ubuntu 7.10 I decided to download the latest updates using software sources and installing them using synaptic package manager ( I think) All this done in accordance with a book on Ubuntu. When I restarted my PC I get the username and password screen, then a blue screen with a couple of icons on it and thats all, no toolbar or anything else. Like i said I'm totally new to computers and Linux, Please help. Thank you.

Hi and it sounds like you have installed xubuntu?

---

### Post by banjo13 on 2007-12-29
Thanks for the quick reply, When I start up my PC, it says Ubuntu 7.10 will start in 10 seconds, Does this mean I've overwritten it or something like that. If so, what can I do about it. Again Thank you

---

### Post by HermanAB on 2007-12-29
Hmm, re-install.  It only takes about 30 minutes - less time than to search for answers.  If you just installed the system then it is up to date, Updating again cannot improve it, therefore it can only do nothing, or worse - as you found.

Soooo, as the old saw says: Don't fix it if it ain't broke!

Cheers,

Herman

---

### Post by meindian523 on 2007-12-29
Please post ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```


edit:
Herman:

That's the easy way out and can always be used if the issue is not resolved.....moreover the OP would learn something from resolution of his problem

---

### Post by banjo13 on 2007-12-29
Thought you might say that. Thanks for your help. I'm sure you'll all hear from me on many occasions.

---

### Post by meindian523 on 2007-12-29
you=who?

---

### Post by banjo13 on 2007-12-29
> **meindian523 said:**
> Please post ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```


edit:
Herman:

That's the easy way out and can always be used if the issue is not resolved.....moreover the OP would learn something from resolution of his problem

Sorry mate, like i said I'm new, so I don't know what any of the above means. Thank you

---

### Post by tmcginn5 on 2007-12-29
Can these commands be performed even if you have it set up to dual boot with windows?

---

### Post by meindian523 on 2007-12-29
@banjo

I meant you have to type(or copy/paste) those commands(separately) which are in the boxes in the Terminal(Applications>>Accessories>Terminal) and post whatever you get over here....

@mcginn

yes,provided you have your Linux system booted up

---

### Post by tmcginn5 on 2007-12-29
I want to make sure I understand:

First, I run the following command in the terminal:

sudo fdisk -l

Then after that is complete, I run this next command in the terminal:

cat /etc/fstab

After that I am to copy the results from the terminal and post them back at this thread, correct?

---

### Post by meindian523 on 2007-12-29
bang on target

---


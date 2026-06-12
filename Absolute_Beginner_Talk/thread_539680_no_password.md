---
title: "no password?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by A-Sylum on 2007-08-31
Theres a computer thats being used for my whole family and it would be really nice if i could make it so you dont have to enter a password to do root activities. is there a way? thanks!!!!

---

### Post by s26c.sayan on 2007-08-31
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)


Note that this is not secure and not at all recommended! You can so easily break your system this way, just like in other operating systems!!

---

### Post by razorednight on 2007-08-31
Don't do it!! :eek:

The "whole family" using the computer, all running as root... someone'll brick it for sure!

;) Hey, I'm not telling you how to run your box.  But friendly advice... I wouldn't do it.

Take care!

---

### Post by A-Sylum on 2007-08-31
thanks ill give it a try! but do you know which file we are searching for that line in

EDIT: Nevermind

---

### Post by bodhi.zazen on 2007-08-31
You can enable the root account and allow root logins.

To enable root, in a terminal, 

```
sudo passws
``` and set a password

Then open configure gdm :

```
sudo gdmsetup
```

tic off "allow local system administrator login" in the security tab

Now log in as root and viola

NOTE : See the above warning about the risks of such things, otherwise it is your box to run as you please.

---

### Post by aysiu on 2007-08-31
Why are all the members of your family doing root activities?

---

### Post by s26c.sayan on 2007-08-31
> **A-Sylum said:**
> thanks ill give it a try! but do you know which file we are searching for that line in

EDIT: Nevermind

The file which you need to edit is /etc/sudoers.
But this file MUST be edited only with the 'visudo' command as root.

---


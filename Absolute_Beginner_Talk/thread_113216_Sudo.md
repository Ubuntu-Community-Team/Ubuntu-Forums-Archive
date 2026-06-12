---
title: "Sudo"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by macneacail on 2006-01-05
I finally got Linux installed and running. 

I can login in under my user name.

However, when I login I get a message that 38 update files are available, but when I click on them I am asked for my password. I give the password and nothing happens.

As far as I am aware I have three passwords, mine, grub and root. How do I run these locked out programs including the Synpatic program manager.

Thanks

John Nichols

Texas without the right to strike is not John Wayne's Texas.

---

### Post by 23meg on 2006-01-05
The root account is disabled by default and you need to enter your user password to run Synaptic and other administrative apps. 

What happens when you type "sudo synaptic" at the terminal and enter your password?

---

### Post by Mustard on 2006-01-05
Did you use expert install or default install?

---

### Post by macneacail on 2006-01-06
I did an expert install, does that matter?

What is the point of Gnome if I can not run such programs?

JMN

---

### Post by bluefrog on 2006-01-06
if u did a server install and then created a user, then this user is not in the sudoers (except if you expressly included it).

put it in the sudoers file and u will be able to sudo

james

---


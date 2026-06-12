---
title: "Problem with packages"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by egoo on 2006-03-17
I installed the first half of Ubuntu fine (with the cd) but when carried on with the installation without the cd after restarting the installing packages got to around 70% when an error came up saying that some packages could not be installed, this happened twice and now ehn ubunto boots up after the modules are loaded im taken to a command shell.

What is this automatix thing? Could that be of use?

---

### Post by Brunellus on 2006-03-17
log into the shell.

then 

sudo apt-get -f install

that'll try to fix any broken packages.

---

### Post by egoo on 2006-03-17
Thanks ill try that now. Can you recommend and sites for learning commands sush as this one?

---

### Post by mcduck on 2006-03-17
[QUOTE=egoo]I installed the first half of Ubuntu fine (with the cd) but when carried on with the installation without the cd after restarting the installing packages got to around 70% when an error came up saying that some packages could not be installed, this happened twice and now ehn ubunto boots up after the modules are loaded im taken to a command shell.

What is this automatix thing? Could that be of use?[/QUOTE]
No, automatix won't help you at this point.

Did you burn the install CD yourself? You could try burning a new one, on some high-quality disk, with very low speed. I use 4x for all install disks myself to make sure that there's no errors.

Or you if the computer is connected to net, you could try to run 'sudo apt-get -f install' and 'sudo apt-get install ubuntu-desktop' to get things fixed. But I'm not sure if that works, and even if it does it might not fix everything. I'd rather try to get a clean install than to fix a failed one.

---

### Post by egoo on 2006-03-17
Just tried got the error message

> dpkg was interrupted, youmust manually run 'dpkg --configure -a' to correct the problem.

After typing 'dpkg --configure -a' in got the error > dpkg: requested operation requires superuser privilage

I will burn a new image now.

---

### Post by Brunellus on 2006-03-17
don't do that yet. 

remember, anything you do with dpkg needs superuser privileges, so you have to prefix it with sudo.  thus

sudo dpkg --configure -a

i

---


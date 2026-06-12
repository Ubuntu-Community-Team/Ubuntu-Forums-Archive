---
title: "Root"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-16
You get root access by typing "sudo su".

How do reverse this? Like get out of it, so you cant damage your PC.

---

### Post by Pobega on 2007-01-16
Type exit to get out of a root login. Alternatively, you can just use "sudo -i" or "sudo -s" to get the same effect. I'm not sure if there are any differences from actually using sudo su, though.

---

### Post by Delkster on 2007-01-16
> **Pobega said:**
> Type exit to get out of a root login. Alternatively, you can just use "sudo -i" or "sudo -s" to get the same effect. I'm not sure if there are any differences from actually using sudo su, though.

su (which is invocated by sudo in the "sudo su" command) doesn't reset the environment when called without parameters. That is, with "sudo su" the root shell will have the same environment (that is, environment variables) that your normal user has. That also applies to "sudo -s". On the other hand, "sudo -i" behaves as if root had logged in via a login prompt, so the environment is reset to root's own.

I believe "sudo -i" is generally the recommended way.

---

### Post by Duppy on 2007-01-16
Ive tried my best with Ubuntu, but it dont work with my printer, wont install on my laptop and just causes me more hassle than it sorts. I cant be bothered anymore.

Back to Mr Bill Gates' creation. :(

Thanks for all your help.

---

### Post by Pobega on 2007-01-16
For the printer, have you tried Settings -> Preferences -> Printers (Not sure where if that is right for Gnome, I run Xfce)

---

### Post by Delkster on 2007-01-16
> **Duppy said:**
> Ive tried my best with Ubuntu, but it dont work with my printer, wont install on my laptop and just causes me more hassle than it sorts. I cant be bothered anymore.

I'm not trying to hold you back, but what kind of a printer do you have?

On the other hand, if the system doesn't even install...

---

### Post by Duppy on 2007-01-16
Lexmark X74, which ive found out isnt supported. It finds it in system > admin > printing does that mean it IS supported?

Btw, its a printer/scanner (all in one) which is harder to support?

---

### Post by zgayby on 2007-01-16
> **Duppy said:**
> You get root access by typing "sudo su".

How do reverse this? Like get out of it, so you cant damage your PC.


I want to understand how can I harm my pc by let's say installing something in the su mode. 
I mean am I such a beginner that i don't see something obvious?

---

### Post by Duppy on 2007-01-16
It basically allows you to move/delete files you cannot normally do. 

So if you delete it, you wont know it was important because it doesnt say your not allowed.

Therefore when your PC comes to find the file and it isnt there... **problem**

---

### Post by zerhacke on 2007-01-16
> **zgayby said:**
> I want to understand how can I harm my pc by let's say installing something in the su mode. 
I mean am I such a beginner that i don't see something obvious?

As root you have permission to edit, create, or delete files anywhere you wish.  Knowing this you know you can screw up configuration files to the point the system can no longer function, boot, or reboot.  Normal users do not have permission to screw around with those important configuration files, so unless you absolutely have to you should not do things as root.

Also as root you could install software that is less than helpful.  Linux may be more secure than Windows, but it is not the perfect secure system most people think it is.  I know of one fellow who used to install kernel modules that were nothing more than keyloggers that dumped results to an email address.  If you're not root, you cannot install kernel modules so you can't have that happen to you.  You also can't remove kernel modules as a regular user, so this prevents you from removing kernel modules that you really do need.

There's a saying in the Linux community - if it can be done outside the kernel, it must be done outside of the kernel.  You can extend that saying to "if it can be done outside of root, it must be done outside of root".  Root really is just that dangerous.  It may not look like you're doing anything wrong, but one slip as root and you can render your whole system unusable.

---


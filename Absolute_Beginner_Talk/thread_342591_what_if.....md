---
title: "what if...."
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jared234 on 2007-01-20
what if you can't log in to sudo any more.  is there a way to revert the permissions?

---

### Post by v8YKxgHe on 2007-01-20
Have you used Sudo before?  You need to enter your accounts password, not root's.

---

### Post by Tomosaur on 2007-01-20
Recovery mode on bootup gives you root permissions.

---

### Post by ComplexNumber on 2007-01-20
> **jared234 said:**
> what if you can't log in to sudo any more.  is there a way to revert the permissions?
when did it go like that?

---

### Post by jared234 on 2007-01-20
rock on! heres the scoop; i loged gksudo nautilus and gave read/write/delete permission over the whole system, and now when i log in as sudo i get this message: sudo: /etc/sudoers is mode 0666, should be 0440

---

### Post by anaconda on 2007-01-20
You can boot to recovery mode (from grub), and then you will have root rights.

Then you can either give root a password, or get your regular user back the lost sudo povers, or create a new user with sudo povers..

to give root a password:
passwd root
then after that you can use 
su root
and give root password to get root rights.(change the current user to root)

to create a new user with sudo powers:
adduser new_user_name
(Answer all the questions. eg. name, password etc)
then:
adduser new_user_name admin
adds the user to admin group (eg. gives the sudo powers)

---

### Post by ComplexNumber on 2007-01-20
> **jared234 said:**
> rock on! heres the scoop; i loged gksudo nautilus and **gave read/write/delete permission over the whole system**, and now when i log in as sudo i get this message: sudo: /etc/sudoers is mode 0666, should be 0440
OMG! why on earth did you do that? you should NEVER do that.

---

### Post by jared234 on 2007-01-20
because when i put a quake4 cd in the drive i could not even access the drive so i decided maybe if i had perm over everything i could get it.  i was not thinking ](*,) ](*,)

---

### Post by v8YKxgHe on 2007-01-20
wowowowowowow you don't wanna be doing that! If I was in your position, knowing that my entire hard drive is set so anyone can access it, I would re-install Ubuntu.

---

### Post by ComplexNumber on 2007-01-20
> **AlexC_ said:**
> wowowowowowow you don't wanna be doing that! If I was in your position, knowing that my entire hard drive is set so anyone can access it, I would re-install Ubuntu.
i would suggest that as well. i wouldn't envy the person who has to go around the whole system setting everything back to the correct permissions so that everything operates normally.


**jared234**
unless anyone has any bright ideas, i would suggest that you reinstall ubuntu. basically, you've messed up your system. the only good thing coming out of this is that you can learn from your mistakes.

---

### Post by taurus on 2007-01-20
+1 for the reinstall and please be careful with the sudo command.

---

### Post by Tiede on 2007-01-20
And don't forget to backup your /home before re-install! This way you get your box just like it was before (without the permission mess of course). Good luck with the reinstall.

---


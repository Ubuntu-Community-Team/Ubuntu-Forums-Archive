---
title: "Logging in as Root"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by PowerPLay on 2007-04-19
Ok here,s my little dilemma.

Want i want to do is log into Ubuntu on my computer with root privileges. That way i can manipulate my external ext3 drive and i don't have to type the password in every time i open something up. 

How do i do this. Is it anything like windows where i can set my user to admin or something. That way i have the privileges. 

Thanks for any help.

-PP

---

### Post by Seisen on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

---

### Post by Terl on 2007-04-19
Just give yourself permissions.

It is not a good idea to work as root anyway.  Very bad idea.... Bad things can happen.  That is why there is a root account.

---

### Post by freesitebuilder on 2007-04-19
This is a useful article on using root:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PowerPLay on 2007-04-19
ok,

So, if this is such a bad idea then how do i get the computer to let me read/write to my external. I really dont want to use terminal. I should be able to do this in gnome gui somehow. 

THe external is ext3 file system.

Gnome automounts it on my desktop but i cant manipulate it in any way. I can read but not write.

What do i do.?

-PP

---

### Post by Nizzle on 2007-04-19
my Ubuntu is dutch but it's prolly in the same thing..

System -> Administration -> Login screen --> Security 

and then there is a checkbox to enable root logins ;)

---

### Post by aysiu on 2007-04-19
You don't need to enable a root login, and you shouldn't enable one.

This will give you access to your Ext3 drive:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by scanez on 2007-04-19
Plug in your drive and let gnome automount it as usual. Then open up a terminal and  run

> sudo chown username.username /media/disk

to change the owner and group of the directory representing your drive (where username is replaced by your username, and assuming your drive is mounted as /media/disk). Then you can access it as your normal user. This should only have to be done once -- next time you plug in your drive again it should mount it as your normal user and you shouldn't have any problems.

---

### Post by teddybairs1 on 2007-04-19
I used to be annoyed with not being able to login as root, also. I was used to it in linspire and didn't see why I was locked out of it.

But the more I use my system, the more I see the wisdom behind it. It's an added layer of security to keep the user, even the root user, from doing things to their system, accidentally of course, which could be fatal. By making you continue to give your password and jump through a few hoops it's making sure that it really is root making those changes and not someone or something else which shouldn't be. The truth is that it is far too dangerous to run as root, especially if you're online and another hacker wants to have fun.

---


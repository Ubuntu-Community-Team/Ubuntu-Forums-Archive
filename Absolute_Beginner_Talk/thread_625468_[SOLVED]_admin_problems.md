---
title: "[SOLVED] admin problems"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by bazarov707 on 2007-11-28
I just installed ubuntu 7.04 on my desktop and I can't log in as an administrator. Whenever I try to do anything like install programs it comes up with something that says I'm not an administrator, but I know the password and I only created one account. What am I supposed to do?

---

### Post by meanburrito920 on 2007-11-28
ubuntu does not create a default root user. the password to the original account you created should suffice for any administrator password it asks for. you could also try sudo apt-get to install programs as administrator

---

### Post by aysiu on 2007-11-28
Read these two links:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vikramsharma on 2007-11-28
> **bazarov707 said:**
> I just installed ubuntu 7.04 on my desktop and I can't log in as an administrator. Whenever I try to do anything like install programs it comes up with something that says I'm not an administrator, but I know the password and I only created one account. What am I supposed to do?

Ubuntu has root login disabled by default (on the desktop), you can change the root password by going to "System"_>"Administration"_>"Users and Groups".  Here you would be prompted to enter the user password you set for the purpose of security.  In there you would see at least two users one being you and the other being root.  Select root and click on properties, In the "Password section" of root properties choose the "Set password by hand" radio button.  Type in the password in the field and confirm it, as instructed in the dialog box.  You should be able to log in as root through shell without any problems.  You can also enable root login on the Desktop also, I would personally advice against it..  Hope what I said helps you out.

---

### Post by aysiu on 2007-11-28
> **vikramsharma said:**
> Ubuntu has root login disabled by default (on the desktop), you can change the root password by going to "System"_>"Administration"_>"Users and Groups".  Here you would be prompted to enter the user password you set for the purpose of security.  In there you would see at least two users one being you and the other being root.  Select root and click on properties, In the "Password section" of root properties choose the "Set password by hand" radio button.  Type in the password in the field and confirm it, as instructed in the dialog box.  You should be able to log in as root through shell without any problems.  You can also enable root login on the Desktop also, I would personally advice against it..  Hope what I said helps you out.
There's really no need to enable a root login or set a root password.

> **bazarov707 said:**
> I just installed ubuntu 7.04 on my desktop and I can't log in as an administrator. Whenever I try to do anything like install programs it comes up with something that says I'm not an administrator, but I know the password and I only created one account. What am I supposed to do?

> **bazarov707 said:**
> I just installed ubuntu 7.04 on my desktop and I can't log in as an administrator. Whenever I try to do anything like install programs it comes up with something that says I'm not an administrator, but I know the password and I only created one account. What am I supposed to do? By what method are you installing programs that you are being told you're not the administrator? If you go to Add/Remove or System > Administration > Synaptic Package Manager, your own user password should work.

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by vikramsharma on 2007-11-28
Enabling the root account is an overkill most of the times as one can do almost everything as sudo.  There are times through being logged in as root helps, in case you want to compile an app, I had permissions problems as sudo while compiling mplayer rc2, logging in as root helped me a lot.  Same thing for updating alsa drivers too, had to log in as root or the modules wouldn't install.

---

### Post by bazarov707 on 2007-11-30
okay, in my system>administrator> menu the only options I have are keyring manager, network tools,  printing, system log, system manager, and update manager. I do not have a add/remove programs option anywhere. When I try to install a program manually it comes up with a window that says:

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.''

---

### Post by Znort_Ubern00b on 2007-11-30
check oiut this link

read anacondas post

[http://ubuntuforums.org/showthread.php?t=626559&highlight=admin+group]("http://ubuntuforums.org/showthread.php?t=626559&highlight=admin+group")that should sort you out.

you prob dont need the first **adduser** command just the **adduser (yourusername) admin**

this will then enable you to use the sudo command

---

### Post by bazarov707 on 2007-11-30
If I push alt+f2 and enter gksudo nautilus nothing happens

---

### Post by Znort_Ubern00b on 2007-11-30
try looking at the thread i posted...seemed to sort out his problem which relates to yours as he needed admin access too.

you are currently not in the admin group hence the reason your menu is not as full as it should be.

---

### Post by bazarov707 on 2007-11-30
> **Znort_Ubern00b said:**
> try looking at the thread i posted...seemed to sort out his problem which relates to yours as he needed admin access too.

you are currently not in the admin group hence the reason your menu is not as full as it should be.

yep, that fixed it. thanks a ton

---

### Post by Znort_Ubern00b on 2007-11-30
no worries...don't forget to mark the thread solved.

---

### Post by bazarov707 on 2007-11-30
I must be having a brain fart tonight. normally I'm fairly astute... I can't even figure out how to mark the post as solved

---

### Post by Znort_Ubern00b on 2007-11-30
at top of thread you have thread tools...in there is mark solved.

---


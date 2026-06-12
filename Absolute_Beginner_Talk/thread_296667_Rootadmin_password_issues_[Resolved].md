---
title: "Root/admin password issues [Resolved]"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by wildsrv on 2006-11-09
Hello every one and if i'm right this is my first post. :mrgreen: 

OKOK i've been playing with linux for about 2 years (few days here and there) more like a total of about 4 weeks. My issue right now is i can't seem to login as root or change user settings. I've searched and fould a command sudo -i and sudo password root but after i enter a password it just goes back to the promt. I don't think my current user (first and only user currently) has much admin rights because i can't even see user settings to make changes or any thing. I'm trying to be as clear as possible but not knowing enough about *nix i'm at a loss. Thanks

---

### Post by yabbadabbadont on 2006-11-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I think that answers most of your questions.  If not, ask away.  :D

---

### Post by wildsrv on 2006-11-10
Thaks for the reply but i've read that thread already :( If it helps in explnation that i don't even have this option
System --> Administration menu--> Users and Groups tool
From what i have read Ubuntu by default has root disabled. In addition sudo uses the users password as a conformation in a matter of speaking. I tried to boot in recovery mode (which is root from what i've heard) but that takes me sright to the prompt. I am not familiar enough with the promt and can't even remember how to start KDE or any other GUI from there to start to edit some things (which is not smart to do with root but at least i could assign me as admin rights).](*,)  Please give me some advise/help.

Thanks

---

### Post by aysiu on 2006-11-10
No, you understand it just fine.

The root account isn't fully disabled, though. For example, when you boot into recovery mode, you are logged in as root.

This is the bottom line:

If you want to run a command as root, just preface it with *sudo*. For example ```
sudo aptitude update
``` instead of ```
su
aptitude update
exit
```

If you want to run a graphical command as root, just preface it with *gksudo*. For example ```
gksudo nautilus
``` instead of ```
su
nautilus
exit
``` In both cases (*sudo* and *gksudo*), always use your user password to authenticate. There is no root password. Forget about root.

---

### Post by digby on 2006-11-10
I'm afraid that I'm really not sure what you are trying to do.  Can you be a little more detailed about what you are wanting?

A few other questions:
Why did you try to use the recovery cd?
Do you have KDE installed? (if so, you can select it from the options > sessions menu on the log-in screen)

Also, could you post the output of```
 cat /etc/group | grep ^admin
```

---

### Post by wildsrv on 2006-11-10
Sorry i guess i never stated my MAIN issue. It won't let me. I'll run some thing simple (i don't have an example) but "sudo command" and it will promt for password. I'll enter My password and it will go right back to the promt with what looks like not doing a darn thing. I know i tried to do some command that updated the database then install updates and it looked like it didn't do any thing. Hope this helps. In addition like i said before how to i assign my self rights or privliages to click on system>administration> user groups or any of the other normal stuff. It is not even on my menu.

nathan@nathan-desktop:~$ cat /etc/group | grep ^admin
admin:x:112:root
nathan@nathan-desktop:~$

---

### Post by aysiu on 2006-11-10
Does this help?
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by wildsrv on 2006-11-10
> **aysiu said:**
> Does this help?
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)


athan@nathan-desktop:~$ sudo visudo
nathan@nathan-desktop:~$

it usualy asks for a password but it didn't this time. :-k

---

### Post by digby on 2006-11-10
Hmm... from the output of his /etc/group, it looks like his account isn't a member of the admin group (and therefore has no sudo privileges)... I have no idea how that could have happened.

To wildsrv:  one thing about unix that seems counterintuitive at first is that when you run a command successfully, it will return no output.  For example if you copy a file or run updatedb, it will just put you back at the prompt unless there was an error in the process.

---

### Post by wildsrv on 2006-11-10
ok i'm not use to not having "file copyed ok or succesfully..." thanks for that.
the only other thing i'm worried about is i know in *nix if you loose the root password there is no recovery. IE winblows has some hacks that can crack it.

---

### Post by aysiu on 2006-11-10
> **wildsrv said:**
> ok i'm not use to not having "file copyed ok or succesfully..." thanks for that.
the only other thing i'm worried about is i know in *nix if you loose the root password there is no recovery. IE winblows has some hacks that can crack it.
As long as you have a live CD of some kind (Ubuntu Desktop CD or Knoppix), you can always recover being in the *admin* group to *sudo* or reset the root password.

By the way, did you take a look at the link I posted? That will get you back in the admin group.

---

### Post by wildsrv on 2006-11-10
aysiu,

Sorry i missed that and it fixed my issues. I edited the sudoers and added under root my user name and copyed the alls. But i did the addgroup username admin and that worked great. THANKS ALL!!!!!!!!!!

---


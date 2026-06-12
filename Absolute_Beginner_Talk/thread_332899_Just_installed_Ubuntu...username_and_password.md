---
title: "Just installed Ubuntu...username and password?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by dressedinvalue on 2007-01-06
Hi. I'm new to Ubuntu and Linux the same. I just installed Ubuntu on an old laptop (took a looooong time!) and now it's loading up asking for a username and password. Forgive me if this makes me sound really really stupid (I promise I'm not--I'm a professional Mac user and have grown up on pc's), but I certainly don't remember specifying a username or password while installing Ubuntu. And now I can use the computer. Is there a way to find out what the U/P is?

Sorry, and thanks.

---

### Post by taurus on 2007-01-06
Did you use the alternate CD to install it on you laptop?  Bet you picked the oem version...  Therefore, your username is oem and your password is whatever the password that you have created during the installing.  And right after you log in, open a terminal, Applications -> Accessories -> Terminal, and run this command.

```
sudo oem-config-prepare
```

---

### Post by dressedinvalue on 2007-01-06
Holy cow! Double holy cow!

Fast reply. And, it works. Thanks! Yes, I installed OEM. I guess I shouldn't have done that. Don't know why I did. Anyway, I'm thinking about installing Xubuntu instead, because my laptop is quite the oldie. It's an old Toshiba Satellite 2100CDT (Some AMD-K6 with 128mb).

Linux feels an exciting place to be, but it's no help that none of the Linux sites post system requirements for the software. It makes it hard to choose.

Thanks again for the help!

---

### Post by taurus on 2007-01-06
With 128MB of RAM, definitely go for Xubuntu or even the fluxbuntu...  And if you plan to download Xubuntu, please use the alternate CD and pick the first option (second option is the oem one) to install it on your laptop.

[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/)

---

### Post by d3v1ant_0n3 on 2007-01-06
I'd definitely give Xubuntu a try with that amount of RAM. Alternatively, try IceWM or FVWM (both are available in the repos, search in Synaptic Package Manager). They don't have the 'bling' of GNOME or even XCFE, but dang are they fast:D  Fluxbox is apparently very quick too, but I've yet to manage to get it set up properly. It hurts my brain.

---

### Post by Rasidrew on 2007-02-18
I had the same problem.  I installed the OEM version, but it will not accept oem as my username.  What else can I do to log in?

---

### Post by taurus on 2007-02-18
Boot into recovery mode and at the prompt, post the output of this command here.

```
ls -la /home
```

---

### Post by Rasidrew on 2007-02-18
I used the useradd -m username command, and created a username and password, and logged on.  However, now when I try to add this user as a super user in Users and Groups, it tells me that my users-admin password is incorrect.  I've tried both my root password and my user name password.  Any help would be appreciated.

---

### Post by taurus on 2007-02-18
Boot into recovery mode and do

```
adduser **username** adm admin
```
And replace the **username** with the actual name of your login.

---

### Post by Rasidrew on 2007-02-18
Tried adduser username adm admin and got a return "adduser: Only one or two names allowed".  Then I tried adduser username adm, which added the username to that group.  I also tried adduser username admin, and got a return "the group admin does not exist".  When I logged into Ubantu and tried to access user and groups, it still refused to accept my password.

---

### Post by taurus on 2007-02-18
Which release do you have?  And what's the output of this command from a terminal?

```
cat /etc/group
```

---


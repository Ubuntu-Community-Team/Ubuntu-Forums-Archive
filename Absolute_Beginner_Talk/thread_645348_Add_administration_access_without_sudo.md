---
title: "Add administration access without sudo"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-12-19
Hi all,


  How can I provide a limited user with access to administration tools (login window, network) without adding him as an administrator? 

Thanks,


Vic.

---

### Post by Severun on 2007-12-20
You can use sudo to allow certin users to only do certain things, i.e. if john sudo's he can do anything whereas sally can only run certain commands.  Do a "man sudo" for more info there.  You can achieve this functionality by putting the right entries in the /etc/sudoers file.

You can also do things like grant the privileges of access to certain things by using groups and ownerships, i.e. chmod, chown, chgrp.

If you really want to get fancy you can create what's called a chrooted environment where they can run things as root, but the are in a virtual area where they can only see things in their directory (This is usually how ISP's that provide shell accounts to people are set up).

---

### Post by victorbrca on 2007-12-20
> **Severun said:**
> You can use sudo to allow certin users to only do certain things, i.e. if john sudo's he can do anything whereas sally can only run certain commands.  Do a "man sudo" for more info there.  You can achieve this functionality by putting the right entries in the /etc/sudoers file.

You can also do things like grant the privileges of access to certain things by using groups and ownerships, i.e. chmod, chown, chgrp.

If you really want to get fancy you can create what's called a chrooted environment where they can run things as root, but the are in a virtual area where they can only see things in their directory (This is usually how ISP's that provide shell accounts to people are set up).

I have one user setup as an administrator (sudoer) and I want the other user to have access to the "login window" configuration, without being part of the administrator group. 

I have CHROOT setup on another machine but it's not exactly what I'm trying to do here.

I'll do some reading on the man pages for sudo tomorrow. Thanks a lot!!!


Vic.

---

### Post by victorbrca on 2007-12-20
I did read the sudo man pages but could not find anything. As far as I understood you need to be in the sudoer file to be able to run anything. 

  Is there a group other than administrator that I can add this user to so she can have access to "gdmsetup" ?? I don't want her to have special permissions, all I want is for her to be able to see and modify the login window.

Thanks,

Vic.

---

### Post by bodhi.zazen on 2007-12-20
No, the point of sudo is to give you this finer grain of control.

See this link, scroll down :

[http://aplawrence.com/Basics/sudo.html](http://aplawrence.com/Basics/sudo.html)

---

### Post by victorbrca on 2007-12-20
> **bodhi.zazen said:**
> No, the point of sudo is to give you this finer grain of control.

See this link, scroll down :

[http://aplawrence.com/Basics/sudo.html](http://aplawrence.com/Basics/sudo.html)

Awesome link... :)

So I should guess that in my case I would append the following line to /etc/sudoers:

```
username        ALL = /usr/sbin/gdmsetup
```

And that would give her access to the login window, however it would prompt for a password. Did I get it right?


Vic.

---

### Post by victorbrca on 2007-12-20
Ok, I was able to test it an it works. But I'm getting an X error when trying to open gdmsetup from the terminal. It looks like it won't let another user use the running xserver.

> Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

If I run this it works:

```
xhost +
sudo gdmsetup &
# after I'm done
xhost -
```

Anyone knows why?

```
echo $DISPLAY
:1.0
```

Vic.

---

### Post by bodhi.zazen on 2007-12-21
yes, that will work, except the user will not be able to open X

To fix this second problem, run visudo and look at the "Defaults" line.

You need to add : env_keep+="DISPLAY XAUTHORITY" 
to the end, like this :

> Defaults        !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY XAUTHORITY"

Then you should be good to go. :twisted:

========

Oh, and yes, this requires the user to put in their (log in) password. From the link I gave you, you should know how to set no password.

---

### Post by victorbrca on 2007-12-21
Cool... I'll try this tonite. 

So I guess I have to force XAUTHORITY to open other user programs within my running X...


Vic.


===================

EDIT: Found it!!

# env_keep is just a variable that holds anything to be preserved in the user's account in this case being used to access the X display.

[Thread]("http://ubuntuforums.org/showpost.php?p=3066782&postcount=41")

[X with sudo, su, and friends]("http://process-of-elimination.net/index.php?title=X_with_sudo%2C_su%2C_and_friends")


Vic

---


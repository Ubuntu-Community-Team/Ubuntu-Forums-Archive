---
title: "[SOLVED] ssh enable X11 forwarding"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by davidc502 on 2007-12-01
A little background... I've been using Putty for about 3 years. I've used it to ssh into the servers at work and then use the applications by forwarding the "DISPLAY". I haven't had any problems doing this from XP using ReflectionX or Suse linux. Now that I've installed Ubuntu, I can't seem to export the  DISPLAY to my Ubuntu. 

This is the current error I get when I try to forward xclock.
# /usr/openwin/bin/xclock
Xlib: connection to "10.xxx.xxx.xxx:0.0" refused by server
Xlib: No protocol specified

I'm getting this though I have the option to forward X11 with Putty.

I have unchecked the "deny TCP connections" to my xserver option in "login windows preferences"
This is my ssh-config file
# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
   ForwardX11 yes
   ForwardX11Trusted yes
#   RhostsRSAAuthentication no

The rest has been omitted.


Any suggestions welcome.

Thanks,

David

---

### Post by kmac on 2007-12-01
do you have any problems with 
```

~> ssh -X user@host_or_ip 

```

---

### Post by davidc502 on 2007-12-01
I tried that in command line "ssh [email]username@10.xxx.xxx.xxx[/email] -X"  and I get the same error.

Thanks for asking.

---

### Post by davidc502 on 2007-12-01
PROBLEM SOLVED:

Before ssh to remote box, I issued the following command xhost 10.xxx.xxx.xxx and Ubuntu comes back and says this IP has been added to the access-list.

I can now export the DISPLAY and administrate the applications remotely on my Solaris systems.

Solution was to issue the xhost command.

I'm not certain on how to lock this thread or make it solved.


Solved.

---

### Post by Dr Small on 2007-12-01
To mark it solved, go to Thread Tools.

By the way, I wrote an article on my blog as how to run x applications remotely:
[http://php.8ez.com/drsmall/blog/?p=181](http://php.8ez.com/drsmall/blog/?p=181)

---


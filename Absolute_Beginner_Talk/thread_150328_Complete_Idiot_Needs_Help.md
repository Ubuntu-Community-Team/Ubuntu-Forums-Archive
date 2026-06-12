---
title: "Complete Idiot Needs Help"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by dpoehls on 2006-03-25
After thinking about it for years, I decided to install Linux on my computer (AMD XP). When installing I chose all the defaults. After a few glitches I got it up and running. Although I THINK it may have to do with priveleges, I cannot seem to load a lot of the SYSTEM applications such as Synaptic, Update Manager, etc. When I choose one of them, sometimes they APPEAR to be loading but then nothing happens. It is like they want to start, see that this idiot is on the computer and then refuse to go any further. I understand that the first User created (that being me) during the install has full administrator priveleges. I have tried to log off and log back on as ROOT, but it tells me I cannot log on as ROOT from that screen (log-on screen). Coming from many years of Windows, I find it sort of frustrating that I cannot even begin to use the vast world of Linux! Thanks!

---

### Post by trent dillman on 2006-03-25
Try running something from the terminal (Applications > Accessories > Terminal)

```
sudo synaptic
```

put in your password when it asks, then post the output.

---

### Post by jrib on 2006-03-25
[QUOTE=dpoehls]After thinking about it for years, I decided to install Linux on my computer (AMD XP). When installing I chose all the defaults. After a few glitches I got it up and running. Although I THINK it may have to do with priveleges, I cannot seem to load a lot of the SYSTEM applications such as Synaptic, Update Manager, etc. When I choose one of them, sometimes they APPEAR to be loading but then nothing happens. It is like they want to start, see that this idiot is on the computer and then refuse to go any further. I understand that the first User created (that being me) during the install has full administrator priveleges. I have tried to log off and log back on as ROOT, but it tells me I cannot log on as ROOT from that screen (log-on screen). Coming from many years of Windows, I find it sort of frustrating that I cannot even begin to use the vast world of Linux! Thanks![/QUOTE]

You shouldn't have a root account unless you did an expert install.  Did you do an expert install?  If you did, then we probably have to fix your sudo.

What does this command in applications > accessories > terminal do:
```
sudo echo hi
```

and this one:
```
gksudo synaptic
```

---

### Post by bored2k on 2006-03-25
Ubuntu saves you from the potentially dangerous root account by using sudo (this is NOT a "that is not true" thread!). For more information on how to handle sudo, check [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) .

---

### Post by IYY on 2006-03-25
Indeed, you cannot login as root in Ubuntu. However, these apps should launch after you type your password. This is a rather annoying bug that I've seen a couple of people have, not your fault. Here are some similar threads:

[http://www.ubuntuforums.org/showthread.php?t=145764&highlight=admin+applications](http://www.ubuntuforums.org/showthread.php?t=145764&highlight=admin+applications)

[http://www.ubuntuforums.org/showthread.php?t=86879&highlight=admin+applications](http://www.ubuntuforums.org/showthread.php?t=86879&highlight=admin+applications)

[http://www.ubuntuforums.org/showthread.php?t=75722&highlight=admin+applications](http://www.ubuntuforums.org/showthread.php?t=75722&highlight=admin+applications)

---

### Post by dpoehls on 2006-03-25
dennis@ubuntu:~$ gksudo synaptic
dennis@ubuntu:~$ sudo synaptic
dennis@ubuntu:~$

When I go into Terminal this is what I get. I have tried sudo and I have tried gksudo. Once, it prompted me for my password, but then nothing happened..Synaptic did not load. I MUST be missing something here!

---

### Post by jrib on 2006-03-25
[QUOTE=dpoehls]dennis@ubuntu:~$ gksudo synaptic
dennis@ubuntu:~$ sudo synaptic
dennis@ubuntu:~$

When I go into Terminal this is what I get. I have tried sudo and I have tried gksudo. Once, it prompted me for my password, but then nothing happened..Synaptic did not load. I MUST be missing something here![/QUOTE]

did you do an expert install?

(If you set a root password during the install, that means you probably did an expert install)
If that is true, try entering ```
su
``` and then your root password.

If that worked, great, now enter ```
cat /etc/sudoers
``` and paste the output here. 

Then exit out of su, type ```
exit
``` and give us the output of the following:
```
id && groups
```

---

### Post by dpoehls on 2006-03-25
Well, I seem to be learning SOMETHING, but it goes slowly. If I begin by typing in "su" intot he terminal it prompts me for my password and then it seems to log me in as ROOT. From that point, I CAN run system apps by simply typing in the name, such as synaptic. While I am running these programs, I have noticed that a bunch of little error messages appear in Terminal... If I close Terminal, all the system apps I have started will simply disappear. i DID manage to update by typing in update-manager.  Per the suggestion of the last poster to this thread, here is what I get when I type cat /etc/sudoers:

root@ubuntu:/home/dennis# cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
root@ubuntu:/home/dennis#

When I go back and type in id && groups , I get the following:

dennis@ubuntu:~$ su
Password:
root@ubuntu:/home/dennis# id && groups
uid=0(root) gid=0(root) groups=0(root)
root
root@ubuntu:/home/dennis#

i DID NOT do an EXPERT INSTALL but simply installed using the defaults.

---

### Post by jrib on 2006-03-25
you missed a step.  I want you to do ``id && groups'' as your user, not as root

---

### Post by dpoehls on 2006-03-26
This is what I get when I type in id && groups into the terminal with my own login:

exit
dennis@ubuntu:~$ id && groups
uid=1000(dennis) gid=1000(dennis) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(dennis)
dennis adm dialout cdrom floppy audio dip video plugdev lpadmin scanner
dennis@ubuntu:~$

So, from what I can see here, I AM a member of many groups, including ADM (which I am assuming is admin)

---

### Post by jrib on 2006-03-26
[QUOTE=dpoehls]This is what I get when I type in id && groups into the terminal with my own login:

exit
dennis@ubuntu:~$ id && groups
uid=1000(dennis) gid=1000(dennis) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(dennis)
dennis adm dialout cdrom floppy audio dip video plugdev lpadmin scanner
dennis@ubuntu:~$

So, from what I can see here, I AM a member of many groups, including ADM (which I am assuming is admin)[/QUOTE]

actually it's usually the admin group that gets set up in sudo.  Here do this as root (su to root):

```
addgroup --system admin; echo "%admin ALL=(ALL) ALL" >> /etc/sudoers && adduser your_normal_username admin
```

That should get your sudo working and admin apps working.  If not, try logging out and back in with your user.  I suggest you follow the instructions at [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for disabling root once you verify sudo is working.

---

### Post by dpoehls on 2006-03-28
Great. This worked perfectly.

---


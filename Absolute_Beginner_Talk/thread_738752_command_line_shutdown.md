---
title: "command line shutdown"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by brdohman on 2008-03-28
I need to be able to shutdown a running ubuntu liveCD through the terminal without having terminal access.  

I know I can do sudo shutdown -h and have it shutdown, but is it possible to do this without having sudo or root access on the terminal? 

I though I remembered a /force option, but can't seem to find anything about it.

Thanks

---

### Post by Joeb454 on 2008-03-28
I don't think you can shutdown in a terminal without using Sudo, or being logged in as Root.

I do know it's possible to edit the /etc/sudoers file to allow you to use sudo shutdown * without entering a password :) But if you venture into editing that file you're treading dangerous ground.

---

### Post by p_quarles on 2008-03-28
Two things that you'll need to explain before anyone will be able to offer useful advice:
1) What do you mean by using the terminal without having terminal access?
2) Why wouldn't you have root privileges on a live CD?

---

### Post by alexforcefive on 2008-03-28
I usually type shutdown -h now. Pretty sure you don't need to be sudo, but I am frequently wrong :)

---

### Post by Joeb454 on 2008-03-29
You do have to run as root (i.e. - Use sudo) :)

I'm always using ```
sudo shutdown -P now
``` :) **EDIT:** I think the OP might want a script to shutdown? I'm not too sure either **p_quarles**

---

### Post by s3a on 2008-03-29
On a live cd, the password is nothing so sudo stuff should work.

---

### Post by brdohman on 2008-03-29
I'm in the process of creating a custom liveCD, and the main user will not have root access.  I'm using a java program that I wrote to keep track of the users time using the liveCD.  Once 60 mins is up, I need to be able to shutdown the machine.  

i'm going to boot up and try sudo shutdown -h now and see if that works.

once i see the response, i'll get back with an answer

---

### Post by Catalyst2Death on 2008-03-29
If memory serves, you can run sudo commands without a password on the Live install... Don't quote me, I know for sure that you can't use shutdown without root (I just tried :P)

"Root is created without predefined password, it does not have a password, but it does not have an empty password either, you just can't login!!!"

you can read more about this here:
[http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way](http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way)

which I think would allow you to set up a temporary root password for the particular live session, allowing you to use shutdown...

you could always use the magic print screen key as well (or ctl+alt+del)
[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

---

### Post by brdohman on 2008-03-29
I attempted to do the shutdown, and it allows me to do sudo shutdown -h now, and then asks for the user password, and i give it and then nothing happens.

Any ideas on how I might be able to make this possible?

---

### Post by dsauxier on 2008-03-29
If you want the PC to shutdown after 60 minutes, just add this to /etc/rc.local 
(this also eliminates the need for java timer)
```

shutdown -h 60

#or if you want to give them an extra minute 
#to make up for the time it takes gnome, etc to start

shutdown -h 61

```

---

### Post by brdohman on 2008-03-29
Can i just add that code into the rc.local file in any spot?  or does it need to be before or after the exit 0

Also, when does this timer take effect?  Does it start after login occurs?

Thanks

---

### Post by N1N31NCHN41L5 on 2008-03-29
how do u become root???

---

### Post by dsauxier on 2008-03-29
It should go after all of the comments (comments start with a "#" character)
And then it should go before the "exit 0"

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

shutdown -h 61

exit 0

```

---

### Post by dsauxier on 2008-03-29
> **N1N31NCHN41L5 said:**
> how do u become root???

Using "sudo" in front of any command runs that command as root (sudo=SuperUserDO)
[INDENT]Example : 
$ whoami
user
$ sudo whoami
root
[/INDENT]
If you have a lot of commands to run as root and don't want to add sudo in front of all of them, you can : 
```
sudo su - root
# or simply
sudo su
```

---

### Post by p_quarles on 2008-03-29
If you are creating a custom live CD, then you should be able to edit the included /etc/sudoers file. Give the default user the privilege to run /sbin/shutdown without a password, and then make an easy to remember alias for:
```
sudo shutdown -h now
```

---

### Post by 3rdalbum on 2008-03-29
Why use sudo shutdown -h now, when you can simply do sudo halt?

The sudoers file is one way to do it. The other way is to make "shutdown" or "halt" setuid commands.

I'm not sure exactly how to do this in the terminal, but I think you do it with the chmod command. In Gnome, you'd open a root file browser, and if you've got "advanced permissions editor" turned on in gconf, you can choose "Set User ID" in the Permissions tab of /sbin/halt.

Setuid means that when the program runs, it runs with the permissions of the program's owner, not of the user who initiated it.

---


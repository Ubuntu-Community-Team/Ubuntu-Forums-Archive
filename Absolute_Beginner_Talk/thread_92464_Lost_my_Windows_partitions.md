---
title: "Lost my Windows partitions"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by bob phillips on 2005-11-19
just loaded up Ubuntu and dual-booting with Win2k

but

i can't use 'discs' to see my FAT windows partitions - it asks for my password, i give it my user one (not the separate ROOT one i entered during install) - it whirrs a bit and then shows me nothing.

(not even a 'discs' window)

and

i tried the FAQ methods for automatically and manually mounting drives, but every time i try something like
```
 sudo fstab -l 
```
it asks me for my password, i do as above, and i get the bob~ thing coming up without a  list of drives

have i biggered something up bigtime?

(the partition i'm running Ubuntu on is about 4GB, which is twice what i thought i needed...)

hoping for a miracle,

bob

---

### Post by Chayak on 2005-11-19
Odd that it has asked you for a root password.  I haven't had it ask me yet.  By default Ubuntu doesn't mount your windows drives.    Try this at the command line for ntfs drives.
```
sudo mkdir /mount/windows (or whatever you want to call it)
sudo mount /dev/(your drive and partition hda1, etc) /mount/windows -t ntfs
```
I could be more specific but I need your drive layout.

---

### Post by juicybananahead on 2005-11-19
Hi Bob,

Does sudo work with anything? Does anything happen when you input your password after you select anything in System->Administration? If nothing does, did you by any chance choose the expert mode when you were installing?

/juicy

---

### Post by estel on 2005-11-19
Sudo allows you to preform administrative tasks.

Sudo before a command, will preform it as a "super user" with complete previledges to edit anything that a normal user doesn't have.

"Disks" doesn't work for me at all, so I'd just stick with command prompt.

---

### Post by bob phillips on 2005-11-19
thanks for the replies, guys

nothing in sytem > admin seems to work

as yes - juicybanana - i did use expert install (cause of a previous FAQ about squueeezing ubuntu into less than 10GB)

can i ever recover from pretending to be expert? (honest, i just did the defaults)

---

### Post by estel on 2005-11-19
What settings did you put? In all honesty, it probably didn't harm the system that much.

After it asks you for the admin password, does it just... disappear? Or tell you off for wrong password?

Try running ```
sudo synaptic
``` from the console. What does that do?

---

### Post by bob phillips on 2005-11-19
estel, i just put in all the defaults 

it doesn't actually ask for an admin password, it just says 'password' - if i give the admin one it says 'wrong', if i give my user one, it just ... does nothing 

(well, not quite - in system > admin a little start-of-a-window comes up saying 'starting discs' .. then goes away and does nothing)

---

### Post by estel on 2005-11-19
The one that it is asking for is the admin one that was for the FIRST user account on the computer - i.e. the password you entered during installation.
The admin and *that* user account passwords should be the same.

And what happens if you type the above in into the Terminal?

---

### Post by Mustard on 2005-11-19
[QUOTE=bob phillips]estel, i just put in all the defaults 

it doesn't actually ask for an admin password, it just says 'password' - if i give the admin one it says 'wrong', if i give my user one, it just ... does nothing 

(well, not quite - in system > admin a little start-of-a-window comes up saying 'starting discs' .. then goes away and does nothing)[/QUOTE]

Expert install sets up a root account and the first user account does not have administrative privileges.  To get administrative privileges you need to log in as root and run the visudo command and this will allow you to edit the /etc/sudoers file, in which you can add your user as an administrator.

Here is mine showing how I added myself;

```
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
mustard ALL=(ALL) ALL

```

To log in as root you would press ctrl + alt + f2, type in 'root' for the username and enter the root password.  Then you would do the necessary edits using the visudo command,  When you have finished doing that you would type 'exit' at the prompt to leave the root login and press ctrl + alt + f7 to return to your gnome desktop.

If you are having trouble working out how to do this try joining the ubuntu IRC help channel.

Server: irc.freenode.net
Channel: #ubuntu

Someone in there might be able to walk you through the process, and give you assistance along the way.

---

### Post by juicybananahead on 2005-11-19
Hi Bill,

I had a similar thing bothering me after I did an expert install (probably because I'm not an expert ;) ). The problem has to do with the fact that you're not able to sudo. Check out the post near the bottom of [http://www.ubuntuforums.org/showthread.php?t=77614](http://www.ubuntuforums.org/showthread.php?t=77614) for instructions to add yourself into the sudoers file.

Good luck!

---

### Post by bob phillips on 2005-11-20
following the marvellous instructions of juicybanana, i can now access all the files i ever wanted to

delighted!
:razz: 

many thanks to all for help received. now to try to do some work with it, not just play.

---

### Post by juicybananahead on 2005-11-20
Anytime. 8-)

---


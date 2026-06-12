---
title: "How do I log on as root"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by byteguy on 2008-04-17
I just loaded Ubuntu and all went well. I have instructions how to do the specific task I need to do but the instructions also say I have to be logged on as root. I tried logging off and back on as root but it won't let me. Same when I try to switch users. Any help what I am doing wrong?

---

### Post by Thelasko on 2008-04-17
Ubuntu doesn't handle root the same way other Linux distributions do.  Instead you have to put the command "sudo" before the command that requires root privileges.

sudo stands for "super user do"

---

### Post by chili555 on 2008-04-17
Ubuntu works with a process called [I]sudo.[/I ]Just open a terminal and do:```
sudo <command_you_are_trying>
```It will ask for your user password. Enter it, press Enter and off you go!

---

### Post by byteguy on 2008-04-17
Awesome, Thank You..

---

### Post by tnl2k7 on 2008-04-17
Not too sure if this is good practice, but when I'm typing a lot of commands that require root access, I just enter
```
sudo su
```
then just type the commands as you would if you were root, then close the session by typing
```
exit
```
twice. You can always unlock the root account (it's still there), but this is a security risk, the same as setting up the 'Administrator' account in Windows.

---

### Post by philinux on 2008-04-17
> **byteguy said:**
> I just loaded Ubuntu and all went well. I have instructions how to do the specific task I need to do but the instructions also say I have to be logged on as root. I tried logging off and back on as root but it won't let me. Same when I try to switch users. Any help what I am doing wrong?

Background info
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2008-04-17
> **tnl2k7 said:**
> Not too sure if this is good practice, but when I'm typing a lot of commands that require root access, I just enter
```
sudo su
```
then just type the commands as you would if you were root, then close the session by typing
```
exit
```
twice. You can always unlock the root account (it's still there), but this is a security risk, the same as setting up the 'Administrator' account in Windows.
I don't know why, but I've read several times here that it's better to use ```
sudo -i
```

---

### Post by LowSky on 2008-04-17
i use ```
sudo -i
``` 
it give you root privaleges for a for as long as you keep the terminal window open, once closed, root access goes away

---

### Post by tnl2k7 on 2008-04-18
> **aysiu said:**
> I don't know why, but I've read several times here that it's better to use ```
sudo -i
```

I'll remember that then. I just find it easier to type that once then not have to prefix every command with sudo, wastes time if you're writing loads of lines. Where possible I write shell scripts to save me doing loads of typing, i.e. on Ubuntu Server (I used to run a server for my games arcade) I used shell scripts to update the system, start up daemons and then clean out trash and archive/delete access/error logs.

---

### Post by compmodder26 on 2008-04-18
AFAIK "sudo -i" and "sudo su" do the same thing.  Can anybody explain a difference?

---

### Post by houstonbofh on 2008-04-18
> **compmodder26 said:**
> AFAIK "sudo -i" and "sudo su" do the same thing.  Can anybody explain a difference?
sudo -i is "super User Do, interactive" and sudo su is actually changing the login.  Where this is an issue is X.  With sudo -i you are still you, but with root power, so X apps open clean, and pathing is somewhat normal.  With sudo su, you are no longer you, but you are root, so you have to force X which can cause issues.  Your pathing is also changed which can cause other issues.  Clear as muddy water? :)

---

### Post by bodhi.zazen on 2008-04-18
Well, close ...

man sudo 

>  -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.

<clipped the rest of the man page entry for -i>



Both sudo and su give root access. With su you enter the root password and have full access.

With sudo you enter the user password and access to applications can be configured as needed.

See man su and man sudo for full details ...

su = swith user. If no user is given it defaults to root. You can su <username> to change to another non-root user. The current environment is passed to the new shell.

$PATH and $HOME are changed however.

the - = login and su - is the same as su -l , so new environment using root.

Example :

> bodhi@VirtualUbuntu:~$ echo $EDITOR
nano
bodhi@VirtualUbuntu:~$ sudo su
root@VirtualUbuntu:/home/bodhi# echo $EDITOR
nano
root@VirtualUbuntu:/home/bodhi# exit
exit
bodhi@VirtualUbuntu:~$ sudo su -
root@VirtualUbuntu:~# echo $EDITOR

root@VirtualUbuntu:~#

See how with sudo su the environmental variable, $EDITOR, was passed to root ? And not with su - ?

===========

sudo = switch user do

sudo defaults to root, but you can run as other users with the -u flag

Since the root account is locked, you can not su in Ubuntu. You can sudo su, as above.

if you sudo -s = user users environmental variables.

sudo -i = log in shell (use root's variables)

again :

> bodhi@VirtualUbuntu:~$ sudo -s

root@VirtualUbuntu:~# echo $HOME
/home/bodhi

bodhi@VirtualUbuntu:~$ sudo -i
root@VirtualUbuntu:~# echo $HOME
/root
root@VirtualUbuntu:~#

See how sudo -s uses your user $HOME ?  sudo -i = root's $HOME ?

So it is not so much as root access, they all give that, it is an issue of **how the environmental variables are handled**. This includes such things as $HOME, $EDITOR, aliases, $PATH, etc. For the gory details (of which variables are set how and when) you need to read the man pages ...

For example :

> bodhi@VirtualUbuntu:~$ alias ll='ls -lA'

bodhi@VirtualUbuntu:~$ sudo -i
root@VirtualUbuntu:~# ll
-bash: ll: command not found
root@VirtualUbuntu:~# exit
logout


bodhi@VirtualUbuntu:~$ sudo -s
root@VirtualUbuntu:~# ll 

<clip> gives listing of current directory <clip>

root@VirtualUbuntu:~# exit
logout

bodhi@VirtualUbuntu:~$ sudo su
root@VirtualUbuntu:/home/bodhi# ll
bash: ll: command not found
root@VirtualUbuntu:/home/bodhi# exit
exit

bodhi@VirtualUbuntu:~$ sudo su -
root@VirtualUbuntu:~# ll
-su: ll: command not found
root@VirtualUbuntu:~# exit
logout

bodhi@VirtualUbuntu:~$ ll

<clip> gives listing of current directory <clip>

And, as if that were not enough, check out su -m :

> -m 	Leave the environment unmodified. The invoked shell is your login shell, and no directory changes are made. As a security precaution, if the target user&#8217;s shell is a non-standard shell (as defined by getusershell(3)) and the caller&#8217;s real uid is non-zero, su will fail.

> bodhi@VirtualUbuntu:~$ sudo su -m

root@VirtualUbuntu:~# echo $HOME
/home/bodhi


:twisted:

---

### Post by tnl2k7 on 2008-04-19
It took me a minute to get my head around all that above, but I suppose now that which method you use depends on what you're trying to do. If you need access to the root user's folder for some reason (maybe a program stores logs there or something) you use
```
sudo su <command>
```
but when you want to just run a program with administrative permissions, you use
```
sudo -i <command>
```
Or at least, that's my understanding....someone'll probably tell me that's all wrong now :P

---

### Post by mister_pink on 2008-04-19
Not really, if you want to do one thing as root always just use 
sudo <command>

[or gksudo, see [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) ]

The above discussion is for when you want to do lots of things as root, and I think the conclusion is 
sudo -s
<command>
<command> etc
exit 

is the best way to do that. I think anyway...

---

### Post by bodhi.zazen on 2008-04-19
LOL, sorry about any confusion.

In Ubuntu, use ```
sudo -i
```

I a system without sudo (ie su) use ```
su -
```

---

### Post by tnl2k7 on 2008-04-20
Woah that really goes to show how many commands there are in Unix/Linux to do the same (or similar, in this case) things. I'll sleep easy tonight now. To the OP: just use
```
sudo <command>
```
unless you intend to use loads of commands, in which case I think I'd be right in saying
```
sudo -i
```
Linux is really simple until you get into a terminal and start typing in commands lol

---


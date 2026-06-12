---
title: "move folder"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-04
hi

i installed a program in ubuntu in a folder inside /home/username/program

i want to move this folder to a place i cannot see it like /home/program.

when i type :

> su

it asks for my password.. when i put it is says:
> 
su: Authentication failure
Sorry.

what should i do to move the folder to /home/program?

---

### Post by Medieval_Creations on 2006-10-04
su doesn't work in Ubuntu.  You need to just use sudo or gksu.

---

### Post by Ben Sprinkle on 2006-10-04
All you have to do is add root to your profile, I'll see if I can find some info.

---

### Post by Ben Sprinkle on 2006-10-04
> **Medieval_Creations said:**
> su doesn't work in Ubuntu.  You need to just use sudo or gksu.

That's incorrect 100%
You can use su in ubuntu.

---

### Post by whizbaby on 2006-10-04
sudo mv /home/username/program /home/program

su (without other arguments) means you want to login to the root account which is disabled (can be enabled) by default in ubuntu.

But putting a program/script/binary in the /home folder does not sound like a  very good idea (it's meant for users). Move it to /home/username/bin/program or /usr/sbin/program so you don't start a disorder.

---

### Post by Medieval_Creations on 2006-10-04
Apologies...

A few other of the posts that I have read said to just use sudo or gksu and I made the ever so fatal error of assuming it didn't work.  Thinking about it everything can work usually just needs more tinkering to do so.

---

### Post by cmaranhao on 2006-10-04
> **Goat Spirit said:**
> All you have to do is add root to your profile, I'll see if I can find some info.

this is what i've done:

system - administration - users and groups

[COLOR="Black"]under users tab[/COLOR], selected show all users and groups. 

[COLOR="Black"]in root[/COLOR], clicked properties, advanced and selected my name as main group. the user privileges are all selected.

[COLOR="Black"]in my name[/COLOR], i clicked properties, and set root as main group.the user privileges are all selected.

[COLOR="Black"]in groups tab[/COLOR], in root i added my name as a group member and in my name i added root as group members

the su does not work. help:???:

---

### Post by cmaranhao on 2006-10-04
> **whizbaby said:**
> sudo mv /home/username/program /home/program

su (without other arguments) means you want to login to the root account which is disabled (can be enabled) by default in ubuntu.

But putting a program/script/binary in the /home folder does not sound like a  very good idea (it's meant for users). Move it to /home/username/bin/program or /usr/sbin/program so you don't start a disorder.

that did not worked either. look at it:

> maranhao@maranhao-desktop:~$ sudo mv /home/maranhao/RealPlayer /home/maranhao/bin/realplayer
Password:
mv: cannot move `/home/maranhao/RealPlayer' to `/home/maranhao/bin/realplayer': No such file or directory
maranhao@maranhao-desktop:~$


---

### Post by anaconda on 2006-10-04
You dont have to enable root -account to get su to work.

But in ubuntu su is used with sudo
```
sudo su
```
will make you root until you tupe exit...

And there is a difference with just adding "sudo" in front of each command and using "sudo su".. With sudo you are who you were before, but you have root rights, but with "sudo su" you became user root..

---

### Post by whizbaby on 2006-10-04
To enable the root account (not recommended if you don't essentially (e.g. no local accounts) need it. Do you?) type
**sudo passwd**

this will ask for your password and then lets you set the password for root. After this **su** will work. (BTW undo all the (unhealthy) changes you did to your root and user account)

---

### Post by cmaranhao on 2006-10-04
> **anaconda said:**
> You dont have to enable root -account to get su to work.

But in ubuntu su is used with sudo
```
sudo su
```
will make you root until you tupe exit...

And there is a difference with just adding "sudo" in front of each command and using "sudo su".. With sudo you are who you were before, but you have root rights, but with "sudo su" you became user root..

the sudo su worked but i could not move the folder.look at this:
> 
maranhao@maranhao-desktop:~$ sudo su
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@maranhao-desktop:/home/maranhao# sudo mv /home/maranhao/RealPlayer /home/maranhao/bin/realplayer
mv: cannot move `/home/maranhao/RealPlayer' to `/home/maranhao/bin/realplayer': No such file or directory
root@maranhao-desktop:/home/maranhao#


i bet i am doing a basic step wrong (i only became linux administrator since saturday) so be gentle :-D

> **whizbaby said:**
> To enable the root account (not recommended if you don't essentially (e.g. no local accounts) need it. Do you?) type
**sudo passwd**

this will ask for your password and then lets you set the password for root. After this **su** will work. (BTW undo all the (unhealthy) changes you did to your root and user account)

what was the original configuration?i made so many changes so many times that i cannot remember how it was before :(

---

### Post by Ben Sprinkle on 2006-10-04
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Try reading that for some helpful information on thie subject. ;)

---

### Post by bulldog on 2006-10-04
Only put a . before the folder and he's hidden.

---

### Post by whizbaby on 2006-10-04
You'll have to create at least /home/maranhao/bin
**mkdir /home/maranhao/bin**

in your home you don't need root privileges:

**mv /home/maranhao/RealPlayer /home/maranhao/bin/**

(with what you tried before the folder /home/maranhao/bin/realplayer would have to exist and your command would have moved all to /home/maranhao/bin/realplayer/RealPlayer )

---

### Post by whizbaby on 2006-10-04
> **bulldog said:**
> Only put a . before the folder and **he**'s hidden.
That's the best for the desired invisibility! (BTW, folders have a gender?;) )
EDIT:
mv /home/maranhao/RealPlayer /home/maranhao/.RealPlayer

---

### Post by bulldog on 2006-10-04
> **whizbaby said:**
> That's the best for the desired invisibility! (BTW, folders have a gender?;) )

No idea,you may say it if you want :D :D

---

### Post by Ben Sprinkle on 2006-10-04
Cmar you see my post?

---

### Post by cmaranhao on 2006-10-04
> **whizbaby said:**
> That's the best for the desired invisibility! (BTW, folders have a gender?;) )
EDIT:
mv /home/maranhao/RealPlayer /home/maranhao/.RealPlayer

i've done it, thanks very much.credits to bulldog too but without the command lines i couldn't have done it.. big thanks to whiz!!

@ goat spirit, yes, i read it, thank you too :-D 

i am learning something new everyday :cool:

---

### Post by cmaranhao on 2006-10-04
> this is what i've done:

system - administration - users and groups

under users tab, selected show all users and groups.

in root, clicked properties, advanced and selected my name as main group. the user privileges are all selected.

in my name, i clicked properties, and set root as main group.the user privileges are all selected.

in groups tab, in root i added my name as a group member and in my name i added root as group members

the su does not work. help

can anyone help me get these settings back to normal? i've done so many combinations that i can't remember how it was.

---

### Post by Fedz on 2006-10-04
All you have to do to install RealPlayer is [download the .bin file](http://www.real.com/linux/?rppr=rnwk) and then double click it. Goto Home folder and it's their.

If any probs you just right click the .deb file and change the permission to 777 (read, write and execute) on all of 'em. Then double clcik it.

It install RealPlayer in your home directory (not hidden) - home > UserName > RealPlayer > realplay.

Hope this helps.

---

### Post by Fedz on 2006-10-04
> **Medieval_Creations said:**
> Apologies...

A few other of the posts that I have read said to just use sudo or gksu and I made the ever so fatal error of assuming it didn't work.  Thinking about it everything can work usually just needs more tinkering to do so.
Not to worry - technically you we're incorrect but, for the general everyday new user (as in this case) you were correct ;)

I also use the same commands as you - it's all I've ever read but, who cares if it works :D

Kind regards

---

### Post by LookTJ on 2006-10-05
> **Goat Spirit said:**
> That's incorrect 100%
You can use su in ubuntu.

yep ```
sudo su
```

---


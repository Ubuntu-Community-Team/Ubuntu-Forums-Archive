---
title: "Cannot do Administrative stuff"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by shizzler on 2006-02-24
Hi. I've just installed Linux, Ubuntu for the first time ever. Looks neat!

I've noticed that i've never been able to do anything 'Administrative' e.g. change the time or add applications from the menus on the desktop.

A friend recommended that i use:
usermod -g root myusername

to add myself to the root group in console mode using 'root'; i did that but nothing has changed.

What could i not have done?

---

### Post by fer5437 on 2006-02-24
Is it you using share pc? B'coz when installing time alone user should be in the root user. Whatever you want to make change you just need to put in the root password and it should be work fine.

---

### Post by mushroom on 2006-02-24
You use sudo for administrative operations. For example: when you want to change the clock and it prompts you for a password, instead of entering the root pass, you would enter your's. And for anything done in the terminal, you would type "sudo" in front of any command you want to execute as root, and likewise enter your password instead of root's.

I'm glad you're trying Ubuntu, it's a great OS if you give it a chance!

---

### Post by shizzler on 2006-02-26
Hi. What i've been doing is that i've been logging in from Recovery Mode so that i can execute commands from there. This makes the system begin from command prompt after inputing root password. I'm not aware of a way to do that from the desktop interface.

Anyway, when i click on, for example, "Add Applications" or "Adjust Date/Time" or "Users and Groups"  from the desktop menu, there is no response at all. There is no prompt for the root password. I wonder if it requires some kind of activation coz they must have been placed there for some reason.

Starting programs like Open Office or games work perfectly.

---

### Post by xhie on 2006-02-26
try to swich to root

in the terminal type : su
it will prompt you for a password, enter that

now your root.

But thats generally not the best way to go about doing stuff. 

if your in the terminal and you want to do something that requires root privledges run whatever command your trying to run with "sudo" in front of it

ex: sudo gedit somefile, instead of gedit somefile (erm.. if its a file you cant edit without being root, but you see what i'm saying)

---

### Post by Qrk on 2006-02-26
hmm, thats a bug. You should be able to do them all.

Type 

```
gksudo synaptic
```

into a terminal and post the output here. The synaptic should be fine, but hopefully gksudo will prompt some error messages. (synaptic is only there because I believe gksudo needs some command after)

---

### Post by xhie on 2006-02-26
>  Posted by tseliot in [this]("http://www.ubuntuforums.org/showthread.php?t=136097&highlight=sudoers+file") thread

Ok, it might be that you're not in the sudoers file

Boot in Recovery mode
then type:

nano /etc/sudoers

get to this part:
# User privilege specification
root ALL=(ALL) ALL

and add your username just below it

your_username ALL=(ALL) ALL

then save (CTRL+O)
and exit (CTRL+X)

then type:
reboot

log into recovery mode and do that if the other stuff dosent work

---

### Post by shizzler on 2006-02-26
Thanks Xhie for the quick reply.

I'll try that. Forgive me if i ask a silly question. I'm just trying to understand.

What do you mean by terminal? 

Does Ubuntu Linux require that even a change of Date require that this be done from command line? 

I'm wondering why its on the menu and its not active.

---

### Post by shizzler on 2006-02-26
Let me try that- typing the command to add me to sudoers.

Thanks alot for now.

---

### Post by xhie on 2006-02-26
[QUOTE=shizzler]What do you mean by terminal? [/QUOTE]

terminal = command prompt
Applications -> Accessories -> Terminal

Ubuntu has actually done a great job of implementing sudo. sudo privlidges are given to the first user you create after an install of ubuntu. Is the account your trying to work from not the first one created? If so, thats why you cant do administrative stuff. 

The other easy way to fix this without messing with the sudoers file is to go System -> Admistration -> users and groups, but from an account other then the one your on, the first one created would be a good choice, and make sure the account you want to have privledges actually has them, youll see a properties button and such in there.

---

### Post by shizzler on 2006-02-27
Xhie, the user i'm using isn't the first user i created.

I don't recall the first username created; but if that's the case, it really explains alot.

I created the current user from recovery mode.

---

### Post by mcduck on 2006-02-27
[QUOTE=shizzler]Xhie, the user i'm using isn't the first user i created.

I don't recall the first username created; but if that's the case, it really explains alot.

I created the current user from recovery mode.[/QUOTE]
You can easily find out the username if you look what directories are under /home.. There is one with every users name. :)

---

### Post by bikeboy on 2006-02-27
[QUOTE=shizzler]Thanks Xhie for the quick reply.

Does Ubuntu Linux require that even a change of Date require that this be done from command line? 

[/QUOTE]

No it's not that picky. Once you get the problem sorted out by following what the others have said, if you go to change the date (for example) you would right click on the date, click "Adjust Date & Time", and a little box will come up. Put your normal user password in there and you will be able to change those preferences.

Same goes for most (if not all) grpahical apps that require root privalages. Sudo covers the command line (Terminal) so you never have to log in as a different user to do admin stuff.

---

### Post by shizzler on 2006-02-27
I put my username in sudoers. Then proceeded to su from terminal and provided the root password. Didn't know what to to next.

Got "root@computer: /home/shizzler# "

Qrk had asked that i run: gksudo synaptic

Which ran successfully and opened Synaptic Package Manager(which i was glad to see!).

There was the follwing output on the terminal interface:

[COLOR="red"]root@computer: /home/shizzler# [/COLOR]gksudo synaptic
(synaptic:7983): Gtk-CRITICAL **:gtk_accel_label_set_accel_closure:assertion
gtk_accel_group_from_accel_closure (accel_closure)!=NULL' failed

(synaptic:7983): Gtk-CRITICAL **:gtk_accel_label_set_accel_closure:assertion
gtk_accel_group_from_accel_closure (accel_closure)!=NULL' failed


______________________
There is still no prompt when i try to click "Add Applications" or "Adjust Date/Time"

I will check the users directory to find which user i had created first. 

Suggestions are still highly appreciated.

---


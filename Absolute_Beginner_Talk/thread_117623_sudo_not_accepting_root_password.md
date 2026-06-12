---
title: "sudo not accepting root password"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Joshatdot on 2006-01-15
I 1st noticed this when starting Synaptic from the GUI, when it asked for root password it would not take it.

So I opened a terminal, ran the **su** command typed the password, I logged in and started synaptic from command line.

Then I tried **sudo synaptic** this also did not take my root password.



Also when I stated **synaptic** from command line I got these messages:

(synaptic:10900): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:10900): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

---

### Post by kosmic on 2006-01-15
When you use SUDO you use **YOUR USER PASSWORD** and **NOT THE ROOT PASSWORD** :)

---

### Post by aysiu on 2006-01-15
Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Joshatdot on 2006-01-15
Ok I am trying to run Synaptic from Gnome, it asks for my password...then nothing happens.  It runs completely fine from command line.

---

### Post by daahli on 2006-01-16
I've had the exact same problem for quite some time now. The issue has been brought up in other threads but now solution has solved my problem. 

It's pretty annoying not only because the admin programs won't launch from the gnome menu, but also because when I run synaptic from the terminal it always promts me twice for my password in the terminal. I really have no idea what might have caused this issue.

Also, I cannot run any of the admin-XXX programs from the terminal either. For example when I try to run admin-disks from the terminal I get an error on startup that the password is wrong, without me even typing in the password. Do you get this error too?


Any help greatly appreciated.

---

### Post by jrib on 2006-01-16
If either of you have enabled root, try disabling it:

```

sudo passwd -l root

```

enabling root will break gui admin tools....

---

### Post by codejunkie on 2006-01-16
[QUOTE=Joshatdot]I 1st noticed this when starting Synaptic from the GUI, when it asked for root password it would not take it.

So I opened a terminal, ran the **su** command typed the password, I logged in and started synaptic from command line.

Then I tried **sudo synaptic** this also did not take my root password.



Also when I stated **synaptic** from command line I got these messages:

(synaptic:10900): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:10900): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed[/QUOTE]
what your describing sounds like you chose the expert install option when installing ubuntu this enable's the root account instead of sudo. in a normal gnome distro the command for gui admin items is "gksu nameofcommand" but the gui admin menu items in ubuntu use "gksudo nameofcommand" and requires you to be a member of the sudoers group. so when you do an expert install it does not add your name to the sudoers file and it dosen't edit the menu items to use the right command but you can fix it by 
opening a terminal use su to gain root access then enter this command
```
export EDITOR=gedit && visudo
```
now add your username to the bottom file like this
```
yourusername ALL=(ALL) ALL
```
save the file and close gedit now try the admin apps that require sudo they should be working now hope this helps.

---

### Post by GreyFox503 on 2006-01-16
[quote=_jason]

enabling root will break gui admin tools....[/quote] 
I have a root password set and all my Administrative GUI tools work fine with sudo and my user password.

---

### Post by newuser111 on 2006-01-16
but you have to type xhost + and then type su

otherwise most apps wont work from the root account

---

### Post by newuser111 on 2006-01-16
Joshatdot did you try going to system>administration>users and groups, click on your user and properties and check all the boxes

---

### Post by daahli on 2006-01-16
I once enabled the root account, but then disabled it again. It is no longer active, but the gui admin programs still do not work. I think the problem may be that it wants the password inputted twice, because this is in fact what I have to do in order to get synaptic to launch from the terminal.

Why in the world does it prompt me for the password twice?

---

### Post by 3rdalbum on 2006-01-16
Couldn't be bothered to read all the pages of this thread, but when I installed Ubuntu recently I specified a root password, and my normal user account wasn't added to the sudoers file.

I reinstalled, but this time I put a blank root password, and voila! My normal user account became "sudoable".

---

### Post by jon66xxx on 2006-01-16
Thank you,codejunkie, those commands worked perfectley. Now i can acess my firewall, sypnaptic,nessus,and my other files. Thanks for helping .:D

---

### Post by jon66xxx on 2006-01-16
Where did codejunkies thread go?  Or was that that too much info?

---

### Post by Joshatdot on 2006-01-17
[QUOTE=codejunkie]what your describing sounds like you chose the expert install option when installing ubuntu this enable's the root account instead of sudo. in a normal gnome distro the command for gui admin items is "gksu nameofcommand" but the gui admin menu items in ubuntu use "gksudo nameofcommand" and requires you to be a member of the sudoers group. so when you do an expert install it does not add your name to the sudoers file and it dosen't edit the menu items to use the right command but you can fix it by 
opening a terminal use su to gain root access then enter this command
```
export EDITOR=gedit && visudo
```
now add your username to the bottom file like this
```
yourusername ALL=(ALL) ALL
```
save the file and close gedit now try the admin apps that require sudo they should be working now hope this helps.[/QUOTE]
Thanks codejunkie! that did the trick.

---

### Post by daahli on 2006-01-17
sorry, did not work for me. I still have the same exact problem

---


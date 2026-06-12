---
title: "Problems with Synaptic"
date: 2005-12-08
forum: Apple PPC Users
---

### Post by seanpbarry on 2005-12-08
I cannot open Synaptic from the GUI, it asks for a password and then does nothing. I've tried logging into terminal and then su - to access as admin and then when I type synaptic it gives the following message:

**(synaptic:5311): Gtk-WARNING **: cannot open display:**

Any ideas anyone???? I have 24hrs experience in Linux so learning as quickly as possible.

---

### Post by noigeaR on 2005-12-08
For KDE try
```
kdesu synaptic
```

and for Gnome try
```
gksudo synaptic
```
to access gui programs in administrator mode from the terminal.

---

### Post by seanpbarry on 2005-12-08
Thanks, I'll give that a try and see what happens. :smile:

---

### Post by RobertLos on 2005-12-09
I have the same kind of problem. It all comes down to a failyre of the dialogue box in gksudo. I can start any application using sudo from the terminal, but starting with gksudo either from the command line or via de e.g. System pull-down window invokes a dialogue box asking me for the sudo password. When I start entering this, the box crashes. There must be a way to reinstall this part or reset user rights or so.

Robert

---

### Post by seanpbarry on 2005-12-09
Just tried gksudo synaptic and dialog opens asking for my password.
I put in the password and nothing happens? Synaptic has opened before, but now it seems like password logins aren't working. Cannot access any administrator options from the system menu. Re-install??? Could there be conflict because I used the same password for both admin and user accounts (I would be amazed!)???

---

### Post by earobinson on 2005-12-09
sudo synaptic in the terminal
if that dont work do a sudo who (this will tell us if your sudo works)
Are you logged in with your admin account, you must be logged in with the account you made on install (or another one with sudo rights) to use sudo.

---

### Post by seanpbarry on 2005-12-09
amazing, did this in the terminal:

sean@ubuntu-pbg4:~$ sudo synaptic
sean@ubuntu-pbg4:~$ gksudo synaptic
sean is not in the sudoers file.  This incident will be reported.
sean@ubuntu-pbg4:~$ sudo who
sean@ubuntu-pbg4:~$ su
Password:
root@ubuntu-pbg4:/home/sean# gk synaptic
bash: gk: command not found
root@ubuntu-pbg4:/home/sean# synaptic

(synaptic:5896): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:5896): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed


and it actually opened up. looks like i'm not recognised as a user in sudo?
what would you advise, a complete re-install or setup new user account?

---

### Post by earobinson on 2005-12-09
I assume that you made a new account and set the root password correct?

---

### Post by seanpbarry on 2006-01-09
Sorry about delay, being away from college. I'll try a new account this week and post the results. :razz:

---

### Post by TER on 2006-01-17
You should add your username to the sudo list. 

[root@computer]# visudo

add "yourusername  ALL=(ALL) ALL"

below the line "root ALL=(ALL) ALL"

write out the file

See also: [http://www.linuxhomenetworking.com/linux-hn/addusers.htm](http://www.linuxhomenetworking.com/linux-hn/addusers.htm)

---

### Post by yigal.weinstein on 2006-01-19
I have the same error that was observed above, that is when opening Synaptic in gnome and Synaptic works, namely,

root@ubuntu:/home/yigal/Desktop# synaptic&
[1] 15326
root@ubuntu:/home/yigal/Desktop#
(synaptic:15326): Gtk-CRITICAL **: gtk_accel_label_set_accel_ closure: assertion `gtk_accel_group_from_accel_closure (accel _closure) != NULL' failed

(synaptic:15326): Gtk-CRITICAL **: gtk_accel_label_set_accel_ closure: assertion `gtk_accel_group_from_accel_closure (accel _closure) != NULL' failed

Synaptic works but why should I have to deal with error output like this.

---

### Post by hunteramor on 2006-02-10
yigal:

try using gksudo instead of sudo or gksu to open synaptic

---

### Post by Tasu on 2006-02-15
Hi, even I have had the same problem, in kde, starting synaptic from the menu, would bring up kdesu interface, after inserting the password, nothing happens, in my case the problem is metatheme (installed following this howto: [http://fak3r.com/articles/2006/01/31/howto-mezzo-desktop-on-ubuntu)](http://fak3r.com/articles/2006/01/31/howto-mezzo-desktop-on-ubuntu)), infact issuing kdesu synaptic from comand line, resulted in no synaptic launch but it throwed me an enlightening error message:

MetaTheme error: Cannot load configuration file (/root/.metatheme/config).

I resolved the problem by copying the .metatheme directory from my user home to root's one:

me@mycomputer:~$ sudo cp -R .metatheme /root/.metatheme

Now, whenever I click on synaptic's icon in the menu, it correctly throws me the kdesu gui and after it starts synaptic! ^_^

So, my advice is to try kdesu synaptic, then look for the errors and try to fix them! ^_^

regards

---

### Post by spaceballl on 2006-02-16
I had this problem - fixed by instead downloading one of the Dapper Daily Builds.

-Kevin

---


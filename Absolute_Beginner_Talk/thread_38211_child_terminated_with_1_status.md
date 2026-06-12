---
title: "child terminated with 1 status ??"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by zarkann on 2005-05-30
Hi,

it's been almost 5 hours that i'm trying to understand why i can't modify any of those admin option :

System>Administration>Login Screen Setup
System>Administration>Networking
System>Administration>Shared folders
System>Administration>Time and Date
System>Administration>Users and Groups

And maybe more but for now those are important for me. i'm trying to open them in Gnome and as soon as i put my password, i have an error that popup...

[COLOR=Red][B]Error when starting user-admin
child terminated with 1 status[/B][/COLOR]

Now, i read almost all the forum and UserDocumentations i'm following line by line all the method but i can't get it to work.

in Console, i did

sudo su, it doesnt work.. 
sudo passwd root , it doesnt work..
visudo , it doesnt work...(i have /etc/sudoer: Permission Denied)

i have this error :

i tried with the root password l:

$username@ubuntu:~$ sudo su
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Wrong password 2 times... blablabla
$username@ubuntu:~$

and i tryed with my password l:

$username@ubuntu:~$ sudo su
Password:
$username is not in the sudoers file. this incident will be reported.
$username@ubuntu:~$

i swear , i have only 1 account on this computer... mine and in the installation i put the administration password (root passwd) and my login name/user password... 

i don't know... i installed few different linux but i never went to something like that just after rebooting the system .

i can't do anything lol  :roll:

---

### Post by zarkann on 2005-05-30
So.. no one know what i'm talking about ?  :?    

Maybe i miss a configuration or something but even after a full day i didnt get it to work.. maybe i will reinstall Fedora 

the weird thing is that it supposed to be mostly the same

---

### Post by Genesius on 2005-05-31
I had the same problem - it may be that your user account isn't listed in the sudoers file. Try rebooting & selecting recovery mode from GRUB. Log in with your root password and run Visudo. You should see a line at the bottom that says "root ALL=(ALL) ALL", just add another line below that with your username in place of "root" Save the file and your problem should be fixed.

If that doesn't work -- well, I'm a newbie here too.

---

### Post by lachmacn on 2005-06-06
Just a tip.  You can change the sudoers file without booting into the recovery console.  Just open a terminal, type 'su', and enter your root password.  Then type vi /etc/sudoers once logged in as root.  Anyway, thanks for the suggestion with the sudoers file.  I was having the same problem.  Pretty stupid bug if you ask me!

---

### Post by pedroescobar on 2005-11-24
phewww, thats solved it

 thanks a lot for the nice tip, i was getting worried then :D 

i agree with the above, stupid bug..... :rolleyes:

---

### Post by Xian on 2005-11-24
A reminder....

Users should not edit their sudoers file with anything other than the visudo command. This tool makes sure that no two system administrators are editing this file at the same time, preserves the permissions on the file and performs some syntax checking to make sure you make no fatal mistakes in the file.

---

### Post by Mustard on 2006-03-08
I would also add that when you install ubuntu using the 'expert' install option at the boot prompt, the first user account is not set up with superuser privileges.  It's not a bug. It's an 'expert' install, which assumes you know what you are doing.

---


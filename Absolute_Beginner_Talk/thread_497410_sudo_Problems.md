---
title: "sudo Problems"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-07-10
Cheers,

I was trying to create a new user from the terminal , but when I typed
sudo adduser myuser

I get this error
this_user is not in the sudoers file.  This incident will be reported.

what happend here? this is the first time that it had happened to me.

Thanks.

---

### Post by Nekiruhs on 2007-07-10
Are you the only user on this computer? It appears that you don't have sudo privelages.

---

### Post by delphiguy on 2007-07-10
I was happily using sudo since I started using Ubuntu. And now this happened.  I happened when I tried to create a new user for my FTP server.

---

### Post by delphiguy on 2007-07-10
I was happily using sudo since I started using Ubuntu. And now this happened.  I happened when I tried to create a new user for my FTP server and Samba.

---

### Post by Wim Sturkenboom on 2007-07-10
Does sudo work for other things?

---

### Post by delphiguy on 2007-07-10
nope sudo totally abandoned me.  I tried doing sudo ls -al and nothing it just give that error.
this_user is not in the sudoers file.  This incident will be reported.


I tried logging in using the old users that I've created before, still no good.
So do I have to reinstall Ubuntu now to have this sudo back??

---

### Post by delphiguy on 2007-07-10
I tried to reboot the system and still nothing.  any ideas?

---

### Post by delphiguy on 2007-07-10
Cheers,

I have tried to post this at the beginners thread but I think this is the better forum for my problems.

I was trying to create a new user from the terminal , but when I typed
sudo adduser myuser

I get this error
this_user is not in the sudoers file. This incident will be reported.

I am happily using sudo since I started using Ubuntu, and then this happens.

I even tried to login using one of the users that I have created before and I even rebooted the
system but still no luck.

Any idea what happend here? this is the first time that it had happened to me.  hopefully someone can give 
me a solution other than reinstalling Ubuntu.  This is not the right time for me to do it, I've got so much in my 
hands at the moment.

Thanks.

---

### Post by destructchaos on 2007-07-10
have you tried using a root shell to do it?

---

### Post by delphiguy on 2007-07-10
how do i do that??

---

### Post by bapoumba on 2007-07-10
> **delphiguy said:**
> how do i do that??
```
sudo -s
```
and enter **exit** to go back to a user shell.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I've merged your other thread in here. Please let me know if you prefer I move it to "General help".

---

### Post by delphiguy on 2007-07-10
i tried it but nothing seems to happen

this_user@mypc:~$ sudo -s
this_user@mypc:~$

---

### Post by bapoumba on 2007-07-10
What does return:
```
groups
```

Your user should be in the admin group to be granted administrative privileges:

```
~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```

---

### Post by destructchaos on 2007-07-10
i get to it by opening a regular konsole and going to the Session menu and clicking "New Root Shell"

---

### Post by delphiguy on 2007-07-10
Here's what I got when I ran groups
delphiguy@zion:~$ groups
delphiguy

any ideas?

---

### Post by bapoumba on 2007-07-10
Please boot in recovery mode from grub menu. You'll be with no graphics environment, with a # prompt meaning you are root.

```
# adduser delphiguy admin
# reboot
```

You should be fine, then.
Consider adding you back (with **sudo adduser delphiguy <group>**) to the default groups I've listed above.

---

### Post by delphiguy on 2007-07-10
yes that fixed it.  thank you very much for the help guys, especially bapoumba.

---

### Post by bapoumba on 2007-07-10
Glad to see you got it to work.
Did you add yourself back to the default groups?

---

### Post by delphiguy on 2007-07-11
yes I did exactly as you said.  again thanks for the help.

---

### Post by bapoumba on 2007-07-11
You're welcome :)
Do not hesitate if you have any other questions.

---

### Post by total wormage on 2007-08-28
a friend of mine has a similar problem, i told him to do the 'adduser * admin' trick, but it said that the group admin didn't exist.

adding the group 'admin' and then the user to that group didn't work.
what to do next?

---

### Post by bapoumba on 2007-08-28
> **total wormage said:**
> a friend of mine has a similar problem, i told him to do the 'adduser * admin' trick, but it said that the group admin didn't exist.

adding the group 'admin' and then the user to that group didn't work.
what to do next?
Is your friend running Ubuntu? (the admin group and sudo setup are specific to Ubuntu and Ubuntu-based distros).
Boot in recovery mode and paste the sudoers file:
```
# cat /etc/sudoers

```

Here is the relevant parts of mine:
```
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Either add the proper privileges to the admin group, or to the <user_login>.
[http://linux.die.net/man/5/sudoers]("http://linux.die.net/man/5/sudoers")

---

### Post by total wormage on 2007-08-28
ah yes, i forgot to mention he runs debian :P

to what group does he have to add himself to in debian? :]

---

### Post by bapoumba on 2007-08-28
> **total wormage said:**
> ah yes, i forgot to mention he runs debian :P

to what group does he have to add himself to in debian? :]

I'm not sure. Look at the link I gave you, I do not know how a default sudoers file is set up in debian (I think only root has admin privilege). Does he want to use sudo?

---

### Post by kerry_s on 2007-08-28
> **total wormage said:**
> ah yes, i forgot to mention he runs debian :P

to what group does he have to add himself to in debian? :]

debian is set up to use "su" not "sudo" you can put him in there so he can use sudo.

su
visudo

his-name    ALL=(ALL) ALL

ctrl+x & y & enter <to save

---

### Post by total wormage on 2007-08-28
many thanks! :]

---


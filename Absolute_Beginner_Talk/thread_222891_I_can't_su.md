---
title: "I can't su"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by levigruber on 2006-07-25
I am trying to su from terminal. It keeps saying "su: Authentication failure - Sorry. I know I typed my passwd correctly. There isn't a second passwd, is there? Thx

Levi-

---

### Post by taurus on 2006-07-25
Try using sudo instead of su, okay...

```

sudo <command>

```

---

### Post by moma on 2006-07-25
o--> [http://ubuntuforums.org/showthread.php?p=1283789#post1283789]("http://ubuntuforums.org/showthread.php?p=1283789#post1283789")

---

### Post by madmetal on 2006-07-25
sudo  :)

---

### Post by mdecler2 on 2006-07-25
Indeed. I am also a Linux beginner, especially to Ubuntu.

On other distros (and in most documentation) root is gained by using the "su" command.
But Ubuntu users use "sudo" for seemingly a similar purpose, and I have never been able correctly authenticate myself using "su" :-k.
A quick look at each of their man pages displays similar results, except that sudo defines "executing a command as another user" which I am guess is automatically set to root in the /etc/sudoers file.

It makes me wonder...
What is the difference between sudo and su?
What's the point of having an su command in Ubuntu if no one (or at least levi and I) cannot correctly authenticate?
Is there a way to use su, and  if so, why would I use it?

---

### Post by levigruber on 2006-07-25
> **mdecler2 said:**
> Indeed. I am also a Linux beginner, especially to Ubuntu.

On other distros (and in most documentation) root is gained by using the "su" command.
But Ubuntu users use "sudo" for seemingly a similar purpose, and I have never been able correctly authenticate myself using "su" :-k.
A quick look at each of their man pages displays similar results, except that sudo defines "executing a command as another user" which I am guess is automatically set to root in the /etc/sudoers file.

It makes me wonder...
What is the difference between sudo and su?
What's the point of having an su command in Ubuntu if no one (or at least levi and I) cannot correctly authenticate?
Is there a way to use su, and  if so, why would I use it?
I wanted to use su to change permissions on files in /var/lib/dpkg , to remove the remains of an aborted install, which returns error message every time I try to install anything.

Levi-

---

### Post by mscman on 2006-07-25
> **levigruber said:**
> I wanted to use su to change permissions on files in /var/lib/dpkg , to remove the remains of an aborted install, which returns error message every time I try to install anything.

Levi-

Alright, quick comparison: sudo vs. su.

In the *NIX world, it is common to use the command su to gain root access. Most Linux distros have followed this pattern and it does it's job fine. Unfortunately, by using su, you introduce a small security problem in your system: you open the terminal, run the su command, and all of a sudden you have absolute power! Now if this terminal is left open with root access, anyone can do anything to the system. Also, you could accidentally delete stuff or change stuff you didn't really want to change.

Ubuntu tries to correct this problem. To start with, they decided to disable the root account altogether. You can enable it if you'd like, but it's not recommended. Instead, by using the command "sudo <command>", you're able to do any administrative tasks you need to. ***NOTE***: Only the first user created during the install is given sudo access. You need to enable other users to use sudo if you want them to have that access (not recommended...)

For more info on su vs. sudo, visit this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mdecler2 on 2006-07-25
> **levigruber said:**
> I wanted to use su to change permissions on files in /var/lib/dpkg , to remove the remains of an aborted install, which returns error message every time I try to install anything.

Levi-

Are you still having problems with sudo?

---

### Post by mdecler2 on 2006-07-25
> Instead, by using the command "sudo <command>", you're able to do any administrative tasks you need to.

I see, so "su" is completely useless in Ubuntu because there is no root user...interesting.

> ***NOTE***: Only the first user created during the install is given sudo access. You need to enable other users to use sudo if you want them to have that access (not recommended...)


I do not beleive this is true. I just installed Ubuntu Dapper and my /etc/sudoers file contains this:
```
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

So I beleive Ubuntu automatically gives "root" proveledges through sudo to anyone on the system with a password.

---

### Post by levigruber on 2006-07-25
Yes. I know what sudo is, but that's all. What are parameters to go into /var/lib/dpkg with sudo and comment out clvm packages to see if that solves my problem.

Levi-

---

### Post by jordilin on 2006-07-25
> **levigruber said:**
> Yes. I know what sudo is, but that's all. What are parameters to go into /var/lib/dpkg with sudo and comment out clvm packages to see if that solves my problem.

Levi-

You can enter into a root console if you want. Just type
```
sudo -i
```
and that's all. You will be as root without enabling root. 8)

---

### Post by mscman on 2006-07-29
> **mdecler2 said:**
> I see, so "su" is completely useless in Ubuntu because there is no root user...interesting.



I do not beleive this is true. I just installed Ubuntu Dapper and my /etc/sudoers file contains this:
```
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

So I beleive Ubuntu automatically gives "root" proveledges through sudo to anyone on the system with a password.

Not quite... try creating a new user and logging in under that name and issue a 'sudo <command>'. You'll either get an error about not being in the sudoers file or nothing will happen. The key line(s) in that file is:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
This means that only users added to the 'admin' group are able to use sudo. However, Ubuntu only gives (by default) the first user created access to sudo. Any users created after installation will have to be manually added to the admin group. :D

---


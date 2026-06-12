---
title: "sudo and su??"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by Iwantu_ubuntu on 2005-06-24
Can someone explain what the difference is between sudo and su? (as simply as possible)  I know sudo means "superuser do".   How come the sudo password is really the password for my user account?  Is the root account disabled by default in Ubuntu?  In FC3 the passwords for su and user were different thats why I'm a little confused...almost re-imaged thinking it was a mistake on my part during the install.

---

### Post by Leif on 2005-06-24
[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

---

### Post by skoal on 2005-06-24
'su' means *switch user*.

In other words, if user 'iwantu' wants to have root priveleges for his machine, he can either:

1. switch to root user using 'su' by typing in the root user password.

*or*

2. simply use sudo by typing in the 'iwantu' user password.

'iwantu' can still accomplish that task by either means.  However, just like the name "sudo" implies, by method 2, 'iwantu' is *acting* like the user root (although not logged in as such by using method 1).

\\//_

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=Iwantu_ubuntu]  Is the root account disabled by default in Ubuntu? [/QUOTE]

Yes.

---

### Post by Iwantu_ubuntu on 2005-06-24
[QUOTE=skoal]'su' means *switch user*.

In other words, if user 'iwantu' wants to have root priveleges for his machine, he can either:

1. switch to root user using 'su' by typing in the root user password.

*or*

2. simply use sudo by typing in the 'iwantu' user password.

'iwantu' can still accomplish that task by either means.  However, just like the name "sudo" implies, by method 2, 'iwantu' is *acting* like the user root (although not logged in as such by using method 1).

\\//_[/QUOTE]
 Thanks a lot for the quick replies, esp skoal. Makes a lot of sense now, getting the hang of it slowly.

---

### Post by janrinok on 2005-06-25
Skoal explained it well but, if  may add a little more that was important for me.  Firstly, if you switch to 'root' using the su command - you are root!  You can do anything that you wish and the computer will not stop you.  However, it is easy to make mistakes this way.  And the downside is, as root there is no much logging of your actions which makes undoing your mistakes harder.  If you use sudo however, you are running programs with 'root' permissions.  While this doesn't seem much safer there are advantages.  Firstly, you must type 'sudo' before each command that you use, although you will only be asked for the password once in any specific time period.  This means that you can run some commands with the safety net of being a simple user (by not using sudo) but can have all the power of root simply be preceding the command with 'sudo' when you need it.  Get into the habit of _only_ using 'sudo' when you need it - it will stop most silly errors that we make.  The other advantage of sudo is that everything that you do is logged and tagged with your normal user ID.  If there is a problem, you can look back in the logs to try to find out where you went wrong and, if there is more than one user on the system, who actually made the mistake in the first place!  HTH Jan

---


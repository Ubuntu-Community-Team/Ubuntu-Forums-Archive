---
title: "gksu vs gksudo"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by frafu on 2007-03-30
Hello,

Could anybody tell me what is difference between gksu and gksudo? 

Thanks in advance.

---

### Post by 23meg on 2007-03-30
[http://www.ubuntuforums.org/showthread.php?t=287563](http://www.ubuntuforums.org/showthread.php?t=287563)

---

### Post by Bachstelze on 2007-03-30
In Ubuntu, they are the same. Traditionnally, gksu is just a graphical su and gksudo a graphical sudo, which means tha gksu will let you run GUI stuff as another use typing the other user's password while gksudo will ask for your password and will look in the sudoears file to see if you're allowed to do whay you want or not.

---

### Post by frafu on 2007-03-30
Thanks for your helpful replies; it makes me also realise the difference between su and sudo.

---

### Post by kerry_s on 2007-03-30
You can just use gksu, in ubuntu gksudo is just a link to gksu, so your always running gksu anyways. You can check for yourself> nautilus /usr/bin

Here's a little known tip, if you run just "gksu" you will get a root run dialog, to run any app as root or other user.

---

### Post by ardchoille42 on 2007-03-30
Confirmed on Ubuntu 6.06.1 LTS
```

[~ @ 12:48:51] which gksudo
/usr/bin/gksudo
[~ @ 13:37:59] file $(which gksudo)
/usr/bin/gksudo: symbolic link to `gksu'
[~ @ 13:38:06] file $(which gksu)
/usr/bin/gksu: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, stripped
[~ @ 13:38:13]

```

---

### Post by ardchoille42 on 2007-03-30
> **kerry_s said:**
> Here's a little known tip, if you run just "gksu" you will get a root run dialog, to run any app as root or other user.
  That may be for Edgy or Feisty, but if you run 'gksu' from a terminal on Dapper, you are greeted with a messagebox that says 

ERROR: Missing command to run

On Dapper, you need to run 'gksuexec' to get that dialog. Someone told me the Ubuntu devs changed gksuexec to gksu but I don't remember if that change is for Edgy or Feisty.

---

### Post by bodhi.zazen on 2007-03-30
man gksu :

> gksu is a frontend to su and gksudo is a frontend to sudo. Their primary purpose is to run graphical commands that need root without the need to run an X terminal emulator and using su directly.

su = switch user. You need to enter the users password. For example su <user_name>
password: <user_password> changes to the user 
user@host$

With no argument (su) the default is root.

In some OS there is no sudo, so to sys amdin you use su.

In Ubuntu you have sudo. In Ubuntu, unless you set a root password, you can not use su to change to root.

=====

sudo = run a single command as root. sudo is configured with visudo. sudo allows finer control over user access to admin privileges (su = all or none, sudo can be set per command per user per machine).

In Ubuntu the first user (anyone in the admin group) has full access via sudo.

So sudo su = run su as root = change to root = su on systems without sudo (well not exactly, but close enough).

man su :> su is used to become another user during a login session. Invoked without a username, su defaults to becoming the super user.

login session = terminal session.

man sudo :> sudo allows a permitted user to execute a command as the superuser or another user, as specified in the sudoers file. The real and effective uid and gid are set to match those of the target user as specified in the passwd file and the group vector is initialized based on the group file (unless the -P option was specified). If the invoking user is root or if the target user is the same as the invoking user, no password is required. Otherwise, sudo requires that users authenticate themselves with a password by default (NOTE: in the default configuration this is the user's password, not the root password). Once a user has been authenticated, a timestamp is updated and the user may then use sudo without a password for a short period of time (5 minutes unless overridden in sudoers).

---

### Post by kerry_s on 2007-03-30
> **ardchoille42 said:**
> That may be for Edgy or Feisty, but if you run 'gksu' from a terminal on Dapper, you are greeted with a messagebox that says 

ERROR: Missing command to run

On Dapper, you need to run 'gksuexec' to get that dialog. Someone told me the Ubuntu devs changed gksuexec to gksu but I don't remember if that change is for Edgy or Feisty.

Yes, your right, i always forget about version specific thing. In edgy and feisty they did away with "gksuexec". Some time back people were still looking for it and hadn't realized it had been dropped to just "gksu" in edgy and feisty.

---

### Post by ardchoille42 on 2007-03-30
> **kerry_s said:**
> Yes, your right, i always forget about version specific thing. In edgy and feisty they did away with "gksuexec". Some time back people were still looking for it and hadn't realized it had been dropped to just "gksu" in edgy and feisty.

This is why I wish the devs would stop changing things around, makes it hard to offer advice when an Edgy user doesn't have an app (gksuexec) that a Dapper user tells them to run in order to solve a problem.

---

### Post by frafu on 2007-03-31
Thanks to all, especially to bodhi_zazen for the replies; I try to sum up the explanations (for edge and feisty): 

1. In Ubuntu (I suppose in most unix/linux systems), there is a user called root (also called superuser) that has the necessary rights (privileges) to do anything that he wants. 

2. In Ubuntu, they have chosen to disable the root user, because any user that belongs to the admin group is able to execute commands as if he was the root user. To execute a command with the same privileges as the root user, he has to put the word "sudo" before the command. (I suppose, sudo stands for SuperUserDO) 

3. There is also the command su, that stands for switch user. It is intended to switch from one user to another user in the terminal; the syntax is "su name_of_the_other_user".

4. If you call su without indicating the name_of_the_other_user, su assumes that the other user is the root user. So Ubuntu edgy and feisty simply replaces sudo with su without the name_of_the_other_user, which corresponds to su root. 
(Question: how can su switch to the root user if the root user is disabled?) 

5. gksu and gksudo are in the graphical environments what su and sudo are in the terminal. 
By the way, I have read in another thread: people should use gksudo in the terminal to launch a graphical application with root privileges; for example "gksudo gedit". It is also possible to use "sudo gedit", but it is not a good way to do it, because gksudo sets up things for a graphical environment, but sudo sets them up for a text environment. (or something like this) 

It might be worth putting this thread in the wiki, and enhance the title with the words su and sudo. 

frafu

---

### Post by dreadlord_chris on 2007-03-31
> **frafu said:**
> 
4. If you call su without indicating the name_of_the_other_user, su assumes that the other user is the root user. So Ubuntu edgy and feisty simply replaces sudo with su without the name_of_the_other_user, which corresponds to su root. 
(Question: how can su switch to the root user if the root user is disabled?) 


Answer: It can't. 

(Semi-)Technical details - the root account is disabled by changing the password to a
value which matches no possible encrypted value.

So, in other words, if you try to **su** to a disabled account (i.e. root) it will give you an error no matter what you enter as password.

Also, **sudo** is _not_ the same as **su root**.
Assuming that for some reason you've enabled the root account, **su** (or su root) will give you a **root** shell. You will be root for the duration of that terminal session (or untill you exit the root shell)
The default setting for **sudo** allows users that are part of the **admin** group (by default - the first user created) to perform certain commands *as* root. These commands are configurable through the /etc/sudoers file - the default is to allow all commands.

---

### Post by 23meg on 2007-03-31
> 
It might be worth putting this thread in the wiki, and enhance the title with the words su and sudo. 
Everything you've summed up is already there: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by frafu on 2007-03-31
So, when the root account is disabled, you can't do "su root". But why is it possible to do "gksu gedit"? 

gksu being the analogue of su, and gksudo being the analogue of sudo, it should not be possible to use gksu, unless gksu was a link to gksudo. But appearantly it is the other way round: gksudo is a link to gksu. 

(terminology: when A is a link to B, this means that B is executed when I call A; or am I wrong?) 

Where is my mistake? 

I hope that I am not annoying you to much, as the main purpose of the thread has already been answered: in Ubuntu, gksu and gksudo are the same. But unfortunately, I don't completely understand the background yet.

---

### Post by 23meg on 2007-03-31
[QUOTE=frafu]So, when the root account is disabled, you can't do "su root". But why is it possible to do "gksu gedit"? 

gksu being the analogue of su, and gksudo being the analogue of sudo, it should not be possible to use gksu, unless gksu was a link to gksudo. But appearantly it is the other way round: gksudo is a link to gksu.[/quote]

Whether you use *gksu* or *gksudo*, the actual library that does the job is *libgksu*, not the executable *gksu*, and according to the manual page, it will decide if it should use su or sudo as backend using the /apps/gksu/sudo-mode gconf key.

---

### Post by steve.horsley on 2007-03-31
> **frafu said:**
> So, when the root account is disabled, you can't do "su root". But why is it possible to do "gksu gedit"? 

gksu being the analogue of su, and gksudo being the analogue of sudo, it should not be possible to use gksu, unless gksu was a link to gksudo. But appearantly it is the other way round: gksudo is a link to gksu. 

(terminology: when A is a link to B, this means that B is executed when I call A; or am I wrong?) 

Where is my mistake? 

I hope that I am not annoying you to much, as the main purpose of the thread has already been answered: in Ubuntu, gksu and gksudo are the same. But unfortunately, I don't completely understand the background yet.

Accounts are disabled by disabling their password - that's all. This is done by entering a special character in the /etc/passwd file that says the password id locked. So if the root account is disabled then you can't log in as root and you can't su root - in both cases this is because you can't enter a correct password - there isn't one. However, if someone was already logged in as root, they don't notice any change - they can still function.

sudo and gksudo are special programs called setuid programs. They always run as the id of the executable owner, regardless of who launches them. In this case, they are owned by root. No root password required. And of course, as root, they can launch any other program rith root's id too. 

If you do **ls -l /bin/su** you see an s (setuid) in place of the of the usual x (executable).

---

### Post by frafu on 2007-03-31
> **23meg said:**
> Whether you use *gksu* or *gksudo*, the actual library that does the job is *libgksu*, not the executable *gksu*, and according to the manual page, it will decide if it should use su or sudo as backend using the /apps/gksu/sudo-mode gconf key.

Considering that the /apps/gksu/sudo-mode gconf key is enabled, it now makes also sense to me. (It probably is enabled on all Ubuntu edgy/feisty by default.) 

> **steve.horsley said:**
> 
sudo and gksudo are special programs called setuid programs. They always run as the id of the executable owner, regardless of who launches them. In this case, they are owned by root. No root password required. And of course, as root, they can launch any other program rith root's id too. 

If you do **ls -l /bin/su** you see an s (setuid) in place of the of the usual x (executable).

I did not until now pay attention to the fact that executables usually run with the id of the user that launches them...  

Indeed: 
ls -l /bin/su
gives me: 
-rwsr-xr-x 1 root root 27056 2006-10-20 00:52 /bin/su

Now I wonder why there is only an s for the owner and not also for the group and all the other users? Should it not be rwsr--r--? 

By the way, how can the s be given, if numbers are used to set privileges: r=4, w=2, x=1, s=? 

Francesco

---

### Post by 23meg on 2007-03-31
[QUOTE=frafu](It probably is enabled on all Ubuntu edgy/feisty by default.) [/QUOTE]

Yes, it is.

[QUOTE=frafu]Now I wonder why there is only an s for the owner and not also for the group and all the other users? Should it not be rwsr--r--?

By the way, how can the s be given, if numbers are used to set privileges: r=4, w=2, x=1, s=?[/QUOTE]

The "s" can only be in the execute field; it corresponds to setuid, which is a special permission mode. [This]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html") will answer your questions.

---

### Post by aysiu on 2007-03-31
Even though *gksudo* appears to be a symbolic link to *gksu*, meaning that they should behave in the same way, I have seen evidence to the contrary a few times on these forums. Someone has some problem with *gksu synaptic*, but *gksudo synaptic* will work... or vice versa.

Oddly enough, most forum users (including me) will advise using *gksudo*, but if you look at the commands for administrative applications in the Gnome menu in Ubuntu, they are usually *gksu* (*gksu users-admin*, for example--not *gksudo users-admin*).

---

### Post by 23meg on 2007-03-31
[QUOTE=aysiu]Even though gksudo appears to be a symbolic link to gksu, meaning that they should behave in the same way, I have seen evidence to the contrary a few times on these forums. Someone has some problem with gksu synaptic, but gksudo synaptic will work... or vice versa.[/QUOTE]

On a healthy system, technically it shouldn't matter at all which one is used, since all *gksudo* is is a symbolic link to *gksu*, and *libgksu* determines what to use by looking at a gconf key. The kind of behavior you describe may be the result of the *gksudo* symbolic link being absent, and *gksu* still being in place. 

[QUOTE=aysiu]Oddly enough, most forum users (including me) will advise using gksudo, but if you look at the commands for administrative applications in the Gnome menu in Ubuntu, they are usually gksu (gksu users-admin, for example--not gksudo users-admin).[/QUOTE]

That may be a GNOME default that's left untouched, since GNOME ships on many distros, perhaps not all of which implement gksu/gksudo the way Ubuntu does. 

A rationale for advising the use of *gksudo* instead of *gksu* may be that its function is more evident in its name, since it includes the word *sudo* in it; it's pretty obvious that it does something like *sudo*.

---

### Post by aysiu on 2007-03-31
Thanks, 23meg. Those explanations make sense to me.

---

### Post by frafu on 2007-04-01
@23meg

Thanks for the link with the tutorial. By the way, that is a very interesting site. 
:)

---

### Post by steve.horsley on 2007-04-01
> **frafu said:**
> 
By the way, how can the s be given, if numbers are used to set privileges: r=4, w=2, x=1, s=? 

Francesco

Good question, anf the linked explanation doesn't seem to say. In fact there are more bits to the file mode than the 9 that make up the usual rwxrwxrwx bits. These higher bits carry flags fo the other unusual modes, but I don't have an exact reference to hand.

---


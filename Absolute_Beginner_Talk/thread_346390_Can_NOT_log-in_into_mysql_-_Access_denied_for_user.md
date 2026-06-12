---
title: "Can NOT log-in into mysql - Access denied for user 'mysql'@'localhost'???"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-25
Hello!

I installed "mysql" in the following way:

1.  /usr/sbin/groupadd mysql
Note:
Before I even install "mysql", I create a group named "mysql".

2. /usr/sbin/useradd -g mysql mysql
Note:
Before I even install "mysql", I create a user name "mysql".

3. apt-get install mysql-server-5.0

4. I then install apache2, php5, etc etc

So basically I have created 3 users on my Ubuntu:

a. user "dimitris"
b. user "mysql"
c. user "root"

So, I try to log-in to mysql, by typing the following:

> dimitris@dimitris-desktop:~$ [color=blue]mysql -u mysql -p[/color]
Enter password: 
ERROR 1045 (28000): Access denied for user 'mysql'@'localhost' (using password: YES)

I thought that this was due to the fact that a password was not set for the user "mysql"...
So, I go ahead & add a password for the user "mysql", by typing this:

> dimitris@dimitris-desktop:~$[color=blue]passwd mysql[/color]
I then type the new password twice.

Again, I try to log-in to mysql, by typing the following:

> dimitris@dimitris-desktop:~$ [color=blue]mysql -u mysql -p[/color]
Enter password: 
ERROR 1045 (28000): Access denied for user 'mysql'@'localhost' (using password: YES)

What is wrong?
How can I log-in into my mysql?
Is it because the in the Terminal I am logged as user "[color=blue]dimitris@dimitris-desktop[/color]"?
I only know how to be user "dimitris" or "root" from the Terminal...
I have never added any other accounts until today...
How do I change to user "mysql" on the Terminal?

I am thinking that maybe I need to be user "mysql" first & then try to log-in the _user_ "mysql" into my "mysql" database...

Thanks.

P.S.> Relevant info:
> dimitris@dimitris-desktop:~$ [color=blue]id mysql[/color]
uid=1001(mysql) gid=1001(mysql) groups=1001(mysql)
dimitris@dimitris-desktop:~$ [color=blue]groups mysql[/color]
mysql : mysql

---

### Post by kebes on 2007-01-25
I believe the mysql user/password list is completely unrelated to the user accounts on your Ubuntu machine. (Unlike FTP, where the two are related.) So even though you created a user "mysql" on your computer, that doesn't mean that there is a "mysql" user inside mysql.

If you want to add a mysql user, you first enter into mysql, on a commandline:
mysql -u root

(Or "mysql -u root -p" if you've already set a password... and note that this is the "mysql root" account which has no relation to your computer's root account! Confusing I know!)

Then you'll have a mysql prompt, and you can go:
```

mysql>use mysql;
mysql> INSERT INTO user (host, user, password, select_priv, insert_priv, update_priv) VALUES ('localhost', 'mysqluser', PASSWORD('secret'), 'Y', 'Y', 'Y');
Query OK, 1 row affected (0.20 sec)
mysql> FLUSH PRIVILEGES;
Query OK, 1 row affected (0.01 sec) 

```

This will add the user "mysqluser" with the password "secret". Adding a user called "mysql" actually just makes things more confusing. It's usually better to add meaningful users like "weblog" or whatever (depending on the purpose of the user).



If you find mysql confusing, consider installing "phpmyadmin" which gives you a very nice web-page interface to all the mysql structures. This makes it much easier to add/remove users, databases, etc.

---

### Post by ieee488 on 2007-01-25
Agree with everything kebes wrote.

You might want to do a re-boot.
MySQL is always a little bit tricky to set up.

---

### Post by dvarsam on 2007-01-25
lol

I did NOT know that "mysql" accounts are NOT linked to my Ubuntu machine's accounts...

Thanks, that solved my problem!
Everything works perfectly now!!!

BTW, since I learned how to _also_ create accounts on my Ubuntu machine, how do I switch between users using the Terminal?

Example:

As I said before, I have 3 accounts:

1. dimitris
2. mysql   (that was funny - lol...)
3. root

When I boot, I am always logged as "dimitris".
And when from the Terminal, I want to log as "root", I type "sudo -i" & I am there!
And to get back to the user "dimitris", I type "exit".

_So the question is_:
How can I switch from user "dimitris" (or "root") to user "mysql" (by using the Terminal)?

Thanks.

---

### Post by kebes on 2007-01-25
In a terminal you can switch user using the "su" command. If you "su" without an argument it assumes you are trying to switch to root, but you can switch to any user you want:

su bob

Then it will ask you for the password. Then you'll be in a shell with the privileges of that user.

---

### Post by dvarsam on 2007-01-25
Thanks for your reply!

[QUOTE=kebes]In a terminal you can switch user using the "su" command. If you "su" without an argument it assumes you are trying to switch to root, but you can switch to any user you want:

su bob

Then it will ask you for the password. Then you will be in a shell with the privileges of that user.[/QUOTE]

I created a group & user, in the following way:

/usr/sbin/groupadd mysql
/usr/sbin/useradd -g mysql mysql
passwd mysql

So, now I use the Terminal to switch users:

> dimitris@dimitris-desktop:/$ su mysql
Password: 
$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
$ cd /home/dimitris
$ ls
amsn_received  Examples    Keyboard Commands (No Mouse Involved)~
Desktop        Incomplete  key.gpg.asc
$ su dimitris
Password: 
dimitris@dimitris-desktop:~$ ls
[color=blue]amsn_received[/color]  Examples    Keyboard Commands (No Mouse Involved)~
[color=blue]Desktop        Incomplete[/color]  key.gpg.asc
dimitris@dimitris-desktop:~$ id mysql
uid=1001(mysql) gid=1001(mysql) groups=1001(mysql)
dimitris@dimitris-desktop:~$ groups mysql
mysql : mysql
dimitris@dimitris-desktop:~$ sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)



_I have the following 3 questions_:

1. The prompt of user "mysql" is "$" while the prompt of user "dimitris" is "dimitris@dimitris-desktop:~$". Why is that? Can I make the prompt of user "mysql" look like the prompt of user "dimitris"? How do I do that?
2. When I perform an "ls" command under the user "dimitris", I see colored folders, but the same "ls" command under user "mysql" does not show any colored folders at all!
How can I make the output of an "ls" command from user "mysql" to be as colorful as the output of the same command performed from user "dimitris"?
3. Why when I try "su mysql" I can change user, but when I try "sudo mysql" I get the Error 1045? Aren't these 2 commands supposed to be the same?
What is the true diff between "su" & "sudo"?

Thanks.

---

### Post by kebes on 2007-01-26
In response to #3, the difference is that "su" causes you to switch into a new shell of a different username. By default if you don't specify the username, it means you are trying to switch into the root account. (Of course the root account doesn't really exist on Ubuntu.)

"sudo" means "run this one command as a different user". By default it assumes you are trying to run the command with "superuser" privileges. Hower you can use the "-u" option to run as a different user. So you cold go:
sudo -u mysql rm filename.txt

And it would the command as if user "mysql" were trying to do it, instead of whatever user you are logged in as. Typically, however, you use "su" to switch into a different user account, and "sudo" when you want to issue a single root-power command. (It's a bad idea to switch into a root shell because you might make a mistake. Using "sudo" reminds you that the command you are issuing is root-power.)



As for #1 and #2, I believe the 'look and feel' of the shell for each user is controlled by each user based on the files ".bashrc_profile" and ".bashrc" which are stored in the user directory. So each user will have their own copies of these files, for example:
/home/mysql/.bashrc
etc.

You can edit these files to make the shell behave the way you want. In your case you should probably be able to copy over the relevant bit from your normal user file to the secondary user.

---

### Post by kpatz on 2007-01-26
Your mysql user doesn't have a home directory, since you didn't specify --create-home in the useradd command.

To give them a home directory, run these commands (as root):```
cp -R /etc/skel /home/mysql
chown -R mysql:mysql /home/mysql
```

Also, the reason the prompt is changing when you su as mysql is because mysql's login shell is /bin/sh, not /bin/bash.  Use this command to switch the shell (as root):```
usermod -s /bin/bash mysql
```

Next time you create a user with useradd, I recommend putting the options --create-home and --shell /bin/bash on the command line, so that the user is set up with a home directory and bash shell (unless you want them to have a different shell).  Also, you can use --password secret to set the password initially to 'secret' (or whatever password you want).

---

### Post by zbog on 2007-11-25
Misposted in another thread. Please delete.

---


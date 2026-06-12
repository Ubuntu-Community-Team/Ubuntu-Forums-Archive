---
title: "Users added with useradd cant login."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by soeten on 2008-04-16
Whenever I use 'useradd' to add a new user in ubuntu (server7.10) the user account seems to be disabled, and I have to use 'passwd $user' in order to activate it.

The command I use: 'sudo useradd -g 1001 -s /bin/bash -m -d /home/www/$user -p $password $user', the adduser command is not a alternative since I must be able to add a new (and working ; P) user on ONE command. 

Help appreciated... : |

---

### Post by wesleybailey on 2008-04-16
I'm sorry, I thought you were missing the "-D" switch. But the command you have is correct.

Maybe the problem is with the password switch

from the man page
> 
       -p, --password PASSWORD
           The encrypted password, as returned by crypt(3). The default is to
           disable the account.



---

### Post by soeten on 2008-04-16
Yeah, probably thats whats wrong. I don't really understand that parameter to be honest. : /

---

### Post by wesleybailey on 2008-04-16
If you have perl installed you can use this command.

```

'sudo useradd -g 1001 -s /bin/bash -m -d /home/www/$user -p  `perl -e 'print crypt("$password", "salt"),"\n"' $user'

```

I have not tried this in a script, so the syntax might be a bit off. But it works from command line

---

### Post by soeten on 2008-04-16
I tried to install perl but I cant seem to get the command working. I get some kind of syntax error ("unexpected T_PRINT") also I tried the perl command separately in the terminal but failed to get any output. Guess there is a reason this is the absolute beginner's forum, but thanks for helping. xD

---

### Post by wesleybailey on 2008-04-16
I apologize for posting untested code.

This code should work from the command line, by itself.
```

perl -e 'print crypt("1234", "salt"),"\n"'

```

If that command prints "saS3eimg8Mg1M", then you can use this line.
```

'sudo useradd -g 1001 -s /bin/bash -m -d /home/www/$user -p  `perl -e 'print crypt($password, "salt"),"\n"'**`** $user'

```

I was missing a quote on the end of my perl statement

---

### Post by bodhi.zazen on 2008-04-16
Or you could user adduser

sudo adduser new_user_name

You will be asked for information such as a password and additional groups ....

Edit, oops, not additional groups ...

---

### Post by spiderbatdad on 2008-04-16
I believe it is preferred to use adduser instead of useradd.
```
man adduser
```

For example:
```
sudo adduser Bob
```

or

```
sudo adduser Bob <groupname>
```

Privileges can be included or added via the GUI utility.

---

### Post by wesleybailey on 2008-04-16
Thanks bodhi.zazen, and spiderbatdad for the help.

However in the original post **soeten** did specify that he/she does not want to use "adduser".

He/she needs to add the user in one line, in a script of some sort.

---

### Post by bodhi.zazen on 2008-04-16
Oh I missed that.


Here are two links re: adding users vis script :

[http://azimyasin.wordpress.com/2007/09/25/adding-users-on-ubuntu-box-via-file/](http://azimyasin.wordpress.com/2007/09/25/adding-users-on-ubuntu-box-via-file/)
		[http://www.linewbie.com/2007/11/using-bash-script-to-mass-create-users-and-change-passwords.html](http://www.linewbie.com/2007/11/using-bash-script-to-mass-create-users-and-change-passwords.html)

---

### Post by soeten on 2008-04-16
Thanks wesleybailey, it did work in terminal. : D

In fact I'm trying to run the command through php. [SIZE="1"](I know its not secure nor a good way to do it, but its part of a school assignment. : p)
[/SIZE]

I did get the following code to work through php:
```
`sudo useradd -g 1001 -s /bin/false -m -d /home/www/$user -p $pass $user`;
```

However, I'm having problems figuring out the proper syntax for this line:
```
`sudo useradd -g 1001 -s /bin/bash -m -d /home/www/$user -p  `perl -e 'print crypt($password, "salt"),"\n"'` $use`
```

Once again, the help is really appreciated. : )

#Solved, thanks for the input. (I ended up generating a shell script through php.) : )

---


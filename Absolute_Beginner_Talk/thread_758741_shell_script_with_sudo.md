---
title: "shell script with sudo?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-04-18
Is it possible to write a shell script that will automatically enter your password as root.
 like "sudo fdisk -l  > /filename" & enter your password all in the script?

---

### Post by mbadawi23 on 2008-04-18
This is not possible. Because if implemented it defeats the basic principles of password security.

But I think it is possible to run a shell script completely as root!

---

### Post by LaRoza on 2008-04-18
It is a really unsafe thing to do, but you can.

I recommend you don't do this, and I think there is a better way (but I don't know how to do it)

It is better to run the script as root, rather than doing this.

```

echo <password> | sudo -S <program>

```

If you don't want to hard code your password, which is a really bad idea, do this:

```

echo $1 | sudo -S <program>

```

You will have to run the script with your password as the first argument.

```

$./script.sh <password>

```

---

### Post by mbadawi23 on 2008-04-18
You may find the following link is helpful and more appropriate to perform the task you want:

[http://blog.mecworks.com/articles/2006/02/23/bash-scripting-tip-running-a-script-as-root/]("http://blog.mecworks.com/articles/2006/02/23/bash-scripting-tip-running-a-script-as-root/")

---

### Post by prkfriryce on 2008-04-18
you can add your script as an Cmnd_Alias to the sudoers file and then add 'NOPASSWD: <alias name>'  for that username.

---

### Post by garyed on 2008-04-18
Thanks for the replies.
I might as well tell you my plan so at least you'll understand why I want to run sudo in a script.
I'm trying to write a script that will warn me when my next boot will be a forced file check.
I think there are programs that do it already but I wanted to try it myself.
I plannend to get info from tune2fs & then post a warning when the max-count  & mount count start getting close. I know it is a security risk but I'm not too worried about that on the computer I want to put it on.

---

### Post by bodhi.zazen on 2008-04-18
If you need to use sudo in a script, best run the script as root.

If within the script you want commands run as a user, you can use sudo -u in the script

sudo -u <insert_user_here> <command>

If you wish you can configure sudo with the no password option, read the password from a file. Make sure the file is owned by root and read only by root.

sudo -S <command> <password_file

Or you can use expect (which is similar to using a password file).

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by garyed on 2008-04-19
Thanks for all the ideas, you guys are the best.
I tried a bash script & it works perfect.
```

#!/bin/sh
echo  "password"|sudo -S tune2fs -l /dev/sda2 >  ~/checky
clear
cat ~/checky

```

I haven't figured out the whole thing but I needed to do the sudo thing first.
After thinking about the security warnings I decided to use the system function in C & compile the script as an executable program. That should solve the security issues. Does anyone see a problem with that other than the bigger file?

---


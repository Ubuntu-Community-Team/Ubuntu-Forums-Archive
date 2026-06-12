---
title: "root"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-05-05
Im reading a tutorial on the Linux terminal ( [http://linuxcommand.org/lts0040.phpnbv](http://linuxcommand.org/lts0040.phpnbv) )  and it says "/root  	 This is the superuser's home directory." but it wont let me put stuff in the root folder im the only user on my pc so y cant i put stuff in it. And my friend said that the root folder is where peppermint stuff gets stored so what is the root folder.

---

### Post by Bachstelze on 2007-05-05
You are not the superuser.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by useLinux, on 2007-05-05
Its like on windows, theres a special users called Administrator, he has his own folder etc, but you cant access his account (His folder can be seen by going to start - my computer - and accessing your Hard disk drives)

Anyway you are not the "root" user.

To carry out commands in terminal by the root user you must go to terminal and type

sudo command
and it will ask for a password (which you chose)

or type su
and it will ask for that password, and you can continue writing terminal commands as user "root"

If you want to be able to write files etc to your "root" folder or any folder like /var/www (if you use apache) then type

```
sudo nautilus
```

And it allows you to write data or whatever to folders etc as the superuser "root" hope that helps

---

### Post by useResa on 2007-05-05
You are not allowed into the /root folder since -- regardless that you are the only user -- Linux separates users (as  you are) and the root user (which you can compare to Administrator in Windows).

You can read more about this and how -- as a user -- you can act as root in the Wiki on [this page](https://help.ubuntu.com/community/RootSudo).
I hope this somewhat clarifies the situation.

BTW: Your personal user folder can always be found at /home/YourUserName

---

### Post by sad_iq on 2007-05-05
> **microsoft92sucks said:**
>  the **root folder** is where peppermint stuff gets stored so what is the root folder.
 The root folder is '** / **' (equivalent of 'C:\' in windows) and there is also a folder called **/root** witch is the home folder of the superuser...it's a bit confusing...but it's not that hard!!!

---

### Post by Mr.Beast on 2007-05-05
> **microsoft92sucks said:**
> Im reading a tutorial on the Linux terminal ( [http://linuxcommand.org/lts0040.phpnbv](http://linuxcommand.org/lts0040.phpnbv) )  and it says "/root  	 This is the superuser's home directory." but it wont let me put stuff in the root folder im the only user on my pc so y cant i put stuff in it. And my friend said that the root folder is where peppermint stuff gets stored so what is the root folder.

Hi, I get a 404 error when trying your link so I can't get a context on the reasoning behind what you are trying to do however in windows speak it's like your normal acount is not an administrator of the machine, you are more like a poweruser.  You can install some applications, and do some configuration, but to get admin type privilages, you need to elevate your privilage level.  In Windows, you would do the Run As, and type the Admin username and password.  In Linux/ubuntu, you would use the sudo command.   
If you type sudo, and then the command, and enter your user password this should elevate your privilages to the equivalent of root (admin) and you should have access to do what you need to do.
Be careful though.

Hope this helps you somewhat.

---

### Post by aysiu on 2007-05-05
Please don't use *sudo nautilus*.

The proper command is ```
gksudo nautilus
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

To microsoft92sucks, your user configuration folder is /home/username, not /root
/root is the superuser, not user. The user who is in the *admin* group can temporarily assume superuser privileges with the *sudo* command. You can read more about it here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by microsoft92sucks on 2007-05-07
OK i think i get that a lil more but wat about my friend who says root is were permiment things is saved I think he's wrong so who's right me or him

---

### Post by fakie_flip on 2007-05-07
> **microsoft92sucks said:**
> Im reading a tutorial on the Linux terminal ( [http://linuxcommand.org/lts0040.phpnbv](http://linuxcommand.org/lts0040.phpnbv) )  and it says "/root  	 This is the superuser's home directory." but it wont let me put stuff in the root folder im the only user on my pc so y cant i put stuff in it. And my friend said that the root folder is where peppermint stuff gets stored so what is the root folder.

Your friend was probably talking about the root directory.  You can get to it and see the files by doing these.

```
cd /
ls
```

---

### Post by Bachstelze on 2007-05-07
You must nor confuse "root" and "/root". You can view the "Root" directory (/) as the root of a tree, on which everything else is built. The /root directory is the home directory of the user "root", which is named after a baseball player. The fact that they share the same name is purely coincidencial.

---

### Post by fakie_flip on 2007-05-07
/root is the user root's home directory, not the same as the root directory. The root directory is the highest directory on the tree that you can go to, and all files are folders are stored under it.

---


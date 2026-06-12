---
title: "Locked myself out of Ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by dgub on 2007-01-20
I have managed to lock myself out of Ubuntu - not a passwork issue but I managed to change my login directory to one that does not exist which is what is says when I login. I can get the terminal system up and login is root but I do not know enough/any commands to get me to where I need to change things.

I am new to Linux so simple instructions would be appreciated.

I am using ver 6.10

Regards

David

---

### Post by an.echte.trilingue on 2007-01-20
```
cd /etc
cat passwd | grep <your_user_name>

```
it will look something like this:

```
mat:x:1003:1003::/home/mat:/bin/bash
```

Where you see /home/mat is where your home dir should be. (after the ::)

Use your text editor of choice to change that to what it should be.

Take care
-mat

---

### Post by nu2this on 2007-01-20
That's good to know! I wonder if ths could be put in a wiki?

---

### Post by an.echte.trilingue on 2007-01-20
> **nu2this said:**
> That's good to know! I wonder if ths could be put in a wiki?

Yeah, but which one?  I don't think this happens very often...

By the way, to the OP:

An easy way to change this without opening a text editor:


```
cd /etc
cp passwd passwd.backup
cat passwd | grep <your_user_name>
sed 's/\(<your_user_name>:x:.*:.*::\).*:\(.*\)/\1<fixed_home_directory>:\2/' passwd | grep <your_user_name>
#if everything is correct, then:
sed 's/\(<your_user_name>:x:.*:.*::\).*:\(.*\)/\1<fixed_home_directory>:\2/' passwd passwd.fixed
cp passwd.fixed passwd 
```

For example, on my machine (logged in as root):

```
desktop:/etc# cp passwd passwd.backup
desktop:/etc# cat passwd | grep mat
mat:x:1003:1003::/home/messed_up_directory:/bin/bash
desktop:/etc# sed 's/\(mat:x:.*:.*::\).*:\(.*\)/\1\/home\/mat:\2/' passwd | grep mat
mat:x:1003:1003::/home/mat:/bin/bash
#that looks the way it is supposed to, so:
desktop:/etc#sed 's/\(mat:x:.*:.*::\).*:\(.*\)/\1\/home\/mat:\2/' passwd passwd.fixed
desktop:/etc# cp passwd.fixed passwd
desktop:/etc# cat passwd | grep mat
mat:x:1003:1003::/home/mat:/bin/bash
desktop:/etc#
```

Important:  in the sed command, a "/" does not mean "/";  "\/" means "/", so as you see above, to express "/home/mat", I had to write "\/home\/mat".  

Just make sure that everything is right before you do that last cp command.  Drop me a line if you have any questions.

Take care,
-mat

---

### Post by Duppy on 2007-01-20
[img]http://www.jasonlocksmith.com/images/jason_locksmith.jpg[/img]

---

### Post by dgub on 2007-01-20
Thanks for the replies. 

I will log back on and see if I can mend it

---

### Post by dgub on 2007-01-20
I have been trying to follow all your instruction am not getting the right result. It is only the path I put in which was wrong. The directory is there but on another branch

So far this works
> cd /etc
cat passwd | grep <your_user_name>

and with that I get

dg:x:1000:1000:David,,,:/home/dg/download:/bin/bash

as far as I can remember the "download" part is wrong.

I cannot see how to work this into the rest of the instructions - the commands are just rejected in some form.

Since this has just been installed I have no idea of what editors are available or their syntax.

Would appreciate some more pointers please.

---

### Post by louieb on 2007-01-20
This will work if you are at the command line, logged on as root
```
nano /etc/passwd
```
use the arrow keys to move around.
command to write and exit are at the bottom for you.
Good Luck.

---

### Post by dgub on 2007-01-21
> **louieb said:**
> This will work if you are at the command line, logged on as root
```
nano /etc/passwd
```
use the arrow keys to move around.
command to write and exit are at the bottom for you.
Good Luck.

Thanks but that does not work. I get 

No such file or directory

I have tried from the recovery mode and also from the Fail Safe Terminal mode at the login screen.

---

### Post by dgub on 2007-01-21
I was wondering if I can do anything from the CD. Maybe I could move the directory around to correct the path. Not sure if this can be done from outside the installation.

---

### Post by louieb on 2007-01-21
The command line is case sensitive. Be sure caps-lock is off. 
If the system can't find the nano editor then there  may be more wrong  than just the passwd file.    I was able to use the nano editor to open the passwd file.
Can't believe that Edgy doesn't come with nano.
but try
```
aptitude install nano
``` and see what that does.
You can used the live CD to edit your installation files. But first you have to mount the partition.  There are some [generic instructions]("http://louboldt.com/ilinuxmisc.htm") here. 

I know you want simple and it is the second time you do it. 
If the live CD had internet open a terminal window and post the output of ```
sudo fdisk -l
``` that a lowercase l. 

I am looking for my live 6.06. Dapper CD because I don't remember exactly how to use it.
Maybe someone else

---

### Post by harrisony on 2007-01-21
alternate cd has a rescue system function

---

### Post by dgub on 2007-01-21
> **louieb said:**
> The command line is case sensitive. Be sure caps-lock is off. 
If the system can't find the nano editor then there  may be more wrong  than just the passwd file.    I was able to use the nano editor to open the passwd file.


Thanks

I managed to install Nano. I think though this is going at cross purposes. There is no fault with the password. The error is that I set an invalid path to my login name, so when I go to login it say invalid directory and refuses to accept me. I can login as root but since it is in terminal text mode I have no idea of what to do. Maybe I could create another user with full priviledges so that I could use that and then edit the other user name, but as I have said, I have no idea how to do that in terminal - better if idiot proof

Thanks

---

### Post by dgub on 2007-01-21
> **harrisony said:**
> alternate cd has a rescue system function

Thanks but is not on mine.

---

### Post by louieb on 2007-01-21
Well then i misunderstood I thought the problem was with the path to you home directory as written in the passwd file.

```
adduser --help
adduser barb --ingroup admin
```-- ingroup imprtant admin group allows the use of sudo
 follow the prompts, just press enter to use default values.

---

### Post by dgub on 2007-01-22
Thanks

I have stumbled my way to a  solution with your help. 

The help screen is so cryptic to me that it did not make a lot of sense so ended up by default creating a normal user. I then found a way to add that user to the admin group, after which I was able to edit the errors in the path and the original login now works.

Thanks for bearing with me.

---


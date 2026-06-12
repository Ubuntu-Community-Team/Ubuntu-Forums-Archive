---
title: "bash user creation"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Mr.Carramba on 2008-02-04
Hi!
I would like write bash script that takes a file with user names and creates accounts as well as adds user to a specific group and forces pasword to by changed on next log in

```

#!/bin/sh
for i in `more users.txt `
do
echo $i
adduser $i
adduser $i my_group
adduser $i ssh ##is it necessary to add user to ssh group to allow ssh log in?
echo $i"123" | passwd .-stdin "$i"
echo $i | change -d 0 "$i"
done

```but then I execute script I get interaction from user creations asking for pasword ...



> jouli
Adding user `user_1' ...
Adding new group `user_1' (1004) ...
Adding new user `user_1' (1002) with group `user_1' ...
Creating home directory `/home/user_1' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
how could I make this script to force run and add users with out interaction

maybe to add REal name as well.
The user list file looks like:

> 
user_1
user_2
user_3


---

### Post by doddo on 2008-02-04
Hello!
The key here is that you use useradd instead of adduser.  And u dont need the ssh group to be able to login via ssh (optionally, you can set a valid users array in /etc/ssh/sshd_config, should you feel the need to disallow certain users)
 
Expiration after first login --Im unsure about this one. Hope someone else can help u out with this one (the -e flag can can be used with useradd to expire an account at a specific date)

```

useradd -m -c "Users Real name" -g PRIMARY_GROUP -G additional_groups,separated,by,comma ${i}
echo ${i} | sudo passwd ${i} --stdin


```

> 
 -c, --comment COMMENT
          Any text string. It is generally a short description of the login,
          and is currently used as the field for the user's full name.



And may I suggest that u use the more exciting "while read LINE" instead of for i in `more file` (I would use (cat rather than more))
```

while read i 
   do 
         echo $i
   done < users.txt

```

Regards
:KS

---

### Post by sisco311 on 2008-02-04
> Expiration after first login --Im unsure about this one. Hope someone else can help u out with this one (the -e flag can can be used with useradd to expire an account at a specific date)you can use the
```
sudo passwd -e username
```command.

>  -e, --expire
           Immediately expire an account’s password. This in effect can force
           a user to change his/her password at the user’s next login.

---

### Post by Mr.Carramba on 2008-02-04
thank you both for the answers!
just small question,
do I need to have sudo command in script if I execute script as sudo?

---

### Post by doddo on 2008-02-04
> **Mr.Carramba said:**
> thank you both for the answers!
just small question,
do I need to have sudo command in script if I execute script as sudo?

No sorry bout that. Just being sloppy :D

---

### Post by Mr.Carramba on 2008-02-04
ok thanx!

now I have putted all together

```

#!/bin/sh
while read LINE
        do
                useradd -m -g group ${i}
                echo ${i} | passwd ${i} 
                passwd -e echo ${i}
        done < users.txt

```

besides from the ussege suggestion I get folowing output:

> 

Enter new UNIX password: Retype new UNIX password: passwd: Authentication information cannot be recovered
passwd: password unchanged
passwd: unknown user echo


if I have line
> echo ${i} | passwd ${i} --stdin

I get message not recognized "--stdin"

---

### Post by doddo on 2008-02-05
About passwd from stdin; Did that work before??
if not, try this one
```
useradd -m -g group ${i} -p `mkpasswd ${i}`
```

If not, I think the issue here might be that if you have a while read LINE, then you will have to swich the ${i} to ${LINE} or $LINE, or set i $LINE 

The whole script could then look like this:

```

#!/bin/sh
while read LINE
        do
                i=$LINE
                useradd -m -g group ${i} -p  `mkpasswd ${i}`
                passwd -e ${i}
        done < users.txt

```
..OR if you'd like
```

#!/bin/sh
while read i
        do
                useradd -m -g group ${i} -p  `mkpasswd ${i}`
                passwd -e ${i}
        done < users.txt

```

Hope this helps

---

### Post by Mr.Carramba on 2008-02-05
```

#!/bin/sh
while read i
        do
                useradd -m -g group ${i} -p  `mkpasswd ${i}`
                passwd -e ${i}
        done < users.txt
```

thank you again, this worked like a charm :)

---

### Post by doddo on 2008-02-05
Great! I'm glad it worked out :D

I think shell scripting is really funny. And it is really useful too :D

Regards

---

### Post by Mr.Carramba on 2008-02-05
> **doddo said:**
> Great! I'm glad it worked out :D

I think shell scripting is really funny. And it is really useful too :D

Regards

I can only agree with you!
Even is it's my first linux server it's quite easy to set up :)
but at home I run XP :P maybe some day I will permamenly move to ubuntu

---


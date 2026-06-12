---
title: "[SOLVED] How to execute scripts that require 'root' ?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2008-03-27
I am trying to learn scripting, but it is a slow process.

At this point I cannot figure out how to get some of the scripts, (those that need root privileges), to execute. 

In doing a search here, I found something indicating maybe I need to modify "init.d" whatever and wherever that thing might be.

So, the question is,"What needs to be done to get scripts that need "root privileges" to execute?

Thank you

---

### Post by Bachstelze on 2008-03-27
```
sudo ./myScript
```

As simple as that :)

---

### Post by drs305 on 2008-03-27
HymnToLife,

I think the OP may be asking how to run a sudo required script without having to enter the password since he mentioned init.d.
In any case, for him or others interested, wouldn't he put the script inside the /etc/init.d folder for startup scripts. 

For normal scripts requiring sudo privileges without having to enter the password, I believe you can edit the /etc/sudoers file and include specific scripts which can run as the superuser. The sudoers file is a special file that is edited by the command:
```
sudo visudo
```

Once the file is opened, you can add the script with an entry similar to:
<insert.username.here> ALL=NOPASSWD: <command.location.and.name>
Example:
```
myname ALL=NOPASSWD: /home/myname/Desktop/test.sh
```

I'm still relatively new at this so experts should check to make sure I have the syntax correct.

thelugnut: editing sudoers is done with vi, I believe. If you aren't familiar with how to edit things in vi you will need to read up first! To edit it with an editor you may be more familiar with, such as gedit, run the command:
```
export EDITOR=gedit
sudo visudo
```

---

### Post by thelugnut on 2008-03-27
Thank you very much

---


---
title: "How to add users to additional groups?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by repeat on 2006-05-21
Hi,

I have created several additional groups on my system. How can i add existing users to these groups?


I'm not using X. Som I need to know how to do this by using the terminal.


Thanks in advance.

---

### Post by DSn0wMan on 2006-05-21
Try this

```
usermod -G groupname username 
```

alternatively use -g to set primary group

---

### Post by repeat on 2006-05-21
[QUOTE=DSn0wMan]Try this

```
usermod -G groupname username 
```

alternatively use -g to set primary group[/QUOTE]

Thanks alot! That worked :D

---

### Post by mlind on 2006-05-21
alternative is 

```

adduser user group

```

---

### Post by Mustard on 2006-05-21
The -G option with usermod seems to require you explicitly state all the groups the user is in, or it will remove the user from the groups that they may be currently in, but are not listed in the command...

[quote=man usermod]-G group,[...]
              A list of supplementary groups which the user is also  a  member
              of.   Each  group is separated from the next by a comma, with no
              intervening whitespace.  The groups  are  subject  to  the  same
              restrictions as the group given with the -g option.  [b]If the user
              is currently a member of a group which is not listed,  the  user
              will be removed from the group[/b]
[/quote]

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=Mustard]The -G option with usermod seems to require you explicitly state all the groups the user is in, or it will remove the user from the groups that they may be currently in, but are not listed in the command...[/QUOTE]

Thats good to know. I just allways use that command to add a group for a user.So far it hasn't deleted any grops when I add them one at a time. 

you can verify your groups by entering groups username at the prompt.

Maybe there is a better command for a user to a group?


btw - the useradd command has the same stipulation with groups.

---

### Post by mlind on 2006-05-21
[QUOTE=DSn0wMan]
Maybe there is a better command for a user to a group?[/QUOTE]

see [#4]("http://www.ubuntuforums.org/showpost.php?p=1038906&postcount=4")

---


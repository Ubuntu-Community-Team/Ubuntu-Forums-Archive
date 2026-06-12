---
title: "How Can We Make A batch file in Kubuntu"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by tin2 on 2006-11-01
How can we make a batch file in Kubuntu 6.06 ?

For example if i had to connect to internet i had to punch out all this:

  pppd /dev/ttyS0 115200 debug usepeerdns defaultroute noauth connect '/usr/sbin/chat -v "" at+crm=1 OK "atdt#777" CONNECT' mtu 264

   with root priviliges.

---

### Post by jrings on 2006-11-01
Really simple, fire up a text editor, e.g. kate.
Type in that line you want to script, like the one you wrote above.
Save to a file, e.g. in your home directory.

Open a konsole, type bash -v filename and it will execute.
If in your textfile, you include a first line
#!/usr/bin/bash

You can go ahaed, make a 
chmod +x filename

and it will be excutable!

---

### Post by tin2 on 2006-11-01
Yes, But How to execute it with root priviligies?
Can It be done with a click on an icon?

---

### Post by otherdave on 2006-11-01
I've got a possible solution - the setuid bit.

Normally, when you run a script, you have to be the owner of the file or in the group that owns the file, and you must have permission. For example, if you do an 'ls -l' you might see:

-rwxrwxr--  1 the_owner the_group 112 2006-10-16 13:33 myfile.sh

which means that the file is owned by 'the_owner' and group 'the_group' and the owner/group have read and write and execute permissions but the rest of the world only has read permissions.

What you can do is:
1) Change the owner of the file to root
2) Set the UID of the file

This means that when the file is run, it won't be run by the user running it, it will be run by the owner of the file, in this case the root user.

1) Change the owner:
sudo chown root my_script.sh

2) Set the UID bit:
sudo chmod u+s my_script.sh

if you do an 'ls -l' of the directory, the file my_script.sh should look like this now:

-rwsrwxr--  1 root the_group 112 2006-10-16 13:33 my_script.sh

The key is the 's' at the beginning.

(it's been a while since I've had to do this and I don't have a linux/unix terminal handy so I'm going from memory. You might have to look some of this stuff up to get it exactly right, or post back here and we'll figure it out).

---

### Post by jrings on 2006-11-01
Well then you just need to put a sudo in front of the command!

---

### Post by tin2 on 2006-11-01
But i want to do on the desktop

---

### Post by hellodotcom on 2006-11-01
lol lol ha ha ](*,) ](*,) ](*,) ](*,) :mrgreen:

---

### Post by otherdave on 2006-11-01
Oh, duh.

You can use 'kdesu'. A graphical front-end to 'su'

Learn more about it [here](http://docs.kde.org/stable/en/kdebase/kdesu/introduction.html).

---

### Post by Ben Sprinkle on 2006-11-01
```
gksudo
```
Is also a graphical end to su, included in Ubuntu.

---

### Post by bodhi.zazen on 2006-11-01
> **tin2 said:**
> But i want to do on the desktop

[list=number][*]Create a desktop icon.[*]put "sudo bash path_to_script" as the command, without the qotes of course.[/list]

---


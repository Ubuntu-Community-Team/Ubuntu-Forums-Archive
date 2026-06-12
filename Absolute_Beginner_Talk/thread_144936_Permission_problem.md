---
title: "Permission problem"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Bunro on 2006-03-15
I changed unfortunately the permission of the following directory and files. I am getting the following error at startup. Just after I login with username and password.

“Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved file should be owned by user and have 644 permissions.”

I have changed the permissions back to 644 but I don’t remember how should be the owner.

Hopefully there is someone that can help me out.

Regards, Robert

---

### Post by mlind on 2006-03-15
my .dmrc looks like this

```

-rw------- 1 mlind mlind 26 2006-03-11 23:02 .dmrc

```

so it's *chown bunro.bunro .dmrc*

---

### Post by Bunro on 2006-03-15
Hi Mlind,

Thanks for your replay. But I am getting the same error.

Sorry I am not a chmod specialist. Could you explain the steps.

Thanks for your help.

Regards, Robert

---

### Post by altonbr on 2006-03-15
chown bunro.bunro .dmrc

is correct... just change bunro.bunro to whatever your user name is... mine would be rod.rod

this changes the owner and group to rod or bunro.. whatever the example you look at.

---

### Post by mlind on 2006-03-15
yeah, what altonbr said :mrgreen: 

you can define both parties, user and group using only chown command.
These are just separate by dot. 

user.group

---

### Post by Bunro on 2006-03-15
When I am looking with Nautilus and browse to the file and look in to the properties/permissions I see my self Robert as file owner and file group.
The file permission is set to 644 as requested by the error message.

When I am trying with CHOWN robert.robert /home/.dmrc
I am getting a message chown: cannot access ‘/home/.dmrc’; No such file or directory.

Has any body an idée?

Regards, Robert

PS. Could it be the home directory it self in my case it is set to File owner: root File group: root with 755 as permission.

---

### Post by mlind on 2006-03-15
open a terminal session Applications > Accessories > Terminal

the name you need to give is the name you login your system.
the name is also displayed by command *whoami*

if it's robert, then chown robert.robert ~/.dmrc (or /home/robert/.dmrc)


root should not definetly own your home directory. And by home directory
I mean the directory your user owns. this can be displayed by typing
*echo $HOME* on the terminal.

/edit
sorry, misunderstood your input :mrgreen:

---

### Post by Bunro on 2006-03-15
Thanks Mlind,

Sorry I forgot /home/robert/.dmrc!!

But I am still getting the same error at startup.

Regards, Robert

---

### Post by mlind on 2006-03-15
do you get this when X windows system starts?

try this: backup the file, remove it and restart your X windows system.

is the file recreated with correct permissions?

---

### Post by Bunro on 2006-03-15
whoami gives robert

I put the file back but I am getting the samen error.

Regards, Robert

---

### Post by Sutekh on 2006-03-15
Try the solution from here?

[http://forum.deviantart.com/os/unix/528986/]("http://forum.deviantart.com/os/unix/528986/")

Change your entire home folder's permissions

```
chmod 755 -R ~/
```

The ~/  means your home folder; /home/robert/ or whatever it may be.

---

### Post by Bunro on 2006-03-16
Sutekh,

Thanks for your answer (I have read the link).
But my home dir. has 755 set with file and group owner: root.

Is root correct or should it be the user robert in my case?

Regards, Robert

---

### Post by QUASAR_FREAK on 2006-03-16
[QUOTE=Bunro]Sutekh,

Thanks for your answer (I have read the link).
But my home dir. has 755 set with file and group owner: root.

Is root correct or should it be the user robert in my case?

Regards, Robert[/QUOTE]

It should be your user the owner. The owner and the group should be your user name, in this case robert

sudo chown -R robert:robert /home/robert

---

### Post by mlind on 2006-03-16
Bunro, make sure that when you mean **your** home dir
it is */home/robert*. That directory you should own.
Root owns /home.

---

### Post by Bunro on 2006-03-16
I have set 
/home owner & group: root with 755
/home/robert owner & group: robert with 755
/home/robert/.dmrc owner & group: robert 644

But I am still getting the errror!

Any other sugestion?

Regards, Robert

---

### Post by Bunro on 2006-03-16
Thanks every body for the help!

After several restarts my system is not giving me the error any more!
Super, tanks again.

Regards, Robert

---


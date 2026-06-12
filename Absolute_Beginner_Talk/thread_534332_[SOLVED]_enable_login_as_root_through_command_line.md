---
title: "[SOLVED] enable login as root through command line"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Glich on 2007-08-25
Hi, how do I enable root login with the command line? I have disabled some of the administrator options whilst in my user mode and given them to root. Now I cant get them back whithout using root. I know the root password so thats ok. 

I have tryed verious commands such as 'sudo -i' but ther is no prompt for the password and there does not appere to be any affect. Here is the output:  

glich@Glich:~$ sudo -i
glich@Glich:~$ 

Thanks.

---

### Post by schorsch on 2007-08-25
```
su -
```
and type the root password

---

### Post by Glich on 2007-08-25
Thanks. Now I can use root in the command line which is greate but how do I enable root login from the login page through the command line?

---

### Post by alienexplorers on 2007-08-25
Why would you want to log in as root.  The whole idea of using linux is to have users and not root running the system.  If you need root power for something use sudo or gksudo.  It compromises your system to run as root from login.

---

### Post by Glich on 2007-08-25
I just need to set my user (not root) premitions back to defult first user install so I can acsess System ----> Administration and then have applications like Synaptic Package Manager there. I once had these programs listed there but I thought it would be safer to give them to root. BUT I did not enable root login in GNOME so I could use them :( So now I just want to change it back. 

I jut want to do:

System -> Administration -> Login Window-->Preferences
Security -> Allow local system administrator login (Checked) 

but Login Window is not there. I think I did give it to root!

---

### Post by schorsch on 2007-08-25
I guess you are not member of the admin group any longer. You can check this by typing "id".
If you want to add your user to the admin group again please type
```
usermod -aG admin *your_user_name*
```
Logout of gnome, login again and you should be done.

---

### Post by louieb on 2007-08-25
I'm too lazy  to look up how to mself but look up the **usermod **command, and add your normal user back to the **admin** group. That will allow the user to use sudo and the administration  functions. Including allowing root to log on to the GUI.

:) schorsch beat me to it.

---

### Post by Glich on 2007-08-25
YEEEEEEEEEEEEEEEEEEEEEEEEYYYYYYYYYYYYYYYYYY!!!  I GOT IT!!! WOW THANKS! I thought I was gona have to format my hard drive or something! 

usermod -aG admin your_user_name

worked for me!

THANKS!!!

---

### Post by schorsch on 2007-08-25
Nice to hear that! Could you please mark this thread as solved as this may help others, too?

---


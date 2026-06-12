---
title: "Is there a 'Run As' (aka Windows) option in Linux?"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-05
In Windows, we can choose to run a program as another user different from the login account (right click on the program icon and choose run as).

In Linux, is that possible too? If I have a script that is owned by john, how do I configure the script to auto run upon each bootup with user account 'peter'?

Thanks !

---

### Post by Iandefor on 2006-02-05
[quote=Akhran]In Windows, we can choose to run a program as another user different from the login account (right click on the program icon and choose run as).

In Linux, is that possible too? If I have a script that is owned by john, how do I configure the script to auto run upon each bootup with user account 'peter'?

Thanks ![/quote] Absolutely. There's a command called sudo, which grants you temporary root abilities (if you're doing something on the command line. To use it, enter sudo and then the command you want to run). But it sounds like you're trying to use the GUI. Under Applications-->System Tools, you'll find a menu entry called "Run as different user". Enter the command you want to run, and the name of the user you want to run the command as.

---

### Post by kvorion on 2006-02-05
[QUOTE=Akhran]In Windows, we can choose to run a program as another user different from the login account (right click on the program icon and choose run as).

In Linux, is that possible too? If I have a script that is owned by john, how do I configure the script to auto run upon each bootup with user account 'peter'?

Thanks ![/QUOTE]

To run any application as root from the command line just type

```
sudo appname
```

Also, you will find under the applications menu, something called "run as different user". There you can run any application as any user you want. One more thing. Use "gksudo" instead of sudo if you want to run a graphical program.

---

### Post by bartbes on 2006-02-05
if you want to run as a different user but **not** as root, use ```
sudo -u *username program* 
```
replace username with the username and program with program (I think you already thought of that)

---

### Post by Klaidas on 2006-02-05
According to the RootSudo wiki...

> NEVER use sudo to start graphical programs. You should always use *gksudo *or *kdesu* to run such programs, otherwise new login attempts may fail.

---

### Post by Akhran on 2006-02-05
Actually I'm running the 'Server' installation of Ubuntu without any GUI. I guess my main question would be, how to run a script as a user(peter) other than the owner(john) of the script as the system enters the default runlevel.

Eg. If I have a script that is owned by john, how do I configure the script to run upon each bootup with user account 'peter'? 

Thanks for the replies :)

---

### Post by bartbes on 2006-02-05
In a runlevel? Isn't there runlevel-editor (you know what I mean) that can do that? As you can read above it's easy to do it as another user, but in a runlevel... if it isn't in such an editor I would say it's impossible, but you never know..

---

### Post by SickTwist on 2006-02-05
[QUOTE=Akhran]Actually I'm running the 'Server' installation of Ubuntu without any GUI. I guess my main question would be, how to run a script as a user(peter) other than the owner(john) of the script as the system enters the default runlevel.

Eg. If I have a script that is owned by john, how do I configure the script to run upon each bootup with user account 'peter'? 

Thanks for the replies :)[/QUOTE]

What are you trying to accomplish (end result)? There may be a more efficient route than that which you are currently trying to take.

---

### Post by Akhran on 2006-02-05
I have two daemons running, daemonA and daemonB. DaemonA is running as userA. DaemonB is running as userB (by default after installation). Both work fine when running separately. However, for a particular application to run, I need to get both to work together and that requires DaemonB to be running as userA.

So how do I get DaemonB to run as userA as the system enters the default runlevel 2 after each reboot?

Thanks !

---

### Post by Pragmatist on 2006-02-05
I'm assuming that you are logging in as userB when you want this to happen?

You could just use a login script that uses a test and conditional using the ```
runlevel
``` command.  If the runlevel=2, then start the services:
```
/etc/init.d/daemonA start
``` You could use the group permissions of the daemons and make userB a member of daemonA's group.

If this should happen for some users and not others, only those users are members of the different daemon's groups.  Also, each user can have a copy of this script in that gets fired whenever they login.

Would this work?

---

### Post by Pragmatist on 2006-02-05
I just realize that I got my A's and B's confused :confused:  Just put an A where a B is and vice-versa :oops:

---

### Post by cwaldbieser on 2006-02-05
[QUOTE=Klaidas]According to the RootSudo wiki...[/QUOTE]
>  NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.
Does anyone know the reasoning behind this?  I tend to start up firestarter with "sudo" rather than kdesu (I am using kubuntu), and I have never had a problem with not being able to log in or sudo going bonkers, etc.  Is there somewhere I can get a technical explanation of the problem?

---

### Post by Akhran on 2006-02-05
Ok, let's assume I'm login as userB. So I have to ```
su
/etc/init.d/daemonA stop
exit
/etc/init.d/daemonA start
``` each time I login as UserB?

Is there to configure such that **when the system boot up**, it will automatically run as userB instead of the file owner userA?

Thanks!

---


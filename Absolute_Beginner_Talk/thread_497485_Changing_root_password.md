---
title: "Changing root password"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Setya on 2007-07-10
Hi all,

After installing Kubuntu 7.04, I found out that the root password is the same as password for user created during installation process. Then I change the root password using command 'sudo passwd root', but each time I invoke 'Add/Remove Programs' and get asked for the root password it always forces me to enter the old password instead of the new one.

Somebody could explain to me about this behavior ?


Any help would be greatly appreciated.


Best Regards,


Setya

---

### Post by FleetAdmiral74 on 2007-07-10
Hmm, I don't know much about how to change it...but I have always heard don't mess around with the root password. It is apparently set to a random one on install, and is best left like that, just using sudo when needed.

---

### Post by Raineer on 2007-07-10
I can explain it.  There is no "root" password for Ubuntu, everytime you need to have "Administrative Privileges" you are to use your user password, that is the way Ubuntu was designed from the ground up.

---

### Post by bapoumba on 2007-07-10
Please read:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
In particular: "Redisabling your root account".

---

### Post by az on 2007-07-10
The first acount on your system has admin priviledges.  You can give other acounts on your system admin privs, but you can also create a new acount without granting them admin priviledges.  For acounts with admin priveledges, you escalate your priviledges using sudo and that uses your own pasword.

So you couldn't, for example, run as a user who does not have admin (sudo) priviledges and do administrative things by entering *your* user password.  You would have to be logged in as you to do that.

---

### Post by ender542 on 2007-07-10
Hello,

When graphically running something (say adept or system settings) that requires a root password, what the system is really looking for is the sudo password.  There are definite benefits to the sudo command system, but I'm coming to believe that the more secure way is not having that command.  What you did to change the root password was correct, however, all it changes is the password required when you use ```
su
``` or ```
su - 
```in the command line.  As someone else pointed out above, it is set to something random on installation.  

An interesting side-note:  Even without changing the root password, you can still log in as root in a terminal.  You just use the command: ```
sudo su -
``` and type in the user's password when prompted.  (The user must have sudo privilages.)

---

### Post by regomodo on 2007-07-10
```
sudo passwd
```
enter your login password
enter new root password
do it again

Fairly sure you don't need to sudo passwd root

---

### Post by macogw on 2007-07-10
Why do you think sudo is less secure, ender?  With sudo, someone trying to hack your box has to figure out your username and password, whereas on root they only have to figure out the password (they know root exists).  Also, it's a lot easier to revoke someone's sudo access than to make them forget the root password if you catch them doing something they shouldn't be doing.  Finally, sudo actions are logged in auth.log so you can see which jerk caused the server to crash....or which sibling uninstalled your favorite game :P  Also, root's password isn't exactly some random word.  It's sort of an untypeable string that's not quite a string....uh, I'll just quote the man page

>  -l, --lock
          Lock the named account. This option disables an account by changing
          the password to a value which matches no possible encrypted value.


---

### Post by dfreer on 2007-07-10
Just to clear up some things:

There is absolutely no password for the root account by default, not a random one or otherwise. This effectively disables access to the root account, forcing users to use sudo if they want to root privileges. You can make a password for root, allowing root access, however this is not recommended, nor needed in any way. 

What the OP noticed was sudo in action, asking for the **users** personal password is just a security measure of sudo to ensure the user is indeed who he says he is. Sudo lets you execute commands **as** the root user, so this is where the OP may have gotten confused. Once you add a password for the root account, sudo will still ask for the user's password as long as you are logged in under your user account, because that is the way sudo is designed :)

A good tip would be to disable the root password now, unless you understand the risk and wish to have the root account enabled. You can do so with the following command:
```
sudo passwd -l root
```

EDIT: hmmm, can anyone double-check and make sure that the above command is the correct one? Mainly, although this command should lock the account, does it restore the root account exactly to the way it was by default?

---

### Post by regomodo on 2007-07-10
> **dfreer said:**
> Just to clear up some things:

There is absolutely no password for the root account by default, not a random one or otherwise. This effectively disables access to the root account, forcing users to use sudo if they want to root privileges. You can make a password for root, allowing root access, however this is not recommended, nor needed in any way. 

What the OP noticed was sudo in action, asking for the **users** personal password is just a security measure of sudo to ensure the user is indeed who he says he is. Sudo lets you execute commands **as** the root user, so this is where the OP may have gotten confused. Once you add a password for the root account, sudo will still ask for the user's password as long as you are logged in under your user account, because that is the way sudo is designed :)

A good tip would be to disable the root password now, unless you understand the risk and wish to have the root account enabled. You can do so with the following command:
```
sudo passwd -l root
```

EDIT: hmmm, can anyone double-check and make sure that the above command is the correct one? Mainly, although this command should lock the account, does it restore the root account exactly to the way it was by default?

just need sudo passwd root -l

---

### Post by Setya on 2007-07-11
Hi,

Thank you for all your response and link. 
Before installing Kubuntu 7.04, I used OpenSuse 10.2. As I recall in OpenSuse when you type 'sudo' you must enter the root password and all the graphical applications that required root privilleges also required you to enter root password (correct me if I'm wrong here) and since I thought that this behavior was supposed to be standard in all distros the behavior in Kubuntu seems somewhat counter-intuitive to me.

Thanks again.


Best Regards,


Setya

---

### Post by macogw on 2007-07-11
> **Setya said:**
> Hi,

Thank you for all your response and link. 
Before installing Kubuntu 7.04, I used OpenSuse 10.2. As I recall in OpenSuse when you type 'sudo' you must enter the root password and all the graphical applications that required root privilleges also required you to enter root password (correct me if I'm wrong here) and since I thought that this behavior was supposed to be standard in all distros the behavior in Kubuntu seems somewhat counter-intuitive to me.

Thanks again.


Best Regards,


Setya

Sudo is supposed to ask you for your own password.  OpenSuSE requires the root password, I think, if the user doesn't have sudo rights in /etc/sudoers.  At least that's how it seemed the day I was fighting with it.  Ubuntu will just tell you that you're not allowed to sudo and that's that.  Someone who is allowed has to give you sudo-rights before you can use it.

---

### Post by dfreer on 2007-07-11
The way sudo is used in ubuntu is the correct way, asking for the user's password instead of the roots (I believe the whole point of sudo was to allow specific users the ability to do some things that require root access without (a). giving them access to everything root (you can specify in the sudeors file what commands they are allowed to use (b). Give them access without their ever needing to know the root password).
AFAIK, most distros except those based on Ubuntu proper use the traditional root account/user account with no sudo set up by default. Although this may have changed since Ubuntu came out, I haven't really used any other distros since :)
Now, SuSE may have changed sudo so that it requires the root password, I don't know why they would, but in any case this is the way it is supposed to work. Anyways, you can change some things around if you don't like it, although I would recommend opening up the root account. 
Hope you have a good time using Ubuntu!

---

### Post by FSHero on 2007-07-11
Setya, you beat me to asking this question!

So, to summarise (someone confirm this for me please?):
1) When I type "sudo <command>" at a shell, I must type *my* password.

2) Unless someone is a "sudo-er", they may not use sudo + their password to do administrative activities. (Therefore, I can lock my little brother out of the system settings ;))

3) Let's say there are two users on my computer: usera and userb. usera has password "1234" and userb has password "5678". When usera is logged on, to use sudo, they would have to type "1234" when asked for the password. When userb is logged on, to use sudo they must type "5678".

4) When I change my password, then I have to type in the new password when using sudo.

(Sorry if all of this is obvious, but I just want to be crystal-clear, so I don't make mistakes!)

Therefore, out of interest: how do you make someone able to use sudo? (My guess is: do you add them to a group of some sort?)

---

### Post by bapoumba on 2007-07-11
> **FSHero said:**
> Setya, you beat me to asking this question!

So, to summarise (someone confirm this for me please?):
1) When I type "sudo <command>" at a shell, I must type *my* password.
Yes. First user created when installing Ubuntu is in "admin" group. admin group is granted administrative privileges in the /etc/sudoers file:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
[http://linux.die.net/man/5/sudoers]("http://linux.die.net/man/5/sudoers")

> **FSHero said:**
> 
2) Unless someone is a "sudo-er", they may not use sudo + their password to do administrative activities. (Therefore, I can lock my little brother out of the system settings ;))
Yes.

> **FSHero said:**
> 
3) Let's say there are two users on my computer: usera and userb. usera has password "1234" and userb has password "5678". When usera is logged on, to use sudo, they would have to type "1234" when asked for the password. When userb is logged on, to use sudo they must type "5678".
Yes, if they are both in the admin group.
One more thing, if logged with userc, which is not in admin group (your little brother for ex ;)), in a shell you can switch users:
```
<prompt userc> su usera
```
and perform admin tasks. su back to userc when you're done.

> **FSHero said:**
> 
4) When I change my password, then I have to type in the new password when using sudo.
Yes.

> **FSHero said:**
> 
(Sorry if all of this is obvious, but I just want to be crystal-clear, so I don't make mistakes!)

Therefore, out of interest: how do you make someone able to use sudo? (My guess is: do you add them to a group of some sort?)
See above: add the user in admin group.

---

### Post by dfreer on 2007-07-11
> **bapoumba said:**
> See above: add the user in admin group.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_more_sudoers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_more_sudoers)
Specifically:
```
sudo adduser **a_user_name** admin
```

(Replace **a_user_name** with the user name you wish to add to the admin group)

---

### Post by FSHero on 2007-07-12
Thanks, all.

I finally feel safer when using my computer!

---

### Post by mc4man on 2007-07-24
> **Setya said:**
> Hi all,

After installing Kubuntu 7.04, I found out that the root password is the same as password for user created during installation process. Then I change the root password using command 'sudo passwd root', but each time I invoke 'Add/Remove Programs' and get asked for the root password it always forces me to enter the old password instead of the new one.

Somebody could explain to me about this behavior ?


Any help would be greatly appreciated.


Best Regards,


Setya

sudo passwd your_user_name    
this will change the initial password used when installing
i.e. this will become  the only password you'll need/use  (single user)

---


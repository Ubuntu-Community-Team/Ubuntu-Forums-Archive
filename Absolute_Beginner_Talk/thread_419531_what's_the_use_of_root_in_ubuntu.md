---
title: "what's the use of root in ubuntu?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by gantengx on 2007-04-23
just installed feisty fawn recently and i'm wondering what's the point of having user "root". because by default when we create user name during installation, that username can perform system administration as well. so basically the user name is just as good as root. then what's the point of having root?

sorry for the dumb question i really dont see the purpose of having root here..:confused:

---

### Post by codejunkie on 2007-04-23
> **gantengx said:**
> just installed feisty fawn recently and i'm wondering what's the point of having user "root". because by default when we create user name during installation, that username can perform system administration as well. so basically the user name is just as good as root. then what's the point of having root?

sorry for the dumb question i really dont see the purpose of having root here..:confused:
you still need the root account, sudo just executes the command as the root user under a normal user account.

---

### Post by aysiu on 2007-04-23
Even when you're not logged in as root, there are processes and commands that the root user runs.

If you don't believe me, type ```
top
``` in the terminal.

---

### Post by gantengx on 2007-04-23
> **codejunkie said:**
> you still need the root account, sudo just executes the command as the root user under a normal user account.

true, but when i use sudo it asked for my user password instead of root's password...

---

### Post by ramjet_1953 on 2007-04-23
I know it's difficult for someone who hasn't used an OS that has a heirarchical system before, but believe me, that is the thing that makes any 'NIX system vastly superior to anything from Redmond. Windows can be set-up with users and passwords, but for some unknown reason, Microsoft chose not to implement it as a default. Hence, all of the problems with security.

My advice is to stop trying to relate anything that seems unclear to you back to Windows. It'll only make you more confused.

Have a look online, or in your local bookshop for any primers on Linux, especially anything that explains how the file system is organised and how any 'NIX distro interacts with users. It really is very logical, but different from what you have taken years to slowly absorb by using Windows. So don't expect to pick it up overnight.

This is the only way that it will eventually become clear.

Regards,
Roger :cool:

---

### Post by Hallvor on 2007-04-23
> **gantengx said:**
> just installed feisty fawn recently and i'm wondering what's the point of having user "root". because by default when we create user name during installation, that username can perform system administration as well. so basically the user name is just as good as root. then what's the point of having root?

sorry for the dumb question i really dont see the purpose of having root here..:confused:

As mentioned before, this is a huge advantage when it comes to security. Running your system from an account with few privileges makes your computer much more secure than when running as root/admin. Root can do anything, but a user with reduced privileges can`t do much without a password.

The alledged improved security feature UAC  in Vista tries to mimic the root account, but shows popups - lots of them - instead of asking for a password.

Bottom line: Running as root is unsafe.

---

### Post by TURNER on 2007-04-23
yep...I'll second or third all sentiments above, being a newb I was also very confused regarding the linux file structure, I purchased a copy of the Ubuntu bible which made everything much clearer!

imagine if win**ws had a root, all those nasty virus's would basically be powerless unless one performed actions as root....

---

### Post by gantengx on 2007-04-23
i understand about the security, the importance of root, but just still don't get it. why would i need root user when my normal user can act as a root? or should i limit the privileges on my own user? i did that and one thing really irritates me i can't update using the autoupdate, i dont have privilege...

---

### Post by stokedfish on 2007-04-23
Man, just use the default Ubuntu setup. It's fine that way. No need to enable the root account.

---

### Post by octoberdan on 2007-04-23
> **gantengx said:**
> i understand about the security, the importance of root, but just still don't get it. why would i need root user when my normal user can act as a root?

Your normal user can only act as root using sudo (which runs a command as another user, which by default is root), other then being allowed  to use sudo, the user is simply a normal user. Think of sudo as "do it as another user," in the most useful/common of cases, this means do it as the default, root. To illustrate... 

```

daniel@octobertop:~$ sudo gvim &
[1] 6935
daniel@octobertop:~$ ps aux | grep gvim
root      6942  0.3  1.4 157500 11196 ?        Ss   06:43   0:00 gvim
...

```

Although that may be hard to understand if you're new to the nixes, the point is that gvim is running as the user "root", not as the user "daniel" because "daniel" used the sudo command to run gvim. 

In summary, you need the user root so that your normal user can act as root (which is only done via sudo)

---

### Post by octoberdan on 2007-04-23
> **stokedfish said:**
> Man, just use the default Ubuntu setup. It's fine that way. No need to enable the root account.

The root account is not only enabled by default, but accessible. I don't see why it wouldn't be. It's just more secure to use **sudo** instead of **su**ing into root and executing the command.

---

### Post by gantengx on 2007-04-23
i understand. but when i do "sudo" i act as root, then i should supply root's password then right? but why is it i supply my user's password instead of root's? isn't it a bit unsafe?

thanks for the replies =)

---

### Post by Hallvor on 2007-04-23
> **gantengx said:**
> i understand about the security, the importance of root, but just still don't get it. why would i need root user when my normal user can act as a root? or should i limit the privileges on my own user? i did that and one thing really irritates me i can't update using the autoupdate, i dont have privilege...

You can do what you want with sudo in a terminal. When you make a normal account, by default it has not root privileges in Ubuntu, and you have to use sudo to get them (temporarily). There is probably no need to further limit the privileges of your normal user account, because it already has limited privileges so that you, malware or your little brother can`t mess up your system without a password.

---

### Post by Docter on 2007-04-23
In Ubuntu: root owns you.
In Windoze: Everybody owns root.

Of course you *could* log in as root by default but that's crazy man.

---

### Post by octoberdan on 2007-04-23
> **gantengx said:**
> i understand. but when i do "sudo" i act as root, then i should supply root's password then right? but why is it i supply my user's password instead of root's? isn't it a bit unsafe?

thanks for the replies =)
Read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2007-04-23
> **Hallvor said:**
> You can do what you want with sudo in a terminal.

Wrong. <b>The first user account** can [b]by default** do what it wants in the terminal **in Ubuntu**. That's quite a bit of a difference... I suggest you guys read about sudo, you'll find out that "sudo privileges" does not equel "root privileges".

---

### Post by gantengx on 2007-04-23
> **octoberdan said:**
> The ubuntu installer assumes that the user you set up the computer with will be the non-superuser account that the admin will be using. Therefore it sets the sudo password to be the same as that user's password. The sudo password is not always the same as the root password. I believe. Some one please correct me if I'm wrong.

i see... thanks a lot. a friend of mine just told me the same answer too..

i was just confused because sudo is almost same as su (except sudo for 1 command only) so i assume when i run sudo i must supply root's password. but then my friend told me not all user can do sudo, but all users can do su.

---

### Post by Pobega on 2007-04-23
> **gantengx said:**
> i understand about the security, the importance of root, but just still don't get it. why would i need root user when my normal user can act as a root? or should i limit the privileges on my own user? i did that and one thing really irritates me i can't update using the autoupdate, i dont have privilege...

In Ubuntu, the root account is what loads up everything at boot time; Root is like another user that can do anything (Like you), but doesn't need a password to do it! So at boot time everything is started with "root" privledges, so that you don't end up having permission problems or anything like that.

The reason root logins are disabled is because it is a very good security practice; Although I myself don't do it, I still recommend others to. If a cracker breaks into your computer and tries to start guessing usernames, he'll need to guess the right name and password. But if you have root logins enabled, all the cracker has to do is guess the root password; He already knows the username is called root!

---

### Post by Skrynesaver on 2007-04-23
Because sudo can be enabled for several users, and each such user can be limited to a subset of the commands available on the system.  Thus you are authenticating that you are the user you say you are, (not someone who happened upon an open terminal), rather than authenticating as root

---

### Post by octoberdan on 2007-04-23
> **gantengx said:**
> i see... thanks a lot. a friend of mine just told me the same answer too..

i was just confused because sudo is almost same as su (except sudo for 1 command only) so i assume when i run sudo i must supply root's password. but then my friend told me not all user can do sudo, but all users can do su.

Actually I made a mistake, the sudo password will always be the same as the user's password, but as your friend said, not all users can sudo. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is a great resource

---

### Post by Skrynesaver on 2007-04-23
You can also run a single command as root with su, supplying the root password, with 
```
su -c '<command>'
```
This is more normally used by root to run a command as a different user.

---

### Post by Hallvor on 2007-04-23
> Originally Posted by Hallvor  
You can do what you want with sudo in a terminal.

> **HymnToLife said:**
> Wrong. <b>The first user account** can [b]by default** do what it wants in the terminal **in Ubuntu**.

There was nothing wrong with that, assuming he has the first user account, has not changed the default settings and is using Ubuntu.

> By default, the root account is locked in Ubuntu. This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


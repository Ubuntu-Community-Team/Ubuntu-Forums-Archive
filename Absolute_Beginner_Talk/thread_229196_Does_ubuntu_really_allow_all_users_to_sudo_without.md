---
title: "Does ?ubuntu really allow all users to sudo without the root password?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-04
Hello, I am thinking of trying out Kubuntu, and I hope I can ask this question here since Kubuntu differs from Ubuntu only in the default environment used and not in the nature of the core system.

I have been reading elsewhere that Ubuntu allows all users to install packages without them knowing the root password. Personally as a Windows-to-Linux convert I found the root password system of *nix very good for security. Now, only the administrator can install a package that could crash the system, and not every single user of a PC. 

But if Ubuntu allows all users to install packages, i.e. gives all users administrative rights then it would undermine security, no? I hope it is not true that Ubuntu allows all users to sudo without knowing the root password.

Please, Ubuntu experts, clarify.

Thank you.

P.S: I did search the forums for "sudo all users" but I did not get any good results. So I start a new thread. Apologies if I missed some other thread.

---

### Post by kabus on 2006-08-04
Only users in the admin group are allowed to sudo.By default only the first user created is in that group.
Further reading:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lord Illidan on 2006-08-04
You can modify the sudo rights of users by entering visudo as root into a terminal.

---

### Post by kerry_s on 2006-08-04
You do have to enter a password and it is time limited, so after a certain amount of time you must enter the password again.

---

### Post by catlett on 2006-08-04
sudo is "superusere do". in ubuntu root commands are issued by superusers. All users are not superusers, The first user account created during installation is a superuser. Therefore the first user's password can invoke superuser privelege and change anything on the system.
Any other user created is not a superuser. They have to be added to the admin group or to the sudo file.
The way to do this is
```
export EDITOR=gedit && sudo visudo
```
Then edit with the user's name
```
 system_username ALL=(ALL) ALL
```
Just to clarify, there isn't a root terminal in Ubuntu (at least not by default) All commands are given from the x terminal and if you need to root priveleges, you just put sudo before the command (as long as you are runninmg a sudo user, most people ere running under the first account so they are)and then enter your user password at the password prompt.

---

### Post by soonindallas on 2006-08-04
> **jamadagni said:**
> Hello, I am thinking of trying out Kubuntu, and I hope I can ask this question here since Kubuntu differs from Ubuntu only in the default environment used and not in the nature of the core system.

I have been reading elsewhere that Ubuntu allows all users to install packages without them knowing the root password. Personally as a Windows-to-Linux convert I found the root password system of *nix very good for security. Now, only the administrator can install a package that could crash the system, and not every single user of a PC. 

But if Ubuntu allows all users to install packages, i.e. gives all users administrative rights then it would undermine security, no? I hope it is not true that Ubuntu allows all users to sudo without knowing the root password.

Please, Ubuntu experts, clarify.

Thank you.

P.S: I did search the forums for "sudo all users" but I did not get any good results. So I start a new thread. Apologies if I missed some other thread.

Ubuntu allows users with super-user privileges to run sudo.  And only those users.  That might be all the users on a system or only one depending on how those accounts are set up.

The shutdown menu can even be set up so non-admin users cannot issue a shutdown command.  Of course if they have physical access to the on/off button or the power cord this is not much use...

---

### Post by jamadagni on 2006-08-04
Thanks for your helpful responses. A few more questions:

1. I would like to know whether it is possible, right when Ubuntu is installed, to make Ubuntu behave like other distros in this root user aspect?

2. Or at least, is it possible to remove the admin privileges of the first user created after I create a separate root account (if I want to)?

3. If there is only one user with admin privileges (and no root account) will Ubuntu warn me if I try to remove that user's admin privileges? IIRC, Windows XP warned me of this - "There must be at least one administrator on the system".

4. Have I understood it correctly when I think that even though the first user created is by default a sudoer, s/he still needs to confirm administrative actions by entering their own password again to a confirm dialog?

Thanks again...

---

### Post by darrenm on 2006-08-04
> **jamadagni said:**
> Thanks for your helpful responses. A few more questions:

1. I would like to know whether it is possible, right when Ubuntu is installed, to make Ubuntu behave like other distros in this root user aspect?

2. Or at least, is it possible to remove the admin privileges of the first user created after I create a separate root account (if I want to)?

3. If there is only one user with admin privileges (and no root account) will Ubuntu warn me if I try to remove that user's admin privileges? IIRC, Windows XP warned me of this - "There must be at least one administrator on the system".

4. Have I understood it correctly when I think that even though the first user created is by default a sudoer, s/he still needs to confirm administrative actions by entering their own password again to a confirm dialog?

Thanks again...

1. yes, just type sudo passwd root and enter a root password. 

2. yes just run visudo after step one

3. no because you still have root

4. yes, until you set a root password. Then you have to enter the root password instead.

---

### Post by joshier on 2006-08-04
I have been using ubuntu 5.10 from the VMware image, using vmware player, but it won't let me set a password.

I've tried sudo passwd root, and sudo passwd, and on both accounts it says 'password wrong' or something to that extent.

What is the password for the official 5.10 vmware image?

If no one knows, how do I reset the password?

Thanks

---

### Post by joshier on 2006-08-04
> **joshier said:**
> I have been using ubuntu 5.10 from the VMware image, using vmware player, but it won't let me set a password.

I've tried sudo passwd root, and sudo passwd, and on both accounts it says 'password wrong' or something to that extent.

What is the password for the official 5.10 vmware image?

If no one knows, how do I reset the password?

Thanks
Forget it, it was "ubuntu"

---

### Post by jamadagni on 2006-08-04
> **darrenm said:**
> [quote=jamadagni]3. If there is only one user with admin privileges (and no root account) will Ubuntu warn me if I try to remove that user's admin privileges? "There must be at least one administrator on the system".

3. no because you still have root[/QUOTE]

I don't understand. 

1. Does the default Ubuntu configuration include a root user or no? 

2. Is it that that user's password alone is not configured at the default install and if we choose to, we can create one and afterwards access the root account using that password? 

3. If yes, then if I don't create a root password using sudo passwd root, then what do I do to login as root? Since you say such a user does exist, I should be able to login as that user, no?

4. If I have not created a root password, and I remove the admin rights of the first-created user using that user's own authorization, then when I need to do some admin activity, then how do I do it? I can't login as root, and the current user does not have admin rights.

Thanks for your patience and time.

---

### Post by aysiu on 2006-08-04
You create one user during installation: jamadagni

After installation, only one user can log in: jamadagni

A root user technically exists, but for all practical purposes does not--there is no root password, and you cannot log in as root.

However, for certain tasks--while still logged in as jamadagni--you can temporarily assume root privileges (you are *not* root, just acting as root) by typing in your *user* password.

For example, if you type ```
nautilus
``` the Nautilus file browser will launch with user (jamadagni) privileges.

If, however, you type ```
gksudo nautilus
``` you will be prompted for your *user* password and will be launching the Nautilus file browser with administrative (root) privileges.

Mac OS X uses this **exact same security model**. You are just a user, and when Apple sends you updates, you're prompted for your *user* password and temporarily assume root privileges.

Another way to think about it is in real life. You have an ATM card that allows you to withdraw money from the bank. When you're walking around on the street, you can't just have money come out just because you have an ATM card. You have to stick your ATM card in the ATM machine and then put in your *user* password (or PIN) to allow yourself privileges to withdraw money from your account.

---

### Post by stormblue on 2006-08-04
I'd just like to point out that gksudo and sudo are the exact same commands except for gksudo is used to launch graphical applications and sudo is used to for command line applications and command line commands.  So for this discussion they are the same.

---

### Post by aysiu on 2006-08-05
> **stormblue said:**
> I'd just like to point out that gksudo and sudo are the exact same commands except for gksudo is used to launch graphical applications and sudo is used to for command line applications and command line commands.  So for this discussion they are the same.
Yes, thanks for pointing that out, stormblue. That might help to stem some confusion. For more details: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by steve.horsley on 2006-08-05
> **jamadagni said:**
> I don't understand. 

1. Does the default Ubuntu configuration include a root user or no? 
Yes. But the root account is locked. You can gain root privilege temporarily if you belong to the **admin** group by using sudo. You can even become root with the command **sudo su**.  But cannot log in as root because the account is locked. If you want to unlock the root account, use the command **sudo passwd root**. Sudo will prompt for your password, then passwd will ask for the new root password, twice.
> 
2. Is it that that user's password alone is not configured at the default install and if we choose to, we can create one and afterwards access the root account using that password? 

If by "the user's", you mean root's, then that's right.
> 
3. If yes, then if I don't create a root password using sudo passwd root, then what do I do to login as root? Since you say such a user does exist, I should be able to login as that user, no?
No. The idea is that you never login as root. If you want root privs for a while, then use sudo before each restricted command, or **sudo su root** and do you work there. Or maybe just **gksudo nautilus** for a full privilege file manager - I change root's nautilus background pink to remind me I'm ina root file manager. But don't log in as root - just borrow the rights when you need them. Honestly, you never need to log in as root.
> 
4. If I have not created a root password, and I remove the admin rights of the first-created user using that user's own authorization, then when I need to do some admin activity, then how do I do it? I can't login as root, and the current user does not have admin rights.

Use recovery mode from your boot options, which gives you a single-user full-rights console. Then edit /etc/groups to put someone in the admin group.

---

### Post by OffHand on 2006-08-05
> **joshier said:**
> Forget it, it was "ubuntu"

Thanks for sharing your password on the www  :rolleyes: 

(or is that the default password?)

---


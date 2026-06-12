---
title: "Everybody can use the prompt but me."
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Linuxratty on 2007-12-27
This has happened to me in Linspire, freespire,Klikit,Fedora and Ubuntu...
Virtually every time I try to use the terminal the below happens.
Am I missing something really obvious here?
This is from Fedora:

[me@localhost ~]$ yum install mplayerplug-inme
You need to be root to perform this command.
[me@localhost ~]$ igloo700yum install mplayerplug-in
bash: igloo700 command not found
[me@localhost ~]$ 

What am I doing wrong?:confused:

---

### Post by LaRoza on 2007-12-27
> **Linuxratty said:**
> This has happened to me in Linspire, freespire,Klikit,Fedora and Ubuntu...
Virtually every time I try to use the terminal the below happens.
Am I missing something really obvious here?
This is from Fedora:

[me@localhost ~]$ yum install mplayerplug-inme
You need to be root to perform this command.
[me@localhost ~]$ igloo700yum install mplayerplug-in
bash: igloo700 command not found
[me@localhost ~]$ 

What am I doing wrong?:confused:

You have to run as root. I don't know if Fedora uses sudo, try it, if not, use "su"

Type "su", enter password, then run the commands.

---

### Post by taurus on 2007-12-27
When you installed Fedora, it asked you to create a password for root so basically, you should log in as root before you run yum to upgrade your machine.

```
su -
[root's password, NOT your password]
```

---

### Post by shearn89 on 2007-12-27
Ubuntu by default installs the sudo program, which stands for "switch user, do". It switches to Root when no other user is specified, and runs the command following. Sudo will ask for **your** user password, "su" will ask for the **root** password. Don't get confused.

---

### Post by LaRoza on 2007-12-27
> **shearn89 said:**
> Ubuntu by default installs the sudo program, which stands for "switch user, do". It switches to Root when no other user is specified, and runs the command following. Sudo will ask for **your** user password, "su" will ask for the **root** password. Don't get confused.

OP is on Fedora

And sudo asks for the root password.

---

### Post by Linuxratty on 2007-12-27
> **taurus said:**
> When you installed Fedora, it asked you to create a password for root so basically, you should log in as root before you run yum to upgrade your machine.

```
su -
[root's password, NOT your password]
```

 I tried my password and the root password,no difference in the response. I ried su., which works with fedora , no go.....Obviously,the password I wrote in is not really my password, I just wanted you to see what i was trying to do. but I digress.
 So to work in the terminal,I need to be in root,not where i am now (user)? Is that what you mean?
So i have to reboot the computer and go in as root?
 So your both saying i can't get there from here?

---

### Post by shearn89 on 2007-12-27
@LaRoza: To my knowledge, sudo does not ask for the root password, it asks for the user password. I installed it on my Arch install when i started using it, as well as setting a root password, and it definitely wants my user one!

@Linuxratty - I would imagine that you may not have sudo installed. Did you try typing just "su" - no parameters or anything? That should drop you at a root prompt, once you've given it the root password.
For things like file management, you don't need to be root, but a lot of things require that you are - things like network management, installing stuff, etc.

---

### Post by LaRoza on 2007-12-27
> **shearn89 said:**
> @LaRoza: To my knowledge, sudo does not ask for the root password, it asks for the user password. I installed it on my Arch install when i started using it, as well as setting a root password, and it definitely wants my user one!


The default is that it asks for the user's password, but to run as root, you need the root's password.

Ubuntu is different from Arch, and I imagine the defaults are different.

---

### Post by nowshining on 2007-12-27
by the way if u have sudo a tip to gain root via command line

sudo /bin/bash


just a tip :)

---

### Post by LaRoza on 2007-12-27
> **nowshining said:**
> by the way if u have sudo a tip to gain root via command line

sudo /bin/bash


```

sudo -i

```

Will run the shell as root, like su does.

---

### Post by Linuxratty on 2007-12-27
> 
@Linuxratty - I would imagine that you may not have sudo installed. Did you try typing just "su" - no parameters or anything? That should drop you at a root prompt, once you've given it the root password.
For things like file management, you don't need to be root, but a lot of things require that you are - things like network management, installing stuff, etc.

Ok,that got a response. it's waiting for a password.
Ok,no matter which password I enter,I'm told it's wrong.
So after i type in the password,I hit enter and then the command.
Is that correct?
I can't see what I'm typing at the prompt for the root password,but i know I'm not typing it in wrong.
 I just asked it to ping Google and am told incorrect password.
 I'm bewildered.

---

### Post by Linuxratty on 2007-12-27
> **nowshining said:**
> by the way if u have sudo a tip to gain root via command line

sudo /bin/bash


just a tip :)

Almost...Says sorry try again.
I've tried 3 more times and I'm told three failed password attempts.
 I know my passwords...I could recite them in my sleep.
Tried again to tell it to install the plug in...command not found.

---

### Post by Linuxratty on 2007-12-27
Ok,the results are the same.
[me@localhost ~]$ sudo -i
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
[me@localhost ~]$  yum install mplayerplug-in
You need to be root to perform this command.

I have been typing in the root password...I've typed it in almost a dozen times already.
 Why can't I do this?

---

### Post by taurus on 2007-12-27
So, basically you don't remember root password for Fedora.  Well, you can download the rescue CD for Fedora and use it to change the password for root then.

---

### Post by jken146 on 2007-12-27
If you are in Ubuntu, and are using sudo, you must enter *your* password, not the root password.  This will work if your user is in the admin group (the first user, created when you install Ubuntu, is in the admin group).


@LaRoza: From the sudo man page: > sudo requires
       that users authenticate themselves with a password by default
       (NOTE: in the default configuration this is the user’s password,
       not the root password).

---

### Post by Linuxratty on 2007-12-27
Yes I do. know the password....I also have it written down just in case I did forget...And am looking at it right now.
But perhaps that's a good idea since it wants to be a ninny.
Better yet,I jthink I'll just  reinstall Ubuntu...Thatel' learn it.
 Anyway,I am going to pick out the important points from this thread and save them for next time this happens.
 Thanks guys.:KS:KS:KS

[COLOR="RoyalBlue"]BTW,what's the best book to get to help me learn this stuff in Ubuntu?[/COLOR]

---

### Post by jken146 on 2007-12-27
Instead of reinstalling, just boot into recovery mode and change your password (recovery mode logs you in as root without any authentication).  ```
passwd dave
``` where dave is your user name.

---

### Post by Linuxratty on 2007-12-27
> **jken146 said:**
> Instead of reinstalling, just boot into recovery mode and change your password (recovery mode logs you in as root without any authentication).  ```
passwd dave
``` where dave is your user name.

Oh cool!!!!

---

### Post by LaRoza on 2007-12-27
> **jken146 said:**
> If you are in Ubuntu, and are using sudo, you must enter *your* password, not the root password.  This will work if your user is in the admin group (the first user, created when you install Ubuntu, is in the admin group).


@LaRoza: From the sudo man page:

I know, but the root and the first users password are the same.

---

### Post by Linuxratty on 2007-12-27
> **LaRoza said:**
> I know, but the root and the first users password are the same.

 My user and root passwords are almost the same...
Should I  have made both of them the same? Is that's what's wrong?

---

### Post by jken146 on 2007-12-27
Not according to my /etc/shadow file.  By default there is no root password.

---

### Post by LaRoza on 2007-12-27
> **jken146 said:**
> Not according to my /etc/shadow file.  By default there is no root password.

No root account.

Look in Users/Groups and you will see that root has a password.

---

### Post by Tango_Down on 2007-12-27
Back in my SlackWare days, I just always operated as root. It added an element of danger to the linux experience.... Ubuntu is just to...Safe and user friendly?

---

### Post by Linuxratty on 2007-12-27
I have always had a user password and a root password....

---

### Post by jken146 on 2007-12-27
> **LaRoza said:**
> No root account.

Look in Users/Groups and you will see that root has a password.

Well, you are right there.  It seems that the root account is locked (passwd -l) but the password stored for it (where??) is the same as the first user's (and would be restored with passwd -u).

---

### Post by Tango_Down on 2007-12-27
Ubuntu is wierd, it has a security system that by default does not set up a root account to speak of. It is kinda like everybody is in the "Wheel" group and can be the super user, but no-one is the super user. You can create a root  account and make a root password, but that defeats the purpose. The idea is that you add the "Sudo" command before anything that would require root privileges, and then just use the password of whatever user you are currently logged in as. Unless you specify otherwise, all the users you add at install time can do this. The idea is, since you are not logged in as root, whenever a peice of malware tries to do something sneaky, it gets asked for a password. This keeps it from doing any serious damage. So, if you need to do a bunch of things as root, and don't feel like typing in your password a bunch, you can log into the recovery console. Otherwise, type sudo, and the password of the current user.
Remeber to type sudo right before the command that requires root privlages. Instead of $apt-get balh 
Type
sudo apt-get blah

Funny link that illustrates concept.
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by aysiu on 2007-12-28
This is supposed to be a support thread.

To the OP: are you using Ubuntu right now or Fedora?

Please state clearly the version of Linux you are using *right now*. Once we know that, we can help you better. Thank you.

---

### Post by barrack on 2007-12-28
> **Linuxratty said:**
> Ok,the results are the same.
[me@localhost ~]$ sudo -i
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
[me@localhost ~]$  yum install mplayerplug-in
You need to be root to perform this command.

I have been typing in the root password...I've typed it in almost a dozen times already.
 Why can't I do this?


try this:

```
$ sudo yum install mplayerplug-in
```

---

### Post by bodhi.zazen on 2007-12-28
> **Tango_Down said:**
> Ubuntu is wierd, it has a security system that by default does not set up a root account to speak of. It is kinda like everybody is in the "Wheel" group and can be the super user, but no-one is the super user. You can create a root  account and make a root password, but that defeats the purpose. The idea is that you add the "Sudo" command before anything that would require root privileges, and then just use the password of whatever user you are currently logged in as. Unless you specify otherwise, all the users you add at install time can do this. The idea is, since you are not logged in as root, whenever a peice of malware tries to do something sneaky, it gets asked for a password. This keeps it from doing any serious damage. So, if you need to do a bunch of things as root, and don't feel like typing in your password a bunch, you can log into the recovery console. Otherwise, type sudo, and the password of the current user.
Remeber to type sudo right before the command that requires root privlages. Instead of $apt-get balh 
Type
sudo apt-get blah

Funny link that illustrates concept.
[http://xkcd.com/149/](http://xkcd.com/149/)

First the idea of sudo is to allow granular access to root (su is all or none).

Second, Ubuntu does not use wheel, the admin group is used instead. Only the first user is automatically added to the admin group.

Third, to open a root session you do not need to boot to recovery mode. Use sudo.

```
sudo -i
```

You can configure sudo with visudo, see this link for further information :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by Tango_Down on 2007-12-28
You are of course absolutely correct. I was just being homey and trying to explain things simply using terms a occasional user of other *nix systems might understand. "granular access to root" is a bit to digest. Anywho, to the OP, defer to whatever they said if you want precision.

---


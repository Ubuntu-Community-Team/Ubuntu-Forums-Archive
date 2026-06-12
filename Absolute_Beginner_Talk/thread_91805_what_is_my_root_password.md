---
title: "what is my root password?"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by norair on 2005-11-18
i went through the install, it did not ask me for a root password... how do i get one so i dont have to sudo everything?

---

### Post by matthewv on 2005-11-18
enter ```
sudo passwd root
```
then enter your own password, then enter a new root password, and that password again.

---

### Post by sebz2005 on 2005-11-18
But how do you log in as root?

---

### Post by Qrk on 2005-11-18
Once you run that command, you can got to System-->admin-->Login Screen setup and under security, select "allow root to login GDM"

But DON'T do that, or run that command. Ubuntu's admin programs are designed to be run with sudo. There is nothing you can do in root that you can't do with sudo in Ubuntu. Ubuntu disables root as a feature, not as crippleware. 

If you really need root, open up a terminal and fire up

```
sudo nautilus
``` 

You'll be able to change what you want that way.

---

### Post by BoyOfDestiny on 2005-11-18
Or for a gui way to run something as root: Applications -> System Tools -> Run as a different user

---

### Post by Burgundavia on 2005-11-18
Please see
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Corey

---

### Post by matthewv on 2005-11-18
or sudo -s -H will give you a root prompt

---

### Post by Biased turkey on 2005-11-18
[QUOTE=norair]i went through the install, it did not ask me for a root password... how do i get one so i dont have to sudo everything?[/QUOTE]

When you install Ubuntu it asks you to enter a username and a password. Even if it's not clearly indicated, it's your "root"  password too.
For example  if you want to edit a file with root permissions , from your "normal user" session, open a terminal and type "sudo gedit". You'll then be asked to enter your password. Just enter the same password you are using to log as a regular user.
You can now edit ANY text file on your sustem.
But if you just enter "gedit" instead of "sudo gedit" all the files with root permissions will be read only
Another example, type the command "sudo nautilus", enter your password and Nautilus will open diplaying the content of the /root directory.

The Ubuntu wiki has an interesting page about the subject:
[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29") 

Quote:
Ubuntu uses sudo command to allow a normal user administrative privileges. Thus the traditional UNIX root account is disabled (i.e. it is not possible to log in as root).

All the graphical configuration utilities use sudo by default. Thus when Synaptic or something similar asks you for a password, it is asking for your user password, not the root password.

The first user created is part of the admin group, which can use sudo. Any users created after that are not by default. It is recommended that all users of Ubuntu use sudo, as it provides clear benefits to security. 

A little confusing huh !

---

### Post by Kyral on 2005-11-18
Since I haven't seen this in the thread yet, and I feel obligated to do it

[I][B]Be careful with root! Don't login to the GUI with it! It is easy to completely nuke your system as root!! Only do it when needed!!!

[/B][/I]Sorry for beating the horse, but it can't be said enough

---

### Post by vtec on 2005-11-18
I agree with every ones comments here on the hidden dangers of using root. However with that being said I feel it is very import to at least set a password for root. A little bit ago doing something stupid i mess up my log in on my normal account. Luckily i was able to log in as root and fix it.

---

### Post by Biased turkey on 2005-11-18
[QUOTE=Kyral]Since I haven't seen this in the thread yet, and I feel obligated to do it

[I][B]Be careful with root! Don't login to the GUI with it! It is easy to completely nuke your system as root!! Only do it when needed!!!

[/B][/I]Sorry for beating the horse, but it can't be said enough[/QUOTE]

I don't get it, messing a config file in GUI mode with Gedit or in console mode with vim give the same catastrophic results.And removing a directory with Nautilus or removing it with the "sudo rm -r ..." command will  screw-up your system the same way.

---

### Post by Kyral on 2005-11-18
Thats the point. Don't sudo stuff unless you need to. Don't access root unless you need to. In my normal day I only access root to update my system (or restore my firewall when I start up). Running sudo rm -rf / is the nightmare scenario that I envision everytime I see a topic like this. I think Stan Lee put it best

> With great power comes great responsibility

---

### Post by SergeantSunshine on 2005-11-18
You can simply use the UNIX command:

$ su - root

You will be asked for the root password you set.

---

### Post by Chayak on 2005-11-18
I agree, root is a dangerous thing to be logged in as.  One misplaced letter in a command sdb or sda can end up formatting the wrong drive and destroying data... I know because I typed sda out of habit and didn't double check before hitting enter.

---

### Post by patrick295767 on 2005-11-19
How to change your root password (if you forgot it) ?
------------------------------------------------
U can boot ur pc with knoppix or liveCD,
mounting ur partition, (mount ...)

then go into the shadow file of the /etc/
and copying the encrypted password of an user (password known)
or resetting the password of root ...(i guess 0:0 should work, ...I have to check)

Then, u reboot normally ur pc, and once root !
type to redefine ur root password:
passwd

Good luck, please let me know about ur results !!!
('cos I forgot a bit)

Patrick
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)

---

### Post by rlong26 on 2005-11-19
That is the bueaty of Ubuntu, It does not require a root password. The first user account becomes in a sence the root user. There is still a root account, which you can see by going to:
System
Administration
Users and Groups

once there click the checkbox to show all users. You will now see the root account.
sudo allows you to execute a root command with out having to switch back and forth between use accounts during a terminal session.  If you still wish to use the su - command you will need to give root a password other than what is already assigned to it. To do this go to users and groups and edit the root account by highlighting it and clicking properties. Next replace the password that is there with one of your choosing and then try the su - command at the terminal prompt. You should now be root. 
example:
longr@ubuntu8300:~$ su -
Password:
root@ubuntu8300:~#

The pound sign at the end of the new prompt indicates that I am now root.

Beware, young Biased Turkey of the Power of the root-side.  Consume you in errors it will.

---

### Post by Kyral on 2005-11-19
[I] Beware, young Biased Turkey of the Power of the root-side.  Consume you in errors it will.

[/I]ROFLMAO!

---


---
title: "How do I change logon to root?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by tphartl on 2006-08-25
How can I change logon to boot to root every time I power up my laptop? :-k  Right now when it boots up it brings me to a log on screen and then password screen and then into desktop.  This in on a second install.  The first install I was root and didn't have to logon, it just booted up desktop and this install I have to logon all the time.  I am thinking about reinstalling.  Any and all advice welcome.  Thanks.  Tiffany

---

### Post by dca on 2006-08-25
Could've sworn Ubuntu uses 'sudo' versus root for root privileges and actions.  What happens if you leave the name & login data blank when you install using LiveCD?  I only ask because I never tried leaving the field(s) blank when installing...  Not to mention, I've been drinking, just take a look at the avatar/picture!!!

---

### Post by benfindlay on 2006-08-25
You really shouldn't log in as root all the time. For starters you have ABSOLUTE power, so can accidentally delete ANY file, including those really important config files.

Your best bet is to go into System, Admin, then Login Window.

In there, under the security tab, you can enable auto login. To do this, I think you tick the box, then pick your user name from the list. It'll probably prompt you to enter your password to confrim (Sorry for the uncertainty, haven't done this in a while, and am not currently at my ubuntu pc) ;)

As for running as root, its much safer to run the necessary commands using sudo * (or gksudo * where appropriate) at the terminal (* being the command in question, e.g. gedit)

Trust me, your computer is MUCH safer this way!

Hope this helps!

---

### Post by b_martinez on 2006-08-25
Okay. My advice is to NOT log on in root mode.Security issues being the primary reason. Secondary is to keep you from breaking your system. There is a way to do an automatic log-in, but I'm not well versed in Ubuntu. In Ubuntu , go to SYSTEM>ADMINISTRATION>LOGIN WINDOW and find the automatic login ection and click the check-box. This allows auto login for whichever user you specify.
hth
Bill

---

### Post by tphartl on 2006-08-25
> **dca said:**
> Could've sworn Ubuntu uses 'sudo' versus root for root privileges and actions.  What happens if you leave the name & login data blank when you install using LiveCD?  I only ask because I never tried leaving the field(s) blank when installing...  Not to mention, I've been drinking, just take a look at the avatar/picture!!!

It won't let you move past that part of the install until all the 'blanks' are filled in.

---

### Post by uberg on 2006-08-25
i don't think you really want to log in as root.  Right?  You just want to have it log you automatically into your user account when you boot up your computer?

---

### Post by tphartl on 2006-08-25
> **b_martinez said:**
> Okay. My advice is to NOT log on in root mode.Security issues being the primary reason. Secondary is to keep you from breaking your system. There is a way to do an automatic log-in, but I'm not well versed in Ubuntu. In Ubuntu , go to SYSTEM>ADMINISTRATION>LOGIN WINDOW and find the automatic login ection and click the check-box. This allows auto login for whichever user you specify.
hth
Bill

Okay, Bill.  I just did that.  I will have to restart to see if it worked.  Thanks.  Tiffany

---

### Post by tphartl on 2006-08-25
> **uberg said:**
> i don't think you really want to log in as root.  Right?  You just want to have it log you automatically into your user account when you boot up your computer?

Right and I also want to be able to install the programs such as Java and Flash without all the errors of not having access rights.  Tiffany

---

### Post by tphartl on 2006-08-25
> **benfindlay said:**
> You really shouldn't log in as root all the time. For strters you have ABSOLUTE power, so can accidentally delete ANY file, including those really important config files.

Your best bet is to go into System, Admin, then Login Window.

In there, under the security tab, you can enable auto login. To do this, I think you tick the box, then pick your user name from the list. It'll probably prompt you to enter your password to confrim (Sorry for the uncertainty, haven't done this in a while, and am not currently at my ubuntu pc) ;)

As for running as root, its much safer to run the necessary commands using sudo * (or gksudo * where appropriate) at the terminal (* being the command in question, e.g. gedit)

Trust me, your computer is MUCH safer this way!

Hope this helps!

Everytime I try to use sudo and such it tells me that I don't have permission or access.  That is why I was thinking about a reinstall.  Tiffany

---

### Post by benfindlay on 2006-08-25
sudo should work fine. In case you don't know, it's short for **S**uper **U**ser **DO**. It is, for all intents and purposes the exact same thing as **SU**(root)

You can make it so you're permanently in sudo for a session by typing```
sudo -s
``` I believe, anyway (can anyone else verify this please?)

If sudo isn't working for you, I'd suggest a reinstall if it's a fairly fresh system. Sounds like something has gone wrong during the initial setup

---

### Post by nickpaton on 2006-08-25
> **benfindlay said:**
> 
You can make it so you're permanently in sudo for a session by typing```
sudo -s
``` I believe, anyway (can anyone else verify this please?)


The command above and the one below are the same and log you in as root:

```
sudo su
```

Exiting the Terminal will cancel the Root level

---

### Post by aysiu on 2006-08-25
> **tphartl said:**
> How can I change logon to boot to root every time I power up my laptop? :-k  Right now when it boots up it brings me to a log on screen and then password screen and then into desktop.  This in on a second install.  The first install I was root and didn't have to logon, it just booted up desktop and this install I have to logon all the time.  I am thinking about reinstalling.  Any and all advice welcome.  Thanks.  Tiffany Did someone set up your first install for you? No default Ubuntu installation would automatically log you in as root.

There seem to be two separate issues here:

**1. Automatically logging in**
Automatically logging in can be set up quite easily by going to System > Administration > Login Window > Security > Enable Automatic Login

**2. The perception that you're logging in as root**
As I said before, there's no way that a default Ubuntu installation would ever log you in as root. Not only is the root account disabled from logging in, it's additionally disabled from logging in graphically.

It's possible you may have thought you were root because you could make changes by entering your password and temporarily gaining root privileges (this behavior, by the way, *is* the default). And if you're not able to do so (for example, if you go to System > Administration > Login Window, and it doesn't accept your password, please state that's the case, and we'll help you figure out why this isn't working for you.

For more on the difference between *sudo* (what Ubuntu does use) and root (what Ubuntu does not use), read this page:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by TFX360 on 2006-08-25
I use sudo -i (does sudo -s work too?) when necessary. I also have an icon of gnome-terminal starting with gksu gnome-terminal so I can do root things inside the terminal.

Kind regards,


TFX

---

### Post by ajgreeny on 2006-08-25
By default sudo only works for the first user on a machine.  If you are that user and sudo will not work, then something has gone wrong.  If you get an error message saying *conversation with su failed*, then you can put it right easily enough by adding your user name to the /etc/sudoers file by ensuring the following line is in the file:-
username   ALL=(ALL) ALL
You may have to do this using visudo as you presumably can not do anything as root.  If you search this forum you will find a lot of info on this subject.
Good luck, whichever way you go.

---

### Post by aysiu on 2006-08-25
Editing the /etc/sudoers file should be a last resort. Add your user to the *admin* group instead.

For more details, go here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by TFX360 on 2006-08-25
O my god, aysiu I see you *everywhere* :D


**Keep up the good work!**


TFX.

---

### Post by aysiu on 2006-08-25
You, too.

P.S. ```
sudo -s
``` works, too.

---

### Post by TFX360 on 2006-08-25
> **aysiu said:**
> You, too.

P.S. ```
sudo -s
``` works, too.

Hehehe sure will! :D


I checked that in the man pages. To completly different entries though... of course both mentioning the shell.


Kind regards,


TFX

---

### Post by kkimes on 2007-04-26
None of the suggestions work for we.  No mater what I try, I always get the message "sudo: pam_authenticate: Conversation error" and it goes right back to my prompt.

I know this is an old thread, but maybe someone is still watching it.  Any help appreciated.  I am in the same group as 'root', so I don't think that that is the problem.

Kit Kimes
Oswego, IL USA

---


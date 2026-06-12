---
title: "Root Password!"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by mvulaomi on 2006-04-08
Dear Friends,

I am new to Linux and to Ubuntu. I managed to acquire a CD (of Version 5.10) that I installed on one of our computers in our Computer Lab for the sole purpose of trying Ubuntu out and to learn more about this OS. I was so bold as to wipe out whatever was on that hard drive. Right now the machine is up and running. I have been trying out the different programmes there. They seem to work well so far.

Now here is the problem: when I try to check anything under system > administration I come up with the problem of the root password. As far as I recall, I was never prompted for the root password during the installation process. It looks like I cannot acquire the root password. This also mean that I cannot make other users for the computer. Any ideas how I can get the root password at this time? Or do I just need to re-install it all over again?

Any help will be appreciated!

Mvula

---

### Post by taurus on 2006-04-08
It was disable as default.  If you need root, use sudo instead!  Otherwise, you can assign a password to root if you REALLY want to
```

sudo passwd root

```

---

### Post by YuHoo on 2006-04-08
Unlike XP and 2000 and other operating systems that have root accounts and user accounts, Ubuntu just has sudo (super user do). The password you use to log into your account is this root password. If you want to manipulate anything beyond your user privileges (which is quite limited) you'll need to input this password. It keeps you more secure and it will become second nature to just input it.

---

### Post by 5-HT on 2006-04-08
The root account is locked by default in Ubuntu for security reasons.
Ubuntu uses 'sudo' to allow escalation to root privileges.
When something is asking for a password, it is asking for your user password.

Here is a link that describes the matter: [Ubuntu Wiki Root-Sudo]("https://wiki.ubuntu.com/RootSudo")

HTH.

---

### Post by OBnascar on 2006-04-08
5-HT pushed his button before I did, same answer !

---

### Post by mvulaomi on 2006-04-08
Thank you for the explanation. I have tried the password for the user and it is working fine. 

Mvula

---

### Post by mvulaomi on 2006-04-08
[QUOTE=taurus]It was disable as default.  If you need root, use sudo instead!  Otherwise, you can assign a password to root if you REALLY want to
```

sudo passwd root

```[/QUOTE]

When trying this I failed to get through. I only got a "Sorry Try Agian" response. What do I do, since I really want to have access to the root password so that I can create a new user for the computer.

Mvula

---

### Post by take_one on 2006-04-08
Try this:

sudo -s //it will go to root without asking password, then set password for root by typing
passwd //just follow the instruction

cherio,
take_one

---

### Post by mvulaomi on 2006-04-09
[QUOTE=take_one]Try this:

sudo -s //it will go to root without asking password, then set password for root by typing
passwd //just follow the instruction

cherio,
take_one[/QUOTE]

I tried this. It did not work either!

Mvula

---

### Post by mcduck on 2006-04-09
[QUOTE=mvulaomi]When trying this I failed to get through. I only got a "Sorry Try Agian" response. What do I do, since I really want to have access to the root password so that I can create a new user for the computer.

Mvula[/QUOTE]You don't need to set root password to do that. You can create new users in System/Administration/Users and Groups, or if you want to use command line, just add 'sudo' before every command that needs root privileges :)

---

### Post by mvulaomi on 2006-04-09
Dear All,

Thank you very much for the reponse that where written here. They really helped. I had the other users set up and they are running well. The root password was also set up for the sake of trying it out. I will revert back to the default setup soon after I try out the use of root password.

I was thrilled by the quickness of the response and how the forums runs in trying to help us who are new to Ubuntu!

Thank you once again!

Mvula

---

### Post by Kuraboy on 2006-04-09
Hi.

I am new here...

I have a question regarding the root thing...

I am trying to instal subeclipse in eclipse... but it give me an error while trying to create a feature file... it means that I am not logged in as a root right?!

and I had the same problem while updating Azureus... it give me "permission denied" ... how can I type sudo and run these programs?! or can't I... must I log in as a root?!

thnx in advacne...

---

### Post by Mustard on 2006-04-09
[QUOTE=Kuraboy]Hi.

I am new here...

I have a question regarding the root thing...

I am trying to instal subeclipse in eclipse... but it give me an error while trying to create a feature file... it means that I am not logged in as a root right?!

and I had the same problem while updating Azureus... it give me "permission denied" ... how can I type sudo and run these programs?! or can't I... must I log in as a root?!

thnx in advacne...[/QUOTE]

You may get an answer in this thread, but I would suggest you start a  new thread that specifically deals with your issue, so that its not lost in this thread and overlooked.

---


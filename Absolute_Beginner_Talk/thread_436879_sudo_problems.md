---
title: "sudo problems"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by uputer on 2007-05-08
Okay, I have some questions but I have some major complaints about Ubuntu as well.   I want to make clear that I think my objections are valid and no matter what some people will say or criticize me about my complaints, I won't waiver.  

I cannot for the life of me figure out why Ubuntu uses this sudo system.   Linux is already secure and people are always 'breaking their system' by installing stuff.   Thus, re-installs are often necessary if you aren't careful and install a lot of software.   So, why then use sudo?

I had to use a live CD (Ubuntu) recently and had trouble with sudo.   Why does Ubuntu require you to type out 'sudo' all the time instead of su?   Debian only requires su and so do others.   I was then asked for a password?  What is the password?  I thought it was 'root' but I don't remember it working.   

How do you change the system so that you can go back to just using 'su' and the password (root)?   Can you?

Anyway, that is my pet peeve, I guess.

---

### Post by benfindlay on 2007-05-08
The root account is disabled by default, but you can acticate it easily by going into the users settings (in System>>Administration>>Users and Groups I think) and setting a password.

The reason it is disabled is that blanket root access to a system makes it far more easier to damage something by mistake. Even in windows, admin access will still prevent you from deleting certain files. In linux, root access gives you total power. There is also a command that you can type so that the shell you are using remembers that you are in sudo mode automatically, and will sudo everything for you until you exit the terminal session.

Needless to say, there is a long list of other reasons as to why ubuntu uses sudo, not su, but a quick search on google or these forums will no doubt find these for you.

---

### Post by PriceChild on 2007-05-08
[uwiki]RootSudo[/uwiki] for the entire reasoning. You can still reactivate su if you really want but its really not advised :)

pricey

---

### Post by rysh on 2007-05-08
You can try use "sudo -i" 
Then you have a root shell

You do not always have to use a password when doing some stuff which requires root privileges. When using sudo commands with just short intervals, the passsword prompt doesn't appear. 

you can also use "sudo passwd" to give re-enable root again. 

Hope this helps you.

---

### Post by zvacet on 2007-05-08
I can not belive that just two letters make you so mad.Password is one you used during installation.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by starcraft.man on 2007-05-08
> **uputer said:**
> Okay, I have some questions but I have some major complaints about Ubuntu as well.   I want to make clear that I think my objections are valid and no matter what some people will say or criticize me about my complaints, I won't waiver.  

I cannot for the life of me figure out why Ubuntu uses this sudo system.   Linux is already secure and people are always 'breaking their system' by installing stuff.   Thus, re-installs are often necessary if you aren't careful and install a lot of software.   So, why then use sudo?

I had to use a live CD (Ubuntu) recently and had trouble with sudo.   Why does Ubuntu require you to type out 'sudo' all the time instead of su?   Debian only requires su and so do others.   I was then asked for a password?  What is the password?  I thought it was 'root' but I don't remember it working.   

How do you change the system so that you can go back to just using 'su' and the password (root)?   Can you?

Anyway, that is my pet peeve, I guess.

1) Why use sudo? Sudo is used so that a user with limited account privledges (i.e. average user with no access to kernel or system settings) can be elevated to administrator access for a single task (i.e. install single program) and then be downgraded again and continue to operate as a limited user WITHOUT having to logout and log back in with administrator account to do so (like in XP and previous windows). Linux is secure, because the default user is limited and NOT administrator like all windows prior to vista (also in part due to the modular design).

2) I don't even get this complaint... whats two letters when your timing many command lines and installing/configuring things. If you really don't wanna type sudo, copy it to clipboard and ctrl + V it.

3) The password for sudo, is whatever password you used to log in, its the same one you set at install. The only reason it wouldn't be this, is if you manually changed it via gui or terminal.

Honestly, your complaints seem kinda frivolous.

---

### Post by Najand on 2007-05-08
Well, "sudo" is not an ubuntu thing. It is included in almost all major distributions. If you hate it just enable "su" and you won't have further problems... Also noone is going to criticize you for your opinion... You have yours and it is respectful.

---

### Post by Memory.Dump on 2007-05-08
I'm not to sure about the whole Sudo thing, but I just went to users and groups and made sure to set a pw I know for root and su command works fine for me, I am sure there are very valid reasons for using Sudo over su but su is what I'm used to and it works for me....

just saying you don't neccisarily need sudo you can just do su

---

### Post by sandman55 on 2007-05-08
I know this is not exactly what you want but if you go Alt + F2 then type in gksudo nautilus you can go through your files like you do in windows and still be in root

---

### Post by houstonbofh on 2007-05-08
I never understood the frustration with sudo.  Especially when it is so simple to work around.
sudo -i
sudo xterm
sudo nautilus

Are these thing really so hard?

---

### Post by Cypher on 2007-05-08
I think we all acknowledge that Ubuntu is the first distro to disable the Root access and make you use SUDO before performing any system activity. But as others have stated, Ubuntu doesn't prevent you from becoming root to perform some lengthy system task. At the same time, SUDO will ask for your password only for the first command, all consecutive commands with a given timespan are performed without asking for the password again.

As a long term Linux user, and with the large influx of people to Linux, I think Ubuntu's decision of using SUDO is a very wise one. It is a constant reminder that what you are doing is a system-level task that could completely break your system. You're bound to be a little more careful when you see that command.

Most other distros resort to just changing the prompt from "$" to "#" indicating that you're Root when you "su". You don't get any other indication and I can't even tell you how many times I've done "rm -rf" without paying close attention.

---

### Post by uputer on 2007-05-08
> **starcraft.man said:**
> 1) Why use sudo? Sudo is used so that a user with limited account privledges (i.e. average user with no access to kernel or system settings) can be elevated to administrator access for a single task (i.e. install single program) and then be downgraded again and continue to operate as a limited user WITHOUT having to logout and log back in with administrator account to do so (like in XP and previous windows). Linux is secure, because the default user is limited and NOT administrator like all windows prior to vista (also in part due to the modular design).

2) I don't even get this complaint... whats two letters when your timing many command lines and installing/configuring things. If you really don't wanna type sudo, copy it to clipboard and ctrl + V it.

3) The password for sudo, is whatever password you used to log in, its the same one you set at install. The only reason it wouldn't be this, is if you manually changed it via gui or terminal.

Honestly, your complaints seem kinda frivolous.
Here's what happened.   I was getting assistance with a computer that needed some partitioning so I used gparted.   But, we were using a live CD with Ubuntu on it.   My helper uses Debian not Ubuntu and is experienced with Linux.   I consider myself a newbie although I've learned a little already.   Anyway, my Linux guru doesn't seem to like the "sudo way" and I could see the perspective.   If you're using command lines, you need to know what you're doing or you can break the system.   So, why use sudo?  Su has been used in Unix forever, right?   In a way, sudo seems to be an insult to linux users as if they need help to avoid screwing up their system.   But, it seems to cause more trouble.   I'm only going by the other perspective.   I guess if I have to do it myself, I would want to understand what you guys are saying and how it works.   

Memory.Dump, houstonbofh, rysh, and/or anybody else, I am interested in the methods you can use to work around sudo.  

Can you clarify things?     I guess sudo -i allows one to be root for the duration of a session in which a terminal window pops up and you're root throughout?   I want to know about the methods that allow using the (traditional?) su system?

p.s.   I plan on using Ubuntu still but I will have Ubuntu and Debian partitions with one Windoze XP.    (Can anyone recommend Feisty Fawn as I think I'd want that one.   I'll probably have an Intel-chipset-based computer with the dreaded JMicron controller chip included.)

---

### Post by sandman55 on 2007-05-08
> **sandman55 said:**
> I know this is not exactly what you want but if you go Alt + F2 then type in gksudo nautilus you can go through your files like you do in windows and still be in root

Did you try the above method? You can make changes without going into terminal.

---

### Post by houstonbofh on 2007-05-09
sudo -i is "Super User Do, interactive."  Effectively it is the same as su.  You are root until you exit.  You use your account password, and there is still no root password.

sudo xterm launches an xterm (old style Xwindow with a terminal so you can easily tell the difference) as root.  When you exit, the windows closes.

sudo nautilus runs the file manager as root.  You will notice your home folder is root.  This is the only clue that you are in a root file manager.  There is some risk here, but you can work quickly, with a lot of versatility.

---


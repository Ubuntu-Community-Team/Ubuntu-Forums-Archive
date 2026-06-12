---
title: "Tired of password prompts"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by hill0795 on 2007-11-01
I don't know if my question has anything to do with keyring manager (I'm a newby to the unix OS) but here goes.  Basically I'm tired of entering passwords to open documents, start applications, and initially logging onto my computer upon startup.  The computer I have Ubuntu 7.10 installed on is for home use and no one really uses it but my wife and I.  Is there any way I can configure Ubuntu to either remember the admin password or just not even ask for it every time I do something?  Another issue I'm having is that whenever I perform a search, nothing is ever found when I use the GUI interface and I think it might have some correlation to permissions because I'm not root.  The only way I can perform a successful search is if I open a terminal, become root using su, and using find . -name "blah",    Is there any way I can be root at all times and not have to login into my username upon startup?  I guess what it boils down to is that I just want to have administrative permissions at all times since this is strictly a home computer.  Thanks for your time.

---

### Post by Cable on 2007-11-01
It's really not recommended to enable or use the root account.  It opens up your computer to lots of insecurities.  Sudo protects your important system files from the outside world.  Read [this]("https://help.ubuntu.com/community/RootSudo").  It talks about sudo and enabling the root account.

---

### Post by steve.horsley on 2007-11-01
You should not have to enter password to open documents or to launch applications. If you do, there is something wrong. You should of course store all your documents under /home/your-user-name as this is your area, similar to My Documents on windows. If you have to use  a password to launch applications, let us know what the application is and we'll try to figure out what's wrong.

System administration is not a thing that you should be doing very often (I know you do a lot when its a new install, but that settles down with time), and I advise you to live with having to enter a password before doing sysadmin work. You can ease the task by remembering that you can get root priviledge for as long as you want with either **sudo -i** for a terminal, or **gksudo nautilus** for a file explorer.

As far as I can tell, the gui search utility is hopelessly broken, and has been so for years. For text searches, **locate** is quicker than **find** but it relies on a database that is only updated once per day so won't find very new files.

---

### Post by aysiu on 2007-11-01
You can enable an automatic login if you go to System > Administration > Login Window

That saves you one password entrance.

You shouldn't have to enter a password to open documents. What documents are you opening? Ones outside your /home directory? That seems wrong.

---

### Post by anaconda on 2007-11-01
OR if you reaaly want you can enable the root user. It's your machine, and you do that on your own risk, and the risk isn't even THAT big.

Just give root a password with (in terminal)
sudo passwd

and then you need to enable graphical root login somewhere from: 
System>administration>Login window

Then just make root to autologin, and you wont ever be asked for a password again..

---

### Post by twiceasworn on 2007-11-01
Alright I will put in my two cents on this issue.  I deal with machines that have root access all day long.  Now, most people would think that I would hate sudo because I am so used to just being at a root prompt, but I actually think sudo is a great asset to the linux desktop.  The reasoning is simple, if you arent a guru and you don't work with linux at the command line every day then you are probably going to totally screw something up with root access.  Sure, at first it seems like the risk is very small but just wait until you fat finger a command or use a command with the slightly wrong syntax and you bork your system, you will wish that you had something saving you from yourself.

---

### Post by bodhi.zazen on 2007-11-01
You can also configure sudo so that no password is needed.

IMO the "best" solution is to use :```
sudo -i
```

That preserves security in that a password is required, but then you have a root terminal so away you go.

Yse gksu for graphical applications, like nautilus :

```
gksu nautilus
```

To configure sudo, see this link : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---


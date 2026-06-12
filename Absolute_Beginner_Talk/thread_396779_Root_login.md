---
title: "Root login?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Senojelyk on 2007-03-29
Hey, im brand new to this linux thing especially ubuntu. I have done some stuff with fedora core at school, im in Net+ right now, and we did some with that, but i got a free copy of this and i cant figure anything out.  I'm trying to ultimately set up a Team Speak server and a web server.  First i need to get my wireless adapter, Linksys wusb54g v1, working right. I downloaded firmware from the site i think anyway and i need to put it into the /usr/lib/hotplug/firmware  folder and in order to do that i need to be on the root account.  How exactly do i get on there? When i used the install disk i created a user account, but how would i go about getting to the root account??

Also if anybody has some site that gives me beginners directions to install the wusb54g it would be greatly appriciated.

-thanks
Kyle Jones

---

### Post by bks on 2007-03-29
use sudo
First type *sudo* {followed by your commands}
It will prompt you for your password and you will be granted root permission for 15 min.

---

### Post by Senojelyk on 2007-03-29
I dont really understand all the commands yet, im brand new to this, is there a way to get on root from the main login page?

---

### Post by danbopes on 2007-03-29
> **bks said:**
> use sudo
First type *sudo* {followed by your commands}
It will prompt you for your password and you will be granted root permission for 15 min.

I use sudo alot, but I noticed when I set the root password, and then use sudo, I need to enter the password of the account im currently on.  Shouldn't sudo ask me for the root password?

---

### Post by danbopes on 2007-03-29
> **Senojelyk said:**
> I dont really understand all the commands yet, im brand new to this, is there a way to get on root from the main login page?

login and type "sudo passwd" enter a root password and then your main login page username/password is root/the password you entered.

---

### Post by martinw89 on 2007-03-29
> **Senojelyk said:**
> I dont really understand all the commands yet, im brand new to this, is there a way to get on root from the main login page?

With Ubuntu, not by default.  But it's generally not a good option (I've seriously messed up everything in the past by doing this and carelessly changing settings.)

More ways to run apps as root user:
[LIST]
[*]You can press ALT+F2 and type "gksudo" before a command to run the application as root
[*]If you type "sudo -i" in a terminal the terminal becomes a root owned terminal
[/LIST]

---

### Post by Maestro23 on 2007-03-29
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Senojelyk on 2007-03-29
> **danbopes said:**
> login and type "sudo passwd" enter a root password and then your main login page username/password is root/the password you entered.

Okay, did that now when i type root/pass  at the login it just goes back to username: 
?

---

### Post by danbopes on 2007-03-29
> **Senojelyk said:**
> Okay, did that now when i type root/pass  at the login it just goes back to username: 
?

Try following his help, im using ubuntu server.  You did indeed change the root password, but you are unable to log into Ubuntu Desktop as default.

---


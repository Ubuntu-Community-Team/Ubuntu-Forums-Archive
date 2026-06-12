---
title: "XChat install"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Gleeed on 2006-03-19
Hi, I downloaded xchat and got an .rpm file on my desktop, I must be really dumb because I cant figure out how do install it, when i doubleclick it it says "could not open" something...?

---

### Post by dermotti on 2006-03-19
Don't install it from RPM. Enable UNIVERSE respositories in synaptic and install it within synaptic. 

delete that rpm.

If you need more help let me know.

---

### Post by mcduck on 2006-03-19
Enabling extra repositories: [http://www.psychocats.net/ubuntu/sources.php]("http://www.psychocats.net/ubuntu/sources.php")

Installing software in Ubuntu: [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

Sources.list generator: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by Madpilot on 2006-03-19
If you're using Ubuntu 5.10 (Breezy Badger), XChat is already installed. 

**Applications -> Internet -> XChat IRC**

If you're already running Dapper, you'll need to install it from Universe, though, as dermotti said.

General Installation advice for Ubuntu: 
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Gleeed on 2006-03-19
Oh many answers here, thanks =) gonna read them, and yea I'm using dapper...

EDIT: What should I choose? Hoary (5.04) or Breezy (5.10) ?

---

### Post by d-x on 2006-03-19
I only installed ubuntu last friday and I'd recommend Breezy to anyone but thats just me.

---

### Post by Gleeed on 2006-03-19
no i mean here: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

What should I choose? I use dapper...

---

### Post by mcduck on 2006-03-19
[QUOTE=Gleeed]no i mean here: [http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

What should I choose? I use dapper...[/QUOTE]With dapper, neither one. You should have 'dapper' where there's 'breezy' in the guide.. In simple way, all you need to do is remove the '#' from the lines with 'universe' and 'multiverse' repositories..

I wasn't expecting you to run Dapper, since this is the Beginner forum and Dapper is still in development stage.. :)

---

### Post by Gleeed on 2006-03-19
[QUOTE=mcduck]With dapper, neither one. You should have 'dapper' where there's 'breezy' in the guide.. In simple way, all you need to do is remove the '#' from the lines with 'universe' and 'multiverse' repositories..

I wasn't expecting you to run Dapper, since this is the Beginner forum and Dapper is still in development stage.. :)[/QUOTE]

Now I dont understand there are no "#" on the lines with "universe" and "multiverse"?

yeah I use dapper and I'm a beginner :p something wrong with that? hehe

please add my msn and talk to me there : [email]glennedler@gmail.com[/email]

---

### Post by mcduck on 2006-03-19
So there's no repository lines with # in front? Than you should be fine now. If some lines have 'breezy' or 'hoary' in them, change that to 'dapper'.

Now open terminal, it's in Applications/Accessories, write 'sudo apt-get update', press enter and enter your password. Now apt-get will check what apps you have installed and what's available in repositories. 

When that's done, run 'sudo apt-get install xchat' to install Xchat. 

If you don't want to use the terminal, you can do the same with Synaptic Package Manager (In System/Administration). First click 'Reload', this does the same thing that command 'apt-get update' does. After that click 'Search', and search for xchat. Now right-click the 'xchat' package and select 'Mark For Installation'. Then click 'Apply' and xchat will be installed.

---

### Post by Gleeed on 2006-03-19
Oh it worked =) thanks very much ::)

---

### Post by mcduck on 2006-03-19
[QUOTE=Gleeed]Oh it worked =) thanks very much ::)[/QUOTE]
no problem :)

---

### Post by Sabour on 2006-04-24
how install & compile xchat 2.6.2 source from author site ( [http://www.xchat.org/files/source/2.6/xchat-2.6.2.tar.bz2](http://www.xchat.org/files/source/2.6/xchat-2.6.2.tar.bz2) ) ?

---


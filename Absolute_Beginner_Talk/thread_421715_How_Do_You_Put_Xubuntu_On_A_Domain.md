---
title: "How Do You Put Xubuntu On A Domain?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2007-04-24
I'm trying to put Xubuntu on the domain at work so I can access, well, anything. How would I go about doing that?

---

### Post by gbold on 2007-04-24
Probably can't since you'd have to be one of the Domain Adminstrators (I think) to add it to the domain...  Most companies don't let their employees do things like that...  Ask your IT person.
Greg

---

### Post by Minker17 on 2007-04-24
> **gbold said:**
> Probably can't since you'd have to be one of the Domain Adminstrators (I think) to add it to the domain...  Most companies don't let their employees do things like that...  Ask you IT person.
Greg

I am an admin.

---

### Post by Minker17 on 2007-04-24
No one?

---

### Post by johnny4north on 2007-04-24
windows server 2000 or linux domain.  here is a link for linux samba how to- [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

---

### Post by Minker17 on 2007-04-24
Is that for making it a server or joining it to an existing domain?

---

### Post by johnny4north on 2007-04-24
making a ubuntu domain controler[samba] for windows.  miss read your 1st question.  i think you know alot more about this matter then i.  some one will come alone soon.  very busy fourm.  sorry..

---

### Post by Minker17 on 2007-04-24
Help?

---

### Post by Minker17 on 2007-04-24
Should this go in networking?

---

### Post by aysiu on 2007-04-24
I used a Knoppix CD to access my work domain in Konqueror, and it worked just fine:
smb:/*DOMAIN-NAME\username*@*000.000.000.000*

Substitute in your domain name for *DOMAIN-NAME*, your username for *username*, and your IP address for *000.000.000.000*.

---

### Post by Minker17 on 2007-04-24
SO I need to get a CD in able to do this?

---

### Post by aysiu on 2007-04-24
> **Minker17 said:**
> SO I need to get a CD in able to do this?
No, you need Samba or SMB (is there a difference?). Not sure the exact package you want, but I'm not sure if Thunar supports this (I've done smb:// successfully through Nautilus and Konqueror).

---

### Post by Minker17 on 2007-04-24
But how can I accomplish this without internet access?

---

### Post by aysiu on 2007-04-24
> **Minker17 said:**
> But how can I accomplish this without internet access?
Well, if you don't have internet access, how would you get on the domain?

---

### Post by Minker17 on 2007-04-24
What I mean to say is. I have a network cable plugged in, however, I can't get out to the net to do anything until I get on the domain.

---

### Post by aysiu on 2007-04-24
Not sure I can help you. There are a bunch of *smb*-related packages, but they all require an internet connection.

---

### Post by Minker17 on 2007-04-24
Anyone?

---

### Post by Minker17 on 2007-04-25
Bump?

---

### Post by aysiu on 2007-04-25
I haven't tried this yet (as I said before, I've been able to successfully use *smb* in Nautilus and Konqueror, but not Thunar, but apparently [Xubuntu does come with a command-line tool called *smbclient*](http://packages.ubuntu.com/feisty/net/smbclient).

According to [this page](http://yolinux.com/TUTORIALS/LinuxTutorialMicrosoftWindowsNetworkIntegration.html), you can join a Windows domain with a command like this: > Use Samba shell: (non-root user)
```
smbclient //MS-SERVER-NAME/MS-Windows-Share -U MS-WINDOWS-DOMAIN/ms-windows-login-name
Password:
```
This places you in a shell mounted to the MS/Windows server. You can enter commands such as ls, put and get like in an ftp client. Type ? for a full list of commands. And according to [this page](http://www.windowsitpro.com/Articles/ArticleID/8897/8897.html), you can do it with something like this: > in larger environments, you'll need to pass the domain name on the command line.. for an account "fred" in Windows Domain "sanford", the syntax would be

```
smbclient -L //BigServe -U sanford/fred
```

note the direction of the slash after "-U"..  If you are able to install software later, you might want to look into installing a GUI frontend like *smb4k*

---

### Post by aysiu on 2007-05-02
Try this:
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

I used something like that today at work, and it worked!

```
sudo apt-get update
sudo apt-get install smbfs
sudo mkdir /media/windowsdomain
sudo mount -t smbfs //100.200.40.30/sharename /media/windowsdomain -o username=minker
```

---

### Post by wog on 2007-05-05
> **aysiu said:**
> Try this:
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

I used something like that today at work, and it worked!

```
sudo apt-get update
sudo apt-get install smbfs
sudo mkdir /media/windowsdomain
sudo mount -t smbfs //100.200.40.30/sharename /media/windowsdomain -o username=minker
```

I'm assuming "windowsdomain" is whatever the network name is, and the IP address is whatever IP address the machine is within the network?

And does specifying the username in the above mount line also mean the username has to be created on the windows machine as a user?

---

### Post by aysiu on 2007-05-05
Yes, that's all correct, and the username should exist on the Windows machine.

---

### Post by wog on 2007-05-05
Can the username be the same as the main username on the windows machine, or does it have to be a different one?

---

### Post by aysiu on 2007-05-05
It can be the same.

---


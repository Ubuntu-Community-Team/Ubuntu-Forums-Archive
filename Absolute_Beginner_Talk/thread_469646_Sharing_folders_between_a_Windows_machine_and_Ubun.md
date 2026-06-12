---
title: "Sharing folders between a Windows machine and Ubuntu laptop"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by srt5 on 2007-06-10
I have one PC which is running Windows XP Pro SP2, and I run Ubuntu (Feisty) on my laptop, both access the internet via a wireless router. I want to know if it is possible to access shared folders on the windows machine from Ubuntu, and how I might go about this? Please excuse my ignorance but I have very little networking experience (both in Windows and Ubuntu). I know that Windows uses the \\WORK_GROUP\COMPUTER_NAME notation. I suspect that this is not the case for Linux. Do i need to use some special options with the mount command?

Thanks a lot :)

---

### Post by ggaaron on 2007-06-10
Samba - this is what you need.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Somewhere there is about sharing files.
And actually \\ip works.

---

### Post by Kobalt on 2007-06-10
Just set your shared folder in Windows and access it from Places > Connect to a server. Select Windows share in the service type and fill in the fields.

---

### Post by srt5 on 2007-06-10
thanks for the quick responses :) I have set up my shared folder in Windows, but when I goto Places > Connect to Server and enter the IP it mounts fine, but when I open the network folder it doesn't display any files. Could this be that my shared folder doesn't have the correct permissions? Also when I browse the network computers, it doesn't seem to find my Windows machine 

Any suggestions?

Edit: When browsing the network computers I am able to see the domains but when I double click to view the computers in the windows domain, it says I can't access the folder.

---

### Post by srt5 on 2007-06-10
ahh okay, now the XP machine is seeing my Ubuntu laptop, but everytime i try to double click on it (from Windows) it asks me for a username and password - i've tried entering my user and password (which i use to log in on Ubuntu) but it isn't accepted - anyone know how i can get around this?

---

### Post by Austin_KW on 2007-06-10
> **srt5 said:**
> ahh okay, now the XP machine is seeing my Ubuntu laptop, but everytime i try to double click on it (from Windows) it asks me for a username and password - i've tried entering my user and password (which i use to log in on Ubuntu) but it isn't accepted - anyone know how i can get around this?

You need to add a samba password for one of your users, and use this username/sambaPassword to access the files;

sudo smbpasswd -a *yourUserName*
Password: *yourSudoPassword*
New SMB password: *yourSambaPassword*

---

### Post by srt5 on 2007-06-10
> sudo smbpasswd -a *yourUserName*
Password: *yourSudoPassword*
New SMB password: *yourSambaPassword*


great! it worked, thank you very much - i can access shared folders on my ubuntu laptop from my XP machine, now all i need is to be able to access shared folders on my XP machine from my laptop

still no joy with this unfortunately ](*,)

---

### Post by Austin_KW on 2007-06-10
> **srt5 said:**
> great! it worked, thank you very much - i can access shared folders on my ubuntu laptop from my XP machine, now all i need is to be able to access shared folders on my XP machine from my laptop

still no joy with this unfortunately ](*,)

That should  have worked, without any setup. Menu places ->network

Check you firewall settings on the XP machine, you might want to temporarily disable firewalls while debugging it.

---

### Post by srt5 on 2007-06-11
> **Austin_KW said:**
> That should  have worked, without any setup. Menu places ->network

Check you firewall settings on the XP machine, you might want to temporarily disable firewalls while debugging it.

Thank you very much for this advice. It turns out that it was a firewall issue that was preventing me from accessing shared folders on my XP machine. The problem I now have is that my laptop can only access XP's shared folders when the firewall (ZoneAlarm) is turned off completely.

Does anyone know how I should configure ZoneAlarm on an XP machine in order to allow the sharing of folders over a LAN? To be completely honest, I feel very uneasy about leaving the built in Windows Firewall as the only line of defence! I hope this isn't too off topic, I appreciate that this is an Ubuntu forum after all! :)

---

### Post by Austin_KW on 2007-06-11
I don't use zone alarm, but check the zonealarm logs to see what ports it is blocking when you try to access file sharing. Some firewalls allow you to right click on the logentry to create a rule and allow it.

Or temporarily turn up the firewall pop-ups alerts to max, And allow the incoming connections for filesharing when alerted.

BTW, You are behind a router, so you have incoming protection in a hardware firewall, so you are not exposing the shares to the internet.

---

### Post by srt5 on 2007-06-11
> **Austin_KW said:**
> I don't use zone alarm, but check the zonealarm logs to see what ports it is blocking when you try to access file sharing. Some firewalls allow you to right click on the logentry to create a rule and allow it.

Or temporarily turn up the firewall pop-ups alerts to max, And allow the incoming connections for filesharing when alerted.

BTW, You are behind a router, so you have incoming protection in a hardware firewall, so you are not exposing the shares to the internet.

I shall sleep easier tonight :) thank you very much for all of the assistance, much appreciated. :D

---


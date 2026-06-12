---
title: "[SOLVED] Ubuntu on MS network"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by ellsanto on 2007-10-01
I have somewhat of an odd question. I have an Ubuntu system that I have joined to my network(Server 2000 A/D). This computer is going to be in our breakroom and used for web browsing for employees during their break times. (We recently installed an iPrism web filter and the internet is strictly filtered on their pc's.) 

I want to make sure the Ubuntu computer cannot access our file servers, terminal server, or any shared folders. I believe that I have successfully done this, but if anyone has any tips on how this could be accomplished, that would be great. I want to make sure I have not missed something. 

Most of the staff is not very tech savvy, but I want to make sure we are safe from the outside as well.

I am a Linux noob, but loving it...

---

### Post by jalanbuntu on 2007-10-01
May be you should uninstall any file sharing client on your ubuntu, like the samba client or NFS client, to make sure that your ubuntu cant acces the shared folder

---

### Post by ellsanto on 2007-10-01
Neither samba nor NFS are installed. Does that keep Ubuntu from accessing shared folders or from even viewing them(the folder icon, I mean)?

 Thanks for the reply.

---

### Post by ukripper on 2007-10-01
Setup looks fine to me without SAMBA and NFS. Also make sure SSH is disabled too if it was installed. You might consider a firewall to check any loop holes.

Guardog is pretty good firewall for ubuntu

---

### Post by iposner on 2007-10-01
Providing that you uninstall the samba client (not just the samba server), then they can't connect to windows machines using windows file sharing. However if a windows machine is running an ftp server, or a webserver, they can still connect to those web/ftp sites.

---

### Post by jalanbuntu on 2007-10-01
Yep, I think so. Just try access the shared folder when you dont have any file sharing client installed. Acces the Main Menu > Places > Network. See if something shows up :)

---

### Post by ellsanto on 2007-10-01
Ok, here is where I am...

I am still able to see the MS network. When I try to access the shares, and input my MS username and password I am able to open shared files. How can I verify that SSH, Samba, and NFS are not installed?My initial statement was obviously incorrect. 

Are these file sharing clients installed by default? I do not remember installing any of them.

Thanks for all of the replies.

---

### Post by ukripper on 2007-10-02
File sharing on ubuntu is disabled by default.

i use this utility to monitor daemons and services running on my machines.

Try it to find out what services are running on your box - [http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html](http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html)

---

### Post by ellsanto on 2007-10-03
Because this was my first foray into the linux world, I decided to reinstall FF, thinking that maybe I enabled sharing unintentionally. 

So , upon reinstallation(no services or clients except the default), I joined the ubuntu box to my MS domain and the shared folders/files are in plain sight for all to see and access.
:confused::confused::confused: -sigh-

I really need to block all file sharing. 

Any help from anyone will be awesome and appreciated.

---

### Post by ukripper on 2007-10-03
> **ellsanto said:**
> Because this was my first foray into the linux world, I decided to reinstall FF, thinking that maybe I enabled sharing unintentionally. 

So , upon reinstallation(no services or clients except the default), I joined the ubuntu box to my MS domain and the shared folders/files are in plain sight for all to see and access.
:confused::confused::confused: -sigh-

I really need to block all file sharing. 

Any help from anyone will be awesome and appreciated.

Strange!

Use firewall instead to stop unwanted protocols/ports and apps.

I use Guarddog- [https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/networking.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/networking.html)

---

### Post by louieb on 2007-10-03
Samba is installed by default. Just go to system>admin>Synaptic
search for samba and uninstall it.  NFS is not a problem unless you have other *NIX machines on the network. 
:rolleyes: Don't trust security by ignorance. Add an unprivileged user to login to while the machine is in the break room. Don't want so wise guy installing samba.

---

### Post by ellsanto on 2007-10-03
Thanks Louieb, I had missed a samba service(?) when I uninstalled the others. After that, I could see that I was on an MS network, but that is all. No shares or other clients. Sweet!!! \\:D/\\:D/
I had considered creating a restricted user now I definitely will.  

Thanks everyone else for your help. These have been the quickest (and most informed) responses I have ever received on a forum.

---


---
title: "Linux/Ubuntu beginner - can't install things"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Rdysn5 on 2008-02-28
Hi,
I have just leased a dedicated server, otherwise known as a seedbox. The server has Ubuntu 6.10 installed on it. My only knowledge of linux up to this point was that the mascot is a penguin and that linux is commonly used as a server OS. Not exactly a broad knowledge base, I know :). The obvious question here is why I got a server with ubuntu when I know hardly anything about linux. There are a few reasons. Firstly, on many forums and websites, I have read that linux is better for servers than windows. I mean that is an opinion that many people have expressed. Also, the server I leased has a memory of 256mb (the cheapest I could find). I've read that windows server needs at least 1GB to function effectively. Also the server provider I am using charges extra for windows server.

So, I thought I may as well get one with a linux distribution. I figured it couldn't be *that* hard to use, I would just have to get used to a new operating system. One has to start somewhere. I think I might be in over my head though. I set up a tightvnc server I could access my seedbox with TightVNC viewer. I can log in to the server without any problems. However, beyond that.. I'm a bit stuck. The biggest difference I have noticed in Linux is that there aren't executables like in windows. So I don't know what to do to install things. I downloaded Azureus, the popular P2P program, and that leaves with a folder on my Ubuntu Desktop called Azureus_3.0.4.2_linux.tar.bz2. I right clicked on that and clicked 'Extract here'. That leaves me with a folder on my ubuntu desktop called 'azureus'. Now here is where I am stuck. How do I actually install the program? What do I type?

Also, when I logged in to the server for the first time, the ubuntu Update Manager started. 187 updates were ready to be installed. I allowed all of them to install. Then I noticed at the top of the update manager screen that Ubuntu 7.04 was available to download. So I allowed it to download, but it said the upgrade process couldn't be completed. A few files could not be installed, one was acpi_something, one was ubuntu_desktop. I'm not sure on the others. Does anyone know why it might have failed?

Also, when I type in 'su' into the terminal, it asks for my root password. What root password? The only password I have is the admin password I received from the hosting company. And when I enter that it says authentication failed. Confusing  :confused:

As I am an absolute beginner, I thought this would be the most appropriate place to post this. Any help or advice at all, I appreciate it :).

---

### Post by SOULRiDER on 2008-02-28
You ahve a lot to learn, but dont worry, were here to help :)
First of all, check this out, it explains how software is managed in Ubuntu (and linux distros in general actually). [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

As for root, this explains a bit [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Just ask if you have more questions :)

(also, you should think about other bittorrent clients)

---

### Post by Kannasu on 2008-02-28
Hello Rdysn5 Welcome to Ubuntu!!!

As you seen installing programs are different in Ubuntu then windows.  Normally you want to check Synaptic when installing programs by going to System -> Administration -> Synaptic Package Manager. Or by typing "gksudo synaptic" in  the terminal.

Synaptic has the listing of all the programs available to be install on your system... just mark a check box and hit apply to begin the installation

The root password you were asked for is just your password for the user you made... so if you made the User of "Kannasu" with the password "Ubuntu"  the root password is "Ubuntu" unless of course you changed it.

---

### Post by aysiu on 2008-02-28
> **Kannasu said:**
> 
As you seen installing programs are different in Ubuntu then windows.  Normally you want to check Synaptic when installing programs by going to System -> Administration -> Synaptic Package Manager. Or by typing "sudo synaptic" in  the terminal. More appropriately, it should be ```
gksudo synaptic
``` or ```
gksu synaptic
``` *sudo* is for terminal programs, not graphical programs.

---

### Post by Kannasu on 2008-02-28
> **aysiu said:**
> More appropriately, it should be ```
gksudo synaptic
``` or ```
gksu synaptic
``` *sudo* is for terminal programs, not graphical programs.

Ahhh, my mistake! thanks for that :P

---


---
title: "How do I share an external drive to my windows machines?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-05-22
I'm running Ubuntu 7.04

Right now I can see my windows shared folders and drives from my Linux box no problem, but now that I'm doing all my main computing from the ubuntu machine, I want to plug my external drives into that computer and share them to the windows machines on my workgroup/network.

I began poking around and wandered accross the System>Administration>Shared Folders thing, and when I opened it I get a message that says:

> You need to install at least either Samba or NFS in order to share your folders.

And there is a check box next to SMB and NFS.

From here, what is my safest choice?  I don't want to mess anything up, and I don't want to expose my computer to the world inadvertently.  I also don't want any services running that I don't need.

Should I install both? One or the other? Which one is better?

Thanks, and I probably should have posted this in the network section, but I figured its such a newb question it belongs here.

Thanks,

E

---

### Post by dbott67 on 2007-05-22
For Windows access, you'll want to install samba.

Documentation for samba starts here (these are for 6.10 but should apply for 7.04 without any modification):
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html)

Just follow the instructions on [installation]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html") and [configuration]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html").


-Dave

---

### Post by Martin on 2007-05-22
You certainly won't need NFS to share drives with windows and you robably won't need it for other things. Though it is worth looking into simply out of interest, there's a nice desription of the history etc. on wikipedia.

---

### Post by EAL on 2007-05-22
> **dbott67 said:**
> For Windows access, you'll want to install samba.

Documentation for samba starts here (these are for 6.10 but should apply for 7.04 without any modification):
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html)

Just follow the instructions on [installation]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/installing-samba.html") and [configuration]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html").


-Dave

I have samba installed and can see my unix box from the windows machine, but when I click on it, it prompts for a password, but doesn't accept the login.

I looked through the configuration howto you linked to above, and there's a lot of stuff there, and I don't know what applies to me and what doesn't.  I also can't seem to figure out how to change to super user in the terminal - when I try it doesn't accept my root password.  I also can't open the smb.conf file in anything but read-only so I can't edit it anyway.

---

### Post by Martin on 2007-05-22
Have you right-clicked upon a folder name in Ubunu and shared it?
sudo gedit /etc/samba/smb.conf should get you read/write access to file at root level.
But - you shouldn't need to have to manually edit smb.conf for sharing to work

---

### Post by dbott67 on 2007-05-24
> **EAL said:**
> I have samba installed and can see my unix box from the windows machine, but when I click on it, it prompts for a password, but doesn't accept the login.

You need to make sure that the Windows account (login name) is added to the SMB database.  So, if you login to Windows XP with the username 'jsmith', you would need to create an account in SMB:
```
sudo smbpasswd -a jsmith
```You will be prompted to enter a new password for the user twice.

> **EAL said:**
> I also can't seem to figure out how to change to super user in the terminal - when I try it doesn't accept my root password.  I also can't open the smb.conf file in anything but read-only so I can't edit it anyway.

As Martin notes, you need to preface the command with 'sudo':
```
sudo nano /etc/samba/smb.conf
```Ubuntu does not have a typical 'root' account (it's disabled by default).  System level changes are performed by prefacing the desired command with sudo (or 'gksudo' for GUI programs):
```
gksudo gedit /etc/samba/smb.conf
```
[COLOR=Purple]The password required is *YOUR* user password.[/COLOR]

Note: most applications can be run using sudo, whether they are GUI or not, however, there are some GUI apps that should be run using 'gksudo'.  You can read up on [gksudo vs. sudo here]("http://www.psychocats.net/ubuntu/graphicalsudo").

-Dave

---


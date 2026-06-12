---
title: "EASY remote desktop"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by goatmale on 2006-09-05
I want to connect to my friends computer to do some basic installing for him, how can I do this in the easiest way possible?

---

### Post by btdown on 2006-09-05
Do you absolutely need a remote desktop type GUI? You can pretty much SSH into the machine (once you have openssh installed) and then apt-get install anything you want.

I've found that installing NX (or FreeNX) is the best way to remote in and get things done. Its really fast. Since NX for Linux is free now, there's no point really in installing FreeNX.

---

### Post by steve.horsley on 2006-09-06
I am utterly confused by the NoMachines web site. They seem to have 5 different server products. Is it documented anywhere which ones are free? Is it just "NX Free Edition"? How does that compare with the other 4? Are there prices anywhere?

---

### Post by bluefrog on 2006-09-06
search wiki.ubuntu.com for freenx.

it might be simpler to start from there

James

---

### Post by makeyre on 2006-09-06
There doesn't seem to be any good information on the Ubuntu wiki; the FreeNX page is blank.  There is [https://wiki.ubuntu.com/FreeNxIntegration](https://wiki.ubuntu.com/FreeNxIntegration) but this is just a todo.  Is there a howto somewhere for setting up FreeNX on Ubuntu?

---

### Post by ewl1217 on 2006-09-06
I've given up on FreeNX myself, since it isn't avaliable in the Ubuntu repositories, but I've found that VNC tunneled over SSH works fairly well over my cable connection. I use the combination of VNC and SSH for all my remote access needs.

---

### Post by goatmale on 2006-09-06
i do need a gui. :(

---

### Post by Maxtorm on 2006-09-06
What is wrong with using VNC built into the default install of Ubuntu?  (System -> Preferences -> Remote Desktop)

The only caveat is that you'll have to configure your friend's firewall, if he/she has one, to allow VNC through.  That is port 5900 I believe.

---

### Post by makeyre on 2006-09-07
It's completely insecure.  It's not tunneled over SSH and there's no way to do so through the GUI.  As far as I can tell, your password is being sent in plaintext.  So, either NX, VNC tunneled over SSH, or X11 tunneled over SSH, is the only way to go.

---

### Post by DSn0wMan on 2006-09-07
NX is far superior to VNC. It's faster and more secure. Be sure you have openSSH installed.

To install NX you need 3 things.

NX Server, NX Node, NX Client. The nomachine site has debs available that I can confirm work just fine on Ubuntu dapper.

If I remember you should install the client, then the node, then the server to take care of dependencies.

---

### Post by Maxtorm on 2006-09-07
> **makeyre said:**
> It's completely insecure.

> **DSn0wMan said:**
> NX is far superior to VNC. It's faster and more secure. Be sure you have openSSH installed.

Thanks to you both for the insight.  I didn't realize VNC was so flakey.  It's odd that Ubuntu, which I am so used to being solid from a security point of view, would use a clearly insecure product.  Is there any talk of using FreeNX by default in future versions?

---

### Post by goatmale on 2006-09-07
I don't care about security, all I want to do is install a program and set it up via GUI.

I don't want to configure anything and my friend doesn't either.

---

### Post by Maxtorm on 2006-09-08
In that case, once your friend has allowed remote desktop through System -> Preferences -> Remote Desktop, all you need to do is invoke the viewer:  Applications -> Accessories -> Terminal and then type "vncviewer <his IP address>".  Type "man vncviewer" for usage details.

---

### Post by goatmale on 2006-09-08
I tried that but it didn't work does he have to be off of his computer?

---

### Post by Maxtorm on 2006-09-09
No, he doesn't have to be off his computer.  Does he have a firewall/router?  Have him navigate to [http://www.realvnc.com/cgi-bin/nettest.cgi](http://www.realvnc.com/cgi-bin/nettest.cgi)

If it says Connection to port 5900 failed, it would indicate that port forwarding is not correctly set up.  If you suspect this might be the issue, see: [http://www.realvnc.com/support/portforward.html](http://www.realvnc.com/support/portforward.html)

---

### Post by btdown on 2006-09-09
Ok...I know the NoMachine site is confusing..It took me a while to figure out what I needed to download also. Here is a quick and dirty tutorial to get you working. You need to follow these instructions for the machine you want to connect to (i.e. server).  I have successfully installed this on both Dapper and Edgy, and the filenames below are the latest NoMachine has on their site, as of today, 9/9/06. Those who may be following these instructions in the future, please check the site and see if any newer files are available, and substitute the new files.

Open up a terminal and become root with:
```
sudo su
``` 
Then install this package by typing:
```
apt-get install libstdc++2.10-glibc2.2
``` and if you dont already have it, install:
```
apt-get install openssh-server
``` In order to get NX working, you need to download 3 things:
1. NX client
2. NX Node
3. NX Server (listed on the site as "**[[B]NX Free Edition for Linux**]("http://www.nomachine.com/select-package.php?os=linux&id=1")"[/B]

Ok now we download the .deb packages we're going to install (cut and paste this into your terminal):
```
wget http://64.34.161.181/download/2.0.0/Linux-NoXft/nxclient_2.0.0-98_i386.deb
``` ```
wget http://64.34.161.181/download/2.0.0/Linux/FE/nxserver_2.0.0-76_i386.deb
``` ```
wget http://64.34.161.181/download/2.0.0/Linux/nxnode_2.0.0-100_i386.deb
``` 
Ok now we're ready to install (please use the install order below) by typing:
```
dpkg -i nxclient_2.0.0-98_i386.deb
``` ```
dpkg -i nxserver_2.0.0-76_i386.deb
``` ```
dpkg -i nxnode_2.0.0-100_i386.deb
``` 
Ok we're all installed..type this to exit root:
```
exit
``` 
Everything should have installed without error.
Installing this way uses the default NoMachine ssh keys, so you dont have to worry about creating them/etc. Now you should be able to log into this machine remotely with an NX Client, using your existing username and password.

If you wish to log into this machine from another ubuntu machine, Follow the instructions to download and install only the nxclient (nxclient_2.0.0-98_i386.deb ) above. It will put an entry in your "Applications->Internet" tab in Gnome, which you can select to access the server machine.

The NoMachine site also has a Windows client available there to download, so if you want to log into your machine from windows, you can download it here:
[http://64.34.161.181/download/2.0.0/Windows/nxclient-2.0.0-98.exe](http://64.34.161.181/download/2.0.0/Windows/nxclient-2.0.0-98.exe)

Its easy to set up, and will start a "wizard" when you start the client for the first time.
Make sure you have all your port 22 forwarded correctly, and that when you set up your client connection you have the correct session type (Gnome or KDE) selected, depending on what desktop you have installed, along with "Enable SSL encryption on all traffic" selected.

Good luck!

---


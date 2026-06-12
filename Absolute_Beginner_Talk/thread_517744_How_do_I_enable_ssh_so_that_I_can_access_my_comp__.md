---
title: "How do I enable ssh so that I can access my comp  remotely"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-08-04
I have a new ubuntu comp on my home network (this makes three now):) and i want to be able to see it from the windows PC's using SSH.  I got it working on one of the comps but I forgot what I did.  I currently use winscp to tranfer files between comps but I forgot how to set it up on the ubuntu side.  Any help will be appreccieated.

VC

---

### Post by Aurdal on 2007-08-04
"sudo apt-get install ssh" will install the ssh server.

---

### Post by saadakhtar on 2007-08-04
ok to have remote access in shell you can use just ssh into the system but you will need to install the ssh server module on your ubuntu machine. type:
sudo apt-get install ssh

and the system will install ssh-server module with it.
make sure you know the ip address of your machine. I would prefer a static ip address.
Now goto your windows machine and download a ssh application like [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

simply type in the ubuntu machine's ip address and connect.

if you need more than shell access then i would recommend FreeNX. I have used it and it works perfectly.

---

### Post by videocheez on 2007-08-04
> **saadakhtar said:**
> ok to have remote access in shell you can use just ssh into the system but you will need to install the ssh server module on your ubuntu machine. type:
sudo apt-get install ssh

and the system will install ssh-server module with it.
make sure you know the ip address of your machine. I would prefer a static ip address.
Now goto your windows machine and download a ssh application like [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

simply type in the ubuntu machine's ip address and connect.

if you need more than shell access then i would recommend FreeNX. I have used it and it works perfectly.

Thx guys.  what do you mean more than shell access?

---

### Post by Aurdal on 2007-08-04
I think he means a graphical interface.

---

### Post by saadakhtar on 2007-08-04
FreeNX is a remote desktop program just like RDP in ms windows. You remote login to your computer as if you are sitting right infront of it.

Installation Method:

Edit /etc/apt/sources.list, add the following lines:

deb [http://free.linux.hp.com/~brett/seveas/freenx]("http://free.linux.hp.com/~brett/seveas/freenx") feisty-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx]("http://free.linux.hp.com/~brett/seveas/freenx") feisty-seveas freenx

You don’t need to add the GPG keys for the repository, but it keeps Ubuntu happy.

wget [http://free.linux.hp.com/~brett/seveas/freenx/seveas.gpg](http://free.linux.hp.com/~brett/seveas/freenx/seveas.gpg) -O- | sudo apt-key add -

Now update the apt cache, and install freenx (the server application)

apt-get update
apt-get install freenx

It seems that the freenx package doesn’t run nxsetup like it use to, so run it manually

nxsetup --install

The question of whether to use the NoMachine SSH keys or your own is debatable. My suggestion is to use NoMachine’s initially, until you have tested and got things working, then before going into production, switch to your own keys.

Now you will get lots of scary warnings, at this stage I’m not sure why they are appearing, but I ignored them and everything worked. I’ll figure it out later.

That, believe it or not, is about it. Now just install the nxclient on another machine (you can download the Nx Client from [NoMachine’s website]("http://www.nomachine.com/download.php")).

Once the client is installed, attempt to login to the server. Specify a valid username/password and you’ll have a client session.

---

### Post by bodhi.zazen on 2007-08-04
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

That link is very helpful

You should also see here :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

And consider installing denyhosts (and read the config file)

---

### Post by Aurdal on 2007-08-04
You do realize that there's a remote desktop application included in Ubuntu, right?

---

### Post by bodhi.zazen on 2007-08-05
> **Aurdal said:**
> You do realize that there's a remote desktop application included in Ubuntu, right?

Yes there is ...

tsclient AKA Terminal Service Client

---

### Post by videocheez on 2007-08-05
> **saadakhtar said:**
> FreeNX is a remote desktop program just like RDP in ms windows. You remote login to your computer as if you are sitting right infront of it.

Installation Method:

Edit /etc/apt/sources.list, add the following lines:

deb [http://free.linux.hp.com/~brett/seveas/freenx]("http://free.linux.hp.com/~brett/seveas/freenx") feisty-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx]("http://free.linux.hp.com/~brett/seveas/freenx") feisty-seveas freenx

You don’t need to add the GPG keys for the repository, but it keeps Ubuntu happy.

wget [http://free.linux.hp.com/~brett/seveas/freenx/seveas.gpg](http://free.linux.hp.com/~brett/seveas/freenx/seveas.gpg) -O- | sudo apt-key add -

Now update the apt cache, and install freenx (the server application)

apt-get update
apt-get install freenx

It seems that the freenx package doesn’t run nxsetup like it use to, so run it manually

nxsetup --install

The question of whether to use the NoMachine SSH keys or your own is debatable. My suggestion is to use NoMachine’s initially, until you have tested and got things working, then before going into production, switch to your own keys.

Now you will get lots of scary warnings, at this stage I’m not sure why they are appearing, but I ignored them and everything worked. I’ll figure it out later.

That, believe it or not, is about it. Now just install the nxclient on another machine (you can download the Nx Client from [NoMachine’s website]("http://www.nomachine.com/download.php")).

Once the client is installed, attempt to login to the server. Specify a valid username/password and you’ll have a client session.

Will this be able to work from Windows to Ubuntu? I have been wondering how to get a remote desktop from windows to Linux since I first got Ubuntu way back in June.

---

### Post by saadakhtar on 2007-08-07
yes this will absolutely work with windows. you can download the latest NX Client from the FreeNX website.

---


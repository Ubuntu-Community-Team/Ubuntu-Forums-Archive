---
title: "Setting up a file server with Ubuntu"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by whitea on 2007-07-13
I think I am in the right place here.  ABSOLUTE BEGINNER!

I have my laptop set up as dual boot.  I have also installed Ubuntu on a P3 box and I would like to set up sharing of files, particularly my files that I have on my external hard drive so that I can access them wirelessly on my laptop without having to plug in the external drive.  I want to be able to access the files in both windows and linux from my laptop.  I also think I need the GUI because I may want to use the box for listening to music etc when I am in the basement.

I have set up the necessary files to share in Samba but I am positive that I am not doing it right as I cannot access them on my laptop in either windows or linux.  

Do I need to make the p3 box a server?  If so, how?
How do I create a name for the server so that I can access it?

Any help would be greatly appreciated!

Andrew

---

### Post by zanglang on 2007-07-13
You've got Samba installed properly, right? Make sure you have it enabled in Sytem > Admin > Services first, and then if you have firewalls on the computers, allow port 137-139 and 445.

Once that's done, from Ubuntu you should be able to see the computer or its shares in Places > Network > Windows Network.

---

### Post by whitea on 2007-07-13
I think I have it installed properly.  It is enabled on both machines and I have allowed those ports through the firewall.  Still not showing the computer or it's shares.  Does one need to be a WINS server?

---

### Post by whitea on 2007-07-15
I have access to the computer in my basement through Windows but not Ubuntu.  Could the problem be with my smb.conf file?

I also added gsambad from add/remove applications on the computer in the basement (p3 box).  Can I add it to my laptop as well?  I guess what I am asking is my laptop a client and the p3 a server?

Any help would be greatly appreciated!

---

### Post by whitea on 2007-07-16
I was able to see the p3 box in ubuntu through Smb4k but then had some difficulty with accessing shares related to passwords.  I rebooted the machine and now I cannot see them at all!!

I know I am in way over my head but any help would really be appreciated.  I would love to get this working so that I can access all of my files on my laptop.

---

### Post by louieb on 2007-07-16
Samba is a pain in the as to set up. For Linux to Linux the easiest way is to: 
1st set up the P3 to use a static IP  I set up my static IP through my routers configuration program. (linksys) you may be able to do it that way  or though  the network manager.
2nd  on the P3 install the ssh server package.
```
sudo aptitude install openssh-server
```after The P3 is running the ssh server package then get on your laptop and open Places>connect to server>chose ssh from the service type drop down. 
use the servers IP for the server. and fill in the name used for connection (that the name that will show up on the desktop and the file browser. 
Now it should show up a just another place in the file browser menu.

---

### Post by whitea on 2007-07-17
Thanks for the help.  I opened up the router configuration program and it says that I should put in a static ip if my ISP requires it, however it states that for my cable connection I should use a dynamic address.  I am concerned that I may mess up my internet connection.  Or am I looking at the wrong one?  Should I be changing the DHCP to a static address?

As for the network manager, I could not figure out a way to do it.

Again, I really appreciate your help.  I am very new to all of this but very eager to learn.

---

### Post by barbz127 on 2007-07-17
ok - hope this will help

So far your pc is on the network and has web?

If you type ifconfig in the terminal you should get an ip listed under an adpater.

Next for samba:

sudo apt-get install samba smbfs (you may have already installed it)

create and save the following file - basicaly links samba users to your ubunutu users (in my case both Paul)

sudo gedit /etc/samba/smbusers

    * Insert the following line into the new file 
system_username = "network username"
eg: paul = "paul"

create a password and enable the account
sudo smbpasswd -a system_username

now find your folder, right click and sharing, select smb give it a name and read/write access if you want it.

next go to your other pc - //ipaddressfromifconfig - insert your user name and password 

and you should see your folder.

PAul

---

### Post by skullmunky on 2007-07-18
whitea: there are two network addresses involved - external (for your cable modem to connect to the internet) and local (for the local network in your house).

any network address can be "dynamic" (DHCP), which means the network router picks an address for you when you connect; or "static" which means it never changes.  Your cable modem has a dynamic IP address.  The cable company has a pool of available network addresses, whenever you turn on your cable modem it gets one assigned, but it will change whenever you reset the modem.  

all the computers in your house have network addresses too, but they only matter within your local network.  the cable modem / router handles connections between your local network and the internet.  by default, it (your router) assigns IP addresses to your computers also using DHCP. 

a static IP allows you to always know the address of a certain computer.  for instance, the IP address of ubuntuforums.org is [http://82.211.81.186/](http://82.211.81.186/)  (put that in your browser location bar - ta da, it's the same thing!)

if ubuntuforums.org had a dynamic IP address it would constantly be moving around to different addresses. this is one reason why it's tricky to serve a website off a cable modem.  anytime you want to set up a server, it always helps to give it a static ip.

so, to get back to the point:

in your router config, don't change it to use a static address.  that's just for the connection to the internet.  you just need to change the settings on the PIII in your basement.

try this on the PIII (i'm assuming you have that on a wired, not wifi, connection):

you'll need to know the IP address of your router; you probably know this already if you got into it's config.  mine, for example, is just 10.0.0.1 ; another common one is 192.168.something or other.  i always like the 10.0.0.xxx addresses because they're way easier to remember :)

Go to System->Administration->Network

click "Wired Connection"
click "Properties"

Change "Configuration" from "Automatic Configuration (DHCP)" to "Static IP Address"

For IP Address, you could use whatever the current IP address is; or choose something like "10.0.0.2".  

For Subnet Mask, put in 255.255.255.0

For Gateway Address, put in the IP address of your router.

Hit OK and then Close the network configuration window.

Make sure you still have internet, then move on to setting up the server.

Louieb: thanks for the tip on using ssh, that is far and away the easiest file sharing i've ever done.  i've never been able to get a samba server to work in linux, but that was a snap!

My usual thing is to use ftp.  linux and windows will both let you browse a remote host just by putting in

[ftp://me@10.0.0.2](ftp://me@10.0.0.2) 

in the file browser (.e.g Explorer, Konqueror, or Nautilus) location bar.  you need to edit a couple of configuration files for this but it's solid.  let me know if you want to try this method.

---

### Post by whitea on 2007-07-18
> **skullmunky said:**
> whitea: there are two network addresses involved - external (for your cable modem to connect to the internet) and local (for the local network in your house).

any network address can be "dynamic" (DHCP), which means the network router picks an address for you when you connect; or "static" which means it never changes.  Your cable modem has a dynamic IP address.  The cable company has a pool of available network addresses, whenever you turn on your cable modem it gets one assigned, but it will change whenever you reset the modem.  

all the computers in your house have network addresses too, but they only matter within your local network.  the cable modem / router handles connections between your local network and the internet.  by default, it (your router) assigns IP addresses to your computers also using DHCP. 

a static IP allows you to always know the address of a certain computer.  for instance, the IP address of ubuntuforums.org is [http://82.211.81.186/](http://82.211.81.186/)  (put that in your browser location bar - ta da, it's the same thing!)

if ubuntuforums.org had a dynamic IP address it would constantly be moving around to different addresses. this is one reason why it's tricky to serve a website off a cable modem.  anytime you want to set up a server, it always helps to give it a static ip.

so, to get back to the point:

in your router config, don't change it to use a static address.  that's just for the connection to the internet.  you just need to change the settings on the PIII in your basement.

try this on the PIII (i'm assuming you have that on a wired, not wifi, connection):

you'll need to know the IP address of your router; you probably know this already if you got into it's config.  mine, for example, is just 10.0.0.1 ; another common one is 192.168.something or other.  i always like the 10.0.0.xxx addresses because they're way easier to remember :)

Go to System->Administration->Network

click "Wired Connection"
click "Properties"

Change "Configuration" from "Automatic Configuration (DHCP)" to "Static IP Address"

For IP Address, you could use whatever the current IP address is; or choose something like "10.0.0.2".  

For Subnet Mask, put in 255.255.255.0

For Gateway Address, put in the IP address of your router.

Hit OK and then Close the network configuration window.

Make sure you still have internet, then move on to setting up the server.

Louieb: thanks for the tip on using ssh, that is far and away the easiest file sharing i've ever done.  i've never been able to get a samba server to work in linux, but that was a snap!

My usual thing is to use ftp.  linux and windows will both let you browse a remote host just by putting in

[ftp://me@10.0.0.2](ftp://me@10.0.0.2) 

in the file browser (.e.g Explorer, Konqueror, or Nautilus) location bar.  you need to edit a couple of configuration files for this but it's solid.  let me know if you want to try this method.



I tried adjusting the network settings but lost the internet!!

---

### Post by movrshakr on 2007-07-19
Just a general comment here...I have a machine in my house that I use essentially as a file server.  There is a subdirectory on it, C:\MyStuff, that I have shared to the network in Windows XP.  That works cleanly--can be connected-to from the other Win machines in the house.  I thought I would try to move into ubuntu on this machine.

But after reading this and other threads, I see that it is immensely difficult to share out of ubuntu to Windows machines.  And that doesn't even begin to address that the folder to be shared is "on the Windows side" rather than in the ubuntu area.  Geeze.  I am disappointed.  After loading the wubi-ubuntu on that machine, I thought it had approached consumer level usability.  But on the file sharing front, it isn't even close. It's intimidating.

---


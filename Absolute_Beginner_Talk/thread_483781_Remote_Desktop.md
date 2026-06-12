---
title: "Remote Desktop"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-06-25
I have got a work colleague to install Ubuntu on his PC and he is enjoying so far, but is having problems following the tutorial on adding multimedia support, java and flash etc.

I have seen that there is a remote desktop option in Ubuntu, will this work over the internet.  We both use routers to connect to our ASDL lines and I have the address that he has given me in the form vncviewer user-desktop:0.

Do we need to do anything else or in their an alternative way of connecting our PC's without him having to install or configure to much.

Thanks

Ian

---

### Post by dfreer on 2007-06-25
The eaisest method (and pretty secure) that I just found out myself would be to create a local user account on his machine, create an SSH server, make sure the SSH port is open to the internet, and then SSH in to the machine. From there, you can install software and such using the terminal, so that's good. You can also enable the remote desktop from there as well, and since it is over SSH it will be secure. For best security only allow vnc to be accessed from the localhost (when you SSH in you would be running vncviewer from the localhost, only having it display on your screen).

---

### Post by xpod on 2007-06-25
You can just use the terminal server client in Applications>internet to conect remotely like that.
Put his ip address in, choose vnc then connect,asks for his password & off you go:p
You`se obviously need to have the relevant permissions set in System>Admin>Remote desktop.

I dont use routers on our two different mini-networks though so dont know how they come into the equation.
There are  securer ways of connecting between machines though but again i`m only just starting to play about with them myself this last few months so cant give you any real advice other than some usefull links mabey

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
[https://help.ubuntu.com/community/AdvancedOpenSSH?highlight=%28openssh%29](https://help.ubuntu.com/community/AdvancedOpenSSH?highlight=%28openssh%29)

---

### Post by skymera on 2007-06-25
i have a router, well my dad does.

my mate tries to VNC my machine but cannot get through, router blocks it.
but he can SSH which is weird.

so router does come into the equation

---

### Post by xpod on 2007-06-25
Cant he just go into Add|Remove and install the restricted packages??

It`s listed under "others" in Add/Remove if i recall correctly.Tell him to make sure he has "All available applications" chosen in the top right....Ubuntu restricted extras:D

---

### Post by ushills on 2007-06-25
The problem I have is if he is already struggling with the command line he won't be able to open ports on his router no install any server on his machine.

I am looking for a similar interface to XP's remote desktop, I need to be able to connect into his machine to install things for him and set up appliactions.

I will look at the options in add/remove though because if he can just install java, flash, MP3, libcssdvd etc he may be able to survive.

However, I also need to set up thunderbird to access his Gmail account.

Is there any easy way to do this or a walkthough explaining each parties steps, preferably all in the GUI or a few simple commands in terminal.

Thanks

---

### Post by dfreer on 2007-06-25
Here's my method's walkthrough, this is using SSH to tunnel to his computer, and then using vncviewer to establish a LOCAL connection. The local connection is important, as it will not let anyone connect to the vncviewer from the internet. Another thing this guide will do is set up fail2ban so that it will block any SSH login attempt after 5 failures to login for 30 minutes or so, wihich will cut down greatly on people trying to bruteforce their way in. One more important thing would be to create a dynamic DNS account, that way you can find his IP address from anywhere he connects. This looks complicated, but really it''s not, it's pretty much all cut+and+paste. Just follow the steps and you'll be fine.

(1) Install SSH server:
```
sudo apt-get install openssh-server
```

(2) Install fail2ban
```
sudo apt-get install fail2ban
```
Configure fail2ban:
```
sudo gedit /etc/fail2ban/jail.local
```
Insert the following lines into the new file:
```

# Fail2Ban local configuration file.
#

[DEFAULT]
ignoreip = 127.0.0.1
bantime  = 600
maxretry = 3

backend = polling
destemail = root@localhost

#
# ACTIONS
#

banaction = iptables-multiport
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s"]
action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s"]
              mail-whois[name=%(__name__)s, dest="%(destemail)s"]

action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s"]
               mail-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s]

action = %(action_)s

#
# JAILS
#

[ssh]
enabled = true
port    = ssh,sftp
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 5
bantime = 1800

```

Restart Fail2ban
```
sudo /etc/init.d/fail2ban restart
```

(3) Open a port for SSH on the router:
You will need to do this manually, because it differs for each router. If you are on the same LAN this is not needed.

(4) Install x11vnc:
Taken from this guide: [http://ubuntuforums.org/showthread.php?t=460206](http://ubuntuforums.org/showthread.php?t=460206)
```
sudo apt-get install x11vnc
```
*Since we are setting this for a localhost connection, there really is no need for a vnc password.*
Backup files:
```
sudo cp /etc/X11/gdm/gdm.conf /etc/X11/gdm/gdm.conf.backup
sudo cp /etc/X11/gdm/Init/Default /etc/X11/gdm/Init/Default.backup
```
Modify two files:
```
sudo gedit /etc/X11/gdm/gdm.conf
```
Find and replace this line:
```
#KillInitClients=true
```
With this line (note the removal of the comment):
```
KillInitClients=false
```

```
sudo gedit /etc/X11/gdm/Init/Default
```
Insert the following line just above the line that starts with PATH:
```
/usr/bin/x11vnc -noxdamage -forever -bg -o /var/log/x11vnc.log -rfbport 5900 -localhost
```

(5) Set up a DynDNS client so you can access the machine from anywhere:
This assumes the computer has a dynamic IP address, and that you will need to access it from the internet. Again, if you are on a LAN this is not needed.
(5.1) Register an account with dyndns.com, and create a free dynamic host.
(5.2) Install the client:
```
sudo apt-get install ddclient
```
It will ask you some questions, go ahead and fill it out using the information from the account you just created above. Don't really worry about messing this up, This just write some stuff to the config file and we are going to modify it anyways.
Edit the config file:
```
sudo gedit /etc/ddclient.conf
```
Insert (or make sure they are correct) the following lines:
```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=members.dyndns.org
login=**your_dyndns_username**
password='**your_dyndns_password**'
**mybox.dyndns.org**   #This is the FQDN you set up with dyndns

```

Restart dyndns:
```
sudo /etc/init.d/ddclient restart
```

(6) create a local user account (this way you can login to his machine using SSH)
```
sudo adduser **your_desired_username**
```
Fill out the form.
If you need to be able to use sudo, do this:
```
sudo adduser **your_desired_username** admin
```thth

(7) Restart the machine (due to the modifications to GDM earlier).

You should now, from anywhere in the world, connect to **mybox.dyndns.org** with SSH (on a linux machine, simply type *ssh -X **your_desired_username**@**mybox.dyndns.org***
From there, to do remote desktop:
```
vncviewer localhost
```


Hope this helps!

> **ushills said:**
> The problem I have is if he is already struggling with the command line he won't be able to open ports on his router no install any server on his machine.
The method to open the ports on his router is the same regardless of whether you are using linux or XP, however if YOU do not know how to open the ports no amount of guides on remote desktop will help you because all connections would be blocked by the firewall.

---

### Post by Seisen on 2007-06-25
This might help you and your friend 

[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")

---

### Post by ushills on 2007-06-26
> **Seisen said:**
> This might help you and your friend 

[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html]("http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html")

Unfortunately this only works on a local LAN I believe, I tried this yesterday and terminal said could'nt find host.

---

### Post by ushills on 2007-06-26
Thanks Dfreer, that looks an excellent walkthrough, as he is a n00b I may get his to give me his machine so that I can set this up for him.

I have wriiten him a guide on how to do certain things so this may suffice, however, I think ubuntu needs a really easy way to set up remote admin through a GUI without the need to configure many things.

He may be able to setup a passthough on his router as we have the same one, but if he cannot install apps though apt-get he won't be able to follow the above.  At least not yet, but there is always hope.

---

### Post by kevdog on 2007-06-26
Excellent tutorial above -- must have taken a long time to write that!!!

I prefer FreeNx over VNC although I know many people have not heard of it.  It tunnels over ssh, and I have found it to be much more zippy!  I used VNC for a long time, but it was always very slow for me.

Anyway thanks for the tutorial!

---

### Post by Smandola on 2007-06-26
I have setup a remote desktop, by using Hamachi.  I use the IP address from Hamachi to tunnel to my server.  I think it was the easy way out.  I don't know if the Hamachi solution is as secure as using SSH and the steps listed above... but for me it was much easier.  

Steps are:
1) download and install Hamachi on your server (or Ubuntu machine to be remotely controlled)
2) ensure your server is running VNC.
3) download and install Hamachi on your PC, or whatever machine you are controlling your server from
4) install VNC on your PC
5) use the ip address of your server (from Hamachi ie: 5.X.X.X:0) in your VNC software
6) remote desktop control is yours.

I think I may have over simplified this, but effectively those are the steps.  
I have this setup and it seems to work really well... although I don't think the speed is that great.  But hey, I can access my files from anywhere.

Hope this helps.

---

### Post by lazyart on 2007-06-26
There is a gui for hamachi-- gHamachi (it's just a front end so you'll need to get hamachi first).  It really works great.  You need to install it on all machines (lin,win and osx can all communicate).  Create a network (name & password) and have others join it with the same info.

---

### Post by dfreer on 2007-06-26
Thanks kevdog!
I just got done setting this up on my sister's pc at college, although I am not quite satisfied with the speed (pretty slow). This is my first time messing with remote desktops for linux, and I would like to experiment with other (free) solutions. I can write a guide for those as well, the only requirements would be:
(1) be able to initiate viewer only from localhost, for security reasons. This way I can still use SSH to encrypt the actual traffic, and I won't need to worry about the security of the remote desktop software (as only a local user would be able to access it).

Any suggestions guys? I'll check out FreeNX and hamachi in the meantime :D

---


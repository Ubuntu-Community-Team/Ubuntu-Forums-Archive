---
title: "fixing broken packages"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by eul0gy on 2007-08-18
I just installled the wonderful ubuntu yesterday on my PC. Im trying to upgrade but everytime I do I get this message> 


It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

or it says:

A error occured, please run package manager from the right click menu or apt-get on a terminal and see what is wrong. THE ERROR MESSAGE WAS: Error: BrokenCount > 0

IDK What to do.  HELP

---

### Post by taurus on 2007-08-18
What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
p.s.  Use the same password that you log in with and when you type it, you won't see any echo on the screen so don't worry about it.

---

### Post by Caffeine_Junky on 2007-08-18
hey there,  yeah open up synaptic package manager and select "Custom Filters" (bottom left)  then "Broken"  that should display broken packages with a red box,  just uninstall them and you should be good to go..

Edit:  heh I was to slow :-P

cheers

---

### Post by eul0gy on 2007-08-18
on Install-f i get a trems and agreement message for Java which i tried installing yesterday. 

on the get upgrade one i got this message: 

eul0gy@EUL0GY:~$ sudo apt-get upgrade
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


eul0gy@EUL0GY:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2007-08-18
You need to shutdown synaptic if you have it open.  You cannot run synaptic and apt-get at the same time.  Only one at a time.

---

### Post by eul0gy on 2007-08-18
what the hell is sypnatic? im extremelly new to this sorry... how woyuld i go abouit doing this?????

---

### Post by taurus on 2007-08-18
In that case, can you post the complete output of this command from a terminal?

```
ps -A
```
p.s.  Synaptic is just a GUI for adept while apt-get is a terminal command.  You can do the same thing with synaptic as you would with apt-get/aptitude.

---

### Post by eul0gy on 2007-08-18
ok I opened up the synaptic package manager and got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2007-08-18
Shutdown synaptic completely.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kwacka on 2007-08-18
open a terminal and type:

sudo dpkg --configure -a

enter your password 

Then open synaptic by clicking on 'System' then 'Administration' 'Synaptic package manager'

---


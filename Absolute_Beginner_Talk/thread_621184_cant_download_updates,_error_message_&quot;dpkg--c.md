---
title: "cant download updates, error message &quot;dpkg--configure&quot;"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Kit_Barb on 2007-11-23
Hello all, 



> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What ever way I try to download stuff, either terminal command, automatix or via the update icon I get the same message , when I run the **dpkg --configure -a** command in the terminal, it tells me I dont have super user status so I cant do it.

TIA

---

### Post by taurus on 2007-11-23
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Kit_Barb on 2007-11-23
Thanks for replying Taurus , I got this.
> 
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
steve@steve-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



Not sure what I do next ?

---

### Post by taurus on 2007-11-23
```
**sudo** apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```
You need to include sudo in front of those commands since you want to run them as root.

---

### Post by overdrank on 2007-11-23
> **Kit_Barb said:**
> Thanks for replying Taurus , I got this.




Not sure what I do next ?

Add sudo  that is why taurus highlighted in bold.

---

### Post by Kit_Barb on 2007-11-23
Ahhhh ok,  sorted now.

Thankyou for your help.

---

### Post by Kit_Barb on 2007-11-23
i thought it was sorted :(
> 
steve@steve-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
steve@steve-desktop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Get:4 [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/restricted Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:7 [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty Release                                
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates Release                        
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/main Sources                 
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/universe Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty/multiverse Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/main Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Fetched 9B in 1s (8B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
steve@steve-desktop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
steve@steve-desktop:~$ 

---

### Post by Kit_Barb on 2007-11-23
opps forgot the sudo again, case closed. cheers.

---

### Post by overdrank on 2007-11-23
> **Kit_Barb said:**
> opps forgot the sudo again, case closed. cheers.

Hi and I would highly recommend using this command ```
gksudo gedit /etc/apt/sources.list
``` and place a comment # if front of the automatix repos.

---

### Post by taurus on 2007-11-23
Apparently, you have two repos for Automatix, one for Feisty and one for Gutsy!  What's up with that?

---

### Post by Kit_Barb on 2007-11-23
> **taurus said:**
> Apparently, you have two repos for Automatix, one for Feisty and one for Gutsy!  What's up with that?

I think I maybe dl'd the wrong automtix version, and then got the correct one.

The problem I have now is my terminal has changed into a sun java licence agreement with

<ok>

at the end, and I cant find a way to click OK and move on to the install?

---

### Post by taurus on 2007-11-23
High the Tab key to highlight the <ok>.  Then, Return key to except it.

---

### Post by Kit_Barb on 2007-11-23
> **taurus said:**
> High the Tab key to highlight the <ok>.  Then, Return key to except it.

Thanks for your patience , that worked fine.

---

### Post by Kit_Barb on 2007-11-23
My update manager is working fine now , thanks for all your replies.

---

### Post by ninja_pie on 2007-11-25
:( Hey every one I'm new to Linux Ubuntu. I keep getting the 

> dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

How can i fix this? I have tried many different ways. If you can please help me fix this. Thanx :)

---

### Post by overdrank on 2007-11-25
> **ninja_pie said:**
> :( Hey every one I'm new to Linux Ubuntu. I keep getting the 



How can i fix this? I have tried many different ways. If you can please help me fix this. Thanx :)

HI and welcome, just as Taurus stated in post #2  
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Run each of those commands in the terminal located under applications, accessories, terminal. :)

---

### Post by ninja_pie on 2007-11-25
I tried the  sudo dpkg --configure -a
and i got this :(

> pkg: unable to access dpkg status area: No such file or director

---

### Post by overdrank on 2007-11-25
> **ninja_pie said:**
> I tried the  sudo dpkg --configure -a
and i got this :(

dy

Try this command ```
sudo apt-get -f install

```

---

### Post by ninja_pie on 2007-11-25
Ok I tried that too and it got this
> 
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

So I did the su command and sing in as root then tried it again, then I got this again

> E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by overdrank on 2007-11-25
> **ninja_pie said:**
> Ok I tried that too and it got this


So I did the su command and sing in as root then tried it again, then I got this again

Ok do you have another package manager open? Like synaptic or add and remove. Also which version of Ubuntu are you using? You can find out under system, about Ubuntu.

---

### Post by ninja_pie on 2007-11-25
I have no idea if i do have something else running I probably do because when I was trying to install limewire it asked me to close out of one so I can install, but I don't know how. I'm using 7.10

---

### Post by overdrank on 2007-11-25
> **ninja_pie said:**
> I have no idea if i do have something else running I probably do because when I was trying to install limewire it asked me to close out of one so I can install, but I don't know how. I'm using 7.10

Ok have you reboot the system since you installed limewire ( and I would recommend frostwire) ? If not reboot and the try the update command again and post all of the out put ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ninja_pie on 2007-11-25
Thanx for the recommendation. =] I have rebooted a few time after downloading it. I wasn't able to install it. I just rebooted again and I have an update but it wont install...

> 
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'

Ounce I login I tried to run the command again and it came up with the same thing but it had more to it.



> Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 4B in 1s (4B/s)  
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---


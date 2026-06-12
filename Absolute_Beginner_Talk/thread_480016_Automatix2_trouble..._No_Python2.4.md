---
title: "Automatix2 trouble... No Python2.4??"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-20
Trying to install Automatix2, and I am having some trouble. I am following this guide: [http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt)

And here is my outcome:

```
   tim@tim-desktop-ubuntulinux:~$ echo "deb http://www.getautomatix.com/apt feisty main" | sudo tee -a /etc/apt/sources.list
deb http://www.getautomatix.com/apt feisty main
tim@tim-desktop-ubuntulinux:~$ wget http://www.getautomatix.com/keys/automatix2.key
--23:16:30--  http://www.getautomatix.com/keys/automatix2.key
           => `automatix2.key'
Resolving www.getautomatix.com... 216.120.255.9
Connecting to www.getautomatix.com|216.120.255.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s             

23:16:30 (56.93 MB/s) - `automatix2.key' saved [1706/1706]

tim@tim-desktop-ubuntulinux:~$ gpg --import automatix2.key
gpg: key E23C5FC3: "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
tim@tim-desktop-ubuntulinux:~$ gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
tim@tim-desktop-ubuntulinux:~$ sudo apt-get update
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Get:3 http://ubuntu.beryl-project.org feisty Release.gpg [191B]                
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Hit http://www.getautomatix.com feisty Release                                 
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:5 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://www.getautomatix.com feisty/main Packages                           
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US              
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://www.getautomatix.com feisty/main Packages                           
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US   
Hit http://download.tuxfamily.org feisty Release                               
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://ubuntu.beryl-project.org feisty Release                             
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages       
Ign http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://ubuntu.beryl-project.org feisty/main Packages                       
Hit http://download.tuxfamily.org feisty/avant-window-navigator Sources        
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:7 http://us.archive.ubuntu.com feisty/main Packages [1307kB]
99% [7 Packages gzip 0]            
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages
  Sub-process gzip returned an error code (1)
Fetched 197B in 1s (101B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tim@tim-desktop-ubuntulinux:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: python2.4 but it is not installable
E: Broken packages
tim@tim-desktop-ubuntulinux:~$ 

```

So, with that, how should I go about installing this?

Let me know, 

-ts51

---

### Post by ts51 on 2007-06-20
Any Ideas?

---

### Post by Bachstelze on 2007-06-20
Simple : do not install Automatix :)

---

### Post by w4ett on 2007-06-21
> **HymnToLife said:**
> Simple : do not install Automatix :)

Very helpful aren't you?


try getting help from the automatix crew at:

[http://www.getautomatix.com/forum/index.php](http://www.getautomatix.com/forum/index.php)

---

### Post by alienexplorers on 2007-06-21
Don't use it.  It just messes up your system.  Hate to see you do a complete reinstall.

---

### Post by bodhi.zazen on 2007-06-21
LOL

without feeding the flames too much ...

Tech support for Automatix is best and most up to date information on the automatix forums.

---

### Post by FleetAdmiral74 on 2007-06-21
> **w4ett said:**
> Very helpful aren't you?


try getting help from the automatix crew at:

[http://www.getautomatix.com/forum/index.php](http://www.getautomatix.com/forum/index.php)

that was EXTREMELY good advice he gave, no bashing him.. That program breaks often, almost assuredly with a major upgrade, and is very messy with its file dependencies and what not.

Just stick with APT, synaptic.

---

### Post by STREETURCHINE on 2007-06-21
> **ts51 said:**
> Trying to install Automatix2, and I am having some trouble. I am following this guide: [http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt)

And here is my outcome:

```
   tim@tim-desktop-ubuntulinux:~$ echo "deb http://www.getautomatix.com/apt feisty main" | sudo tee -a /etc/apt/sources.list
deb http://www.getautomatix.com/apt feisty main
tim@tim-desktop-ubuntulinux:~$ wget http://www.getautomatix.com/keys/automatix2.key
--23:16:30--  http://www.getautomatix.com/keys/automatix2.key
           => `automatix2.key'
Resolving www.getautomatix.com... 216.120.255.9
Connecting to www.getautomatix.com|216.120.255.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[====================================>] 1,706         --.--K/s             

23:16:30 (56.93 MB/s) - `automatix2.key' saved [1706/1706]

tim@tim-desktop-ubuntulinux:~$ gpg --import automatix2.key
gpg: key E23C5FC3: "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
tim@tim-desktop-ubuntulinux:~$ gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
tim@tim-desktop-ubuntulinux:~$ sudo apt-get update
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Get:3 http://ubuntu.beryl-project.org feisty Release.gpg [191B]                
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Hit http://www.getautomatix.com feisty Release                                 
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:5 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://www.getautomatix.com feisty/main Packages                           
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US              
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://www.getautomatix.com feisty/main Packages                           
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US   
Hit http://download.tuxfamily.org feisty Release                               
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://ubuntu.beryl-project.org feisty Release                             
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages       
Ign http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://ubuntu.beryl-project.org feisty/main Packages                       
Hit http://download.tuxfamily.org feisty/avant-window-navigator Sources        
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:7 http://us.archive.ubuntu.com feisty/main Packages [1307kB]
99% [7 Packages gzip 0]            
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages
  Sub-process gzip returned an error code (1)
Fetched 197B in 1s (101B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tim@tim-desktop-ubuntulinux:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: python2.4 but it is not installable
E: Broken packages
tim@tim-desktop-ubuntulinux:~$ 

```

So, with that, how should I go about installing this?

Let me know, 

-ts51

go to the automatix forum and ask arnie he will help you out.
there is a link to the forum in my signature below.

oh and take what others say  on here with a grain of salt when they state it breaks things but never offer solid proof.
i have used automatix on three ubuntu installs dapper,edgy,feisty no drama at all .
it is very usefull program,you can get your computer set up then go about learning in your own time.:D

---

### Post by ts51 on 2007-06-21
OK... thanks for all your help, advice, and opinions. 

I thought about my choices and decided that I just won't go about installing Automatix...

Now I just need to find a good VirtualBox tutorial.

Thanks again,

ts51

---

### Post by meborc on 2007-06-21
maybe this - [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

---

### Post by jonward0690 on 2007-06-21
Here is a great virtual box tutorial just follow the insructions very simple. 

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by ts51 on 2007-06-21
Thanks for the tutorials, but I get tons of errors (I miss Automatix..) and I think this is the problem (check out the screenshot)

---

### Post by bodhi.zazen on 2007-06-21
Innotec maintains a repository for Virtualbox, so ...

Follow these steps : [http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host](http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host)

Otherwise you will have to install the dependencies manually ...

---

### Post by ts51 on 2007-06-21
> **bodhi.zazen said:**
> Innotec maintains a repository for Virtualbox, so ...

Follow these steps : [http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host](http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host)

Otherwise you will have to install the dependencies manually ...

I did all of that! Can you explain how to do it manually? I think my Synaptic is messed up. 

I will try those steps again though...

Outcome:

> tim@tim-desktop-ubuntulinux:~$ sudo gedit /etc/apt/sources.list
Password:
tim@tim-desktop-ubuntulinux:~$ wget [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) sudo apt-key add innotek.asc
--12:06:44--  [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)
           => `innotek.asc.1'
Resolving [www.virtualbox.org](www.virtualbox.org)... 88.198.19.108
Connecting to www.virtualbox.org|88.198.19.108|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [text/plain]

100%[====================================>] 1,706         --.--K/s             

12:06:45 (455.86 KB/s) - `innotek.asc.1' saved [1706/1706]

--12:06:45--  [http://sudo/](http://sudo/)
           => `index.html'
Resolving sudo... failed: Name or service not known.
--12:06:45--  [http://apt-key/](http://apt-key/)
           => `index.html'
Resolving apt-key... failed: Name or service not known.
--12:06:45--  [http://add/](http://add/)
           => `index.html'
Resolving add... failed: Name or service not known.
--12:06:45--  [http://innotek.asc/](http://innotek.asc/)
           => `index.html'
Resolving innotek.asc... failed: Name or service not known.

FINISHED --12:06:45--
Downloaded: 1,706 bytes in 1 files
tim@tim-desktop-ubuntulinux:~$ sudo aptitude update sudo aptitude install virtualbox
E: The update command takes no arguments
tim@tim-desktop-ubuntulinux:~$ 


---

### Post by ts51 on 2007-06-21
?

---

### Post by Nikron on 2007-06-21
> **ts51 said:**
> I did all of that! Can you explain how to do it manually? I think my Synaptic is messed up. 

I will try those steps again though...

Outcome:

Copy paste this

```

cd
sudo apt-key add innotek.asc
sudo aptitude update
sudo aptitude install virtualbox

```

---

### Post by ts51 on 2007-06-21
```
tim@tim-desktop-ubuntulinux:~$ cd
tim@tim-desktop-ubuntulinux:~$ sudo apt-key add innotek.asc
Password:
OK
tim@tim-desktop-ubuntulinux:~$ sudo aptitude update
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US                   
Get:2 http://ftp.us.debian.org etch Release.gpg [378B]                          
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]             
Get:4 http://ubuntu.beryl-project.org feisty Release.gpg [191B]                 
Get:5 http://us.archive.ubuntu.com feisty Release.gpg [191B]                    
Ign http://www.getautomatix.com feisty/main Translation-en_US                   
Hit http://www.getautomatix.com feisty Release                                  
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                  
Get:6 http://www.virtualbox.org feisty Release.gpg [189B]                       
Ign http://ftp.us.debian.org etch/main Translation-en_US                        
Ign http://ftp.us.debian.org etch/non-free Translation-en_US                    
Ign http://ftp.us.debian.org etch/contrib Translation-en_US                     
Ign http://security.ubuntu.com feisty-security/main Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US              
Hit http://www.getautomatix.com feisty/main Packages                            
Get:7 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US    
Ign http://www.virtualbox.org feisty/non-free Translation-en_US                 
Hit http://ftp.us.debian.org etch Release                                       
Err http://ftp.us.debian.org etch Release                                       
  
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US       
Hit http://www.getautomatix.com feisty/main Packages                            
Ign http://www.virtualbox.org feisty/non-free Translation-en_US                 
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US               
Hit http://security.ubuntu.com feisty-security Release                          
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US    
Hit http://www.virtualbox.org feisty Release                                    
Get:8 http://ftp.us.debian.org etch Release [58.2kB]                            
Hit http://security.ubuntu.com feisty-security/main Packages                    
Hit http://ubuntu.beryl-project.org feisty Release                              
Ign http://www.virtualbox.org feisty/non-free Packages                          
Hit http://security.ubuntu.com feisty-security/restricted Packages              
Hit http://ubuntu.beryl-project.org feisty/main Packages                        
Ign http://www.virtualbox.org feisty/non-free Packages                          
Hit http://security.ubuntu.com feisty-security/multiverse Packages              
Hit http://security.ubuntu.com feisty-security/main Sources                     
Hit http://security.ubuntu.com feisty-security/restricted Sources               
Hit http://us.archive.ubuntu.com feisty Release                                 
Hit http://us.archive.ubuntu.com feisty-updates Release                         
Hit http://www.virtualbox.org feisty/non-free Packages                          
Hit http://security.ubuntu.com feisty-security/universe Packages                
Hit http://security.ubuntu.com feisty-security/universe Sources                 
Ign http://us.archive.ubuntu.com feisty/main Packages                           
Hit http://www.virtualbox.org feisty/non-free Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                     
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                     
Hit http://us.archive.ubuntu.com feisty/main Sources                            
Ign http://ftp.us.debian.org etch Release                                       
Hit http://us.archive.ubuntu.com feisty/restricted Sources      
Hit http://us.archive.ubuntu.com feisty/universe Packages       
Hit http://us.archive.ubuntu.com feisty/universe Sources        
Hit http://us.archive.ubuntu.com feisty-updates/main Packages   
Hit http://ftp.us.debian.org etch/main Packages                                 
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages             
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                    
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources              
Get:9 http://us.archive.ubuntu.com feisty/main Packages [1307kB]                
Hit http://ftp.us.debian.org etch/non-free Packages                             
99% [9 Packages gzip 0] [Waiting for headers] [Connecting to download.tuxfamily.
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/main Packages                           
  Sub-process gzip returned an error code (1)
Hit http://ftp.us.debian.org etch/contrib Packages                              
Get:10 http://download.tuxfamily.org feisty Release.gpg [189B]  
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://download.tuxfamily.org feisty Release
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages
Hit http://download.tuxfamily.org feisty/avant-window-navigator Sources         
Fetched 58.8kB in 6s (9465B/s)                                                  
Reading package lists... Done
W: GPG error: http://ftp.us.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems
tim@tim-desktop-ubuntulinux:~$ sudo aptitude install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  virtualbox 
The following NEW packages will be automatically installed:
  bridge-utils libxalan110 libxerces27 uml-utilities 
The following packages have been kept back:
  acpi adduser alsa-base alsa-utils apmd aptitude aspell 
  avant-window-navigator-svn base-passwd belocs-locales-bin brltty 
  brltty-x11 bsdmainutils bsdutils ca-certificates console-terminus 
  coreutils cpio dash dcraw defoma dhcdbd dhcp3-client dhcp3-common 
  dmidecode dosfstools dpkg dselect ed eject ekiga fdutils fontconfig 
  fontconfig-config fping freeglut3 ftp gamin genisoimage gnome-mount 
  gnome-pilot gnupg gpgv groff-base grub hal hal-device-manager hdparm 
  initramfs-tools initscripts iputils-arping iputils-ping iputils-tracepath 
  iso-codes klibc-utils libaa1 libao2 libapm1 libart-2.0-2 libasound2 
  libaspell15 libaudio2 libavc1394-0 libbrlapi1 libdaemon0 libdb4.2 
  libdb4.3 libedit2 libelfg0 libflac7 libfontconfig1 libgamin0 libgdbm3 
  libgdl-1-0 libgdl-1-common libgksu2-0 libglade2-0 libgnome-pilot2 
  libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgpmg1 
  libgtkspell0 libhal-storage1 libhal1 libhtml-tagset-perl 
  libhtml-tree-perl libjasper-1.701-1 libjpeg62 libklibc libkpathsea4 
  libkrb53 liblcms1 libldap2 liblocale-gettext-perl liblzo1 libmagick9 
  libmng1 libnewt0.52 libnotify1 libopal-2.2.0 libparted1.7-1 libportaudio0 
  libsane libscrollkeeper0 libsdl1.2debian libsdl1.2debian-alsa libsensors3 
  libslp1 libsmbclient libsnmp-base libsnmp9 libspeex1 libtext-iconv-perl 
  libtiff4 liburi-perl libusb-0.1-4 libvisual-0.4-0 libvorbis0a 
  libvorbisenc2 libvorbisfile3 libwrap0 libxdamage1 libxkbfile1 
  libxplc0.3.13 libxrender1 libxres1 libxss1 libxxf86dga1 libxxf86misc1 
  libxxf86vm1 linux-sound-base login logrotate lsb-base lsb-release lsof 
  ltrace man-db mii-diag mktemp module-init-tools mount 
  mozilla-firefox-locale-en-gb mtr-tiny nano netbase netcat ntpdate 
  openssh-client parted passwd patch popularity-contest ppp pppoeconf 
  python-gnome2-extras python-gnupginterface samba-common 
  scim-modules-table screen scrollkeeper sed sgml-data smbclient 
  ssh-askpass-gnome ssl-cert synaptic sysv-rc tar tasksel tasksel-data 
  tcpdump time ttf-arabeyes ttf-arphic-ukai ttf-bengali-fonts ttf-dejavu 
  ttf-devanagari-fonts ttf-freefont ttf-gujarati-fonts ttf-indic-fonts 
  ttf-kannada-fonts ttf-lao ttf-malayalam-fonts ttf-oriya-fonts 
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ucf update-inetd 
  util-linux util-linux-locales vnc-common wamerican wbritish whiptail 
  wodim wvdial x-ttcidfont-conf xbitmaps xfonts-100dpi xfonts-75dpi 
  xfonts-base xml-core xsane xsane-common xserver-xorg-input-elographics 
  xserver-xorg-input-synaptics xserver-xorg-video-savage xvncviewer zip 
The following NEW packages will be installed:
  bridge-utils libxalan110 libxerces27 uml-utilities 
0 packages upgraded, 5 newly installed, 0 to remove and 212 not upgraded.
Need to get 15.8MB of archives. After unpacking 37.1MB will be used.
The following packages have unmet dependencies:
  virtualbox: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.7-4+b1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
virtualbox [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?] 

```

So, um, what should I press?

---

### Post by kelvin spratt on 2007-06-21
bodhi.zazen
removed as recommending Atomatix offends people

---

### Post by bodhi.zazen on 2007-06-21
> **ts51 said:**
> ```
tim@tim-desktop-ubuntulinux:~$ cd
tim@tim-desktop-ubuntulinux:~$ sudo apt-key add innotek.asc
Password


<..Clip...>


tim@tim-desktop-ubuntulinux:~$ sudo aptitude install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  virtualbox 
The following NEW packages will be automatically installed:
  **bridge-utils libxalan110 libxerces27 uml-utilities**
 
The following packages have been kept back:

..clip..

The following NEW packages will be installed:
  bridge-utils libxalan110 libxerces27 uml-utilities 
0 packages upgraded, 5 newly installed, 0 to remove and 212 not upgraded.
Need to get 15.8MB of archives. After unpacking 37.1MB will be used.
The following packages have unmet dependencies:
  virtualbox: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.7-4+b1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
virtualbox [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?] 

```

So, um, what should I press?

Well, you have several "problems"

[list][*]your sources are a mess. You have all kinds of stuff in there. Debian, Ubuntu, automatix, ... I ran a mixed system for a while, BUT unless you know what you are doing you are headed to breakage.

[*]I would return to a fresh /etc/apt/sources.list

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

^^ There is a clean list there along with a few instructions.


[*]OK, once that is done, lets restore your system (if you like). BUT this is where you may get trouble ;)
all those 3rd party sources (debian, automatix) can be problematic ...

[list=number][*]clean up your /etc/apt/sources.list (as much as you are going to at least). At a minimum remove the automatix stuff.
[*]Run these commands :```
sudo apt-get update
sudo apt-get dist-upgrade
```[/list]


[*]Now, install virtualbox : ```
sudo apt-get install virtualbox
```[/list]


=================


If you want to keep a mixed system, install those dependencies (select yes) and re-try virtualbox.

```
sudo apt-get install bridge-utils libxalan110 libxerces27 uml-utilities
sudo apt-get install virtualbox
```

If that fails, install the dependencies : ```
sudo apt-get install bridge-utils libxalan110 libxerces27 uml-utilities
```

Then, download and install "All distributions i386 | AMD64" from here :

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Install with ```
sudo ./VirtualBox_1.4.0_Linux_x86.run
```


===============

CAUTION : With a sources list the way you have you *MAY* be headed to more broken packages, let alone a broken system.

---

### Post by bodhi.zazen on 2007-06-21
> **kelvin spratt said:**
> download Automatix for Ubuntu from there site it will install it al including python,l take no notice of the tossers, their is nothing wrong with automatix its Mediabuntu in a graphical format.

Kelvin, and others :

FYI there is an "official" policy regarding automatix :

[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)

I am sorry if you do not agree with it or do not like it, but I expect no further comments like this ...

---

### Post by kelvin spratt on 2007-06-22
bodhi.zazen

I've edited my post to suit your opinion that its ok for you to sound of your opinions, but other people have to be silent well you don't like Automatix thats your opinion and you are offended when somebody takes a stand when people are flaming people for wanting to use
Automatix

---

### Post by bodhi.zazen on 2007-06-22
My stance is with the flames, not automatix.

---


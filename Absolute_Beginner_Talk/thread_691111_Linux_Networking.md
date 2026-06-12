---
title: "Linux Networking"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nebu on 2008-02-08
In school we had computers with fedora and red hat installed..... i remember that we could log onto computers in the school network using our user accounts on particular workstations(ones we were trying to access)

could u tell me how to do this on my home pc network.... i have ubuntu installed on my laptop and desktop computers...... however whenever i try to telnet to my desktop(with its ip address) from my laptop it gives me an error of request denied.....

how can i setup this service on my computers???
is there a particular port to which i should "telnet"???


:confused::confused::confused::confused::confused:

---

### Post by njparton on 2008-02-08
Use ssh if you just need the command line or vnc if you need to see the desktop.  Gnome comes with a vnc server built in which can be enabled under the admin menu (session option?).

Then you just need to install a vnc client on your other PC. Check out "xming" if the other PC is running windows.

If you go with ssh, install the ssh server from the repos in ubuntu and use putty as the ssh client in windows.  Otherwise, from an ubnutu client you can log in via:

```
ssh username@ipaddress
```

eg

```
ssh bob@192.168.1.2
```

---

### Post by doddo on 2008-02-08
Hello!
You could use telnet, but nowdays people use ssh instead, because it is more secure. 

The difference is that with ssh, your connection is encrypted, all traffic too.

to set this up, pop up one of those terminals and type
```
 $ sudo apt-get install ssh
$ sudo /etc/init.d/ssh start

```
ths init.d/ssh is the daemon script for the ssh server. 
Each computer you have started a server like that, does now listen for TCP connections on port 22 (make sure that port is accessible)

to log into other computers
```
 ssh your_user@other.computer
```

other.computer can be replaced with the hostname or IP of target comuter.
your_user can be replaced with the name of an existing computer on the server box.


Have fun but beware: There are some security issues with weak passwords and ssh. Make sure u set a real good password, because remote machines will target you with dictionary attacks (this happens to all of us, just make sure to set a good password for your users).

---

### Post by njparton on 2008-02-08
> **doddo said:**
> Hello!
You could use telnet, but nowdays people use ssh instead, because it is more secure. 

The difference is that with ssh, your connection is encrypted, all traffic too.

to set this up, pop up one of those terminals and type
```
 $ sudo apt-get install ssh
$ sudo /etc/init.d/ssh start

```
ths init.d/ssh is the daemon script for the ssh server. 
Each computer you have started a server like that, does now listen for TCP connections on port 22 (make sure that port is accessible)

to log into other computers
```
 ssh your_user@other.computer
```

other.computer can be replaced with the hostname or IP of target comuter.
your_user can be replaced with the name of an existing computer on the server box.


Have fun but beware: There are some security issues with weak passwords and ssh. Make sure u set a real good password, because remote machines will target you with dictionary attacks (this happens to all of us, just make sure to set a good password for your users).

Isn't it:

```
sudo apt-get install openssh
```

---

### Post by kenvac on 2008-02-08
install ssh and try to connect two linux desktop with ssh....... if u want to do networking with linux and windows do it with installing samba server on linux machine....

---

### Post by nebu on 2008-02-08
> **doddo said:**
> Hello!
You could use telnet, but nowdays people use ssh instead, because it is more secure. 

The difference is that with ssh, your connection is encrypted, all traffic too.

to set this up, pop up one of those terminals and type
```
 $ sudo apt-get install ssh
$ sudo /etc/init.d/ssh start

```
ths init.d/ssh is the daemon script for the ssh server. 
Each computer you have started a server like that, does now listen for TCP connections on port 22 (make sure that port is accessible)

to log into other computers
```
 ssh your_user@other.computer
```

other.computer can be replaced with the hostname or IP of target comuter.
your_user can be replaced with the name of an existing computer on the server box.


Have fun but beware: There are some security issues with weak passwords and ssh. Make sure u set a real good password, because remote machines will target you with dictionary attacks (this happens to all of us, just make sure to set a good password for your users).

thnx...... the ssh server worked perfectly

---

### Post by trig on 2008-02-09
i know this may seem retarded but i cant get samba to run. Im tring to connect 2 windows compys to my linux.   this is what i have tried.
trig@trig-desktop:~$ man smb.con
No manual entry for smb.con
trig@trig-desktop:~$ sudo apt-get install ssh
[sudo] password for trig:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 libxvidcore4 libmp4v2-0 libx264-54 libmjpegtools0c2a libsidplay1
  libquicktime1 libfaac0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openssh-server
Suggested packages:
  rssh molly-guard
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 249kB of archives.
After unpacking 688kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  openssh-server ssh
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main openssh-server 1:4.6p1-5ubuntu0.1 [247kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main ssh 1:4.6p1-5ubuntu0.1 [1098B]
Fetched 249kB in 1s (125kB/s)          
Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 117633 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.6p1-5ubuntu0.1_i386.deb) ...
Selecting previously deselected package ssh.
Unpacking ssh (from .../ssh_1%3a4.6p1-5ubuntu0.1_all.deb) ...
Setting up openssh-server (1:4.6p1-5ubuntu0.1) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd                           [ OK ] 

Setting up ssh (1:4.6p1-5ubuntu0.1) ...

trig@trig-desktop:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                             [ OK ] 
trig@trig-desktop:~$ sudo chmod u+s /usr/bin/smbmnt /usr/bin/smbumount
chmod: cannot access `/usr/bin/smbmnt': No such file or directory
chmod: cannot access `/usr/bin/smbumount': No such file or directory
trig@trig-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release [44.0kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages [22.3kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [70.1kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages [14B]     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages [74.6kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [152kB]        
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages [6660B]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [34.1kB]        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [64.3kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [12.3kB]      
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources [10.2kB]    
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [9942B]  
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [1883B]   
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]      
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [42.1kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [5908B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2903B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]
Fetched 671kB in 6s (112kB/s)                                                  
Reading package lists... Done
trig@trig-desktop:~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 libxvidcore4 libmp4v2-0 libx264-54 libmjpegtools0c2a libsidplay1
  libquicktime1 libfaac0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  smbfs
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 485kB of archives.
After unpacking 1126kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main smbfs 3.0.26a-1ubuntu2.3 [485kB]
Fetched 485kB in 3s (138kB/s) 
Selecting previously deselected package smbfs.
(Reading database ... 117646 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.26a-1ubuntu2.3_i386.deb) ...
Setting up smbfs (3.0.26a-1ubuntu2.3) ...
trig@trig-desktop:~$ sudo chmod u+s /usr/bin/smbmnt /usr/bin/smbumount
trig@trig-desktop:~$ sudo `s
> mkdir /mnt/data
> 
>  ssh [email]your_user@other.comp[/email]uter
>  ssh [email]your_user@other.comp[/email]uter
> sudo apt-get install openssh
> 


any ideas on what i am doing wrong
trig

---

### Post by nebu on 2008-02-10
are u trying to just acess files or are u tryin to get shell acess.....

if u r trying to get acess to ur files on a pc which has ubuntu from one that has windows.... try this.....
[http://ubuntuforums.org/showthread.php?p=4228646](http://ubuntuforums.org/showthread.php?p=4228646)

i had written how exactly to get it done

---


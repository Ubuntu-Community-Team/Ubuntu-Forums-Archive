---
title: "Package install problems"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by mattgsx on 2007-02-13
I tried installing the vmware package using the apt-get line command (cut-pasted from the wiki), and the installation failed. I'm not too worried about that, but every time I try downloading another package, the vmware installation kicks back in. I can't update my computer, install new packages, or even remove existing ones because the computer tries resolving the vmware issue first, and that usually causes my computer to hang and sometimes lock up. Is there a command that I can clear that out, so it doesn't keep trying to run that installation?

Thanks!

---

### Post by taurus on 2007-02-13
Can you post the whole message when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by mattgsx on 2007-02-13
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [62.1kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources  
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [64.0kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [5689B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [3785B]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [31.9kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [12.3kB]           
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [923B]       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources [430B]       
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3432B]     
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]         
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages [14B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages [10.7kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [19.7kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources [871B]
Fetched 306kB in 3s (96.8kB/s)                  
Reading package lists... Done

---

### Post by taurus on 2007-02-13
And now what happens when you run the next command?

```
sudo aptitude upgrade
```

---

### Post by mattgsx on 2007-02-13
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.157.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] no

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...



The subnet 192.168.33.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.192.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.199.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while process

---

### Post by taurus on 2007-02-13
What if you remove it with

```
sudo aptitiude --purge remove vmware-player
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mattgsx on 2007-02-13
That did it. Thanks!

---


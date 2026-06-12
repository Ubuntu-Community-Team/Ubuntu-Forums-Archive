---
title: "error after changing domain name in Xubuntu"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2007-12-27
I used the Network Manager in Xubuntu to change the Domain Name of my Xubuntu box to match that of my Ubuntu box, but I have since been getting an error whenever i load Xubuntu.  It goes something like "Could not look up internet address for <name>.  This will prevent Xfce from operating correctly.  Yada Yada /etc/hosts on your system."

Anyway, I checked my /etc/hosts file and my /etc/hostname files against those of my Ubuntu box and updated them to the same format:

hosts
```
127.0.0.1 localhost
127.0.1.1 <name>**.**<domain>

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

hostname
```
<name>
```

I also checked to make sure the 'Hosts" tab of the network manager was reporting the same information.  This setup on the Ubuntu box was able to access SMB shares on the Xubuntu box before I reinstalled it (Xubuntu).  However, I was getting the error on the Xubuntu box then too and at some point one of my share folders stopped allowing me to write to it across the network.  Strangely, although I can't see the Xubuntu box in the Network browser, the shortcut to the previous Xubuntu install 'works.'  That is, I can connect to smb://<name> see the newly created share folders, and open/copy files, but I can't write to them despite them not being marked read only.  I get ```
Error "Access denied" while copying "blahblahblah-yackety.schmackety"
```  Any help would be greatly appreciated.

---

### Post by bone2006 on 2007-12-27
it's probably ownership.  You copied a folder, file with another owner?
open up a terminal and type chown user:group to change the ownership to what you want.  If you could careless about protection
sudo chmod 777 to the directory, and a -R to recursively change everything to 777, which gives everybody all access to what your changing.  Probably not a good idea, so look into changing the status

Type stat and the name of the file to see who owns it, the premissions..etc

---

### Post by alphaniner on 2007-12-27
The permission/ownership is not really the heart of the issue.  The problem is with the networking/domain.

---


---
title: "I don't think apt-get is working..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Nexus... on 2007-08-05
When I go into terminal and enter "sudo apt-get update" this is what is displayed. It all seems fine other than the parts I have made red, could someone tell me whether or not I should do something about it and if so how?

nexus@Venom:~$ sudo apt-get update
Password:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_GB
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages [1307kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources [385kB]
99% [7 Packages gzip 0]
[COLOR="Red"]gzip: stdin: not in gzip format
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
  Sub-process gzip returned an error code (1)
99% [8 Sources gzip 0] 
gzip: stdin: not in gzip format
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
  Sub-process gzip returned an error code (1)
Fetched 8B in 0s (9B/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]
nexus@Venom:~$ 

Future thanks and help is greatly appreciated.

EDIT - Also just found out I cannot install "Alien" or "Amarok" and many other things as I keep getting:

ALIEN
nexus@Venom:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alien is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alien has no installation candidate
nexus@Venom:~$ 

AMAROK
nexus@Venom:~$ sudo apt-get install amarok
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

The following packages have unmet dependencies.
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: ruby but it is not installable
          Depends: python-qt3 but it is not installable
          Depends: kdebase-kio-plugins but it is not going to be installed
          Depends: kdelibs4c2a (>= 4:3.5.5-1) but it is not installable
          Depends: libifp4 but it is not installable
          Depends: libmtp5 (>= 0.1.3) but it is not installable
          Depends: libmysqlclient15off (>= 5.0.27-1) but it is not installable
          Depends: libnjb5 but it is not installable
          Depends: libruby1.8 (>= 1.8.5) but it is not installable
          Depends: libtunepimp5 but it is not installable
E: Broken packages
nexus@Venom:~$

---

### Post by fimbulvetr on 2007-08-05
The server "gb.archive..." is probably just down for the moment, try again later (Several hours or even a day) and paste back if it's the same thing.

---

### Post by dreadlord_chris on 2007-08-05
that's telling you that there is a problem with the package lists from those 2 repos...
there's nothing wrong with your apt-get

---

### Post by insane_alien on 2007-08-05
i'm on the same servers you are on and i'm getting everythring through fine.

---

### Post by Nexus... on 2007-08-05
So the best thing I can do is wait?

EDIT - It's ok now I switched to the Main Server instead of using the one hosted in the United Kingdom thanks for the support guys :)

---


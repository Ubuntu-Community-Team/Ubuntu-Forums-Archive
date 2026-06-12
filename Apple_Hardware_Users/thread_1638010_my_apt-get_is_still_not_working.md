---
title: "my apt-get is still not working"
date: 2010-12-05
forum: Apple Hardware Users
---

### Post by johnbendie on 2010-12-05
after trying to change my server from Main to US servers and back my apt-get update still persistently returns errors and 404. I have checked the url it uses and have found there is no directory for binary-powerpc in the maverick/multiverse folder. what is the current folder to use for apt-get in the software-sources list. here i paste the error message i get when i run apt-get update:

chijioke@opportunity-pc:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation- en      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick Release.gpg                               
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation- en        
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation-en         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US.UTF-8
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation- en         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation-en_US      
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation-en_US.UTF-8
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation- en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation- en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US.UTF-8 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation- en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US.UTF-8
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation- en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation-en_US.UTF-8
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation- en  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner powerpc Packages             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US.UTF-8
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation- en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US.UTF-8
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation- en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation-en_US.UTF-8
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US.UTF-8
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation- en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation-en_US.UTF-8
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick Release                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation- en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US.UTF-8
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US.UTF-8
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                    
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/universe powerpc Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/main powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/restricted powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/multiverse powerpc Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main powerpc Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe powerpc Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main powerpc Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main powerpc Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse powerpc Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse powerpc Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main powerpc Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main powerpc Packages
  404  Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe powerpc Packages
  404  Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted powerpc Packages
  404  Not Found [IP: 91.189.92.169 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe powerpc Packages
  404  Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse powerpc Packages
  404  Not Found [IP: 91.189.92.169 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse powerpc Packages
  404  Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main powerpc Packages
  404  Not Found [IP: 91.189.92.169 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-powerpc/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-powerpc/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-powerpc/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-powerpc/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-powerpc/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-powerpc/Packages.gz)  404  Not Found [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by linuxopjemac on 2010-12-05
post your /etc/apt/sources.list file pls

---

### Post by johnbendie on 2010-12-05
> **linuxopjemac said:**
> post your /etc/apt/sources.list file pls

here it is:

# 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release powerpc (20101008)]/ maverick main restricted

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release powerpc (20101008)]/ maverick main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe restricted multiverse main
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick universe main restricted multiverse

thanks

---

### Post by linuxopjemac on 2010-12-05
have a look here:
[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)

replace lucid by maverick

---

### Post by johnbendie on 2010-12-05
> **linuxopjemac said:**
> have a look here:
[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)

replace lucid by maverick

thanks. apt-get update works just fine now. I'll mark thread as solved.

---


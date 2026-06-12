---
title: "questions"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-12-20
Hi well ok i am still new to this but finding my feet quite ok they are just a few gremlins that need to be worked out and here is were i need some help.

Ok the first one i cant to download anything from synaptic package manager i get a error 

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.3.0.0debian1-4build1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-6_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/universe/3/3ddesktop/3ddesktop_0.2.9-6_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]
 
Second error i can see the upgrade button but when i click it tells me 
authentication failed my internet is fine i using the same laptop to get to this website

I really need some help here....

---

### Post by PmDematagoda on 2007-12-20
Could you post the result of:-
```

sudo apt-get update
```

---

### Post by crazysexycool on 2007-12-20
cheeseboi@cheeseboi-laptop:~$ sudo apt-get update
Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/universe Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security Release                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/multiverse Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Sources               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/multiverse Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/main Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/restricted Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/restricted Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/main Sources                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/multiverse Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/universe Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/universe Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-security/multiverse Packages           
Fetched 4B in 9s (0B/s)                                                        
Reading package lists... Done
cheeseboi@cheeseboi-laptop:~$

---

### Post by PmDematagoda on 2007-12-20
That seems to have worked without problems, try and see if your problem has now been solved.

---

### Post by crazysexycool on 2007-12-20
It works in a terminal window but not in synaptic 

could it be that i am using a wireless card when at home to get onto the net and the proxy when i am at work 

Here is the error i got now 

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2-dev_2.1.30-13.3_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/o/openldap2/libldap2-dev_2.1.30-13.3_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_1.95.8-3.4build1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1-dev_1.95.8-3.4build1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/d/db4.4/libdb4.4-dev_4.4.20-8ubuntu2_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/d/db4.4/libdb4.4-dev_4.4.20-8ubuntu2_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.04.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.04.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3-dev_7.4-0ubuntu0.7.04.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3-dev_7.4-0ubuntu0.7.04.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/uuid-dev_1.2-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/uuid-dev_1.2-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1-dev_1.2.7-8.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1-dev_1.2.7-8.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/libsqlite3-dev_3.3.13-0ubuntu1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/libsqlite3-dev_3.3.13-0ubuntu1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3-13ubuntu4_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3-13ubuntu4_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.2_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.2_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm55_1.4.4-5ubuntu3.3_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm55_1.4.4-5ubuntu3.3_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/comerr-dev_2.1-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/comerr-dev_2.1-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.4.4-5ubuntu3.3_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.4.4-5ubuntu3.3_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq-dev_8.2.5-0ubuntu0.7.04.1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq-dev_8.2.5-0ubuntu0.7.04.1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-dev_1.2.7+dfsg-2build1_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-dev_1.2.7+dfsg-2build1_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-threaded-dev_2.2.3-3.2ubuntu2_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-threaded-dev_2.2.3-3.2ubuntu2_i386.deb)
  407 Proxy Authentication Required [IP: 172.28.11.134 8080]

---


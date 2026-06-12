---
title: "[SOLVED] update issue"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by crazysexycool on 2007-10-05
This is the error i get when i try to get updates any ideas PLEASe HELP!!!


cheeseboi@cheeseboi-laptop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_ZA      
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_ZA            
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_ZA      
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_ZA          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty Release.gpg                            
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/main Translation-en_ZA                 
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_ZA        
  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/restricted Translation-en_ZA           
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/universe Translation-en_ZA             
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_ZA
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty/multiverse Translation-en_ZA
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/main Translation-en_ZA
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) feisty-updates/restricted Translation-en_ZA
  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_ZA
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_ZA
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.137.129). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused) [IP: 91.189.88.37 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_ZA.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_ZA.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_ZA.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_ZA.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (111 Connection refused) [IP: 91.189.89.6 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
cheeseboi@cheeseboi-laptop:~$

---

### Post by overdrank on 2007-10-05
HI do you have internet access?

---

### Post by crazysexycool on 2007-10-05
yes i do i am using the same pc to send this message over the net

---

### Post by overdrank on 2007-10-05
> **crazysexycool said:**
> yes i do i am using the same pc to send this message over the net

Ok you may try, go to system, administration, sources and change which server you are using.

---

### Post by Anicka on 2007-10-05
I think the server might be "tired". Today was a big update for openoffice (20 packages I think). It took me 45 minutes to download it from the Swiss server which was only uploading at ~25kB/sec. This always happen when there is a big update, but by tomorrow it should be better.

My advise would be: patience...

---

### Post by crazysexycool on 2007-10-05
same error i did what you said

---

### Post by n3tfury on 2007-10-05
he/she was saying you might want to wait a bit longer because it seems that the servers are getting hit with so many requests that it might timeout for some users.  i've never had this happen, but am only speculating.

---

### Post by crazysexycool on 2007-10-05
the problem is that i keep getting this  error this isnt the first time

---


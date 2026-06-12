---
title: "can not update, nor install new programs"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-04
After I enter sudo apt-get update...
the following appears
E: dpkg was interrupted, you mush manually run 'dpkg ---configure - a' tro correct the problem.
Same happens when I try to use synaptic, and add programs.

Anybody got any suggestions?
have an amazing day....

---

### Post by mostwanted on 2006-06-04
Have you tried running the command it tells you about?

Anyway, try to use the broken packages filter in Synaptic and see if anything shows up. If a package is broken, try removing it.

---

### Post by mostwanted on 2006-06-04
*double post

---

### Post by catlett on 2006-06-04
Open the terminal and enter ```
dpkg ---configure - a
``` Let it run and try the apt-get update again and see if that cleared the error.

P.S. Use the exact lettering from the error prompt. This looks a little off and I'm wondering if you cut/pasted the reply from the error or did it by hand and made a typo. It doesn't matter here but it will in the terminal. 
I am just cutting/pasting from your post so don't go by my reply. Enter the command inside the quotes from your error prompt.

P.S. Didn't see the previous post. Anyone else getting real slow server response? It's taking me a minute or more to change pages.

---

### Post by wannabesurfer on 2006-06-04
it does give me this reply
dpkg: requested operation requires superuser privilige.
I also checked synaptic for broken, but everything looks fine.

---

### Post by catlett on 2006-06-04
```
sudo dpkg ---configure - a
``` Sorry about that. Since the error didn't mention it I didn't think of it. Sudo is used in Ubuntu to invoke root priveleges (like administrative in windows) Sudo is short for "superuser do". So if you see " requires superuser priveleges" it means put sudo before the command. When it asks for a password, use the password you log on with.

---

### Post by kenny1948 on 2007-11-05
OK I'm having problems too. Heres what happens when I try to run apt-get update:


$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://www.debian-multimedia.ort](http://www.debian-multimedia.ort) etch Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg                            
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://www.debian-multimedia.ort](http://www.debian-multimedia.ort) etch/main Translation-en_US               
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://www.debian-multimedia.ort/dists/etch/Release.gpg](http://www.debian-multimedia.ort/dists/etch/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://www.debian-multimedia.ort/dists/etch/main/i18n/Translation-en_US.bz2](http://www.debian-multimedia.ort/dists/etch/main/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
kenny1948@kenny1948-desktop:~$ 

So what gives, anybody have any ideas?

---


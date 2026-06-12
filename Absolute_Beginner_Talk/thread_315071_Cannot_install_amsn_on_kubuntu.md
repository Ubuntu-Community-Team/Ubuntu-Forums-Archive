---
title: "Cannot install amsn on kubuntu"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by VenQWish on 2006-12-08
Hi all, I'm not new to computers, but I am totally brand spanking new to linux.

First I installed ubuntu, then changed it gnome to kde. Then I wanted to get amsn. 

I always saw these two commands as the way to go:

```
sudo apt-get update
sudo apt-get install amsn
```

However, I get stuck at "sudo apt-get update". It says the following:

> venqwish@venqwish-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) kubuntu Release.gpg [189B]                   
Ign [http://www.getautomatix.com](http://www.getautomatix.com) kubuntu/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) kubuntu Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://www.getautomatix.com](http://www.getautomatix.com) kubuntu/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources              
99% [Connecting to be.archive.ubuntu.com (195.238.1.5)] 

And then it just stays there, my internet connection works fine. I also tried to download a package file from amsn, but I have no clue what to do with it, clicking it opens it in some editor I guess. So well.. I'm pretty much stuck, can I use anything else? In the gnome add/remove programs, amsn shows up, but it doesn't when I'm in the kde add/remove program :/.

Thx for any help.

---

### Post by mahy on 2006-12-08
Maybe the server is screwed up. Replace the "be" for something else; "nl" and "fr" are probably the best options due to geographic proximity.

EDIT: You have to replace it in /etc/apt/sources.list

---

### Post by VenQWish on 2006-12-09
Thx, I just changed the repositories to US server in the setting, no problems anymore.

---


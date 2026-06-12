---
title: "problem adding universe and multiverse repositories"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-11
I went to the following link to follow instructions, but I dont have the software properties under system.  I'm using Edgy Eft. WHat do I do to add universe and multiverse repositories? 

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by taurus on 2007-02-11
Do it the old fashion way, from a terminal.

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list   /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
And remove the # sign in front of all the lines with deb.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by r4ik on 2007-02-11
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

From,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Ceta on 2007-02-11
When I paste in the first part of the code in the terminal, I get the following error:

(gedit:14809): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by taurus on 2007-02-11
> **Ceta said:**
> When I paste in the first part of the code in the terminal, I get the following error:

(gedit:14809): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

But does a window open with /etc/apt/sources.list?

---

### Post by Ceta on 2007-02-11
No, it just gives that error in the terminal. Doesnt bring any other window up.

---

### Post by aysiu on 2007-02-11
> **Ceta said:**
> No, it just gives that error in the terminal. Doesnt bring any other window up.
So this is what you're seeing? ```
ceta@ubuntu:~$ gksudo gedit /etc/apt/sources.list
(gedit:14809): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ceta@ubuntu:~$
```

---

### Post by Ceta on 2007-02-11
When i type in /etc/apt/sources.list I get the following:
bash: /etc/apt/sources.list: Permission denied

---

### Post by Ceta on 2007-02-11
Aysiu, yes, thats what I get when i put in the following:
sudo cp /etc/apt/sources.list   /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list

---

### Post by aysiu on 2007-02-11
That's weird. It shouldn't just go to the next line.

What about if you do this? ```
sudo nano /etc/apt/sources.list
``` Same thing? It goes to the next line? Or does it open up /etc/apt/sources.list with a terminal-based text editor?

---

### Post by Ceta on 2007-02-11
That brings up a text editor, Aysiu, but I cant figure out how to delete the # signs.

---

### Post by taurus on 2007-02-11
> **Ceta said:**
> That brings up a text editor, Aysiu, but I cant figure out how to delete the # signs.

Move around with the arrow keys and delete with the Backspace.  Save the changes by holding down <Ctrl> while pressing x.  Answer the question with Y and Return.

---

### Post by Ceta on 2007-02-11
Okay, I did that, then I put in sudo aptitude update then sudo aptitude upgrade.  I think it worked, but how can I find out for sure?

---

### Post by taurus on 2007-02-11
Why don't you paste the complete outputs here.  Then, we will know for sure.

---

### Post by Ceta on 2007-02-11
The outputs to what?

---

### Post by taurus on 2007-02-11
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Ceta on 2007-02-11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 4B in 2s (2B/s)  
Reading package lists... Done
rain@the-cube:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by taurus on 2007-02-11
I would edit /etc/apt/sources.list again and remove the **ca.** from all the repos.  Then, run those two commands again.

---

### Post by Ceta on 2007-02-11
Take the ca out from where? The urls?

---

### Post by taurus on 2007-02-11
> **Ceta said:**
> Take the ca out from where? The urls?

You know what, don't worry about the ca.  Forget what I just said then.

---

### Post by Ceta on 2007-02-11
It's too late. I already did it.  Here are the results now.

rain@the-cube:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US            
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release                               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [38.4kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]               
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]                      
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [45.0kB]               
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]                 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]                
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]                 
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [64.0kB]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]         
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]          
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [19.7kB]             
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources [14B]          
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources [871B]           
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [2857B]           
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]       
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [16.0kB]      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [4824B]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [1592B]            
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]        
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [5295B]        
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [1466B]      
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [80.3kB]            
99% [32 Packages gzip 0]                                             33.8kB/s 1s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                        
  Sub-process gzip returned an error code (1)
Fetched 7192kB in 3m7s (38.4kB/s)                                               
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
rain@the-cube:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by r4ik on 2007-02-11
You could give post #3 a try.

---

### Post by jmattos on 2007-03-10
> **taurus said:**
> Do it the old fashion way, from a terminal.

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list   /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
And remove the # sign in front of all the lines with deb.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

Wait.. All of them? I just uncommented teh following one as the instructions just mentioned the universe ones..

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

```

---


---
title: "Repositary in UBUNTU"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by anuraggautam on 2007-08-08
I have install UBUNTU just now.....but please tell me how to configure the Repositary path....so that my apt-get will work.....and i am able to install all things in my system.....:guitar:

---

### Post by Vague on 2007-08-08
Which repositories are you trying to enable?  The easiest thing to do is just open up Synaptic and go to Settings>Repositories.  From there, you can decide which repositories you need to enable.  Then just click Reload and you'll be set.

If you're apt actually isn't working at all, though, that's a different problem.  Give us some more details.

---

### Post by anuraggautam on 2007-08-08
i want to run apt-get ..its not working in my system.....btwn i am behind the proxy in my school.

so please tell me what should i edit and where ?:guitar:

---

### Post by Vague on 2007-08-08
Not working how?  Do you get any error messages when you try to use it?

---

### Post by anuraggautam on 2007-08-08
yea.....its cmng ...whenever iam trying to update its coming like that 
```

anurag@TopCoder:~$ sudo apt-get update
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_IN
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com feisty Release.gpg              
Ign http://security.ubuntu.com feisty-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/main Translation-en_IN                 
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_IN    
Ign http://in.archive.ubuntu.com feisty/restricted Translation-en_IN
Ign http://security.ubuntu.com feisty-security/universe Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/universe Translation-en_IN
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com feisty/multiverse Translation-en_IN
Ign http://security.ubuntu.com feisty-security Release           
Ign http://in.archive.ubuntu.com feisty-updates Release.gpg      
Ign http://security.ubuntu.com feisty-security/main Packages     
Ign http://in.archive.ubuntu.com feisty-updates/main Translation-en_IN
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://in.archive.ubuntu.com feisty-updates/restricted Translation-en_IN
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://in.archive.ubuntu.com feisty Release                                
Ign http://security.ubuntu.com feisty-security/restricted Sources              
Ign http://in.archive.ubuntu.com feisty-updates Release          
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://in.archive.ubuntu.com feisty/main Packages            
Ign http://security.ubuntu.com feisty-security/universe Sources  
Ign http://in.archive.ubuntu.com feisty/restricted Packages      
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://in.archive.ubuntu.com feisty/main Sources             
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://in.archive.ubuntu.com feisty/restricted Sources       
Err http://security.ubuntu.com feisty-security/main Packages     
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty/universe Packages        
Err http://security.ubuntu.com feisty-security/restricted Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty/universe Sources
Err http://security.ubuntu.com feisty-security/main Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty/multiverse Packages      
Err http://security.ubuntu.com feisty-security/restricted Sources              
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty/multiverse Sources                     
Err http://security.ubuntu.com feisty-security/universe Packages 
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty-updates/main Packages    
Err http://security.ubuntu.com feisty-security/universe Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty-updates/restricted Packages
Err http://security.ubuntu.com feisty-security/multiverse Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty-updates/main Sources     
Err http://security.ubuntu.com feisty-security/multiverse Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com feisty-updates/restricted Sources
Err http://in.archive.ubuntu.com feisty/main Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/restricted Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/main Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/restricted Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/universe Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/universe Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/multiverse Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty/multiverse Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty-updates/main Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty-updates/restricted Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty-updates/main Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com feisty-updates/restricted Sources
  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  407 Proxy Authentication Required
Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by Happy_Man on 2007-08-08
You're going to have to set up your computer to talk through your school proxy.

---

### Post by anuraggautam on 2007-08-08
yea sure ...i want to run my apt-get commads.....so tell me what should i do so that it will work properly :popcorn:

---

### Post by Vague on 2007-08-08
Indeed.  Here's some information on how to do that:

[http://www.linuxforums.org/forum/debian-linux-help/55599-configuring-proxy-synaptic-package-manager-ubuntu.html](http://www.linuxforums.org/forum/debian-linux-help/55599-configuring-proxy-synaptic-package-manager-ubuntu.html)

---

### Post by anuraggautam on 2007-08-08
i have already edit that file but it is not working  properly.......whenever i am trying to update it again same problem is occurring regarding the authentications.....:guitar:

---

### Post by Vague on 2007-08-08
Hmmm.  Have you double-checked to make sure "username," "password," "proxy" and "port" are all set correctly?

---

### Post by anuraggautam on 2007-08-08
yea every thing is right....

---

### Post by Happy_Man on 2007-08-08
Oh right! I forgot. Reboot.

---


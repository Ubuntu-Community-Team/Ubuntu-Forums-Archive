---
title: "Beryl Troubles"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-02
Hey folks. I'm in the process of installing Beryl, because I like shiny things. ~LOL~
I'm using this walkthrough . . .
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)
 I've gotten to this step (Step 2) and it gives me this :
mac@mac-desktop:~$ deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
bash: deb: command not found
mac@mac-desktop:~$ deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
bash: deb: command not found
mac@mac-desktop:~$ Install your *ubuntu-desktop metapackage specific to your DE, e.g. sudo apt-get install ubuntu-desktop
bash: Install: command not found
mac@mac-desktop:~$ sudo apt-get update
Password:
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_CA     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release                       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources                             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_CA
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_CA
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_CA
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Fetched 7B in 1s (4B/s)  
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
mac@mac-desktop:~$ deb [http://beryl-mirror.pricechild.co.uk](http://beryl-mirror.pricechild.co.uk) edgy main
bash: deb: command not found
mac@mac-desktop:~$ deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
bash: deb: command not found
mac@mac-desktop:~$ deb [http://beryl.limitless.lupine.me.uk](http://beryl.limitless.lupine.me.uk) edgy main
bash: deb: command not found

Any thoughts?

---

### Post by kinematic on 2007-01-02
it says it right there..."bash:deb:command not found."....because deb is not a command.
add the repository for beryl to your sources.list,do sudo aptitude update,sudo aptitude search beryl to find the packages that you'll need and then sudo aptitude install whateveryouneed.

---

### Post by spockrock on 2007-01-02
ok what you should do is this,
```
gksudo gedit /etc/apt/sources.list
```

copy this, and add it to the bottom of the file
```

##Nvdia drivers
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable

##Beryl
deb http://ubuntu.beryl-project.org edgy main
deb-src http://ubuntu.beryl-project.org edgy main
```

save and then exit, then back in terminal do 
```
sudo apt-get update 
sudo apt-get upgrade
```

if you havent, then make sure you install the nvidia drivers, restart, and then open terminal and then enter this, and setup xorg.conf for beryl.
```
sudo apt-get install beryl
```

press alt-f2, enter "beryl-manager" no quotes, and enjoy.

---


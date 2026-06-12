---
title: "Java trouble"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by pajim17020 on 2007-11-22
I'm having problems with java. I have java 6 installed. When I try to open a page that uses java. It says "java not found or not working. I tried to reinstall it but all I got was java 5. So now I have two javas.  I'm not really sure what to do from here. Any suggestions? I don't know how to remove them. Is there a particuler version for linux?

---

### Post by taurus on 2007-11-22
How did you install it?  Did you also remember to install the plugin?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
sudo update-alternatives --config java
```

---

### Post by kleo skywalker on 2007-11-22
To remove java 5, search for sun-java5-jre in Synaptic and uninstall it. To be sure, search for sun-java5 and check if anything with java5 in the name is still installed. If it is, then uninstall it.
To install java 6, search for sun-java6-jre and install it. This also installs some related stuff.

---

### Post by pajim17020 on 2007-11-22
> **taurus said:**
> How did you install it?  Did you also remember to install the plugin?

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
sudo update-alternatives --config java
```I tried running these commands but it didn't help. Here is what I got:
jim@mycomputer:~$ sudo apt-get update                                          
[sudo] password for jim:
Sorry, try again.
[sudo] password for jim:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper Release.gpg                                
  Could not resolve 'us.archive.ubuntu'
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Err [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/universe Translation-en_US                 
  Could not resolve 'us.archive.ubuntu'
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Err [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/multiverse Translation-en_US               
  Could not resolve 'us.archive.ubuntu'
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Get:6 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US           
Ign [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/universe Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Ign [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/multiverse Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Err [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/universe Packages                          
  Could not resolve 'us.archive.ubuntu'
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources  
Err [http://us.archive.ubuntu](http://us.archive.ubuntu) dapper/multiverse Packages    
  Could not resolve 'us.archive.ubuntu'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Fetched 7B in 1s (5B/s)  
Failed to fetch [http://us.archive.ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu/dists/dapper/Release.gpg)  Could not resolve 'us.archive.ubuntu'
Failed to fetch [http://us.archive.ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu/dists/dapper/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu'
Failed to fetch [http://us.archive.ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu/dists/dapper/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu'
Failed to fetch [http://us.archive.ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu'
Failed to fetch [http://us.archive.ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jim@mycomputer:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@mycomputer:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java
          4    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
jim@mycomputer:~$ sudo update-alternatives --config java

---

### Post by taurus on 2007-11-22
What the heck did you do to your /etc/apt/sources.list?  You are running Gutsy but you have Dapper repos in there and on top of that, there is that thing called Automatix!

You need to remove anything that is not Gutsy in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by pajim17020 on 2007-11-22
> **kleo skywalker said:**
> To remove java 5, search for sun-java5-jre in Synaptic and uninstall it. To be sure, search for sun-java5 and check if anything with java5 in the name is still installed. If it is, then uninstall it.
To install java 6, search for sun-java6-jre and install it. This also installs some related stuff.

I did this and java 5 is  now gone. I checked java 6 and the plug is installed. It still doesn't work.

---

### Post by pajim17020 on 2007-11-23
> **taurus said:**
> What the heck did you do to your /etc/apt/sources.list?  You are running Gutsy but you have Dapper repos in there and on top of that, there is that thing called Automatix!

You need to remove anything that is not Gutsy in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
I don't know how that dapper stuff go in there. You guy will have to be bare with me. I know know window very well. Linux is totally new to me. 

I ran gksudo gedit /ect/apt/sources.list for some reason there is nothing there. There was a whole list a few days ago. It is gone now. The window opened but it was blank.:confused:

---

### Post by kleo skywalker on 2007-11-23
> **pajim17020 said:**
> I did this and java 5 is  now gone. I checked java 6 and the plug is installed. It still doesn't work.

Hi, this worked for me, but I hadn't made any of the changes you seem to have made - maybe that's coming in the way?
Maybe you could follow taurus's instructions and undo those changes, and then try reinstalling sun-java6-jre?

---

### Post by Elegorod on 2007-11-23
What browser do you use? If Opera, path to java must be set in Opera settings

---

### Post by taurus on 2007-11-23
> **pajim17020 said:**
> I don't know how that dapper stuff go in there. You guy will have to be bare with me. I know know window very well. Linux is totally new to me. 

I ran gksudo gedit /**[COLOR="Blue"]ect[/COLOR]**/apt/sources.list for some reason there is nothing there. There was a whole list a few days ago. It is gone now. The window opened but it was blank.:confused:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by pajim17020 on 2007-11-24
Ok, I got the sources list and removed the dapper lines. I had typed ect instead of etc. My browser is monzilla firefox 2.0.0.8. Automatix is a program I downloaded that install several programs. It worked very good. Is there problems with it? [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by skarp on 2007-11-24
Hello!
I've had about the same problem as pajim17020 with jre5 and jre6. This thread solved my problems. Thank you!

---

### Post by pajim17020 on 2007-11-24
> **skarp said:**
> Hello!
I've had about the same problem as pajim17020 with jre5 and jre6. This thread solved my problems. Thank you!
How did it solve your problem? I'm still having the problem. HELP!:(

---


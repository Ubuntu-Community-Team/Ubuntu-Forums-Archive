---
title: "Add/Remove Applications won't allow apps to be instaled"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-01-03
[SIZE="2"]Suddenly the Add/Remove Applications is not allowing me to install packages I have installed before plus many others. Here is what it says:
>  Audacity
This application is provided by the Ubuntu community.
Audacity cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type. 
I don't know where the i386 designation came from.
I get the same message for Wine, Mozilla (which I had installed before),  and a very large number of others. 

This is from the System Log Viewer (Xorg.O.log):
> Current Operating System: Linux pk-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686

I installed both the Audacity and Mozilla packages, using Add/Remove, a few days ago but have since reinstalled Ubuntu and wanted them again. The only change I've made is to GRUB's menu default from 0 to 4. I tried rebooting but that didn't help. Is there anyway to reset/refresh A/R?[/SIZE]

---

### Post by igknighted on 2007-01-03
> **Patrick K said:**
> [SIZE="2"]Suddenly the Add/Remove Applications is not allowing me to install packages I have installed before plus many others. Here is what it says:
 
I don't know where the i386 designation came from.
I get the same message for Wine, Mozilla (which I had installed before),  and a very large number of others. 

This is from the System Log Viewer (Xorg.O.log):


I installed both the Audacity and Mozilla packages, using Add/Remove, a few days ago but have since reinstalled Ubuntu and wanted them again. The only change I've made is to GRUB's menu default from 0 to 4. I tried rebooting but that didn't help. Is there anyway to reset/refresh A/R?[/SIZE]

Open the terminal and type this command:
```
sudo aptitude update
```

post the results of this if there are any issues.

after this try add/remove and see if that helps.

---

### Post by Patrick K on 2007-01-03
That did the trick! Thanks

---

### Post by snacker on 2007-01-06
This worked for me

[http://ubuntuforums.org/showthread.php?t=291302]("http://ubuntuforums.org/showthread.php?t=291302")

System -> Administration -> Software Sources -> Choose "Main Sources"

For some reason the US mirrors wouldn't work.

Also aptitude update kept failing:
> 
~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                                                                                                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US                                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US                                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                                                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                                                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages                                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources                                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                                                                                                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]                                                                                                     
99% [4 Packages gzip 0]                                                                                                                                      8087B/s 0s
[B][COLOR="Red"]gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                                                                                                
  Sub-process gzip returned an error code (1)
[/COLOR][/B]Fetched 4B in 8s (0B/s)                                                                                                                                                
Reading package lists... Done


I wish there was an FAQ for this.

---


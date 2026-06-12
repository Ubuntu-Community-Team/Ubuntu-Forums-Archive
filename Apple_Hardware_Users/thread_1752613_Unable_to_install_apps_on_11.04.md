---
title: "Unable to install apps on 11.04"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by clenny on 2011-05-08
I've upgraded to 11.04 and now I can't add any apps through Ubuntu Software Center. I select an app and then click Install. After that, I get this:

An unhandable error occured
There seems to be a programming error in aptdaemon. The software that allows you to install/remove software and to perform other package management related tasks.

Then this window pops up:

System program problem detected
Do you want to report the problem now?


Now, when I choose to report the problem, I get another window:

Sorry, the program "aptd" closed unexpectedly

If you were not doing anything confidential (entering passwords or other private information), you can help to improve the application by reporting the program.

It appears something is seriously wrong here.

Any ideas?

---

### Post by sanderd17 on 2011-05-08
do the following two command give errors?

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by jingaling on 2011-05-13
This fixed the problem for me. Thanks Sanderd17.

Jing

---

### Post by clenny on 2011-05-14
I tried it but it doesn't seem to have worked. Is there anything else I should try?

I didn't really answer  your question. The only errors I saw in the terminal were inreference to iSight tools but that is another issue. I installed a USB camera since I couldn't get the iSight tools to install.

---

### Post by sanderd17 on 2011-05-14
So can you tell me WHAT errors it gave? I should know if you have to reconfigure dpkg or purge the package you talk about or something else.

---

### Post by clenny on 2011-05-15
I'm unsure of the errors put here is the terminal output:

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
victor@victor-laptop:~$ 

And then when I ran apt-get update:

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
victor@victor-laptop:~$ 


I hope this helps.

---

### Post by sanderd17 on 2011-05-16
you ran the same code twice. the second time, it's up**gr**ade, not up**d**ate. I know it's easy to misread, but since the error happens in the second command, I need to see it.

PS. Please post the output between CODE tags (click on the #)

---

### Post by clenny on 2011-05-19
Here is the output after running apt-get upgrade. Thanks for taking a look.

[CODE]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  isight-firmware-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
69 not fully installed or removed.
Need to get 0 B/33.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 249176 files and directories currently installed.)
Preparing to replace isight-firmware-tools 1.4.2-3 (using .../isight-firmware-tools_1.4.2-4_i386.deb) ...
Unpacking replacement isight-firmware-tools ...
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: error processing /var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for install-info ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pauljwells on 2011-05-20
Hi
First - you need to start the code with "CODE" and **end** with "/CODE"! (both in square braces)

It does look like the iSight firmware is screwing up and this stops anything else from happening.

Try:

```
sudo apt-get --purge remove isight-firmware-tools
```

then run the commands that sanderd17 gave you. Post all your output!

---

### Post by clenny on 2011-05-24
I ran the code you gave me in the Terminal and got an interesting result. Before I try reinstalling like it suggests I wanted to get your input.

```
sudo apt-get --purge remove isight-firmware-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  isight-firmware-tools*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
69 not fully installed or removed.
After this operation, 229 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing isight-firmware-tools (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 isight-firmware-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
victor@victor-laptop:~$ 
```

So I take it wasn't removed, correct?

I decided to run those commands just in case:

```
sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
victor@victor-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  binutils glib-networking isight-firmware-tools libapr1 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4
22 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
69 not fully installed or removed.
Need to get 17.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse isight-firmware-tools i386 1.4.2-4 [33.4 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main binutils i386 2.21.0.20110327-2ubuntu3 [2,170 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main glib-networking i386 2.28.6.1-0ubuntu1 [30.2 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libapr1 i386 1.4.2-7ubuntu2.1 [79.7 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-svg i386 4:4.7.2-0ubuntu6.1 [138 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-qt3support i386 4:4.7.2-0ubuntu6.1 [1,044 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-scripttools i386 4:4.7.2-0ubuntu6.1 [225 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-opengl i386 4:4.7.2-0ubuntu6.1 [286 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-help i386 4:4.7.2-0ubuntu6.1 [194 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-declarative i386 4:4.7.2-0ubuntu6.1 [954 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqtgui4 i386 4:4.7.2-0ubuntu6.1 [3,992 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-designer i386 4:4.7.2-0ubuntu6.1 [3,683 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-script i386 4:4.7.2-0ubuntu6.1 [829 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-xmlpatterns i386 4:4.7.2-0ubuntu6.1 [1,070 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-network i386 4:4.7.2-0ubuntu6.1 [469 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-dbus i386 4:4.7.2-0ubuntu6.1 [193 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-xml i386 4:4.7.2-0ubuntu6.1 [93.6 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql-sqlite i386 4:4.7.2-0ubuntu6.1 [24.7 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql-mysql i386 4:4.7.2-0ubuntu6.1 [31.8 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql i386 4:4.7.2-0ubuntu6.1 [98.8 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-test i386 4:4.7.2-0ubuntu6.1 [58.1 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libqtcore4 i386 4:4.7.2-0ubuntu6.1 [1,825 kB]
Fetched 17.5 MB in 25s (686 kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package isight-firmware-tools.
(Reading database ... 249176 files and directories currently installed.)
Preparing to replace isight-firmware-tools 1.4.2-3 (using .../isight-firmware-tools_1.4.2-4_i386.deb) ...
Unpacking replacement isight-firmware-tools ...
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: error processing /var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Preparing to replace binutils 2.21.0.20110327-2ubuntu2 (using .../binutils_2.21.0.20110327-2ubuntu3_i386.deb) ...
Unpacking replacement binutils ...
Preparing to replace glib-networking 2.28.5-0ubuntu1 (using .../glib-networking_2.28.6.1-0ubuntu1_i386.deb) ...
Unpacking replacement glib-networking ...
Preparing to replace libapr1 1.4.2-7ubuntu2 (using .../libapr1_1.4.2-7ubuntu2.1_i386.deb) ...
Unpacking replacement libapr1 ...
Preparing to replace libqt4-svg 4:4.7.2-0ubuntu6 (using .../libqt4-svg_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-svg ...
Preparing to replace libqt4-qt3support 4:4.7.2-0ubuntu6 (using .../libqt4-qt3support_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-qt3support ...
Preparing to replace libqt4-scripttools 4:4.7.2-0ubuntu6 (using .../libqt4-scripttools_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-scripttools ...
Preparing to replace libqt4-opengl 4:4.7.2-0ubuntu6 (using .../libqt4-opengl_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-opengl ...
Preparing to replace libqt4-help 4:4.7.2-0ubuntu6 (using .../libqt4-help_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-help ...
Preparing to replace libqt4-declarative 4:4.7.2-0ubuntu6 (using .../libqt4-declarative_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-declarative ...
Preparing to replace libqtgui4 4:4.7.2-0ubuntu6 (using .../libqtgui4_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqtgui4 ...
Preparing to replace libqt4-designer 4:4.7.2-0ubuntu6 (using .../libqt4-designer_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-designer ...
Preparing to replace libqt4-script 4:4.7.2-0ubuntu6 (using .../libqt4-script_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-script ...
Preparing to replace libqt4-xmlpatterns 4:4.7.2-0ubuntu6 (using .../libqt4-xmlpatterns_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-xmlpatterns ...
Preparing to replace libqt4-network 4:4.7.2-0ubuntu6 (using .../libqt4-network_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-network ...
Preparing to replace libqt4-dbus 4:4.7.2-0ubuntu6 (using .../libqt4-dbus_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-dbus ...
Preparing to replace libqt4-xml 4:4.7.2-0ubuntu6 (using .../libqt4-xml_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-xml ...
Preparing to replace libqt4-sql-sqlite 4:4.7.2-0ubuntu6 (using .../libqt4-sql-sqlite_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-sql-sqlite ...
Preparing to replace libqt4-sql-mysql 4:4.7.2-0ubuntu6 (using .../libqt4-sql-mysql_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-sql-mysql ...
Preparing to replace libqt4-sql 4:4.7.2-0ubuntu6 (using .../libqt4-sql_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-sql ...
Preparing to replace libqt4-test 4:4.7.2-0ubuntu6 (using .../libqt4-test_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqt4-test ...
Preparing to replace libqtcore4 4:4.7.2-0ubuntu6 (using .../libqtcore4_4%3a4.7.2-0ubuntu6.1_i386.deb) ...
Unpacking replacement libqtcore4 ...
Processing triggers for install-info ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/isight-firmware-tools_1.4.2-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
victor@victor-laptop:~$

---

### Post by sanderd17 on 2011-05-25
try the following:

```

sudo dpkg reconfigure -a
sudo apt-get --purge remove isight-firmware-tools

```

Hopefully dpkg can solve this.

---

### Post by pauljwells on 2011-05-26
> **clenny said:**
> 
 Package is in a **very bad** inconsistent state - you should
 reinstall it before attempting a removal.

Crumbs! How on earth did you manage to cause this much damage? ;-) I've never seen that error before!! To be perfectly honest, this is beyond me now. In your position I would reinstall from scratch... It looks like sanderd17 is more knowledgeable than me so I have to sign off and leave you in his hands. Good luck...

---

### Post by sanderd17 on 2011-05-27
> **pauljwells said:**
> Crumbs! How on earth did you manage to cause this much damage? ;-) I've never seen that error before!! To be perfectly honest, this is beyond me now. In your position I would reinstall from scratch... It looks like sanderd17 is more knowledgeable than me so I have to sign off and leave you in his hands. Good luck...

I have seen that before. You can get it when you suddenly interrupt the installation process. Normally, trying different reconfigure commands can solve the problem.

---

### Post by clenny on 2011-05-27
This is what I got when I typed in the first  command:

```
sudo dpkg reconfigure -a
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
 
```

I'm considering starting over but I'll wait and see what else I might be able to try.

---

### Post by sanderd17 on 2011-05-28
Sorry, my fault, it's

```

sudo dpkg --configure -a

```

And if that doesn't work, try 

```

sudo dpkg --purge --force-all isight-firmware-tools

```

After that, update your apt-get with the commands from the beginning.

---

### Post by clenny on 2011-05-29
I ran both commands. When I ran the second one I got this:

```
sudo dpkg --purge --force-all isight-firmware-tools
[sudo] password for victor: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 249174 files and directories currently installed.)
Removing isight-firmware-tools ...
rm: cannot remove `/lib/firmware/isight.fw': Is a directory
dpkg: error processing isight-firmware-tools (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Errors were encountered while processing:
 isight-firmware-tools
 
```

This is turning out to be pretty complicated, yes?

---

### Post by sanderd17 on 2011-05-29
Ok, since dpkg can not remove that file (it complains it's a directory), just remove it by hand and create an empty file (so dpkg can remove it)

```

sudo rm -r /lib/firmware/isight.fw
sudo touch /lib/firmware/isight.fw

```

then try the previous commands again.

---

### Post by clenny on 2011-06-01
Thank you sander17. That worked. I like using Linux. I wish I knew more about how to troubleshoot it rather than learn by trial and error like this. We'll keep after it and see what develops.

---

### Post by shamz_71 on 2011-06-02
> **sanderd17 said:**
> Sorry, my fault, it's

```

sudo dpkg --configure -a

```And if that doesn't work, try 

```

sudo dpkg --purge --force-all isight-firmware-tools

```After that, update your apt-get with the commands from the beginning.

i have the same problm , i cant download anything from the software centre anything and i get the same error that Mr Bean got.

I m the newest Ubuntu user ,just switched over from win7 and i ve no idea what to do. 100% pure newbie.

when i ran these 2 commands in terminal i got this 

farooq@KhalidTank:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process
farooq@KhalidTank:~$ sudo dpkg --purge --force-all isight-firmware-tools
dpkg: error: dpkg status database is locked by another process



also when typing this , screen gets scrolled up and down automatically and sometimes it switches to some other option

---

### Post by shamz_71 on 2011-06-02
Oh even i m bean , dint know this. i meant i ve the same problem as clenny

---

### Post by sanderd17 on 2011-06-02
Oh well, it's not that difficult. You just have to search the right tools (for package management, you can use apt-get, aptitude and the backend dpkg), then you ask the manual of those tools with the man command. You search things that interest you (in this case repairing a broken package or removing it) and you try it. If you're lucky, you'll get a helpful error message with a hint. 

In this case, the first hint came from apt, about removing one specific package and the second hint from dpkg about some file that could not be removed. So creating an empty stub file worked.

Not everything must be done via the command line, but it's just easier to copy-paste an "rm" command than to describe what you have to remove and how.

---

### Post by shamz_71 on 2011-06-02
listen , just tell me the steps i need to follow. i have no idea whats packages,right tools,dpkg.
i have same problm like clenny , downloading error.

---

### Post by sanderd17 on 2011-06-02
> **shamz_71 said:**
> i have the same problm , i cant download anything from the software centre anything and i get the same error that Mr Bean got.

I m the newest Ubuntu user ,just switched over from win7 and i ve no idea what to do. 100% pure newbie.

when i ran these 2 commands in terminal i got this 

farooq@KhalidTank:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process
farooq@KhalidTank:~$ sudo dpkg --purge --force-all isight-firmware-tools
dpkg: error: dpkg status database is locked by another process



also when typing this , screen gets scrolled up and down automatically and sometimes it switches to some other option

the packages database can not be edited by two programs at the time, so close all programs that have something to do with package management (installing, updating ...) and try again.

If that doesn't work, log out and back in and try agian or reboot and try again.

I don't think your problem is the same as clenny's, so just start at the beginning of the post and try the commands. When you get a different output than clenny got, post your output here and ask for help.

EDIT:
> **shamz_71 said:**
> listen , just tell me the steps i need to follow. i have no idea whats packages,right tools,dpkg.
i have same problm like clenny , downloading error.

I hadn't read your post, it was a reply to clenny. I only read the mail and didn't see yours yet.

---

### Post by shamz_71 on 2011-06-02
dpkg: error: dpkg status database is locked by another process

maybe this will help u

---

### Post by sanderd17 on 2011-06-02
> **shamz_71 said:**
> dpkg: error: dpkg status database is locked by another process

maybe this will help u

yes, that means that some other program is using the database. So close all programs and try again. If that doesn't work, do a complete reboot and try again. As I said before.

---

### Post by shamz_71 on 2011-06-02
Nothing was opened or running . I restarted it said something partial upgrade and i said ok and now its fine. Can u refer me to some place where i can learn how Ubuntu works , how to operate and all FROM SCRATCH. i cant even find built in games here

---

### Post by sanderd17 on 2011-06-02
> **shamz_71 said:**
> Nothing was opened or running . I restarted it said something partial upgrade and i said ok and now its fine. Can u refer me to some place where i can learn how Ubuntu works , how to operate and all FROM SCRATCH. i cant even find built in games here

It must have been some system service running in the background. So now you can install apps I suppose.

About the games: Linux doesn't have many games. In the software center you find some card games and stuff like that, but no popular games. You can install some games via Wine, look at the wine database to see how good they are supported: [http://appdb.winehq.org/]("http://appdb.winehq.org/"). You should know, platinum apps install and run without major problems, siver apps are apps that can run if you do a lot of hacking (so they will not run out of the box). The program called play-on-linux (it's in the software center) is wine with the hacks applied for certain apps. So if your app is in play-on-linux, than it will also run.

But most Linux users (even die-hards) that also like to game keep a windows installation on their computer (just to game) or use consoles like the playstation, xbox, wii or others. I don't game, so I don't have a Windows partition anymore.

As for your screen problem, at login time you can choose your window manager (when you have to type your password), there you can choose gnome-classic. Try if you still have the problem.

For a manual, see this: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) I think there are also translated manuals, but I don't know where they are or how good. It's a manual for 10.04 (so the version from a year ago), but most things will be the same if you use gnome-classic.

If you want to learn more about the command line, see this site: [http://linuxcommand.org/](http://linuxcommand.org/) it's linux command line (including filesystem and hardware handling) explained in 8 clear pages.

I hope this solved some questions.

---


---
title: "Edgy update times out"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2007-03-31
Synaptic tells me that my edgy on my Dell Latitude laptop has 39 updates to apply. So I tell it to go ahead, than I wait and wait and nothing happens.

So then I go into Terminal and type in:
sudo apt-get update
...and I get this:

```
Get: 1 http://archive.canonical.com edgy-commercial Release.gpg [191B]         
Ign http://archive.canonical.com edgy-commercial/main Translation-en_GB        
Get: 2 http://security.ubuntu.com edgy-security Release.gpg [191B]             
Ign http://security.ubuntu.com edgy-security/main Translation-en_GB            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_GB      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_GB        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_GB      
Get: 3 http://archive.ubuntu.com edgy Release.gpg [191B]                       
Ign http://archive.ubuntu.com edgy/main Translation-en_GB                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_GB                
Ign http://archive.ubuntu.com edgy/universe Translation-en_GB                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_GB                
Hit http://archive.canonical.com edgy-commercial Release                       
Get: 4 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_GB             
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_GB       
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_GB         
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_GB       
Hit http://security.ubuntu.com edgy-security Release                           
Get: 5 http://archive.ubuntu.com edgy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_GB              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_GB        
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_GB          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB        
Get: 6 http://archive.ubuntu.com edgy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB            
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB     
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB       
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB     
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://archive.ubuntu.com edgy-proposed Release                            
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://archive.ubuntu.com edgy/main Packages                               
Hit http://archive.ubuntu.com edgy/restricted Packages                         
Hit http://archive.canonical.com edgy-commercial/main Packages                 
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://archive.ubuntu.com edgy/universe Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                         
Hit http://archive.ubuntu.com edgy/main Sources                                
Hit http://archive.ubuntu.com edgy/restricted Sources                          
Hit http://archive.ubuntu.com edgy/universe Sources                            
Hit http://archive.ubuntu.com edgy/multiverse Sources                          
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Hit http://archive.ubuntu.com edgy-proposed/main Packages                      
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages                
Hit http://archive.ubuntu.com edgy-proposed/universe Packages                  
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages                
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Hit http://archive.ubuntu.com edgy-updates/universe Packages                   
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages                 
Hit http://archive.ubuntu.com edgy-updates/main Sources                        
Hit http://archive.ubuntu.com edgy-updates/restricted Sources                  
Hit http://archive.ubuntu.com edgy-updates/universe Sources                    
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources                  
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources 
Hit http://archive.ubuntu.com edgy-backports/restricted Sources                
Hit http://archive.ubuntu.com edgy-backports/universe Sources                  
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources                
Errhttp://packages.freecontrib.org edgy-plf Release.gpg                        
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Errhttp://packages.freecontrib.org edgy-plf/free Translation-en_GB
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Errhttp://packages.freecontrib.org edgy-plf/non-free Translation-en_GB
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 6B in 6m20s (0B/s)                                
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy-plf/Release.gpg  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy-plf/free/i18n/Translation-en_GB.bz2  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/i18n/Translation-en_GB.bz2  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
steve@laptop:~$ 


```

Obviously the update failed, but I don´t know what to do about it.

Any suggestions?

---

### Post by victorbrca on 2007-03-31
Looks like "packages.freecontrib.org" is down. I was not able to access or ping it (could be due to ICMP being blocked).

  Maybe try uncomenting the line from sources.list or wait for the site to come back on-line.



Vic.

---

### Post by SteveHoffmanUK on 2007-03-31
Thanks Vic. I´ve been trying to update all evening, so it must have been down a long time!  If you can access it either, then it must be them and not me, so I guess I&#314;l just have to wait until it comes up.

Didn´t understand your suggestion about uncommenting the line. Where is the line (which file? Which line?).

---

### Post by K.Mandla on 2007-03-31
If you open /etc/apt/sources.list and put a hash mark (#) in front of the lines that mention packages.freecontrib.org, you can re-update and it should be fine. 

The hash mark means that the text that follows it is a *comment* -- that it's not meant as instructions for Ubuntu. It's just for humans. So when you add that hash at the start, you're *commenting out* the lines, and your computer should ignore them. :)

Later you can uncomment them (remove the hashes) and try to update again, and see if that repository is working again.

---

### Post by victorbrca on 2007-03-31
No prob....

  if you go to you terminal and do: 

> less /etc/apt/sources.list

  You'll see your list of repositories, which are web sites Ubuntu download programs and updates. Press "q" to get out of the command.

  You can edit the file so it does not try to access "packages.freecontrib.org". All you'd have to do is issue the command:

> gksudo gedit /etc/apt/sources.list

  It will open a text editor which will allow you to uncoment (put a "#" in front of the line) so Ubuntu does no try to download anything from the site.

Take a look here, read it out before you do it if you are not familiar with it.

[**_Link_**]("http://www.psychocats.net/ubuntu/sources")


Vic.

---

### Post by pppetter on 2007-03-31
Please do note that you leave packages.freecontrib.org in your sources.list it still won't affect the others...
Alas, you can just leave it there, and everything will still function as it should - but you will continue to get that error message. But you are still safe to upgrade your system.

---


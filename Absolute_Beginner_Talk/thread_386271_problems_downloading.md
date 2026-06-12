---
title: "problems downloading"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by teez88 on 2007-03-16
Hi all. I have decided to make the leap to Linux but seem to be having a few problems with my settings. I can surf the net now after a bit of mucking around, but when I try to download anything (including updates and emails) it times out on me. I have installed Ubuntu Christian Edition, which was the only one that I could get to show web pages, and have disabled ipv6 (as recomended on many of the threads I have been reading) but alas, still no joy with updates, emails or downloads. If anybody can see what I am missing and could straighten me out it would be much appreciated. Thanks.

---

### Post by wpshooter on 2007-03-16
What type of internet connection are you using ?

DSL, Dialup, or Cable ?

---

### Post by teez88 on 2007-03-16
Adsl 2+ using a Netcomm NB5 router

---

### Post by mhancoc7 on 2007-03-16
> **teez88 said:**
> Hi all. I have decided to make the leap to Linux but seem to be having a few problems with my settings. I can surf the net now after a bit of mucking around, but when I try to download anything (including updates and emails) it times out on me. I have installed Ubuntu Christian Edition, which was the only one that I could get to show web pages, and have disabled ipv6 (as recomended on many of the threads I have been reading) but alas, still no joy with updates, emails or downloads. If anybody can see what I am missing and could straighten me out it would be much appreciated. Thanks.

Which version of Ubuntu CE are you using? Have you disabled the web content filtering? If not I would suggest that you do that using the built in GUI. (System>Administration>Configure Parental Controls).

Jereme

---

### Post by teez88 on 2007-03-17
Hi and thanks for your help so far. I am not sure which version of CE I have installed, but when I fire up the system it mentions kernal 2.6.17-10-generic. Am I looking in the right place? I could not find anything which would spell it out any clearer for me. I'm sure its there somewhere but this is all new for me!! I did have a look in the Parental Controls and put a few #'s at the front of some of the lines. Now I am having trouble pulling up web pages again and changing back all that I thought I had modified hasnt fixed this issue. :( 
Is there a list of settings available that I could compare to what I have, or is it a matter of learning the lingo and how Linux uses and stores this kind of info? Appreciate the help.

---

### Post by mhancoc7 on 2007-03-17
> **teez88 said:**
> Hi and thanks for your help so far. I am not sure which version of CE I have installed, but when I fire up the system it mentions kernal 2.6.17-10-generic. Am I looking in the right place? I could not find anything which would spell it out any clearer for me. I'm sure its there somewhere but this is all new for me!! I did have a look in the Parental Controls and put a few #'s at the front of some of the lines. Now I am having trouble pulling up web pages again and changing back all that I thought I had modified hasnt fixed this issue. :( 
Is there a list of settings available that I could compare to what I have, or is it a matter of learning the lingo and how Linux uses and stores this kind of info? Appreciate the help.

The first thing I would do is disable dansguardian (System>Administration>Configure Parental Controls).  Then see how your connections work.
Jereme

---

### Post by teez88 on 2007-03-18
I must have an older version of dansguardian installed as the parental controls do not have the "enable/disable" function. I have just downloaded the 1.4.5 version and will have another look at it tomorrow night. I will let you know how it goes. Thanks again.

---

### Post by teez88 on 2007-03-19
Just installed the new version of danguardian (very nice look) and  disabled it. I can surf the web but still no joy with downloading the updates. It just sits there trying to connect and then times out. Are there any other firewall/security type settings that can be enabled or disabled which might help?

---

### Post by mhancoc7 on 2007-03-19
> **teez88 said:**
> Just installed the new version of danguardian (very nice look) and  disabled it. I can surf the web but still no joy with downloading the updates. It just sits there trying to connect and then times out. Are there any other firewall/security type settings that can be enabled or disabled which might help?

What happens when you do the following?

Open terminal and run:
```

sudo apt-get update
```

Could you post the output?

Jereme

---

### Post by teez88 on 2007-03-19
Here is the info that came up in terminal. I hope it means more to you than me:confused: 

Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg                                                                            
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                                                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                                                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ichthux.com](http://archive.ichthux.com) grace Release.gpg                                                                            
  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                                                                 
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                                                                   
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ichthux.com](http://archive.ichthux.com) grace/main Translation-en_US                                   
  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Failed to fetch [http://archive.ichthux.com/ichthux/dists/grace/Release.gpg](http://archive.ichthux.com/ichthux/dists/grace/Release.gpg)  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ichthux.com/ichthux/dists/grace/main/i18n/Translation-en_US.bz2](http://archive.ichthux.com/ichthux/dists/grace/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
teez88@teez88-desktop:~$

---

### Post by mhancoc7 on 2007-03-19
Try this:

Open:
System>Preferences>Network Proxy

Make sure the it is set for "Direct internet connection".

Then try the update again.

Jereme

---

### Post by teez88 on 2007-03-20
The Network Proxy was set for Direct Internet Connection so I tried the update again. I think it is the same result, but here it is anyway. I am still feeling very positive about Ubuntu, but also very confused. It is times like this when I find myself learning the most and I thankyou for your help.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                                                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                                                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg                                                                            
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://archive.ichthux.com](http://archive.ichthux.com) grace Release.gpg                                                                            
  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                                                                   
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                                                                 
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://archive.ichthux.com](http://archive.ichthux.com) grace/main Translation-en_US                                                                 
  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                                                             
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Failed to fetch [http://archive.ichthux.com/ichthux/dists/grace/Release.gpg](http://archive.ichthux.com/ichthux/dists/grace/Release.gpg)  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ichthux.com/ichthux/dists/grace/main/i18n/Translation-en_US.bz2](http://archive.ichthux.com/ichthux/dists/grace/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ichthux.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mhancoc7 on 2007-03-20
I am kind of at a loss on this one. Can you check out the proxy settings in your browser (firefox) and see if it is set using a proxy. If so change your system proxy to that and try again. The only other thing that I could think would be to completely uninstall the web content filtering to be sure it is not causing this.

Jereme

---

### Post by RodneyW on 2007-03-20
Hey,

Sounds like you have the same problem I did. My problem was that my gateway and DNS server were the same. Go into your network settings and change the DNS to whatever your ISP's DNS are. Just google it or as a last result use any old dns from google. Works if theyre the same in windows, but not in linux for some reason. Pretty sure that will fix your prob. If not there is one more thing to try, disable iPv6 system wide by following instructions below:
[http://www.ubuntuforums.org/showthread.php?t=6841&highlight=ipv6](http://www.ubuntuforums.org/showthread.php?t=6841&highlight=ipv6)

I think changing DNS to any DNS u get out of google will work though.

---

### Post by teez88 on 2007-03-20
I have disabled ipv6 already but it did not seem to have an effect. I will give the DND settings a go tonight and let you know what happens. Thanks.

---

### Post by teez88 on 2007-03-21
Hi. Just changed my DNS settings and it worked!! :)  Thanks to all for your help.... I am sure I will need more help as I am learning, and hopefully can pass some knowledge on to others. As for now, I think ubuntu has just become my primary OS.

---

### Post by mhancoc7 on 2007-03-21
> **teez88 said:**
> Hi. Just changed my DNS settings and it worked!! :)  Thanks to all for your help.... I am sure I will need more help as I am learning, and hopefully can pass some knowledge on to others. As for now, I think ubuntu has just become my primary OS.

Awesome!! 

Jereme

---


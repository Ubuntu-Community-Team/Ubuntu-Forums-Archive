---
title: "Synaptic Isn't Finding Any Package"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by bob-aptllc on 2007-02-22
I tried installing VirtualBox and have since discovered my Edgy lacked some prerequisite packages. When I opened Synaptic to download them, I received an error message that the VisualBox deb package was broken and to run "dpkg --configure -a", which I did. Now, whenever I open Synaptic I receive these messages:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I again downloaded the deb package from VirtualBox's website and tried to reinstall it. If I close the error-message panel and search for a package, Synaptic can't find any package (including Firefox, Thunderbird, etc.) even though I have Universe selected. Does anyone know what the problem is or a way to reinstall Synaptic? Thank you!

Bob

---

### Post by Ben Sprinkle on 2007-02-22
Paste the output of:
```

sudo apt-get update

```
Here.

---

### Post by bob-aptllc on 2007-02-22
...:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources                 
Fetched 3B in 10s (0B/s)                                                       
Reading package lists... Done
...:~$

---

### Post by Ben Sprinkle on 2007-02-22
My reccomendations.

1:
Open synaptic now that you updated, try to reinstall.

2:
Your package is missing dependancies, I believe the command is:
```

sudo apt-get install -f

```
Or try it without install. Tell me if problems still exist.

---

### Post by bob-aptllc on 2007-02-22
I receive the same error messages when opening Synaptic.

... :~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

Opening Synaptic again, I receive the same error messages as before apt-get install -f.

---

### Post by Ben Sprinkle on 2007-02-22
Is this package in the ubuntu repositories or an external one?

Edit: must be external because I cannot find it on [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

### Post by bob-aptllc on 2007-02-22
When I try to reinstall the package by right-clicking on the .deb file and selecting "'Open with GDebi Package Installer'", I receive the following message:

[INDENT][/INDENT]"Could not open 'VirtualBox_1.3.6_Ubuntu_edgy_i386.deb'

[INDENT][/INDENT]The package might be corrupted or you are not allowed to open the file. Check the permissions of the file"

---

### Post by Ben Sprinkle on 2007-02-22
Ok try this. Open synaptic and there will be 4 buttons near the bottomish, click each one (I forget whic one it is) find the broken packages and then find yours. Remove it.
Then try reinstalling the .deb.

---

### Post by bob-aptllc on 2007-02-22
"Custom Filters" / "Broken", Search: "virtualbox", Look In: "Description and Name". No package was found.

---

### Post by Ben Sprinkle on 2007-02-22
Don't search, just see what's there. There is also a filter for custom or offline or not official or something, try to find your package there.

---

### Post by bob-aptllc on 2007-02-22
No packages display at all. Nothing I do with Synaptic displays a package, not even when just starting the application.

---

### Post by Ben Sprinkle on 2007-02-22
Wow, okay then go in a terminal and type:
```

sudo aptitude

```
Play around in it and see if you can find your package, might take a little time getting used to aptitude.

---

### Post by bob-aptllc on 2007-02-22
Ben, thanks for all your help. I worked with the Aptitude package, but still couldn't fix Synaptic. I've only been using Ubuntu for a few days, so I did a fresh install. Now Synaptic is back to normal. Thanks again! - Bob

---

### Post by Ben Sprinkle on 2007-02-23
> **bob-aptllc said:**
> Ben, thanks for all your help. I worked with the Aptitude package, but still couldn't fix Synaptic. I've only been using Ubuntu for a few days, so I did a fresh install. Now Synaptic is back to normal. Thanks again! - Bob

Ah, okay then. :)

---

### Post by bigyoy on 2007-03-03
I've just had this problem - I found a fix for it. I'm new to linux but hopefully this will help others


1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "virtualbox" you should find the following lines:
Package: virtualbox
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save

You should now be able to use synaptic again!

---

### Post by vikasvishnu on 2007-03-18
Thanks a lot buddy, you are a life saver. I was almost near to re-installing my new system, and you appeared like an angel through Google. Thanks a million. Guys, guys, this is the perfect answer to the issue.

:) Vikas

---

### Post by xyz on 2007-03-21
> **bigyoy said:**
> I've just had this problem - I found a fix for it. I'm new to linux but hopefully this will help others


1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "virtualbox" you should find the following lines:
Package: virtualbox
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save

You should now be able to use synaptic again!
Hi,
I'm also having this problem following an attempt at installing VirtualBox.
What you are suggesting seems to be the way to go but 
> /var/lib/dpkg/status
simply won't open. Any ideas why? Permissions are OK.
Thanks for your time.

---

### Post by xyz on 2007-03-23
Don't ask me why one day the file 'status' wouldn't open and the next it does!!!
The fact is I was able to remove those lines...thank you **bigyoy**.
Synaptic is now back up!

---


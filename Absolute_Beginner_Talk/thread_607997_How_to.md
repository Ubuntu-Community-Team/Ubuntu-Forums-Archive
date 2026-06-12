---
title: "How to"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-09
How do you install screenlets?

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> How do you install screenlets?

Please read the section "How do I install screenlets?"

[http://www.screenlets.org/index.php/FAQ#Installation](http://www.screenlets.org/index.php/FAQ#Installation)

---

### Post by RobotoWorks on 2007-11-09
I frankly just dont understand a single thing from that tutorial.

---

### Post by Paul820 on 2007-11-09
> **RobotoWorks said:**
> I frankly just dont understand a single thing from that tutorial.

:shock:
 Are you serious?

---

### Post by RobotoWorks on 2007-11-09
Yes I am pretty new to the whole world of coding and computers(Just came from the world of video games) and that tutorial really means nothing to me, thtas why I ask question over and over hoping someone can explain it easy.

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Yes I am pretty new to the whole world of coding and computers(Just came from the world of video games) and that tutorial really means nothing to me, thtas why I ask question over and over hoping someone can explain it easy.

So this "coding" under EASY WAY is giving you trouble...

> How do I install new Screenlets?
**Easy Way**

Simply open up the Screenlets manager (System - Preferences - Screenlets). Select the Install option on your right, search for the screenlet you want to install, select it, and you're all set. 

---

### Post by RobotoWorks on 2007-11-09
Heres what happened when I attempted to try the first part of the tutorial:

robotoworks@robotoworks-laptop:~$  wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get updat
--14:58:52--  [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg)
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================>] 1,353         --.--K/s             

14:58:57 (84.74 MB/s) - `-' saved [1353/1353]

OK
E: Invalid operation updat

---

### Post by RobotoWorks on 2007-11-09
> **Maestro23 said:**
> So this "coding" under EASY WAY is giving you trouble...
I dont have a "System - Preferences - Screenlets"

---

### Post by Paul820 on 2007-11-09
My apologies, that was a bit harsh. Anyway open a terminal and type or copy and paste this
> sudo gedit /etc/apt/sources.list
Now copy this to the bottom of the file, this is if you have gutsy
> deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
If you have feisty, copy this one
> deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
save the file and close it.
Copy and paste this into the terminal and press enter
> wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get update
Now in the terminal copy and paste this
> sudo apt-get update
In the terminal again, copy and paste this
> sudo apt-get install screenlets
Now you should have screnlets. :)

---

### Post by Maestro23 on 2007-11-09
> **RobotoWorks said:**
> Heres what happened when I attempted to try the first part of the tutorial:

robotoworks@robotoworks-laptop:~$  wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get updat
--14:58:52--  [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg)
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================>] 1,353         --.--K/s             

14:58:57 (84.74 MB/s) - `-' saved [1353/1353]

OK
E: Invalid operation updat

Why are you trying to install the screenlets program again? I saw in one of your other posts, someone gave you **exact commands to install the screenlets program**.  I even gave you this link. Did you not follow them or have trouble installing the actual screenlets program?

Edit: Paul820 has broken it down for you already.

---

### Post by RobotoWorks on 2007-11-09
Thanx! Im sorry for being "Super n00b" but for the 3rd step heres what I got
OK
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                      
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US   
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release                
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Packages    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
  404 Not Found
Fetched 1B in 6s (0B/s)                                                        
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by philinux on 2007-11-09
Have you got gusty installed on your hard drive.

And is your internet connection ok?

---

### Post by RobotoWorks on 2007-11-09
I have Gutsy installed yes. As for the internet connection, Im using a laptop which usually conects via Wireless AirCard, I also have a modem, no one has plain and simply told me how to install the AirCard so right now Im using a modem.

---

### Post by Paul820 on 2007-11-09
Do you have updates from CDrom enabled in System->Administration->Software Sources? If you do, disable updating from CD.

---

### Post by Maestro23 on 2007-11-09
> **Paul820 said:**
> Do you have updates from CDrom enabled in System->Administration->Software Sources? If you do, disable updating from CD.

System>>Admin>> Software Sources

---

### Post by RobotoWorks on 2007-11-09
It wont let me update because of errors

---

### Post by spiff95 on 2007-11-12
> **RobotoWorks said:**
> I dont have a "System - Preferences - Screenlets"

I used the Synaptic Package Manager and searched "screenlets." Then I marked the results for installation, and boom, now I have a System>Preferences>Screenlets.

Hope this helps.

---


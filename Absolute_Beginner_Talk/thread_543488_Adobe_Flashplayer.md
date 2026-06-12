---
title: "Adobe Flashplayer"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by jonmichi on 2007-09-05
Hello I am brand new at linux.  I can't seem to install adobe flash player.  Exactly how do I do it?  Thanks in ADvance

---

### Post by jonmichi on 2007-09-05
Actually while I am also being at new and asking did anyone figure out how to get onboard sound to work in Feisty?  Thanks

---

### Post by tbresson on 2007-09-05
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by alienexplorers on 2007-09-05
Go to adobe and download the tar.gz file for flash.  Un tar the file using tar -xvzf *.tar.gz
Read the readme.txt file and follow the directions.  Can't get much easier.

---

### Post by jonmichi on 2007-09-05
It tells me to do this.    

 In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).  

I know where the terminal is but I don't know how to navigate to the directory.  How do I do that?

---

### Post by jonmichi on 2007-09-05
Go to adobe and download the tar.gz file for flash. Un tar the file using tar -xvzf *.tar.gz
Read the readme.txt file and follow the directions. Can't get much easier.

How do I un tar the file?....sorry :(... I am very new at this

---

### Post by jonmichi on 2007-09-05
Thank you for your help though!!!!!  I just feel really new HAHAHA!!!

---

### Post by jonmichi on 2007-09-05
Go to adobe and download the tar.gz file for flash. Un tar the file using tar -xvzf *.tar.gz
Read the readme.txt file and follow the directions. Can't get much easier.

How do I un tar the file?....sorry ... I am very new at this

---

### Post by scxtt on 2007-09-05
sudo aptitude install flashplugin-nonfree

forget about the gzipped tar file.

---

### Post by jonmichi on 2007-09-05
Thanks.  What does this meaN?  

jonmichi@jonmichi-desktop:~$ sudo aptitude install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by scxtt on 2007-09-05
it's in the multiverse section, you probably don't have it enabled ... should be in /etc/apt/sources.list - but commented out ... you'll need to uncomment it and do **sudo aptitude update** to re-read what's available - then it should work - i just did it about an hour ago (i ruined LILO on an install and had to reinstall :()...

---

### Post by por100pre1 on 2007-09-05
Another way is just to follow this [instructions]("http://ubuntuforums.org/showthread.php?t=413624").

---

### Post by R_U_Q_R_U on 2007-09-05
As a fellow noob, I can attest that this site will help you get many items you want installed:

[http://www.stchman.com/](http://www.stchman.com/)

He even has an install procedure for Google Earth if you want. He gives very detailed instructions and makes it go as it should. You will learn much.

Thanks Stchman!!!

---


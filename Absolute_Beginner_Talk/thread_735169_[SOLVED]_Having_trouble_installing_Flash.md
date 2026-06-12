---
title: "[SOLVED] Having trouble installing Flash"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by MeTylerDurden on 2008-03-25
:popcorn:AFAIK...you just open terminal then type :==> sudo apt-get install ubuntu-restricted-extras
or from system - administration-synaptic
search for flash...nonfree.....CMIIW    i took the advice given  by another of the faithfuls (oedha) 
   it intalled alot   .. but i still cant get hulu...   let me check myspace..   ummm still nothing happening there with the embedded videos.. and no music...
     The end result is always the same   as we trusted microsoft and adobe they have given us piles of useless garbage in return ..    dont take candy from stranger       hellll with adobe

---

### Post by gandaran on 2008-03-25
[QUOTE 
   it intalled alot   .. but i still cant get hulu...   let me check myspace..   ummm still nothing happening there with the embedded videos.. and no music...
     The end result is always the same   as we trusted microsoft and adobe they have given us piles of useless garbage in return ..    dont take candy from stranger       hellll with adobe[/QUOTE]

MeTylerDurden
you installed the ubuntu-restricted-extras and still no flash, correct?
if you updated synaptic first you would have no problem.
to correct this you must go to synaptic and uninstall the flashplugin-nonfree (complete removal ) then update synaptic or use this command » sudo apt-get update « then install again the same  new flashplugin-nonfree package, do this, it'll work, the old flash package in your synaptic was broken.

---

### Post by MeTylerDurden on 2008-03-25
ok  Gandaran  i did the uninstall..   i am having a little trouble with the command line..     i can press alt - f2  and enter there   or application - terminal  , but when i enter there it seems to say my name password or something like that       how should this work normally..

---

### Post by gandaran on 2008-03-25
> **MeTylerDurden said:**
> ok  Gandaran  i did the uninstall..   i am having a little trouble with the command line..     i can press alt - f2  and enter there   or application - terminal  , but when i enter there it seems to say my name password or something like that       how should this work normally..

type on the terminal, sudo apt-get update, hit enter, type your password (password doesn't show ) hit enter again, thats all.

---

### Post by aysiu on 2008-03-25
The terminal asks for a user and password? Can you post a screenshot of what you see?

---

### Post by MeTylerDurden on 2008-03-25
/home/tylerdurden/Desktop/Link to Screenshot.png 
    hope that works.. terminal just is confusing right now because there is no communication back to tell you if you are successfull or not..

---

### Post by MeTylerDurden on 2008-03-25
/home/tylerdurden/Desktop/Link to Screenshot.png

   llet me know if that link works , my first time doing a screenshot

---

### Post by aysiu on 2008-03-25
> **MeTylerDurden said:**
> /home/tylerdurden/Desktop/Link to Screenshot.png

   llet me know if that link works , my first time doing a screenshot
We can't see what's on your desktop.

For more details, see [How do I attach an image to my post?](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

---

### Post by gandaran on 2008-03-25
MeTylerDurden
look if you have trouble using the terminal, you can open synaptic and just click the reload button to update.
if you want to post a screenshot, you'll have to upload to a server like imageshack and post the url in your thread.

to open the terminal, go to applications » accessories » console

---

### Post by aysiu on 2008-03-25
> **gandaran said:**
> 
if you want to post a screenshot, you'll have to upload to a server like imageshack and post the url in your thread. Actually, the forums themselves can host images.

---

### Post by gandaran on 2008-03-25
> **aysiu said:**
> Actually, the forums themselves can host images.

thanks I didn't know that!

---

### Post by MeTylerDurden on 2008-03-25
iss this it///??

---

### Post by gandaran on 2008-03-25
it's sudo apt-get update
not sudo apt-get update,
see the deference, it's the comma

---

### Post by aysiu on 2008-03-25
> **MeTylerDurden said:**
> iss this it///??
Well if you're using the terminal, you can just copy and paste the text from the terminal instead of uploading a screenshot, but, yes, that's how you attach an image.

By the way, you added an extra comma at the end of *sudo apt-get update*

**What you wrote**: ```
sudo apt-get update,
``` **What you should have written**: ```
sudo apt-get update
``` Generally speaking, it's a good idea to copy and paste commands instead of retyping them--takes less time, leaves less room for error.

---

### Post by MeTylerDurden on 2008-03-25
```
tylerdurden@tylerdurden-desktop:~$ sudo apt-get update
[sudo] password for tylerdurden:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/main Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:5 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security Release.gpg [191B] 
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                      
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy Release 
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/universe Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/universe Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) gutsy-security/multiverse Sources
Fetched 5B in 2s (2B/s)  
Reading package lists... Done
tylerdurden@tylerdurden-desktop:~$  
``` :popcorn:LET THE GOOD TIMES ROLL-  worked perfectly without the comma  ,:lolflag:

---

### Post by gandaran on 2008-03-25
now for the flash, you did uninstall the flashplugin-nonfree? if correct, now just reinstall the same package (flashplugin-nonfree), then go to youtube see if it works.

---

### Post by aysiu on 2008-03-25
> **gandaran said:**
> now for the flash, you did uninstall the flashplugin-nonfree? if correct, now just reinstall the same package (flashplugin-nonfree), then go to youtube see if it works.
I prefer to have people [install Flash manually](http://www.psychocats.net/ubuntu/flashmanual), but the command for gandaran's instructions is: ```
sudo apt-get remove flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

---

### Post by MeTylerDurden on 2008-03-25
Gandarin , Aysiu     we are victorious  ..  Hulu now works along with everything else  Myspace wooo!         I did as you instructed and uninstalled and  updated and reinstalled and I also got rid of Gnash..   i am fully functional and dont   forget....
                                          Time makes two  , it takes 2 to heal a broken heart.....  :popcorn:

---


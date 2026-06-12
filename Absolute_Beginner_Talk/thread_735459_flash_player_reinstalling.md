---
title: "flash player reinstalling"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by webdreamer on 2008-03-25
I hadn't enabled what some things in the add/remove program, so, before I figured that out, I installed flash player by getting a script from Adobe's website and running it. Before Firefox asked to install the stuff it needed to get flash videos running, but now it reacts has it has everything it needs - only the videos won't play. The videos are presented, then the data starts to be transferred and then something seems to get stuck; the video doesn't load, and the window turns gray, until I finally decide to kill the process. I tried both  uninstalling firefox and flash plugin, but either solved the problem. The thing I installed (I don't know where, that's the major issue) was a library, that went by the name of libflashplayer.so.

---

### Post by MeTylerDurden on 2008-03-25
follow my thread on flash card   i just had problem and had to uninstall flash in Synaptic package manager ,  then get the unresticted stuff  ,  then update all that and then get flash  ,  easier if you followed my name to thread..   but thats about it..   :)

---

### Post by (((X))) on 2008-03-25
Hi

Things you experience at the moment video loads have to do with flashplayer, wich is a propriatory software of course.
There is an alternative to that, look here: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
Gnash is opensource, so may work better.
By the way, have you noticed when firefox needs flashplugins, it suggests to install flashplayer-nonfree or gnash, worth trying I guess.

---

### Post by MeTylerDurden on 2008-03-25
I just had Gnash  and unless something was broken in my packages was not working on myspace or hulu   but  hey try that first if you can get to work i may go back and try  I installed the flash9 in sympatic packeges..     here is some help
Post Reply
	
Page 2 of 2 	< 	1 	2 	
 
	Thread Tools 	Search this Thread 	Display Modes
  #11   Report Post  
Old 5 Hours Ago
gandaran's Avatar 	
gandaran gandaran is online now
A Carafe of Ubuntu
	  	
Join Date: Oct 2007
Beans: 115
Ubuntu 7.10 Gutsy Gibbon User
Thanks: 0
Thanked 15 Times in 13 Posts
Re: Having trouble installing Flash
Quote:
Originally Posted by aysiu View Post
Actually, the forums themselves can host images.
thanks I didn't know that!
__________________
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
The Following User Says Thank You to gandaran For This Useful Post: 	Remove Your Thanks
MeTylerDurden (4 Hours Ago)
gandaran
View Public Profile
Send a private message to gandaran
Find all posts by gandaran
Add gandaran to Your Buddy List
  #12   Report Post  
Old 5 Hours Ago
MeTylerDurden's Avatar 	
MeTylerDurden MeTylerDurden is online now
5 Cups of Ubuntu
	  	
Join Date: Mar 2008
Beans: 33
Thanks: 33
Thanked 0 Times in 0 Posts
Re: Having trouble installing Flash
iss this it///??
Attached Thumbnails
Click image for larger version Name: Screenshot.png Views: 5 Size: 114.1 KB ID: 63800  
__________________
Thanks Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
MeTylerDurden
View Public Profile
Send a private message to MeTylerDurden
Find all posts by MeTylerDurden
Add MeTylerDurden to Your Buddy List
  #13   Report Post  
Old 4 Hours Ago
gandaran's Avatar 	
gandaran gandaran is online now
A Carafe of Ubuntu
	  	
Join Date: Oct 2007
Beans: 115
Ubuntu 7.10 Gutsy Gibbon User
Thanks: 0
Thanked 15 Times in 13 Posts
Re: Having trouble installing Flash
it's sudo apt-get update
not sudo apt-get update,
see the deference, it's the comma
__________________
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
The Following User Says Thank You to gandaran For This Useful Post: 	Remove Your Thanks
MeTylerDurden (4 Hours Ago)
gandaran
View Public Profile
Send a private message to gandaran
Find all posts by gandaran
Add gandaran to Your Buddy List
  #14   Report Post  
Old 4 Hours Ago
aysiu's Avatar 	
aysiu aysiu is online now
IceBuntu User
	  	
Join Date: May 2005
Bean Count Hidden
Ubuntu 7.10 Gutsy Gibbon User
Thanks: 0
Thanked 162 Times in 136 Posts
Re: Having trouble installing Flash
Quote:
Originally Posted by MeTylerDurden View Post
iss this it///??
Well if you're using the terminal, you can just copy and paste the text from the terminal instead of uploading a screenshot, but, yes, that's how you attach an image.

By the way, you added an extra comma at the end of sudo apt-get update

What you wrote:
Code:

sudo apt-get update,

What you should have written:
Code:

sudo apt-get update

Generally speaking, it's a good idea to copy and paste commands instead of retyping them--takes less time, leaves less room for error.
__________________
If someone asks you to sudo rm -rf anything, don't do it, and don't run any command with rm in it unless you know exactly what you're doing. Read this for more information.

Getting the Best Help on Linux Forums
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
The Following User Says Thank You to aysiu For This Useful Post: 	Remove Your Thanks
MeTylerDurden (4 Hours Ago)
aysiu
View Public Profile
Send a private message to aysiu
Visit aysiu's homepage!
Find all posts by aysiu
Add aysiu to Your Buddy List
  #15   Report Post  
Old 4 Hours Ago
MeTylerDurden's Avatar 	
MeTylerDurden MeTylerDurden is online now
5 Cups of Ubuntu
	  	
Join Date: Mar 2008
Beans: 33
Thanks: 33
Thanked 0 Times in 0 Posts
Re: Having trouble installing Flash
Code:

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

LET THE GOOD TIMES ROLL- worked perfectly without the comma ,
__________________
Last edited by aysiu : 4 Hours Ago at 02:13 PM. Reason: Added in [code] tags for terminal output
Thanks Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
MeTylerDurden
View Public Profile
Send a private message to MeTylerDurden
Find all posts by MeTylerDurden
Add MeTylerDurden to Your Buddy List
  #16   Report Post  
Old 4 Hours Ago
gandaran's Avatar 	
gandaran gandaran is online now
A Carafe of Ubuntu
	  	
Join Date: Oct 2007
Beans: 115
Ubuntu 7.10 Gutsy Gibbon User
Thanks: 0
Thanked 15 Times in 13 Posts
Re: Having trouble installing Flash
now for the flash, you did uninstall the flashplugin-nonfree? if correct, now just reinstall the same package (flashplugin-nonfree), then go to youtube see if it works.
__________________
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
The Following User Says Thank You to gandaran For This Useful Post: 	Remove Your Thanks
MeTylerDurden (3 Hours Ago)
gandaran
View Public Profile
Send a private message to gandaran
Find all posts by gandaran
Add gandaran to Your Buddy List
  #17   Report Post  
Old 4 Hours Ago
aysiu's Avatar 	
aysiu aysiu is online now
IceBuntu User
	  	
Join Date: May 2005
Bean Count Hidden
Ubuntu 7.10 Gutsy Gibbon User
Thanks: 0
Thanked 162 Times in 136 Posts
Re: Having trouble installing Flash
Quote:
Originally Posted by gandaran View Post
now for the flash, you did uninstall the flashplugin-nonfree? if correct, now just reinstall the same package (flashplugin-nonfree), then go to youtube see if it works.
I prefer to have people install Flash manually, but the command for gandaran's instructions is:
Code:

sudo apt-get remove flashplugin-nonfree && sudo apt-get install flashplugin-nonfree

__________________
If someone asks you to sudo rm -rf anything, don't do it, and don't run any command with rm in it unless you know exactly what you're doing. Read this for more information.

Getting the Best Help on Linux Forums
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
The Following User Says Thank You to aysiu For This Useful Post: 	Remove Your Thanks
MeTylerDurden (3 Hours Ago)
aysiu
View Public Profile
Send a private message to aysiu
Visit aysiu's homepage!
Find all posts by aysiu
Add aysiu to Your Buddy List
  #18   Report Post  
Old 3 Hours Ago
MeTylerDurden's Avatar 	
MeTylerDurden MeTylerDurden is online now
5 Cups of Ubuntu
	  	
Join Date: Mar 2008
Beans: 33
Thanks: 33
Thanked 0 Times in 0 Posts
Re: Having trouble installing Flash
Gandarin , Aysiu we are victorious .. Hulu now works along with everything else Myspace wooo! I did as you instructed and uninstalled and updated and reinstalled and I also got rid of Gnash.. i am fully functional and dont forget....
Time makes two , it takes 2 to heal a broken heart.....

---

### Post by webdreamer on 2008-03-25
Tried it, but it's not working form me. When I update I don't get exactly the same stuff, but it seems to go just fine. Also the problem is I don't know if I installed it in the wrong folder. Even if I go on to remove flash plugin I still get the same error.

---


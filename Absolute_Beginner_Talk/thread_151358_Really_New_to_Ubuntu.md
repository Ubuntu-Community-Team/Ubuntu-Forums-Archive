---
title: "Really New to Ubuntu"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Mr.Maiden on 2006-03-27
I just recently installed ubuntu and like it but im in need of installing driver help. I have an ati 9800 pro and im confused on how to install the driver ( Keep in mind this is my first time useing ubuntu) If any 1 would please help me i would really apperciate it. Thanks:D

---

### Post by davidmoore83 on 2006-03-27
welcome :)

Get yourself into the #ubuntu IRC channel - there are plenty of peeps there happy to help.

---

### Post by Mr.Maiden on 2006-03-27
ok thanks i don t no if you can help me i have no idea what is wrong this is the message i get 


you have 1 broken package on your system!

Use the "Broken" filter to locate it.


i also get a box that says i have a bunch of problems i don t kno if i should just reinstall. I don t have any drivers or anyhting so yea i might reinstall.   I get this big box that says all this stuff here it is





: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) hoary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_hoary_Packages) - stat (2 No such file or directory)

---

### Post by catlett on 2006-03-27
Follow this link to a post about installing the latest ATI drivers   [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)     Hopefully it helps. If not keep posting eventually the really smart Ubuntus will find you. Good luck. Regards, Catlett

---

### Post by Mr.Maiden on 2006-03-27
Thanks do you kno what any of those problems are ?


The following problems were found on your system:





W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) hoary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_hoary_Packages) - stat (2 No such file or directory)

---

### Post by catlett on 2006-03-27
I am pretty new ti Ubuntu but it looks like those are listings to your repositories and that it couldn't find what you wanted it too. Those URLs listed are the repositories. The repositories are where the programs, drivers etc are stored. When you run apt-get that is where it is doing the getting. Apt-get goes to those repositories and gets whatever packages are there. Then you can choose to install them ot not. I don't know if this will help but do an update on your repository. Open up the terminal and type  ```
 sudo apt-get update
```  this will update your list. Then type  ```
sudo apt-get upgrade
```    . This will update all the software you have installed, if there is an update. Then re-run the command that gave you the error. You might want to search the forum or google for /etc/apt/sources.list  .If you find a post that has a current list or a list that has something you don't you might want to add it to your list and run apt-get update, apt-get upgrade again. If you don't know how to add to your list I'll explain. The  /etc/apt/sources.list  is where the apt-get function goes to search for software. There are many different ones, that is why looking for a different list may help you. To change your list is just a matter of editing the text. In windows it would be a matter of opening a .txt file in the notepad. Making changes and saving those changes. In linux you can use the progran  gedit (gnome edit). So to get the file you have to give a command with the program you want and what you want it to get. So open the terminal and type  ```
 sudo gedit /etc/apt/sources.list
```  this will open up the document in a notepad type of environment. I just use cut and paste to add. Cut and paste works here just like in windows. So if you find a post with a good modern list just cut and paste it in and hit save then close the window. Then run sudo apt-get update and sudo apt-get upgrade again and finally rerun your original command. (Also remember to type   sudo  before your command to install a driver. Sudo gives you root priveleges [administrator priveleges in windows] without root privelege you won't be able to do anything that alters your sytem). Like I said before if your problem persists, keep posting, eventually someone smarter will come along. Also try cutting and pasting your first line of the error into the google search box. Most of the time it will link you to a post with the same problem and hopefully the thread has an answer. Good luck. Once you get the wrinkles out Ubuntu is great. Regards.

---

### Post by Mr.Maiden on 2006-03-27
ok lol but i have a question how do i get to the terminal 0_0

---

### Post by Perfect Storm on 2006-03-27
Ubuntu Hoary:
Application tab ---> System Tools ---> Terminal

Ubuntu breezy:
Applications tab ---> Accessories ---> Terminal

---

### Post by Mr.Maiden on 2006-03-27
ahaha ok thanks everyone im gonna try getting my ati driver worken from what i have red it seems people have diffucilty with ati. I do plan to switch out the motherboard for a pce-express:)  but for now im gonna use ati 9800:mrgreen:

---

### Post by Sef on 2006-03-27
This is another way to add the repsitories without taking a chance of breaking your system.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

After you add them, then

sudo apt-get update

sudo apt-get upgrade

---

### Post by Mr.Maiden on 2006-03-27
im stuck on something im tryinf to get my ati driver working and im stuck at this part 

Change to the download directory (cd /path/to/directory). You'll need Universe enabled in your sources.list file to download module-assistant. You may replace your /etc/apt/sources.list with this one if you wish and then sudo apt-get update before proceeding.


The artice for it is right here [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by catlett on 2006-03-29
Follows Sef's link.
>  Sef
Skinny Soy Caramel Ubuntu
 
Join Date: Dec 2005
Beans: 670
	
Default Re: Really New to Ubuntu
This is another way to add the repsitories without taking a chance of breaking your system.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

After you add them, then

sudo apt-get update

sudo apt-get upgrade

---


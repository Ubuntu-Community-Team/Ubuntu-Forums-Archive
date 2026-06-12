---
title: "Easy Ubuntu Troubles"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by dosmode on 2007-03-02
I installed, I assume, "Easy Ubuntu" on my machine but the program won't launch.  There is a shortcut to the program in the Applications/Systems menu so I am assuming that it was successfully installed and it states that it is installed when I checked in Synaptic.  Question is why won't it launch?  When I hit the shortcut nothing happens... zip... no window pops up.... puzzling.  Can someone give me a possible reason why the program isn't launching.  Thanks... BTW, I am using Ubuntu 6.10, if that helps.

---

### Post by techamed on 2007-03-02
You need to have administrator privileges in order to install any kind of software... Chances are you are not root.


> **dosmode said:**
> I installed, I assume, "Easy Ubuntu" on my machine but the program won't launch.  There is a shortcut to the program in the Applications/Systems menu so I am assuming that it was successfully installed and it states that it is installed when I checked in Synaptic.  Question is why won't it launch?  When I hit the shortcut nothing happens... zip... no window pops up.... puzzling.  Can someone give me a possible reason why the program isn't launching.  Thanks... BTW, I am using Ubuntu 6.10, if that helps.

---

### Post by steve101101 on 2007-03-02
even if your not root you can use the sudo command such as...

sudo apt-get program-name

---

### Post by dosmode on 2007-03-02
Thanks for the quick response and please bear with the Ubuntu newbie here...
I thought that I was taking to Ubuntu like a penguin to water, pun intended, but then it keeps on hitting me with curve balls... :) Still, I am not one to give up easily.... 
Here are the things I tried:
I logged in as root and tried Easyubuntu and still nothing.
I changed my user settings to "admin" by clicking the System/Administration/User and Groups and still nothing.
I did notice though that when I reboot my system, login and try opening Easyubuntu a window pops up telling me that I need administrative privilege to use the program upon which I enter my password but still nothing happens.  Stumped... :confused:  Question is, I am not sure if I am going about this right, i.e., logging in as root...

---

### Post by steve101101 on 2007-03-02
I have used EasyUbuntu once, but the installation was painstaking and not worth it for me. I either use the package manager or aptitude in the terminal. 

What are you trying to install and ill try to help you install it without easy Ubuntu.

---

### Post by richardgundersen on 2007-03-02
I found Automatix worked first time for me, after a few failed attempts with EasyUbuntu (which at the time wasn't ready for Edgy, but now it might be - not sure).

Give Automatix a try.

---

### Post by steve101101 on 2007-03-02
the thing with automatix which i have read, never used, is that it can force changes which can affect your entire system. I have been much happier with apt and systematic package manager.

---

### Post by dosmode on 2007-03-02
steve said:
> I have used EasyUbuntu once, but the installation was painstaking and not worth it for me. I either use the package manager or aptitude in the terminal
I am with you on this... aptitude and synaptic pretty much does everything.  Just that it is a minor hassle to apt this, apt that, apt the other.... I guess I am missing the .exe files from MS just a tiny lil bit.... 
It is not that I am needing Easyubuntu to install anything.... more like I am on a steep learning curve at the moment and figure that if I can't get something accomplished in Ubuntu then I am slipping up somehow along my way to becoming adept at maneuvering myself around Ubuntu.  I guess that I will just have to get used to the fact that some things can't or won't work, for example, I have not been able to get my Canon Pixma IP1000 printer to print from Ubuntu as yet...  I must say that I am in for good even if it means thrashing my system while I am at it.... it happened when I first learned windows... thrashed my first system on that stint.  BTW, I am on my third clean install of Ubuntu and wished there was a way to back up all my updates, which usually takes about 3 hours to download, so that I don't need to download again everytime I do a fresh installation... but that probably is for a new thread... thanks y'all

---

### Post by steve101101 on 2007-03-03
I am also on my third installation of ubuntu i think. you get used to how to maneuver in linux and user the terminal quite well.

---


---
title: "Please dont do this to me!!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by TigerTail on 2007-05-27
I converted all of my computers to ubuntu. I really enjoy the interface and putting me in the drivers seat of my software. The only problem is that sometimes im not the best driver ha ha. anyways I followed all of the directions given to me to install Frostwire and it shows up in my internet scroll but when i click on it nothing happens??? confused some help would be nice im running Ubuntu 7.04 on a 2.4ghz 512mb ram computer. I love ubuntu but this may pose a problem for me also my torrent downloads are slow like 20Kbps on a good feed 1482 seeders  867 leechers also will I have any problems Do i need to upgrade my computer when i start really using ubuntu? thanx everyone!

---

### Post by taurus on 2007-05-27
Try to run it from a terminal to see what's wrong with it.  Also, you did install java first before you run frostwire, right?

Applications -> Accessories -> Terminal
```
java -version
frostwire
```

---

### Post by DJ Wings on 2007-05-27
Try a different torrent. Maybe it's the seeder(s). Ubuntu doesn'thave anything that would slow your 'net connection down...

---

### Post by TigerTail on 2007-05-27
My java version is 1.4.2

---

### Post by TigerTail on 2007-05-27
Ok thanx guys for responding so quickly and yes you can say it im an idiot ha ha. I just needed to update java and as for the torrents ive tried alot of different torrents and i cant get a good speed im using freeloader

---

### Post by taurus on 2007-05-27
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
java -version
```

---

### Post by nickpaton on 2007-05-27
May I suggest that you uninstall Frostwire and reinstall using [Automatix2]("http://www.getautomatix.com/") (under filesharing section).  

This way, if you are missing any dependencies or your Java needs updating etc, then this will be done automatically for you.

Personally I've not used FW but use Azureus which again is available via Automatix2.  Even P2P dowloading using a very low spec PC runs very rapidly indeed.  As has been said already download speeds are not usually down to the spec of the PC.

Also general P2P rules - make sure you have set your port forwarding correctly (sure you have but just a reminder !!), and remember that uploading slows down your downloading speed (but not usually to the slow speed you've mentioned).

Could you send the the URL of the site you're using & I'll give it a go if you like.

---

### Post by TigerTail on 2007-05-27
when i try to install automatix2 it tells me that only one software management tool is alowed to run at the same time but im not running anything else ..............

---

### Post by TigerTail on 2007-05-27
brandon@Desktop-Hacker:~$ sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
brandon@Desktop-Hacker:~$

---

### Post by nickpaton on 2007-05-27
Try Taurus's solution - that should work for you.

I'll get back with the Autmatix2 problem - it's a useful app to have in any case.

---

### Post by TigerTail on 2007-05-27
I tried taurus solution also my computer is haveing dpkg problems i cant even get update codecs on totem movie player

---

### Post by taurus on 2007-05-27
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by TigerTail on 2007-05-27
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

I looked on java.com and cant find anything i did the new update procedure u gave me taurus and that worked great now my updates and dpkg problem is fixed

---

### Post by TigerTail on 2007-05-27
The following NEW packages will be automatically installed:
  gsfonts-x11 sun-java6-jre 
The following packages have been kept back:
  sun-java5-bin 
The following NEW packages will be installed:
  gsfonts-x11 sun-java6-bin sun-java6-jre sun-java6-plugin 
0 packages upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 93.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
brandon@Desktop-Hacker:~$ 

what the heck does this mean?

---

### Post by nickpaton on 2007-05-27
Make sure Synaptic and the Command Terminal are closed down just in case.  If that makes no difference try closing every program to just leave the desktop.

If that doesnt work try a reboot.

If that doesn't work, try posting on the Automatix2 forum - I'll keep looking though.

---

### Post by taurus on 2007-05-27
Did you try to install sun-java5-bin some time before?

```
sudo aptitude --purge remove sun-java5-bin
sudo aptitude update
```

---

### Post by nickpaton on 2007-05-27
Can you post the contents of this terminal command:

```
gksudo gedit /etc/apt/sources.list
```

This gives your repository list and it's possible you need to add extra repos.

EDIT - Taurus I'll leave this one for you - you know somewhat more than me LOL!!

---

### Post by TigerTail on 2007-05-27
yes and now when i try to update it it keeps asking me if im "root"  and i cant do anything because of missing arch?

---

### Post by TigerTail on 2007-05-27
Oh and yes i tried closing everything and even rebooted twice since ive been talking here and nothing is working

---

### Post by taurus on 2007-05-27
> **TigerTail said:**
> yes and now when i try to update it it keeps asking me if im "root"  and i cant do anything because of missing arch?

It would be nice if you post the command and the exact error message.

---

### Post by TigerTail on 2007-05-27
sudo aptitude --purge remove sun-java5-bin

after i did that i tried to install automatix2 and now that is installing now how do i use it?
mabey that will fix my java problems when i try to get frostwire

---

### Post by TigerTail on 2007-05-27
My cpu load is at 100 and my computer is trying to update java through automatix2 and it hasnt gone anywhere in a long time

---

### Post by nickpaton on 2007-05-27
If you have managed to install A2, then you should find it under Applications > System Tools.

Click on the icon and allow it to start (it takes a while).

Have a look through the various sections and select what you want to install.  Any extra "behind the scenes" programs will also be downloaded.

Re the codecs for Totem, you will find them in the codecs and plugins section.

---

### Post by nickpaton on 2007-05-27
Install Frostwire and it will install the correct version of Java and any other dependent program as required, as I said in an earlier post.

---

### Post by TigerTail on 2007-05-27
This is everything i have done and at the bottom is the error i get everything else works for me.




brandon@Desktop-Hacker:~$ sudo aptitude --purge remove sun-java5-bin
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
brandon@Desktop-Hacker:~$ sudo dpkg --configure -a
brandon@Desktop-Hacker:~$ sudo aptitude update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
brandon@Desktop-Hacker:~$ sudo aptitude --purge remove sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  sun-java5-jre 
The following packages will be REMOVED:
  sun-java5-bin 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
brandon@Desktop-Hacker:~$ sudo aptitude update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done
brandon@Desktop-Hacker:~$ sudo aptitude update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
brandon@Desktop-Hacker:~$ sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find package "sun-java6-font".  However, the following
packages contain "sun-java6-font" in their name:
  sun-java6-fonts 
The following NEW packages will be automatically installed:
  gsfonts-x11 sun-java6-jre 
The following packages have been kept back:
  sun-java5-bin sun-java5-jre 
The following NEW packages will be installed:
  gsfonts-x11 sun-java6-bin sun-java6-jre sun-java6-plugin 
0 packages upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 93.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
brandon@Desktop-Hacker:~$

---

### Post by discmaster on 2007-05-27
You're not alone TigerTail...> Install Frostwire and it will install the correct version of Java and any other dependent program as required, as I said in an earlier post. I can't get it to open at all after I install this way. I read in other threads about installing java 6.1, but can't seem to make that work either.

I am using beryl, which unfortunately causes a blank white screen when starting frostwire...

---

### Post by TigerTail on 2007-05-27
Discmaster i tried running beryl and as soon as i turned it on i got a white screen try disabling it then i bet frostwire will work for you

---

### Post by nickpaton on 2007-05-27
OK, just stop a second, we're getting out of sync here!!

Please can you concentrate on using Automatix2, since I think for you it may be easier.

I assume it starts OK and you eventually end up in a screen with a nunber of headings in the left side and a number of programs relating to each heading which can be downloaded on the right hand side.

On the left hand side click on "File Sharing" and select Frostwire from the right hand list.
Click Start button at the top to start the installation.

When you have finished all your downloads File > Remove Automatix Repos.
When the A2 repos have been removes from your sources list back to File > Quit in the normal way.

---

### Post by TigerTail on 2007-05-27
my automatix2 is getting java right now im hopeing that its going to work this time i just got back from a reboot and i removed my old java and now its updating so i think i just have two seperate javas working or something but i think its workin give me a minute to be sure

---

### Post by TigerTail on 2007-05-27
yess finally i got automatix2 installed fully finally. but first things first how do i get rid of my old frostwire since its not in my remove program list?

---

### Post by TigerTail on 2007-05-27
hey thanks alot nickpaton!!! if i understand this right all i have to do is search with this program and select a program and it will install for me. If thats right this has almost all the software i need
 :)

---

### Post by nickpaton on 2007-05-27
Copy the following into a terminal:

```
sudo apt-get remove frostwire
```

or do it via Synaptic. (Search Frostwire, and when found right click and select remove).

EDIT: DO NOT run A2 and Synaptic at the same time, or have them both open at the same time.  There's a big danger of damaging your OS

---

### Post by nickpaton on 2007-05-27
> **TigerTail said:**
> hey thanks alot nickpaton!!! if i understand this right all i have to do is search with this program and select a program and it will install for me. If thats right this has almost all the software i need
 :)

Yup that's right!

---

### Post by TigerTail on 2007-05-27
Thanx you everyone for all your help. Like i said i am willing to take the time to figure this stuff out! frostwire is up and running now!!!! java is updated and installed right. im going to try another program for torrents. The sky is the limit.


Go Ubuntu free for all open source!!!!!!

---

### Post by nickpaton on 2007-05-27
It's a pleasure and have fun!

Nick

---


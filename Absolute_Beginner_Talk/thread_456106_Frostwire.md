---
title: "Frostwire"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-05-27
I have used frostwire but had problems with the keyboard not inputting text! I have uninstalled it and on trying to reinstall it I get the following.
Any ideas?

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2007-05-27
Is another process like synaptic running while you try to install frostwire again?

---

### Post by Benbow on 2007-05-27
Thanks Taurus, I live and learn. Trouble is I'm getting this now!

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for frostwire
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by taurus on 2007-05-27
Did you install frostwire with apt-get before?  Which release are you running right now?

---

### Post by Benbow on 2007-05-27
I can't remember which release I had as I have uninstalled it. To reinstall I used:   sudo aptitude install frostwire

---

### Post by taurus on 2007-05-27
Try

```
sudo aptitude update
sudo aptitude install frostwire
```
Are you running Feisty Fawn (release)?

---

### Post by Benbow on 2007-05-27
Yes, Feisty Fawn but I did have the original download working for a few days.
This is the result of your suggestions:

desktop:~$ sudo aptitude update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Fetched 7B in 1s (7B/s)  
Reading package lists... Done
benbow@benbow-desktop:~$ sudo aptitude install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for frostwire
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by Benbow on 2007-05-27
I have downloaded it again from the Frostwire site and it is a binary file......

---

### Post by Outrunner on 2007-05-27
Are you sure you're downloading the right thing? Because I get a .deb file

[http://www.frostwire.com/download/?fileid=ubuntu&sid=57491847](http://www.frostwire.com/download/?fileid=ubuntu&sid=57491847) if you use feisty

---

### Post by taurus on 2007-05-27
What is the exact name of the file that you downloaded?  If it's .deb, then you can double click it to install it or install it from a terminal with

```
cd ~/Desktop
sudo dpkg -i filename.deb
```

---

### Post by Benbow on 2007-05-27
I must be doing something radically stupid!! I am using the right download and following your last instructions, get this:

benbow@benbow-desktop:~$ sudo dpkg -i filename.deb
Password:
dpkg: error processing filename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 filename.deb

---

### Post by taurus on 2007-05-27
You need to replace filename with the actual name of the file that you have downloaded.  If you are not sure the name of it, look at the output of this command (and I believe you saved it to ~/Desktop so you need to change to that directory first).

```
cd ~/Desktop
ls -la
```

---

### Post by Benbow on 2007-05-27
I saved it as new file:

drwxr-xr-x  2 benbow benbow     4096 2007-05-27 17:49 .
drwxr-xr-x 69 benbow benbow     4096 2007-05-27 15:31 ..
-rw-r--r--  1 benbow benbow      257 2007-04-12 07:15 blah-00db085529.desktop
-rw-------  1 benbow benbow      432 2007-05-15 22:34 Google-googleearth.desktop
-rw-r--r--  1 benbow benbow     3183 2007-05-10 23:01 kaffeine.desktop
-rwxr-xr-x  1 benbow benbow      199 2007-05-10 19:16 kvirc.desktop
-rw-r--r--  1 benbow benbow 13217378 2007-05-27 17:50 new file
-rw-r--r--  1 benbow benbow        0 2007-05-21 20:31 new file~
-rw-r--r--  1 benbow benbow      202 2007-05-13 18:21 shoutcast-playlist.pls
-rw-r--r--  1 benbow benbow      269 2006-07-20 01:59 sysinfo.desktop
-rw-r--r--  1 benbow root        205 2007-05-12 21:10 xtpconfig.desktop
-rw-r--r--  1 benbow root        237 2007-05-12 21:10 xtpsetup.desktop

---

### Post by taurus on 2007-05-27
From firefox, type in this link [http://www.frostwire.com/download.shm?os=ubuntu](http://www.frostwire.com/download.shm?os=ubuntu) and click the "No, I am not interested" option on the right.  Wait for it to finish downloading and from a terminal, run

```
cd ~/Desktop
sudo dpkg -i frostwire-4.13.1.7.i586.deb
```

---

### Post by Benbow on 2007-05-27
Oh dear! Same result:

benbow@benbow-desktop:~$ cd ~/Desktop
benbow@benbow-desktop:~/Desktop$ sudo dpkg -i frostwire-4.13.1.7.i586.deb
dpkg: error processing frostwire-4.13.1.7.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.13.1.7.i586.deb

---

### Post by taurus on 2007-05-27
What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by Benbow on 2007-05-27
Taurus, problem solved. Thankyou for sticking with me, if we lived in the same country I would buy you a drink!!
Thanks again

---

### Post by Nekiruhs on 2007-05-27
Have you tried just double clicking the .deb?

---

### Post by dunomous on 2007-05-27
What the keyboard issue? I am having this same problem.

---

### Post by gn2 on 2007-05-27
A workaround that works for me is to open Mousepad, type the text then cut and paste it into Frostwire.

After you've done that a few times it starts accepting text inputs directly.

---

### Post by pappapump on 2007-05-27
Well, I know I solved my problem with frostWire.
Frostwire AND azureus worked fine before this last update and never worked after.
I had to burn another feisty CD since i wore the old one out.
Anyway, I did the Azureus install driectly from the add/remove area by selecting all programs.
BUT it seems that frostwire won't work with the newest updates, no Problem.
Limewire has a new package for Deb which works flawlessly.
I had decided to go for FrostWire since the older version of limewire didn't work with ubuntu.
This new version works perfectly.
BUT remember NOT to use any torrent downloader while either limewire or frostwire is running or you'll get severe problems from the magnet linker.
This is true with either windows or linux.
Also remember that when you close azureus, frostwire or limewire that it doesn't completely close.
Right click the minimized icon and choose close then you can be sure its closed.
In my other post i stated that I have had to reinstall Ubuntu several times since these programs crashed.
This isn't simply because these programs won't run but because in the process of removing these apps I managed to break a few other apps along the way.
No remedy for my bungling presented itself so the quickest way was to start all over.
I have confidence that things will only get better for Ubuntu so to me this is all worth the effort.
I'd rather sweat a whole year over the small things with Ubuntu than mess with anything made by Bill Gates ever again.

---


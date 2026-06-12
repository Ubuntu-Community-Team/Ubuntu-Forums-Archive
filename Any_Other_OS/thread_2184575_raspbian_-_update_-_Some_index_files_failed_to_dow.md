---
title: "raspbian - update - Some index files failed to download"
date: 2013-10-29
forum: Any Other OS
---

### Post by Marchello_Lippi on 2013-10-29
Hi all, 

my system failed to update, it lasts few days... What is wrong? 

$ sudo apt-get update -y; sudo apt-get upgrade -y; sudo apt-get autoremove -y; sudo apt-get clean -y
Hit [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy Release.gpg                                                                         
Hit [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy Release.gpg                                                                           
Hit [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy Release.gpg
Hit [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy Release
Hit [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy Release
Hit [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy Release
Hit [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy/rpi armhf Packages        
Hit [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy/main armhf Packages         
Ign [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy/main Translation-en
Hit [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/contrib armhf Packages
Hit [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/non-free armhf Packages
Hit [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/rpi armhf Packages
Ign [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy/rpi Translation-en
Get:1 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/main armhf Packages [9509 kB]
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/contrib Translation-en
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/main Translation-en
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/non-free Translation-en
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/rpi Translation-en
Fetched  1 B in 22s (0 B/s)                                                                                                                                             
W: Failed to fetch  gzip:/var/lib/apt/lists/partial/mirrordirector.raspbian.org_raspbian_dists_wheezy_main_binary-armhf_Packages   Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2013-10-29
Marchello_Lippi; Hi !

Possible file(s) corruption (??).
Try:
```

sudo rm -vf /var/lib/apt/lists/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update ##rebuilds the index files
sudo apt-get upgrade

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Marchello_Lippi on 2013-10-30
Unfortunately, this didn't help. 
Any other suggestions? 


pi@raspberrypi ~ $ sudo rm -vf /var/lib/apt/lists/*
removed `/var/lib/apt/lists/archive.raspberrypi.org_debian_dists_wheezy_main_binary-armhf_Packages'
removed `/var/lib/apt/lists/archive.raspberrypi.org_debian_dists_wheezy_Release'
removed `/var/lib/apt/lists/archive.raspberrypi.org_debian_dists_wheezy_Release.gpg'
removed `/var/lib/apt/lists/lock'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_contrib_binary-armhf_Packages'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_main_binary-armhf_Packages'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_non-free_binary-armhf_Packages'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_Release'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_Release.gpg'
removed `/var/lib/apt/lists/mirrordirector.raspbian.org_raspbian_dists_wheezy_rpi_binary-armhf_Packages'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/raspberrypi.collabora.com_dists_wheezy_Release'
removed `/var/lib/apt/lists/raspberrypi.collabora.com_dists_wheezy_Release.gpg'
removed `/var/lib/apt/lists/raspberrypi.collabora.com_dists_wheezy_rpi_binary-armhf_Packages'
pi@raspberrypi ~ $ sudo rm -r /var/lib/apt/lists/*
pi@raspberrypi ~ $ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists/partial'
pi@raspberrypi ~ $ sudo apt-get update
Get:1 [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy Release.gpg [836 B]
Get:2 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy Release.gpg [490 B]        
Get:3 [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy Release.gpg [490 B]             
Get:4 [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy Release [2035 B]                     
Get:5 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy Release [14.4 kB]                      
Get:6 [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy Release [7218 B]                     
Get:7 [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy/rpi armhf Packages [2863 B]
Get:8 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/main armhf Packages [7414 kB]     
Get:9 [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy/main armhf Packages [11.1 kB]      
Ign [http://raspberrypi.collabora.com](http://raspberrypi.collabora.com) wheezy/rpi Translation-en                                     
Ign [http://archive.raspberrypi.org](http://archive.raspberrypi.org) wheezy/main Translation-en                
Get:10 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/contrib armhf Packages [23.3 kB]                                                                                    
Get:11 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/non-free armhf Packages [48.0 kB]                                                                                   
Get:12 [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/rpi armhf Packages [569 B]                                                                                          
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/contrib Translation-en                                                                                                 
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/main Translation-en                                                                                                    
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/non-free Translation-en                                                                                                
Ign [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/rpi Translation-en                                                                                                     
Err [http://mirrordirector.raspbian.org](http://mirrordirector.raspbian.org) wheezy/main armhf Packages                                                                                                    
  
Fetched 7526 kB in 43s (171 kB/s)                                                       
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirrordirector.raspbian.org_raspbian_dists_wheezy_main_binary-armhf_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2013-10-30
Marchello_Lippi; Hey,

Let's see what the package manager is talking about... I do not know what gzip has to do with it at this time.
Post back the output of terminal command:
```

ls -la /var/lib/apt/lists/partial

```
And let's have a look.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Marchello_Lippi on 2013-10-30
$ ls -la /var/lib/apt/lists/partial
total 33648
drwxr-xr-x 2 root root    4096 Oct 30 06:00 .
drwxr-xr-x 3 root root    4096 Oct 30 05:59 ..
-rw-r--r-- 1 root root 9508667 Oct 28 05:13 archive.raspbian.org_raspbian_dists_wheezy_main_binary-armhf_Packages
-rw-r--r-- 1 root root 9508667 Oct 28 05:13 archive.raspbian.org_raspbian_dists_wheezy_main_binary-armhf_Packages.decomp.FAILED
-rw-r--r-- 1 root root 7710365 Oct 28 05:13 archive.raspbian.org_raspbian_dists_wheezy_main_source_Sources
-rw-r--r-- 1 root root 7710365 Oct 28 05:13 archive.raspbian.org_raspbian_dists_wheezy_main_source_Sources.decomp.FAILED

---

### Post by Bashing-om on 2013-10-30
Marchello_Lippi; Hey !

Once more I am flabbergasted at what I do not know.
This:
[http://forums.debian.net/viewtopic.php?f=10&t=61493](http://forums.debian.net/viewtopic.php?f=10&t=61493)
advised that the mirror may have been in the process of updating, and to try your update at a later time.
I think now it is later. What results now when you "update/upgrade" ?

Or might consider changing your mirror site ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Marchello_Lippi on 2013-10-31
I followed this suggestion 
[http://forums.debian.net/viewtopic.php?f=10&t=108618](http://forums.debian.net/viewtopic.php?f=10&t=108618)

*by subhuman » 2013-10-30 16:57*
*/var/lib/apt/lists/partial/ - what if you just remove the file in that directory?*

And it did the trick: 

[COLOR=#333333][FONT=Lucida Grande]$ sudo rm /var/lib/apt/lists/partial/*[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]$ sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release.gpg[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://raspberrypi.collabora.com]("http://raspberrypi.collabora.com/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release.gpg [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspberrypi.org]("http://archive.raspberrypi.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release.gpg [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://raspberrypi.collabora.com]("http://raspberrypi.collabora.com/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspberrypi.org]("http://archive.raspberrypi.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy Release[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Get:1 [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/main Sources [6252 kB][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://raspberrypi.collabora.com]("http://raspberrypi.collabora.com/")[COLOR=#333333][FONT=Lucida Grande] wheezy/rpi armhf Packages [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspberrypi.org]("http://archive.raspberrypi.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/main armhf Packages[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://raspberrypi.collabora.com]("http://raspberrypi.collabora.com/")[COLOR=#333333][FONT=Lucida Grande] wheezy/rpi Translation-en[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://archive.raspberrypi.org]("http://archive.raspberrypi.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/main Translation-en[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/contrib Sources [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/non-free Sources [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/rpi Sources [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Get:2 [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/main armhf Packages [7414 kB] [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/contrib armhf Packages [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/non-free armhf Packages [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Hit [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/rpi armhf Packages [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/contrib Translation-en [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/main Translation-en [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/non-free Translation-en [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Ign [/FONT][/COLOR][http://archive.raspbian.org]("http://archive.raspbian.org/")[COLOR=#333333][FONT=Lucida Grande] wheezy/rpi Translation-en [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Fetched 13.7 MB in 1min 29s (154 kB/s) [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Reading package lists... Done
[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-10-31
Marchello_Lippi; Well,

Glad you are up and running. But to be honest, post #2 did the same thing in removing the contents of the partial directory.
This command "rm -vf /var/lib/apt/lists/*" is inclusive of this;
 "rm /var/lib/apt/lists/partial/*"
What can I say, strange things happen. As the situation is under control now, please mark this thread as solved (1st post -> thread tools).

As we ->
[INDENT][INDENT]move on to greater things
[/INDENT][/INDENT]

---


---
title: "[SOLVED] Compizfusion"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-01-31
I am trying to run compizfusion. I'm running i810 on ubuntu edgy can anyone help me out?

---

### Post by oedha on 2008-01-31
sudo apt-get install compiz
sudo apt-get update
sudo apt-get install python-compizconfig

set the compiz:==> ccsm

regards;
~E~

---

### Post by emarkd on 2008-01-31
Does your Compiz already work?  If not, go to System > Preferences > Appearance and Select the Visual Effects tab to turn it on.

If you want full control over your new Composited Desktop, install compizconfig-settings-manager in Synaptic

---

### Post by overdrank on 2008-01-31
Please note the OP is using edgy and I believe the OP will have to add some repos. :KS

---

### Post by emarkd on 2008-01-31
Good catch overdrank!  I didn't see that the first time around.

To the OP:  Disregard my previous advice.  It won't work for you.

---

### Post by ssharps711 on 2008-02-01
I'm getting;

Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
  404 Not Found
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/dev Packages                              
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/dev Packages        
  404 Not Found
Get:6 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages [9597B]
Fetched 26.9kB in 1s (15.8kB/s)
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz](http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz)  404 Not Found

Is this ok?

---

### Post by ssharps711 on 2008-02-01
After "sudo apt-get install python-compizconfig"

I get;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-compizconfig

Something is not right.

---

### Post by ssharps711 on 2008-02-01
Bump.

C'mon man, someones gotta know.

---

### Post by jan quark on 2008-02-01
perhaps you have to enable the sources 

go to menu> systesm > ahhhh sources window you will find it I am sure

and check all available sources except the source code and the cd

the run 
```

sudo apt-get update 
```

in the terminal and try to install the needed packages once again

---

### Post by ssharps711 on 2008-02-01
After "sudo apt-get update"

I get:

Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US              
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US          
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Get:3 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release.gpg [307B]              
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                  
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_US             
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release.gpg                                   
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US                   
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Get:5 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release [17.0kB]                
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/dev Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release                                       
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
  404 Not Found
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources            
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/dev Packages                               
Get:6 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages [9597B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/dev Packages                                  
  404 Not Found
Fetched 26.9kB in 1s (17.9kB/s)
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz](http://gandalfn.club.fr/ubuntu/dists/edgy/dev/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

???:confused:

---

### Post by oedha on 2008-02-01
sorry...i didnt notice that you're using edgy......
have you try beryl ?

i am not so sure compiz can be run on edgy....sorry
~E~

---

### Post by barbedsaber on 2008-02-01
If you dont have a really good reason to use edgy, you should try gutsy.

---

### Post by jan quark on 2008-02-01
try this guide, and search the forums first :)
[http://ubuntuforums.org/showthread.php?t=239613](http://ubuntuforums.org/showthread.php?t=239613)

---

### Post by ssharps711 on 2008-02-01
in synaptic manager I have;

Compiz
Compiz-core
Compiz-gnome
Compiz-plugins

That's it.

---

### Post by ssharps711 on 2008-02-01
How do I access source.list? I'm uber newb of 2 days.:)

---

### Post by jan quark on 2008-02-01
```
sudo gedit /etc/apt/sources.lst
```

---

### Post by Tobi-fp on 2008-02-01
Hey there mate.. just run "system --> administration --> software sources" within that windows you have to check the lists on the "third party software".... After that you must enter the synaptic package thing and search for compiz.. Check compiz and gnome-compiz for installation and done.

Hope it helped

---

### Post by jan quark on 2008-02-01
sorry typo
```

sudo gedit /etc/apt/sources.list
```

---

### Post by ssharps711 on 2008-02-01
Nm, I have sourcelist. 

Do I add "deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy aiglx-edgy" before or after all the other stuff?

---

### Post by jan quark on 2008-02-01
just add it at the end
I guess it's not important where

---

### Post by Tobi-fp on 2008-02-01
Anyway, i have almost the same graphics card as you.. Intel i810 right? You have to twist some stuff after the installation anyways.. I can help you with that if you want? The card has been banned from compiz..

---

### Post by ssharps711 on 2008-02-01
K. I've done all that. Now what?

---

### Post by ssharps711 on 2008-02-01
That would be great Tobi. I'm going to need it. I can tell.

---

### Post by Tobi-fp on 2008-02-01
WEll, dont mention it mate.. Do you speak any other language then english? maybe danish or spanish? my english is not that good..

---

### Post by ssharps711 on 2008-02-01
MFing awesome! I love linux! 

Thank you guys very much. Let me know if you ever need anyone taken off of this place (like murdered).

Jk. Seriously thanks.

---

### Post by jan quark on 2008-02-01
make a backup of the file we want to change

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup
```

and now open it with the command
```

sudo gedit /etc/X11/xorg.conf
```

I only apply what is said in the guide posted above

---

### Post by ssharps711 on 2008-02-01
Nah, Tobi. Only English, mis espanol es muy malo. No hablo pero comprendo.

It's running a little on the lsow side.I'm going to shut down and see if that helps. but I think I'm going to need that tweeking.

---

### Post by Tobi-fp on 2008-02-01
so...? how is it?

---

### Post by ssharps711 on 2008-02-01
K. So I'm running on XP now because I couldn't type in firefox on ubuntu. Something happened. Uhmm any help?

---

### Post by Tobi-fp on 2008-02-01
Ok, well.. that sucks.. do you have your cd near you? you should try to reinstall firefox using the cd (you have to active the cd in the software sources list) and then open synaptic.. use the "reinstall for firefox" and you should be good to go.. did the 3d effects work

---

### Post by ssharps711 on 2008-02-01
Yea, 3d effects worked awesome. A little bit of a lag, also, compiz took the close, minimize, and expand keys from the top right of my windows. I'm guessing it is supposed to do that.

I'll just reinstall firefox I guess. brb.

---

### Post by Tobi-fp on 2008-02-01
Well, i guess you dont have that problem in feisty with the banning of the card.. Thats neat.. Hope it works.. you should set this problem as "solved"... Greetings..

---

### Post by ssharps711 on 2008-02-01
K. Will do.

Uhmm yea, I can't type in any of the system boxes either, like search in Synaptic Package manager, nor in search in add/remove, I **can** type in my IM client though.

Kind of strange. Kind of sucks.

---

### Post by ssharps711 on 2008-02-01
Can't type in terminal either.

Damn.:confused:

---

### Post by jan quark on 2008-02-01
why don't you try the latest version of ubuntu gutsy gibbon 7.10 ?
there are many improvements since the edgy version

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Tobi-fp on 2008-02-01
I think i know the problem.. Just take out the ubuntu cd and restart the system,

---

### Post by ssharps711 on 2008-02-01
Just restart the system or completely reinstall?

---

### Post by ssharps711 on 2008-02-01
Oh, I can't move any of my windows either. But I can open the file, edit, view,history,bookmarks, tools, and help.

---

### Post by ssharps711 on 2008-02-01
Ok, so I found a solution. Went into an alternate terminal called Konsole. and typed 

```
metacity --replace&
``` 

Now all of my desklets have boxes around them but I'm assuming I won't need those (desklets) after I get compiz running correctly.

---


---
title: "cant update / install anything 6,06"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by oisuxx on 2008-11-08
ive had problems installing anything after 6.06 on my g3 imac. so im posting this from 6.06. i cant seem to install anything or even update the system i get these errors....


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-powerpc/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-powerpc/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-powerpc/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-powerpc/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-powerpc/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-powerpc/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]

then if i try to open up terminal and get stuff heres what i get, this example im trying to install pan newsreader:

basement@basement-desktop:~$ sudo apt-get install pan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pan
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 507kB of archives.
After unpacking 3781kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  pan
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main pan 0.14.2.91-5ubuntu2
  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pan/pan_0.14.2.91-5ubuntu2_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pan/pan_0.14.2.91-5ubuntu2_powerpc.deb)  404 Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


i get the same thing when i run apt-get update, and when i use the add/remove option from the "start menu"..

can anyone help me out with this, please??

thanks in advance!

---

### Post by cyfur01 on 2008-11-08
First off, you said 6.06 (Drapper), but the links in the posted printouts are actually for Edgy (6.10). Support for Egdy was [recently ended (end of life-cycle).]("http://www.ubuntu.com/news/ubuntu610end-of-life")

I would suggest upgrading to a newer distribution. Otherwise, Drapper (6.06) is the old long-term support (LTS) version, for which you can still get updates.

---

### Post by oisuxx on 2008-11-08
hrmmm. well its says 6.06 when i open up firefox. and i think the live boot disk had 6.06 on it. reguardless, i cant even update to 7 cause i get the same messages. is there a workaround other then re-installing agian?

i tried 8.10 7 and a few others, both live boot disk and alternative, but kept running into problems.

---

### Post by crapple on 2008-11-08
What are the problems you ran into with 8.10?

What are your computer specs.

I might be able to help you get 8.10 running

---

### Post by oisuxx on 2008-11-08
well with all of them i can get it to install. with one it would only load in low graphics mode. the error i got was when the load screen came up i got the error "exploded" and it would go into low graphics to fix the problems.

8.10 i think video=ofonly or whatever it is on yaboot, would just shut down. 

i tried like 6 different versions (7 8 6 live AND alternative) and the only one that worked was what im assumming is 6.06.
 all the alternative versions installed i just couldnt get them to boot after the install. 

i DO know the version i am running, is very speedy. the web browser is quick, and all, but i cant install the programs i need. normally the computer upstairs (running 8.04) i do the easy add/remove and things are great. this is just becoming a pain. i only need it for like 3 programs, audacity, or audour (which i think only runs in gnome), pan newsreader, and JACK audio effects.

i think the fact that since its a g3, updated with 1 gig of ram, its still problematic.

i dont know all my specs for the g3 but its got 1 gig of memory, its a slot loading, orange and white-ish imac

i wanna get a "decent semi-fast" xubuntu running on there. if i could get this dependencies thing working it would be perfect. i know that regular ubuntu is too intense for it. so thats why i went with xubuntu.

---


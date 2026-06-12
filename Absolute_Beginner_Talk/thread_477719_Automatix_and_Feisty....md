---
title: "Automatix and Feisty..."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by AndrewS on 2007-06-18
Good evening

I recently installed Feisty, which works fine.  When I first ran Automatix, it said it could only find Feisty (which was correct) and that it would only work with Edgy.  So I found the right version of Automatix, which was straightforward enough.  However, Update Manager now keeps offering to "upgrade" my Automatix installation to 1.1-4.0-6.10edgy_i386, which sort of seems a retrograde step!  Has anyone else had this, and is there a solution?

TIA

Andrew

---

### Post by aktiwers on 2007-06-18
Just uninstall that version. :)

---

### Post by arnieboy on 2007-06-18
> **AndrewS said:**
> Good evening

I recently installed Feisty, which works fine.  When I first ran Automatix, it said it could only find Feisty (which was correct) and that it would only work with Edgy.  So I found the right version of Automatix, which was straightforward enough.  However, Update Manager now keeps offering to "upgrade" my Automatix installation to 1.1-4.0-6.10edgy_i386, which sort of seems a retrograde step!  Has anyone else had this, and is there a solution?

TIA

Andrew

Please post the results of the following:
```
cat /etc/apt/sources.list
```

---

### Post by AndrewS on 2007-06-22
Arnieboy

This is what I get:

/etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

Thanks

Andrew

---

### Post by Seisen on 2007-06-22
Remove this line or uncomment it.```
deb http://www.getautomatix.com/apt edgy main

```

If you running feisty you'll want to remove or uncomment out all those edgy repos's too.

---

### Post by AndrewS on 2007-06-22
Seisen

Thanks, that seems to have fixed it.

Andrew

---

### Post by stchman on 2007-06-22
> **AndrewS said:**
> Good evening

I recently installed Feisty, which works fine.  When I first ran Automatix, it said it could only find Feisty (which was correct) and that it would only work with Edgy.  So I found the right version of Automatix, which was straightforward enough.  However, Update Manager now keeps offering to "upgrade" my Automatix installation to 1.1-4.0-6.10edgy_i386, which sort of seems a retrograde step!  Has anyone else had this, and is there a solution?

TIA

Andrew

I have Automatix installed on my Feisty laptop, use this version:

[http://www.stchman.com/tools/automatix2_1.1-3.12-7.04feisty_i386.deb](http://www.stchman.com/tools/automatix2_1.1-3.12-7.04feisty_i386.deb)

Hope this helps.

---

### Post by maduranga on 2007-06-24
Thanx. It works. :D

---

### Post by ububaba on 2007-06-29
> **stchman said:**
> I have Automatix installed on my Feisty laptop, use this version:

[http://www.stchman.com/tools/automatix2_1.1-3.12-7.04feisty_i386.deb](http://www.stchman.com/tools/automatix2_1.1-3.12-7.04feisty_i386.deb)

Hope this helps.

I followed your suggestion and got the response that I already have a later version on my box. 
However, when I try to use the one I have, I get this notice! 
[HTML]This version of Automatix is for Ubuntu 6.10 only.[/HTML]

 Aren't we going around in circles?

---

### Post by tarek on 2007-06-29
I don't recommend using Automatix, but that's just me.

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> I don't recommend using Automatix, but that's just me.
Good. My next question is how can I install RAR/UNRAR? I had assumed Automatix would be 
one way out. Whenever I try ```
 sudo apt-get install rar unrar

``` I get stuck at F-Prot which won't install either. Hope you get the drift. Thanks.

---

### Post by tarek on 2007-06-29
I just tried installing rar and unrar and the installation worked, no problems at all and I don't have Automatix
```
sudo aptitude install rar unrar
```

I didn't try F-Prot cuz I don't know what that is.

I attached a screenshot of my Software Sources.

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> I just tried installing rar and unrar and the installation worked, no problems at all and I don't have Automatix
```
sudo aptitude install rar unrar
```

I didn't try F-Prot cuz I don't know what that is.

I attached a screenshot of my Software Sources.

I am not all that interested in F-Prot either but ....This is the outcome from the Terminal

```
$ sudo apt-get install rar unrar
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rar is already the newest version.
unrar is already the newest version.
The following packages were automatically installed and are no longer required:
  cdda2wav ntp-simple libwavpack0 ntp
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up at (3.1.10ubuntu4) ...
 * Starting deferred execution scheduler atd                                    invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up f-prot-installer (0.5.22) ...
dpkg: error processing f-prot-installer (--configure):
 subprocess post-installation script returned error exit status 30
Errors were encountered while processing:
 at
 ubuntu-standard
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am forced to choose one of the following alternatives:
The result is the same...I can't proceed further. Haha

---

### Post by tarek on 2007-06-29
From what I see you have packages that aren't used anymore and again I don't know what f-prot is but it looks like it's causing the problem.

I still have the terminal window opened, this is the output I got when I installed rar and unrar

```
tarek@csmonkey:~$ sudo aptitude install rar unrar
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  rar unrar 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 603kB of archives. After unpacking 1270kB will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com feisty/multiverse rar 1:3.7b1-2 [506kB]
Get:2 http://archive.ubuntu.com feisty/multiverse unrar 1:3.7.3-1 [96.3kB]
Fetched 603kB in 1s (366kB/s) 
Selecting previously deselected package rar.
(Reading database ... 138718 files and directories currently installed.)
Unpacking rar (from .../rar_1%3a3.7b1-2_i386.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from .../unrar_1%3a3.7.3-1_i386.deb) ...
Setting up rar (3.7b1-2) ...
Setting up unrar (3.7.3-1) ...
tarek@csmonkey:~$ 
```

---

### Post by ububaba on 2007-06-29
I totally agree that I must get rid of the F-Prot thingy. Question is how?

---

### Post by tarek on 2007-06-29
I think this should do it:
```
sudo aptitude remove f-prot
```

When it's done, run the following as suggested by the system:
```
sudo apt-get autoremove
```

now update the repository to see if there are any problems:
```
sudo aptitude update
```

and try again:
```
sudo aptitude install rar unrar
```

let me know how it goes.

tk

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> I think this should do it:
```
sudo aptitude remove f-prot
```

When it's done, run the following as suggested by the system:
```
sudo apt-get autoremove
```

now update the repository to see if there are any problems:
```
sudo aptitude update
```

and try again:
```
sudo aptitude install rar unrar
```

let me know how it goes.

tk

Thanks I would follow your suggestion and am hopeful that it will do the tricks. If I don't return soon, it will mean that I have opened the champagne bottle.

---

### Post by ububaba on 2007-06-29
When I run```
sudo aptitude update 
```

at the bottom of the page I get ```

W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

Because I was again made to choose the F-Prot thing. We could not circumvent it. I am going to 
cry perhaps.

---

### Post by tarek on 2007-06-29
You just need to edit your sources.list, let's do it:

1) backup the file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2) edit it:
```
gksudo gedit /etc/apt/sources.list
```

3) find [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release or anything that's called medibuntu and add a # at the beginning of the line to comment it out.

4) save close and run:
```
sudo aptitude update
```

It's gotta work now. If you don't get any errors try the unrar rar command again.

When this thing works I'm the one who's gonna open a champagne bottle :D

---

### Post by ububaba on 2007-06-29
I followed the steps but when I run```
sudo aptitude update

```

I get this at the bottom of the page. I am obviously far more stupid than I had assumed. Thanks
for the patience shown

```
Reading package lists... Done
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by tarek on 2007-06-29
humm...  go to System -> Administration -> Software Sources and click on Authentication tab

Do you find medibuntu there? If you do then select it and click on remove and run: sudo apt-get update

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> humm...  go to System -> Administration -> Software Sources and click on Authentication tab

Do you find medibuntu there? If you do then select it and click on remove and run: sudo apt-get update

Not under Authentication but under Third-Party Software I did find Medibuntu and got rid of the 
whole bunch. When I did run ```
sudo apt-get update
```

in the Terminal I still got```
Errors were encountered while processing:
 at
 ubuntu-standard
 f-prot-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tarek on 2007-06-29
No, recheck the boxes, those are not the problem.

If we cannot get rid of mediubuntu then run this command to get the key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Run this again:
```
sudo apt-get update
```

tk

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> No, recheck the boxes, those are not the problem.

If we cannot get rid of mediubuntu then run this command to get the key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Run this again:
```
sudo apt-get update
```

tk

I was able to run ```
sudo apt-get update
``` however RAR could yet not be installed because
I keep running into F-Prot problem. Darn.

---

### Post by tarek on 2007-06-29
Good, at least we got rid of medibuntu errors.

can you please post the output of the installation. like the one posted before.

---

### Post by ububaba on 2007-06-29
> **tarek said:**
> Good, at least we got rid of medibuntu errors.

can you please post the output of the installation. like the one posted before.

[COLOR="Red"]Terminal output:[/COLOR]

[HTML]$ sudo apt-get updateGet:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:2 http://packages.medibuntu.org feisty Release.gpg [189B]
Ign http://packages.medibuntu.org feisty/free Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Hit http://packages.medibuntu.org feisty Release
Err http://packages.medibuntu.org feisty Release
  
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US
Get:5 http://packages.medibuntu.org feisty Release [2195B]
Ign http://packages.medibuntu.org feisty Release     
Get:6 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release             
Hit http://us.archive.ubuntu.com feisty-security Release
Ign http://packages.medibuntu.org feisty/free Packages              
Hit http://us.archive.ubuntu.com feisty-backports Release           
Hit http://us.archive.ubuntu.com feisty/main Packages               
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Ign http://packages.medibuntu.org feisty/non-free Packages
Ign http://packages.medibuntu.org feisty/free Sources
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://packages.medibuntu.org feisty/non-free Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://packages.medibuntu.org feisty/free Sources
Hit http://us.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://packages.medibuntu.org feisty/non-free Sources
Fetched 2388B in 0s (3958B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
[/HTML]

---

### Post by dpar on 2007-06-29
Hi people, I just did a Google and F-Prot is an antivirus. It's listed in synaptic, so maybe check there and if it's installed, try uninstalling it.
Just a thought.

---

### Post by ububaba on 2007-06-29
> **dpar said:**
> Hi people, I just did a Google and F-Prot is an antivirus. It's listed in synaptic, so maybe check there and if it's installed, try uninstalling it.
Just a thought.

Thanks for your contribution. I got rid of F-Prot from Synaptic and then tried to install RAR
 but yet it talks of failure in processing dpkg...See at the end of this output:

```
~$ sudo apt-get install rar 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rar is already the newest version.
The following packages were automatically installed and are no longer required:
  cdda2wav ntp-simple libwavpack0 ntp
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up at (3.1.10ubuntu4) ...
 * Starting deferred execution scheduler atd                                    invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 at
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ububaba on 2007-06-29
Despite the error message RAR has been installed. That is almost a happy ending for me. 
Thanks a lot guys for all the help....;););)

---

### Post by tarek on 2007-06-29
> **ububaba said:**
> Despite the error message RAR has been installed. That is almost a happy ending for me. 
Thanks a lot guys for all the help....;););)

I was out for awhile ... it's good that you got rar working and got rid of the mediubuntu problem but you should clean up the system from packages that you no longer use.

Run the following command to clean it up:
```
sudo apt-get autoremove
```

tarek

---

### Post by Do0odz on 2007-07-01
I'm a new Ubuntu feisty fawn user ..
When installing automatix I keep getting this msg "E: Type '&#8220;deb' is not known on line 43 in source list /etc/apt/sources.list"
 in the terminal after entering this command "sudo apt-get update"

what should  I do ??

---

### Post by tarek on 2007-07-01
> **Do0odz said:**
> I'm a new Ubuntu feisty fawn user ..
When installing automatix I keep getting this msg "E: Type '“deb' is not known on line 43 in source list /etc/apt/sources.list"
 in the terminal after entering this command "sudo apt-get update"

what should  I do ??

Can you post your sources.list please?

Go to /etc/apt/sources.list and copy the content of the file here.

---

### Post by Do0odz on 2007-07-02
> **tarek said:**
> Can you post your sources.list please?

Go to /etc/apt/sources.list and copy the content of the file here.

Hope this is right lol .. 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
â€œdeb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty mainâ€
â€œdeb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty mainâ€

---

### Post by tarek on 2007-07-02
The last two lines should not be quotes

"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main"
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main"

If you don't want to use them then replace the quotes with # like this:

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

Save, exit and run this command to check:

sudo aptitude update

tarek

---

### Post by Do0odz on 2007-07-02
> **tarek said:**
> The last two lines should not be quotes

"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main"
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main"

If you don't want to use them then replace the quotes with # like this:

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

Save, exit and run this command to check:

sudo aptitude update

tarek

Thanks Tarek :) 
but I got another problem after entering sudo apt-get update at the end I got the following error : "E: Some index files failed to download, they have been ignored, or old ones used instead."

and after entering  sudo apt-get install automatix2 , I got "E: Couldn't find package automatix2"

I'm seriously a new user lol I've only been using it for 4 days now .. :)

---

### Post by tarek on 2007-07-03
I think you're getting this error because you have three edgy packages and you're running feisty.

Add # to the beginning of these lines:

deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all


To install automatix remove # from:

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by stchman on 2007-07-03
> **ububaba said:**
> I followed your suggestion and got the response that I already have a later version on my box. 
However, when I try to use the one I have, I get this notice! 
[HTML]This version of Automatix is for Ubuntu 6.10 only.[/HTML]

 Aren't we going around in circles?

The one I have works on Feisty with no problems.  I have only used it once or twice so I have not thoroughly tested it.  I prefer to install my apps through apt-get.

---


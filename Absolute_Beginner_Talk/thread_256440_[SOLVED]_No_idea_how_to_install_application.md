---
title: "[SOLVED] No idea how to install application"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Repus on 2006-09-13
Hello

I am less then a week new to Ubuntu and can’t quite figure out the synaptic tool. I would like to install Bacula. I searched for bacula and found a dozen or more bacula-named things to install. The problem is whenever I select one of them I get various discrepancy or dependency warnings. So naively I find the items it says I need and try to install them. Unfortunately I get yet more warnings or worse just a msg that’s says it “needs (xyz) but wont install it” …kind of a snotty msg actually. 

I have walked down the tree of every bacula named thing I can find in synaptic, tried to install every dependency it has and in 3 days I haven’t been able to select a single thing that will just install.

I have read every post on the forums about bacula, probably half about synaptic and the first 7 pages retuned by google on the topic of ubuntu, synaptic, and bacula.

Please help

---

### Post by Crayoneater on 2006-09-13
it works for me to install bacula with synaptic...i just open synaptic, search for bacula, double click the one that says "bacula", then it tells me i need to install other dependencies, i select mark, then i click apply, then apply again and all works fine...

make sure your system is up to date by typing this in a terminal:
sudo apt-get update
sudo apt-get upgrade

then try installing bacula again
sudo apt-get install bacula

---

### Post by misfito on 2006-09-13
Hello 
I'm also a new user and I have no idea of how to install apps using ubuntu neither :confused: . I've been trying to install google earth with no sucess. I've tried to install some other apps and I end up on the download window with no clue of what to do next. Because when I opened the file I just downloaded, another window appears with the folder containing the app I'm wishing to install, i double clic on the folder and the folder opens with all the files that came with the app, then when I tried to open the installer another windows popups that said "open file" but I got no available application to run the installer.](*,) 
I just installed Ubuntu today, and I know is hard to learn how to do many things when you just do the switch from windows to linux. Because I'm still acostume to of how windows works...
The synaptic package manager is a little hard to use (at least for a non experience user like me) even though it has many apps ready to be installed.
Well, I hope that there's someone out there that could give me a hint.
Any help would be really appreciate. :)

---

### Post by Crayoneater on 2006-09-13
can you be more specific as to what you are wanting to install...there are different ways to install different files...i think google earth has a file with a .bin extension or something....you can probably just double click that and it will install it...you might have to check the files permissions so that it is executable

---

### Post by andb on 2006-09-13
Here is a great page about instsalling: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Linux is totaly different from windows. Basically forget what you know. Almost everyhting on ubuntu can be installed using centralized repositories. You add these software collection points in a file called /etc/apt-get/sources.list  You can then use the cetralized software installers, synaptic or apt-get or aptitude, to do everything for you. All you have to know is the name. installing packages by themselves or compiling code is rarely needed for a typical user.

---

### Post by Arevos on 2006-09-13
> **misfito said:**
> I've been trying to install google earth with no sucess.
Automatix (getautomatix.com) makes installing Google Earth, along with many other applications not included with Ubuntu by default, a case of point and click.

---

### Post by Repus on 2006-09-13
It appears that my problem has to do with repositories. I’m guessing this since no matter which application I choose to install I get an error and whenever I update the list (apt-get etc...) that generates errors too. 

Thanks for the suggestions. I'm off to read about repositories now. Nothing is ever easy. Seriously its 2006 already, where is HAL? Aside from the killing humans quirk that was a good OS.

---

### Post by Arevos on 2006-09-13
Could you report the errors you receive when you type "sudo apt-get update" into a terminal? Also, whilst this is a rather obvious thing, is the computer you're trying to install applications from connected to the internet?

Another thing to look at would be /etc/apt/sources.list, which is the file that contains details on all of the repositaries being used in apt.

---

### Post by Repus on 2006-09-14
> **Arevos said:**
> Could you report the errors you receive when you type "sudo apt-get update" into a terminal? Also, whilst this is a rather obvious thing, is the computer you're trying to install applications from connected to the internet?

Another thing to look at would be /etc/apt/sources.list, which is the file that contains details on all of the repositaries being used in apt.

Here are the errors. yes the computer is connected to the net, its what i am currently using.

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages [619kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [71.4kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages [821kB]
61% [8 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Sub-process gzip returned an error code (1)
Fetched 729kB in 2m4s (5870B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



and here is my sources.list file

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http:://us.archive.ubuntu.com/ubuntu dapper main restricted universe
deb http:://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universedeb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by Najand on 2006-09-14
Do you have a probelm with your internet connection or using proxy, firewalls or something similar?

---

### Post by buckethead27 on 2006-09-14
if you download a .deb file, then just double click and install.

---

### Post by Repus on 2006-09-14
> **Najand said:**
> Do you have a probelm with your internet connection or using proxy, firewalls or something similar?

None. The firewall im using is currenlty letting the ubuntu box do whatever it likes. A direct pass through. I have watched all the connections and nothing is stopped.

---

### Post by Repus on 2006-09-14
BTW thanks for everyones help so far.

---

### Post by Najand on 2006-09-14
Try to make another sources.list from [www.ubuntulinux.nl/source-o-matic](www.ubuntulinux.nl/source-o-matic) again, without entering your country code. Copy and Paste it to your /etc/sources.list and try:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Repus on 2006-09-14
> **Najand said:**
> Try to make another sources.list from [www.ubuntulinux.nl/source-o-matic](www.ubuntulinux.nl/source-o-matic) again, without entering your country code. Copy and Paste it to your /etc/sources.list and try:
```

sudo apt-get update && sudo apt-get upgrade

```

Results. It had issues at "Get:6" seems to have timed out and then of course the normal "zip" errors at the end

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34.8kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [71.4kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [46.3kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [15.4kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [3129B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [821kB]
88% [22 Packages gzip 0] [10 Packages bzip2 1798144]                 280kB/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4693kB in 2m20s (33.4kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Najand on 2006-09-14
Hmm, it seems it is just working but something happens with your network and something like firewall or a router just terminate your connection.

---

### Post by Repus on 2006-09-14
> **Najand said:**
> Hmm, it seems it is just working but something happens with your network and something like firewall or a router just terminate your connection.

For this system there is effectivly no firewall. Do you have any ideas what the problem may be or where else I could look?

After reading some other forum posts I downloaded the "offending" gzip using wget. Now what? I have a large gz file. How do I make that integrate so its usable in synaptic?

---

### Post by Repus on 2006-09-15
In case anyone is curious I figure out the apt-get issue I had. While looking though my network IDS logs I found pages upon pages of dropped packets due to improper formation. When I checked further I found most of them coincided with my ubuntu update attempts. To fix this problem I had to create an IDS rule that ignored improper packets going from my system to the sources.list servers and visa versa. Not the best solution but it immediately worked.

---


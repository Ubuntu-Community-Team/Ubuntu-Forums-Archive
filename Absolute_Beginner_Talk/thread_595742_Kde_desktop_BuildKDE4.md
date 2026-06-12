---
title: "Kde desktop Build/KDE4"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by sn1flz on 2007-10-29
Since I'm new to linux AND to forum posting I'm going to just do what i've seen others do, so i'm sorry if i overpost...bare with me :)

I'll start by saying I'm using kubuntu gutsy 7.10 on an nvidia 6600 gt (?) video card

I went here: and noticed an update to kde desktop
[http://www.kde.org/announcements/announce-4.0-beta3.php](http://www.kde.org/announcements/announce-4.0-beta3.php)

after following some links i ended up here:
[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

where i scrolled down to kubuntu and the gutsy note to add *yes i didn't initially read required software, i assumed i had it all. -lesson 1 learned right there.-anyhow.

i followed all the instructions but when i got to the command cmakekde it kept saying command not found. I read the info in troubleshooting, about You might want to do a cmake $KDE_SRC/KDE/MODULE_NAME prior to compiling any kde modules (like kdelibs, kdepimlibs etc.) but i have NO idea what all that means. so-i backtracked to the required software and made sure it was all installed-when i got to svn (?) i noticeed 109384039483409 entries on synaptic ( i was copying and pasting each required item into synaptic to see if it was marked 'installed') - as far as I can tell, I have all required software, but I'm not sure since i get results like websvn,svnload, etc. (again NO idea what all that means, even after reading the info on the side)

I'm pretty much stuck here. I'm new, don't know how to undo what i've done, or to finish what i've started. it doesn't find the kde library, nor does it know what i mean when i type in the command cmakekde

here's a copy of what it says
sn1flz@sn1flz-desktop:~$ cd kdelibs
sn1flz@sn1flz-desktop:~/kdelibs$ cmakekde
bash: cmakekde: command not found
sn1flz@sn1flz-desktop:~/kdelibs$

i've tried to google search "command" , "command line not found" but i'ts too general, too many results come up that aren't relevant to my issue. 

If someone can help i'd really appreciate it. My boyfriend is stumped even, as I didnt tell him what i was doing / did until i got the error. 

I'm afraid I tried to do something I'm just not ready to do yet.

1. i need to either remove what damage i may have done
2. or i need to successfully complete the installation.

I dont even know if i done any damage yet, i'm afraid to reboot and find out.

---

### Post by JBAlaska on 2007-10-29
First open a terminal and paste (make sure synaptic package manager is not running);
```
sudo aptitude install dbus-x11 libqt4-dev libqca2-dev libeigen-dev \
libstreamanalyzer-dev libsoprano-dev libstrigiqtdbusclient-dev
```
Hit enter

**Now it might be a good idea to stop here and forget about installing kde4**, If your determined to install a beta (and most likely unstable) desktop environment you will have to follow the remainder of the howto. 
First you will have to add this script ```
http://techbase.kde.org/Getting_Started/Increased_Productivity_in_KDE4_with_Scripts/.bashrc
``` to your ~/.bashrc file or the **cs** in line 2 below will not work.

Then add these lines ONE BY ONE in the terminal, hitting enter after each;
```

cd   
**cs**
mkdir KDE && cd KDE
svn checkout svn://anonsvn.kde.org/home/kde/trunk/KDE/kdelibs
cd kdelibs
cmakekde
```

[b] What's Happening

We change to the base source directory (line 1) then make and go into the KDE directory (line 2). We download the sources for kdelibs using subversion (line 3), go into the new ~/kde/src/KDE/kdelibs directory (line 4), and commence the build (line 5). This will leave us in the kdelibs build directory after the build is completed. [/b]

That should get you ready for the next steps ( kdepimlibs,  kdebase).
```
http://techbase.kde.org/Getting_Started/Build/KDE4#kdelibs
```

Hope this helps somewhat.

---

### Post by sn1flz on 2007-10-29
thanks....im not sure much about linux...but i know in ANY language what unstable means...it means wait before i mess with it..thanks for your help. :)  im glad at least the pc won't go defunct when i boot up now.

---


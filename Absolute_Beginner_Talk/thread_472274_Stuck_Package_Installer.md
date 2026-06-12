---
title: "Stuck Package Installer"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by davidwfox on 2007-06-12
How do I close a stuck package installer?

Several days ago I attempted (unsuccessfully) to install the Java runtime environment. It appears that the failed attempt to install the JRE has locked up the package installer because now, if I try to install anything else, I get an error pop-up advising:  "Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'Update manager', 'aptitude' or 'Synaptic' first." 

How do I close whatever application was trying to install the JRE? And then how do I successfully install the JRE?

---

### Post by WNDS1701 on 2007-06-12
> **davidwfox said:**
> How do I close a stuck package installer?

Several days ago I attempted (unsuccessfully) to install the Java runtime environment. It appears that the failed attempt to install the JRE has locked up the package installer because now, if I try to install anything else, I get an error pop-up advising:  "Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'Update manager', 'aptitude' or 'Synaptic' first." 

How do I close whatever application was trying to install the JRE? And then how do I successfully install the JRE?

Hello davidwfox!

I had a similar problem, but I am not sure, if I can give you a good advice with yours. What happened with me was that synaptic once screwed up, so I could not use any package manager. I had to relaunch Synaptic and it gave me back a command line which I typed into a terminal (with sudo!) and afterwards it worked.

To your problem: Which package manager did you use? Start the same package manager and then try again. If it doesn't work, please post a more detailed problem description.

Cheers! ;)

---

### Post by zvacet on 2007-06-13
Synaptic doesn´t work because you didn´t accept Java licence agreement,so Java is not completly installed.That make you troubles.Try to uninstall Java with synaptic and reinstall it with synaptic again if you want to.Both ways you will have synaptic again.If this doesn´t work post here and we will see what to do next.

---

### Post by davidwfox on 2007-06-13
Thanks WNDS1701 - your comments have at least thrown up a few more clues.

Launching Synaptic brought up:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't understand the significance of, or the action required by, the last line but opening Terminal and running the previous line, firstly without sudo and then with sudo, resulted in:
david@david-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
david@david-laptop:~$ sudo dpkg --configure -a
Password:
david@david-laptop:~$ 

I then tried a re-install of an application and am once again stuck because of the Java issue.
I reach the point of:  Installing dependencies - preparing sun-java5-bin...  
and that's where everything comes to a standstill.

Going back to Terminal and repeating the process now results in:
david@david-laptop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
david@david-laptop:~$ 

Re-running Synaptic results in:
Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

So, this time it's not Synaptic that's locked, it's something else. How / where do I:
1.  Locate the app that's locking it this time;
2.  Close that app;
3.  Get JRE installed properly so that it stops blocking every installation I try??

---

### Post by davidwfox on 2007-06-13
Thanks zvacet - looks like we were both preparing our posts at the same time.

Yes, I'm sure you're right, JRE is only partially installed. I don't recall accepting/not accepting the licence, it was a few days ago and too much has happened since then.

Once I discover how to regain access to Synaptic (after unlocking whatever has locked me out this time!), how do I go about uninstalling  and then re-installing JRE? I carefully followed all the installation instructions for JRE and currently have a symbolic link:
Link to libjavaplugin_oji.so
sitting on my Desktop.

---

### Post by zvacet on 2007-06-13
```
sudo apt-get  --purge remove sun-java5-bin
```

Or you can do it manualy.First detect where is Java package

```
whereis java
```

and you will get list of directories with java files.Go to the each of them (this is for example)

```
cd /usr/bin
```

and when you are inside

```
sudo rm -r file_name
```
[B][B]
 file_name = name of java file in directory[/B][/B]

---

### Post by davidwfox on 2007-06-13
Thanks zvacet - we're getting there. I did a search (whereis java) and a manual removal of each of the files that I came up with. I did a further "whereis" and got a nil list, then for interest I tried the automated method. That resulted in:
david@david-laptop:~$ sudo apt-get  --purge remove sun-java5-bin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
david@david-laptop:~$ sudo dpkg --configure -a
david@david-laptop:~$ sudo apt-get  --purge remove sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java5-bin sun-java5-jre
0 upgraded, 0 newly installed, 2 to remove and 50 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing sun-java5-bin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing sun-java5-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-laptop:~$ 
so there's still a couple in there that we need to fix. What's my next step?

---

### Post by Anicka on 2007-06-13
Maybe you could try to reinstall it just as suggested by apt-get
```
sudo aptitude reinstall sun-java5-bin sun-java5-jre
```
When I did my original install with aptitude, the terminal turned into a licence-agreement-form,and by tabing to the place where it said "ok" and punching enter, the program installed correctly.

I hope this helps you.

---

### Post by Outrunner on 2007-06-13
```
sudo dpkg --configure -a
```

The error message even tells you what to do...

---

### Post by davidwfox on 2007-06-13
Anicka - ran the re-install and it gave:
david@david-laptop:~$ sudo aptitude reinstall sun-java5-bin sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial apport apport-gtk capplets-data file firefox 
  firefox-gnome-support gimp gimp-data gimp-python gnome-control-center 
  gnome-panel gnome-panel-data hwdb-client-common hwdb-client-gnome 
  libexif12 libfreetype6 libgimp2.0 libgnome-window-settings1 libmagic1 
  libmetacity0 libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libslab0 
  libsmbclient linux-generic linux-headers-generic metacity metacity-common 
  python python-apport python-gdbm python-minimal python-problem-report 
  python2.5 python2.5-minimal rdesktop tzdata unattended-upgrades 
  update-manager update-manager-core vim-common vim-tiny xscreensaver-data 
  xscreensaver-gl 
The following packages will be REINSTALLED:
  sun-java5-bin sun-java5-jre 
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 50 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
david@david-laptop:~$ 

There were still 6 Java5-related files on the system. I didn't know how to locate them within Ubuntu - whereis java5 didn't help - so I logged back into Win XP and located them from there. The -bin and the -jre files were in /var/cache/apt/archives, then there are 3 x 1 kb Desktop files in  /usr/share/app-install/desktop and a 5 kb XPM file in /usr/share/app-install/icons. 

I used the manual method of removing the -bin and -jre files as advised by zvacet (#6) and now I'm rid of them. Hope I did the right thing there! (I'm assuming the 4 remaining files in the /app-install sub-directory are of no significance.)

So, now that I've cleared out everything that was Java- or Java5-related, what's the best method of getting the JRE correctly loaded onto the system?

Just for the record, the 2 files I deleted were sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb and sun-java5-jre_1.5.0-11-1ubuntu2_all.deb - 22 MB and 7 MB respectively.

---

### Post by Anicka on 2007-06-13
Try something like this:
```
sudo updatedb
locate java5
rm /the/files/given/by/locate (might be dangerous and might need sudo)
sudo aptitude update
sudo aptitude install sun-java5-bin
```

---

### Post by davidwfox on 2007-06-13
Anicka -
It went well until the last line:
Fetched 3B in 8s (0B/s)                                                         
Reading package lists... Done
david@david-laptop:~$ sudo aptitude install sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial apport apport-gtk capplets-data file firefox 
  firefox-gnome-support gimp gimp-data gimp-python gnome-control-center 
  gnome-panel gnome-panel-data hwdb-client-common hwdb-client-gnome 
  libexif12 libfreetype6 libgimp2.0 libgnome-window-settings1 libmagic1 
  libmetacity0 libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libslab0 
  libsmbclient linux-generic linux-headers-generic metacity metacity-common 
  python python-apport python-gdbm python-minimal python-problem-report 
  python2.5 python2.5-minimal rdesktop sun-java5-jre tzdata 
  unattended-upgrades update-manager update-manager-core vim-common 
  vim-tiny xscreensaver-data xscreensaver-gl 
The following packages will be upgraded:
  sun-java5-bin 
1 packages upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
Need to get 0B of archives. After unpacking 66.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
david@david-laptop:~$

---

### Post by Anicka on 2007-06-13
You have many kept back packages. Is there any reason why you haven't updated your system. Run "sudo aptitude upgrade" to do that. Maybe you need to run "sudo aptitude -f install" to force those installs and then try to install the java again.

---

### Post by zvacet on 2007-06-13
There was no need to delete files from var/cache/apt/archives because they are like setup files in windows.One more thing I would like to know is why don´t you install Java from synaptic?I belive you have newest version there.

---

### Post by Anicka on 2007-06-13
> **zvacet said:**
> There was no need to delete files from var/cache/apt/archives because they are like setup files in windows.One more thing I would like to know is why don´t you install Java from synaptic?I belive you have newest version there.

The reason why I recommended using aptitude (or apt-get if you would prefer) is that most install problems and java seems to come from an unsuccessful attempt to install it with synaptic. It seems that the licence agreement thingy is the problem. It also seams as only after a complete clean uninstall can it be installed again. Just search the forum and you'll realise the magnitude of this issue.

---

### Post by davidwfox on 2007-06-13
Anicka - many thanks - we're steadily getting there. I have no idea why the update hadn't taken place, however 49 files have now been downloaded. The update has progressed to the point where I now have a Terminal on screen, with a blue background on which is Package Configuration.  Superimposed on the window are the Java licence terms, with the heading Configuring sun-java5-bin. At the bottom of the licence is <ok>. 

I do now recall this coming on-screen during my initial installation, and I had the same problem then as I have now - how on earth do I accept this? There is nowhere to click on Agree or Accept or Yes. I can't edit the body of the Terminal window. I can click on each of the normal 6 tabs along the menu bar, but that's it. How do I accept the licence agreement?

---

### Post by davidwfox on 2007-06-13
zvacet - I am only following the advice you guys give me - I'm told to delete anything Java-related and out they go, wherever I find them. At this early stage of my Linux / Ubuntu experience I have absolutely no idea what is where or what anything is for. It's like following a recipe to make a cake - you say it, I do it.

Anyway, the archive files are back again, although I notice the byte sizes are marginally different to the ones I deleted even though they are similarly named. Not much different, just slight.

But Anicka appears to be correct about this licence thingy - see my previous post in reply.

Why don't I install from Synaptic? I have no idea, I don't know one from the other. As above, I just follow the advice you guys offer.

---

### Post by Anicka on 2007-06-13
Try one of thesesuggestions: [http://ubuntuforums.org/showthread.php?t=472524&highlight=java+install](http://ubuntuforums.org/showthread.php?t=472524&highlight=java+install)

---

### Post by silkstone on 2007-06-13
David - I remember having the same problem when I reached the licence screen - how to accept it.

Scroll down (arrow keys if necessary) so you can see the YES or ACCEPT button or whatever it's called, then use the left/right or up/down arrow keys (can't remember which) until YES changes colour, then hit Return. :)

Note that the mouse does not work in this screen.

---

### Post by davidwfox on 2007-06-13
Guys - it's 0120 hr and I'm too tired to battle with this any longer tonight. I'll attack it again when I wake up and post the result. Thanks for all your help.

---

### Post by zvacet on 2007-06-13
> It also seams as only after a complete clean uninstall can it be installed again.

I agree of course.But i tryed to install both ways and find out that install with synaptic is easyer for many reasons.One of them is acceptance of licence agreement.It is seams to me that many people are confused when they get to that point.It is easer to accept licence when you instll with synaptic because you have good graphic and all you have to do is chek box on the left and hit forward.

To **davidwfox**

Sorry for not get you more specific advice.My mistake.

---

### Post by davidwfox on 2007-06-13
Complete success!!!

My grateful thanks to each of you who offered comments and advice. Your collective efforts have completely solved the problem. I've just installed two apps that previously became stuck because of the JRE thing; this time they each loaded without problem.

Now I have to address a network problem that's appeared - but that's another thread.

Again, my sincere thanks to each of you.

---


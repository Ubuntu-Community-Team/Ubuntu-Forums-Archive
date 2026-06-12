---
title: "wine: is it just me or is it hard to use?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-03
I have wine instalel dbu tI have no idea how to use it. I want to use dvdshrink...

so how do i get it running in wine, or better yet, how do i use wine at all?


robi

---

### Post by Jerry N on 2007-11-03
Check at      [http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)  

Jerry

---

### Post by Presto123 on 2007-11-03
Honestly, I would update to the latest Wine program. It is much easier to use than the old(er) version. Go to this site: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Copy and paste that into your terminal and let it do its thing, then go into system/Administration and go to update manager and start it up. It should show the new Wine (0.9.47) as an update. I would remove your previous Wine beforehand, though, in synaptic.

It should allow you to use the Wine Windows Emulator (Right click on program to show how to open.) afterwards, and if that doesn't work for your program we can move on to other attempts.

---

### Post by SomeGuyDude on 2007-11-03
From what I've seen with the new Wine it's pretty simple. Find a Windows installer file, and when you download it Firefox gives you the option to run it via Wine. Then, any software you've installed with it showed up in Applications -> Wine -> Programs.

Unless that's just the new one and the older was tougher to use. So far I've put installed a handful of applications this way and it was just like using Windows.

---

### Post by beanco on 2007-11-03
I am very confused now.

I used

```
sudo apt-get remove wine
```

to get rid of what I had, then followed the instructions at winehq and got this


```
rob@rob-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  openoffice.org-writer openoffice.org-impress openoffice.org-filter-mobiledev
  libevent-execflow-perl openoffice.org-draw openoffice.org-java-common
  libfame-0.9 libintl-perl libpvm3 openoffice.org-math libevent-rpc-perl
  python-uno gtk2-ex-formfactory-perl transcode anyevent-perl gocr
  libevent-perl libnetpbm10 hal-info openoffice.org-base openoffice.org-calc
Use 'apt-get autoremove' to remove them.
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
rob@rob-desktop:~$ 


```

what I do wrong?

robi

---

### Post by maestrobwh1 on 2007-11-03
That has nothing to do with wine.  I get this all of the time on one of my machines and it drives me nuts.  I don't know what causes the system to lock apt when no apt applications are running.  If you know how to bring up your process table, you can check to see if anything with "apt" is running.

Also, I don't like how apt-get suggests removing things it should not remove.  I have had it remove stuff I needed (i.e. my network manager - thus killing my ability to connect).  I suggest you use "aptitude" in place of apt-get.  It is a smarter frontend for apt.

At any rate:

do this in terminal

sudo rm var/cache/apt/archives/lock

and then it will ask you to enter your password.  This removes (deletes) the lock file, and there may be a better way to do this, but it is quick and dirty so that apt can do things.  If someone knows how to keep this from happening, post here!

then 

sudo aptitude update 
sudo aptitude install wine

or in one line
sudo aptitude update && sudo aptitude install wine

if it tells you then that there is another 'lock" file somewhere else, sudo rm [path] that as well and repeat the procedure to install wine.

---

### Post by MSchenker on 2007-11-03
> **Presto123 said:**
> Honestly, I would update to the latest Wine program. It is much easier to use than the old(er) version. Go to this site: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Copy and paste that into your terminal and let it do its thing, then go into system/Administration and go to update manager and start it up. It should show the new Wine (0.9.47) as an update. I would remove your previous Wine beforehand, though, in synaptic.

It should allow you to use the Wine Windows Emulator (Right click on program to show how to open.) afterwards, and if that doesn't work for your program we can move on to other attempts.

Thanks for the instructions on Wine.  I was also confused!  But I downloaded the latest version of Wine and it loaded fine.

I am trying to install Irfanview.  I downloaded the iview410_setup.exe file.  Then I right clicked on it.  I saw the option "open with Wine windows emulator."  I choose that, and it starts working, but then it just stops.  I don't receive any error messages or anything, but the software does not install.

Did I do something wrong?

Thanks for your help.

Matt

---

### Post by Presto123 on 2007-11-03
> **MSchenker said:**
> Thanks for the instructions on Wine.  I was also confused!  But I downloaded the latest version of Wine and it loaded fine.

I am trying to install Irfanview.  I downloaded the iview410_setup.exe file.  Then I right clicked on it.  I saw the option "open with Wine windows emulator."  I choose that, and it starts working, but then it just stops.  I don't receive any error messages or anything, but the software does not install.

Did I do something wrong?

Thanks for your help.

Matt

I know it does that on certain programs. Some files Wine has problems with. Try using either Wine launcher or Wine console. This involves more steps, but may help. Right click, Open with other application, and use a custom command. Browse for one or both programs in the custom command area and see what happens.

---

### Post by MSchenker on 2007-11-03
> **Presto123 said:**
> I know it does that on certain programs. Some files Wine has problems with. Try using either Wine launcher or Wine console. This involves more steps, but may help. Right click, Open with other application, and use a custom command. Browse for one or both programs in the custom command area and see what happens.

When you say "Wine launcher" and "Wine Console" are you referring to this path:
Applications > Wine > Configure Wine

I'm still getting a grasp of this system, so sorry if I'm missing something obvious.

Thanks,
Matt

---

### Post by the_rajah on 2007-11-03
I'm having Wine problems, too. I use it on my old 6.06 LTS machine and it works pretty well, but on 7.10 it does absolutely nothing. I can double click on an executable and nothing happens, I right-click and select run with Wine and nothing happens. I can go to "Configure Wine" in the applications menu and try to run that, but absolutely nothing happens.  I've installed and removed it 4 times total now and even rebooted in between re-installs and nothing....  I've just got a couple of older Windows programs that I'd like to run with it, but zero luck.

I've had XP installed in Virtualbox and that ran very well, but XP can't access my local drives or network so that's not much help. I couldn't get a "bridge" to work, admittedly probably due to my newbie mistakes.

Anyway, this isn't helping anyone other than me by venting a little of my frustration. Thanks!

---

### Post by P4man on 2007-11-03
After installing wine, make sure you run winecfg at least once.
Open a console and type

```
winecfg
```

 Choose your windows version (I would suggest XP). You probably don't have to change anything else there, so just exit

 If you have not run winecfg, nothing will work in wine!

---

### Post by P4man on 2007-11-03
> **the_rajah said:**
> . I can double click on an executable and nothing happens, I right-click and select run with Wine and nothing happens. I can go to "Configure Wine" in the applications menu and try to run that, but absolutely nothing happens.

Try running it in a console, at least you will see the error. Sometimes it is because you need to install some DLL, like Visual Basic 6 before the windows apps will run under wine. So open console, and first try "winecfg". If that doesnt work, something is screwed. 

Assuming that works, try launching the app from the console. Open a console, type "cd /home/yourname/wherever_the_file_is" and then "wine name_of_app". Post the error message here, I'm betting on a missing DLL.

---

### Post by the_rajah on 2007-11-03
Aha! Running winecfg from CLI, I get:

[INDENT]~$ winecfg
/usr/bin/wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory[/INDENT]

Looks like something is missing. This is a very fresh install of wine using apt-get. Same result as when installed via add/remove.  Ideas? Older version works fine on 6.06LTS with the same WIndows program I'm trying on 7.10 - LeapFTP.

Thanks for the suggestions.  :)

---

### Post by P4man on 2007-11-03
Are you running 64 bit version of Ubuntu perhaps ?

---

### Post by Presto123 on 2007-11-03
> **MSchenker said:**
> When you say "Wine launcher" and "Wine Console" are you referring to this path:
Applications > Wine > Configure Wine

I'm still getting a grasp of this system, so sorry if I'm missing something obvious.

Thanks,
Matt

No. When you right click and see "Open with other App" use that and go down to the bottom where it says, "Use Custom Launcher" and hit "Browse" and a list of programs will come up.

---

### Post by poudin on 2007-11-03
just a question...you mention in your initial post you installed wine to use DVDShrink...are you aware that there is a linux version of the program that you can run natively???

it is best to avoid use of wine to emulate programs...unless you can't find a linux equivalent.

just a thought.

---

### Post by Duck2006 on 2007-11-03
You can find dvdshrink in Synaptic Package Manager.

---

### Post by the_rajah on 2007-11-03
*"Are you running 64 bit version of Ubuntu perhaps ?"*

If that was directed to me. No, it's not the 64 bit version.

---

### Post by the_rajah on 2007-11-04
Further attempts...  Here's what I tried next..

I followed the procedure for Gutsy here:  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

It failed.
[INDENT]
~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.9MB of archives.
After unpacking 48.9MB of additional disk space will be used.
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main wine 0.9.48~winehq0~ubuntu~7.10-1 [10.9MB]
Fetched 10.9MB in 48s (222kB/s)                                                       
Selecting previously deselected package wine.
(Reading database ... 96320 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
roger@roger-ubuntu:~$ winecfg
bash: /usr/bin/winecfg: No such file or directory[/INDENT]

Now what?? Is this something I did wrong, or is something screwed up in the installation files? I'm lost.

---

### Post by P4man on 2007-11-04
did you try installing wine by compiling it, before using apt-get ? try removing everything related to wine:
```

sudo apt-get purge wine
```

if you tried compiling wine your self, you should also do something like  "make uninstall" from the source folder, not quite sure, ask someone who knows. If you no longer have the source, you might have to download it in order to be able to remove it.. or ask someone who knows better than me :)

One thing is for sure, your wine install is messed up. I'm too noob to give better help than that, so I can only suggest to do as with windows: reinstall :)

---

### Post by TeaSwigger on 2007-11-04
Hello the_rajah,

If you haven't tried installing wine from source and these errors occured, run 

```
sudo apt-get update
```

And if that works ok, run

```
sudo apt-get upgrade
```

And once you're updated, if that worked ok, use

```
sudo apt-get autoclean
```

And if things are hunky dorey still, as P4Man said, run

```
sudo apt-get remove --purge wine
```

Then try installing something small. If that works, try installing wine again. After a successful install, I suggest the following in a terminal:

```
wineprefixcreate
```

Wait for it to say it's done. Then run 

```
winecfg
```

Yes wine can be a pain but it's getting better with age (harde har) and so will you at using it. :)

---

### Post by the_rajah on 2007-11-04
Thanks, but I'm still stuck.. I followed all those steps down to the point where I actually apt-get installed wine without any errors or indication of trouble, but when I did that step, I still get an error:

[INDENT]$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.9MB of archives.
After unpacking 48.9MB of additional disk space will be used.
(Reading database ... 96320 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

I'm about to the point of trying a complete re-install, but I think that is giving up without actually solving the problem or learning anything. Then, if I do that and it's still borked.. I'll really be unhappy.

Thanks, as always, for the help!

---

### Post by the_rajah on 2007-11-04
Follow up... Problem solved.

It was a bad file, wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb  that had to be removed, then on the next install, it downloaded an intact file and all is good.  I had this with another application where I had to navigate to the archive and sudo rm the bad file.

I don't see how to mark this solved, but for me, it is.

---

### Post by TeaSwigger on 2007-11-04
> **the_rajah said:**
> Follow up... Problem solved.

It was a bad file, wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb  that had to be removed, then on the next install, it downloaded an intact file and all is good.  I had this with another application where I had to navigate to the archive and sudo rm the bad file.

I don't see how to mark this solved, but for me, it is.

Look up at the top of the thread, you'll find "thread tools." That's where you can set it solved.

A tip, you can clean the cache of those downloaded .debs by just entering this:

```
sudo apt-get clean
```

:)

---

### Post by beanco on 2007-11-05
could my installing, uninstalling, updating, purging etc have cause the problems where, after I enter my password, I get that orange screen and then nothing. the cursor is there, it moves but nothing else.


I can get into terméinal using ctrl alt F1 ...

Robi

---

### Post by Sturmeh on 2007-11-05
Just incase the guides before didn't help you...

1. Go in synaptic, click the apps list and start typing "wine" then apply for install and apply.
2. When done installing, find any exe right click and press "Open With..." > "Open with other Application..."
3. In the  bottom box, write "wine" or "wine %1" ...

( Personally I use "wine" but some guides say to pass the argument. )

Now just doubleclick the DVDShrink installer exe, and hope for the best? xD

---

### Post by MSchenker on 2007-11-05
I think Wine is an excellent concept, but it is not quite ready for prime time.  The point, if I'm not mistaken, is to make it easy to run Windows applications.  But it appears to me that it adds many layers of complexity.

I do hope that Wine evolves in the coming months, because I do have some Windows applications I would like to run in Linux.  For the moment, though, I am trying to find native Linux applications in the repositories.

Matt

---

### Post by P4man on 2007-11-05
Wine is insanely easy to use...seriously,  install it through add/remove programs, run winecfg once (not even sure if that is still required with the latest versions), and thats it. You can now  launch many windows apps, including installers no different that you would in windows. If you download and run a windows installer, it will even create the "startmenu" in the gnome panel. How much easier could it be? Its completely invisible!

Its only that it doesnt work with everything. That shouldn't surprise anyone, but I find it amazing how many apps do work. For instance, IL-2 sturmovik (/pacific fighters/1946) quite an advanced WW2 flightsim, works just fine, and barely slower than under windows.

Its only when you try to get a non working app to work, that it gets  difficult. It would also be nice wine had an easier way to install missing DLLs for those programs that need them, but even that can hardly be called a difficult process. The OP's problem had nothing to do with wine as such; he had a corrupted file, could happen with any app.

---

### Post by MSchenker on 2007-11-05
P4man,
I wonder why we have such different experiences?  Well, I haven't tried to use Wine for much yet, so maybe I should wait to judge it.

I've tried to install Irfanview, and that didn't work.

The only other thing I can think of is that I am running Kubuntu.  Maybe Wine works better in Ubuntu?

Matt

---

### Post by P4man on 2007-11-05
> **MSchenker said:**
> P4man,
I wonder why we have such different experiences?  Well, I haven't tried to use Wine for much yet, so maybe I should wait to judge it.

I've tried to install Irfanview, and that didn't work.

The only other thing I can think of is that I am running Kubuntu.  Maybe Wine works better in Ubuntu?

Matt

Well, I just tried it. Not only did I try it, I actually recorded my attempt. I got it installed in 1::50 seconds :) Im uploading it to youtube now.

 The only thing I can think where you went wrong, is using an old version of MFC42.dll, or not installing it all. Its worth pointing out however, that it won't work under windows either without that DLL, or with a too old version of it.

 I got mine from here:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html)

Or copy it from your windows partition if you have one.

Copy that DLL  to ~/home/.wine/drive_c/windows/system32.

meanwhile youtube upload is complete. Video is still being processed as I am typing this, but soon you can view it here:

**EDIT**
Youtube doesnt like OGMs, so i had to transcode it. Its now online here:
[http://www.youtube.com/v/5-nQ7RIUfBM](http://www.youtube.com/v/5-nQ7RIUfBM)

That really doesnt look very hard to me ?

---

### Post by MSchenker on 2007-11-05
> **P4man said:**
> ...  The only thing I can think where you went wrong, is using an old version of MFC42.dll, or not installing it all. Its worth pointing out however, that it won't work under windows either without that DLL, or with a too old version of it.

 I got mine from here:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html)

Or copy it from your windows partition if you have one.

Copy that DLL  to ~/home/.wine/drive_c/windows/system32.

I no longer have Windows on my machine, so I think I would have to put the DLL somewhere else.  Or maybe that's the reason it won't work?  Does Windows have to be on the computer for Wine to work?

Matt

---

### Post by aktiwers on 2007-11-05
Or have a look at wine-doors
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

It works like Synaptic, just with windows apps. It will download and install DVD Shrink 3.2 soon..  at least its on there todo list.

---

### Post by P4man on 2007-11-06
> **MSchenker said:**
> I no longer have Windows on my machine, so I think I would have to put the DLL somewhere else.  Or maybe that's the reason it won't work?  Does Windows have to be on the computer for Wine to work?


You still have to copy that file, just like I did in that movie, you don't need a windows partition.
If you installed wine, then you will have a ~/.wine folder i which contains a drvei_c folder with a windows folder etc. Windows programs expect such a folder structure to exist, so wine creates it.

In the GNOME menu Just go to "places", "home folder".iThen in the 'menu" view select "show hidden folders". Then /home/yourname/.wine will appear . Might be slightly different in KDE though.

---


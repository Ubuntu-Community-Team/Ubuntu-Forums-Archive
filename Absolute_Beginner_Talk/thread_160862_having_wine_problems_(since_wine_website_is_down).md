---
title: "having wine problems (since wine website is down)"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-15
so what do you do after you've installed wine, autodetected drives, and then inserted a certain red alert 2 disk? i tried clicking setup.exe or autorun.exe but it's telling me to restart the computer?!...........](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by John.Michael.Kane on 2006-04-15
Don't know if this will help
[http://www.winehq.com/site/howto](http://www.winehq.com/site/howto)
[http://www.witch.westfalen.de/Wine-HOWTO/book1.html](http://www.witch.westfalen.de/Wine-HOWTO/book1.html)

---

### Post by user1397 on 2006-04-15
[quote=SD-Plissken]Don't know if this will help
[http://www.winehq.com/site/howto]("http://www.winehq.com/site/howto")
[http://www.witch.westfalen.de/Wine-HOWTO/book1.html]("http://www.witch.westfalen.de/Wine-HOWTO/book1.html")[/quote]
Thanks but... the first link is down as mentioned in my title, and the second one just seems to old to me to even try! in one part it says: "assuming you have windows 3.1..."  !!!

---

### Post by John.Michael.Kane on 2006-04-15
the frist link works fine looking at now in fact heres the text off the site.```
Wine HowTo

Before you install Wine, make sure that there is no previous Wine installation on your system, either from a package or from source. If you haven't yet installed Wine, you should be fine. See the Removing old Wine versions chapter in the User Guide for details.

Many Linux distributions come with an included Wine package, but due to Wine's rapid development rate these are usually old and sometimes broken versions. It is best to uninstall included package versions and update to the latest Wine version available here.

Ready-made, updated binary packages for Wine can be found at the WineHQ downloads page here. In addition, full source code is available for both the current Wine development tree and every Wine release here. For help with installing from a package or from source, please consult the Getting Wine chapter of the User guide here.

As of Wine release 20050628 we have transitioned away from the config file and now place these values in registry files found in your .wine directory. Winecfg (wine configurator) in conjunction with regedit (registry editor) are two graphical front ends that makes changing registry values easier for end user's. Winecfg while still beta software can be used for basic configuration and optimizations, more advanced users may wish to use regedit to make changes that winecfg isn't capable of performing.

If you are upgrading don't forget to update your registry using the wineprefixcreate command. This will ensure that you have all default registry values set.

Note to Debian users: The packages included in the main distribution are currently very out of date. We're working on having the latest packages available officially from Debian's servers, but until then we suggest you install the latest Wine by using our apt repository here. Ubuntu users can install the latest Wine packages by using one of the repositories from the Ubuntu backports project .
How to help get applications working in Wine

If you want to help get an application working in Wine, the first thing you should do is register yourself in the applications database and use one of your votes to indicate that you'd like more effort to be spent on the application. Every once in a while, a Wine developer will finish a project and look for something to do - combing through the higher voted apps to find one that people need work on is a great way to spend one's time and fill up a todo list.

If the application that you want working is not listed in the applications database, there is an easy to use form available for you to add it. If the application is in the database, but lacks a maintainer, you should consider becoming one. If you are familiar with Wine and have a desire to test the application and help get or keep it working, please apply by clicking the link in the application's page. Each application should have a supermaintainer, and, if different versions of the application are substantially different (such as in Internet Explorer), each subversion should have a maintainer. Please don't feel deterred by the need to apply to become a maintainer - the application form is largely a formality to prevent abuse and we can virtually guarantee your acceptance.

If you are the developer or publisher of the application, you obviously have a very big incentive to help get your application working under Wine. Fortunately, there are many options available to you other than reporting bugs and hoping someone will fix them. By far the easiest way is to simply send free copies of your software to Wine developers and hope they'll take an interest in getting it working. You'd be amazed how effective this approach can be, particularly for games. An alternative option, perhaps more effective and expensive, is to pay Wine developers for their work on your application, either directly through a negotiated contract or indirectly by posting a bounty. CodeWeavers, a major Wine developer, offers a special section for pledges at their compatibility center website. The most direct method, however, is to help develop Wine itself and contribute code directly, which is exactly what Corel did for WordPerfect several years ago. In any case, making a post on the Wine developers email list can go a long way.
If your application doesn't work:

If your application experiences problems in a particular area, or fails to even run at all, there are a number of steps you can take to help us. The most important thing is to find out where exactly the application is failing. To diagnose application problems, the first step is to run the program from the console using Wine, rather than from a gui shortcut. This will allow Wine to output error messages to the console, the understanding of which are key to solving the problem and getting the application to work.

An application may not work because Wine doesn't yet fully implement one of the DLL files the application is trying to use. If you encounter a DLL not found error, or see a lot of "FixMe:" messages while running the application in Wine, this is likely the case. When this occurs, you can try using native (non-Wine) DLL files in place of Wine's builtin ones. Check the application database page for the program. There may be special configuration options or instructions for installing native DLL files there that you can try to get the application working. For further configuration help, please see the Running Wine section of the User Guide.

If the application still doesn't work, it's probably due to a bug or deficiency in Wine and we'd like to hear about it. Please see the reporting bugs page for instructions on how to best report bugs with applications. Alternatively, if you're a programmer, we'd really like it if you tried to help us directly; please read the getting started with Wine development guide if you're interested.
If your application does work, but with some difficulty:

Sometimes, applications run under Wine but don't function quite as smoothly as they do in windows. They may have display errors, a feature may be broken, or they may run unusually slow. These applications should receive a lower rating from their maintainers ("bronze" or "garbage") in the Application's Database, depending on the degree of difficulty encountered.

If you have found a way to make an application work that is more complicated than simply installing it, please share that information by posting on the application's page in the database. If you are the maintainer for the application, please post the instructions in a "howto" which will appear inside green bars at the top of the application's page.
If your application used to work, but has since broken in a new version of Wine:

Wine is a large and complex project, composed of many files written by different authors. Sometimes, an attempt to change a file and expand support for one application will unexpectedly cause another application to stop functioning. These changes are known as "regressions", and they are unfortunately sometimes found in the Wine source code because the author of a patch that causes a regression is quite simply unaware of it. Since the Wine developers can't possibly test every application with every patch, we have to rely on the community to inform us of when regressions occur so that the problem can be easily identified and ultimately fixed. Without community involvement, regressions can go unfixed for potentially very long periods of time.

If your application has experienced a regression, please try and provide us with as much information as you can about when and how it broke. This allows us to isolate the exact thing we screwed up in the code and provide a fix. Please provide as much as you know about which version of Wine worked, and which version didn't, including the version number and how you installed it (from source, binary packages, etc.) Finally, please post these things in the Application Database page for the application.

If you wish to be extremely helpful, you can try to isolate the exact patch which broke your application. This takes quite a bit of time and effort, but it is quite simply the best way to get your application working again. When it comes to fixing regressions, the only thing more helpful to the Wine developers than knowing exactly which patch caused a regression is receiving a fix for the patch itself. For help with isolating problem patches, please see the documentation on regression testing.

 
```

---

### Post by user1397 on 2006-04-15
[quote=SD-Plissken]the frist link works fine looking at now in fact heres the text off the site. you don't want to use the howto that i posted thats on you.```
Wine HowTo

Before you install Wine, make sure that there is no previous Wine installation on your system, either from a package or from source. If you haven't yet installed Wine, you should be fine. See the Removing old Wine versions chapter in the User Guide for details.

Many Linux distributions come with an included Wine package, but due to Wine's rapid development rate these are usually old and sometimes broken versions. It is best to uninstall included package versions and update to the latest Wine version available here.

Ready-made, updated binary packages for Wine can be found at the WineHQ downloads page here. In addition, full source code is available for both the current Wine development tree and every Wine release here. For help with installing from a package or from source, please consult the Getting Wine chapter of the User guide here.

As of Wine release 20050628 we have transitioned away from the config file and now place these values in registry files found in your .wine directory. Winecfg (wine configurator) in conjunction with regedit (registry editor) are two graphical front ends that makes changing registry values easier for end user's. Winecfg while still beta software can be used for basic configuration and optimizations, more advanced users may wish to use regedit to make changes that winecfg isn't capable of performing.

If you are upgrading don't forget to update your registry using the wineprefixcreate command. This will ensure that you have all default registry values set.

Note to Debian users: The packages included in the main distribution are currently very out of date. We're working on having the latest packages available officially from Debian's servers, but until then we suggest you install the latest Wine by using our apt repository here. Ubuntu users can install the latest Wine packages by using one of the repositories from the Ubuntu backports project .
How to help get applications working in Wine

If you want to help get an application working in Wine, the first thing you should do is register yourself in the applications database and use one of your votes to indicate that you'd like more effort to be spent on the application. Every once in a while, a Wine developer will finish a project and look for something to do - combing through the higher voted apps to find one that people need work on is a great way to spend one's time and fill up a todo list.

If the application that you want working is not listed in the applications database, there is an easy to use form available for you to add it. If the application is in the database, but lacks a maintainer, you should consider becoming one. If you are familiar with Wine and have a desire to test the application and help get or keep it working, please apply by clicking the link in the application's page. Each application should have a supermaintainer, and, if different versions of the application are substantially different (such as in Internet Explorer), each subversion should have a maintainer. Please don't feel deterred by the need to apply to become a maintainer - the application form is largely a formality to prevent abuse and we can virtually guarantee your acceptance.

If you are the developer or publisher of the application, you obviously have a very big incentive to help get your application working under Wine. Fortunately, there are many options available to you other than reporting bugs and hoping someone will fix them. By far the easiest way is to simply send free copies of your software to Wine developers and hope they'll take an interest in getting it working. You'd be amazed how effective this approach can be, particularly for games. An alternative option, perhaps more effective and expensive, is to pay Wine developers for their work on your application, either directly through a negotiated contract or indirectly by posting a bounty. CodeWeavers, a major Wine developer, offers a special section for pledges at their compatibility center website. The most direct method, however, is to help develop Wine itself and contribute code directly, which is exactly what Corel did for WordPerfect several years ago. In any case, making a post on the Wine developers email list can go a long way.
If your application doesn't work:

If your application experiences problems in a particular area, or fails to even run at all, there are a number of steps you can take to help us. The most important thing is to find out where exactly the application is failing. To diagnose application problems, the first step is to run the program from the console using Wine, rather than from a gui shortcut. This will allow Wine to output error messages to the console, the understanding of which are key to solving the problem and getting the application to work.

An application may not work because Wine doesn't yet fully implement one of the DLL files the application is trying to use. If you encounter a DLL not found error, or see a lot of "FixMe:" messages while running the application in Wine, this is likely the case. When this occurs, you can try using native (non-Wine) DLL files in place of Wine's builtin ones. Check the application database page for the program. There may be special configuration options or instructions for installing native DLL files there that you can try to get the application working. For further configuration help, please see the Running Wine section of the User Guide.

If the application still doesn't work, it's probably due to a bug or deficiency in Wine and we'd like to hear about it. Please see the reporting bugs page for instructions on how to best report bugs with applications. Alternatively, if you're a programmer, we'd really like it if you tried to help us directly; please read the getting started with Wine development guide if you're interested.
If your application does work, but with some difficulty:

Sometimes, applications run under Wine but don't function quite as smoothly as they do in windows. They may have display errors, a feature may be broken, or they may run unusually slow. These applications should receive a lower rating from their maintainers ("bronze" or "garbage") in the Application's Database, depending on the degree of difficulty encountered.

If you have found a way to make an application work that is more complicated than simply installing it, please share that information by posting on the application's page in the database. If you are the maintainer for the application, please post the instructions in a "howto" which will appear inside green bars at the top of the application's page.
If your application used to work, but has since broken in a new version of Wine:

Wine is a large and complex project, composed of many files written by different authors. Sometimes, an attempt to change a file and expand support for one application will unexpectedly cause another application to stop functioning. These changes are known as "regressions", and they are unfortunately sometimes found in the Wine source code because the author of a patch that causes a regression is quite simply unaware of it. Since the Wine developers can't possibly test every application with every patch, we have to rely on the community to inform us of when regressions occur so that the problem can be easily identified and ultimately fixed. Without community involvement, regressions can go unfixed for potentially very long periods of time.

If your application has experienced a regression, please try and provide us with as much information as you can about when and how it broke. This allows us to isolate the exact thing we screwed up in the code and provide a fix. Please provide as much as you know about which version of Wine worked, and which version didn't, including the version number and how you installed it (from source, binary packages, etc.) Finally, please post these things in the Application Database page for the application.

If you wish to be extremely helpful, you can try to isolate the exact patch which broke your application. This takes quite a bit of time and effort, but it is quite simply the best way to get your application working again. When it comes to fixing regressions, the only thing more helpful to the Wine developers than knowing exactly which patch caused a regression is receiving a fix for the patch itself. For help with isolating problem patches, please see the documentation on regression testing.

 
```[/quote]
Thanks! 
i wonder why the winehq website doesn't load on my comp...

---

### Post by John.Michael.Kane on 2006-04-15
your welcome the site is up and running [http://www.winehq.com/](http://www.winehq.com/) try clicking this link see if you get to the site. however i hope the info has been of some help.

---

### Post by user1397 on 2006-04-15
[quote=SD-Plissken]your welcome the site is up and running [http://www.winehq.com/]("http://www.winehq.com/") try clicking this link see if you get to the site. however i hope the info has been of some help.[/quote]
nope it just won't open. even tried it in another browser - galeon, and it still didn't work!   :(

---

### Post by John.Michael.Kane on 2006-04-15
Dont know what to tell you the site is working. heres the pdf doc's don't know if they will help any
[http://www.winehq.com/docs/en/wineusr-guide.pdf](http://www.winehq.com/docs/en/wineusr-guide.pdf)
[http://www.winehq.com/docs/en/winelib-guide.pdf](http://www.winehq.com/docs/en/winelib-guide.pdf)
[http://wiki.winehq.org/](http://wiki.winehq.org/)
[http://www.winehq.com/site/docs/wine](http://www.winehq.com/site/docs/wine)

---

### Post by Grey on 2006-04-17
Try going to about:config in Firefox, and then change this entry:

network.dns.disableIPv6

to true.  That fixed the problem with winehq on my laptop.

---

### Post by user1397 on 2006-04-17
[quote=Grey]Try going to about:config in Firefox, and then change this entry:

network.dns.disableIPv6

to true.  That fixed the problem with winehq on my laptop.[/quote]
I'm not sure why but it still doesn't work for me...

---

### Post by GarethMB on 2006-04-17
Assuming that the installer works with wine try this:

Open a terminal.
Navigate to the directory with the installer you want to use. ```
cd directory_name
```
Then
```
wine installername.exe
```
That should start the installer, everything should be handled just like it would in windows. An important thing to note is that wine creates a virtual C: drive. Which gets hidden away in the files system somewhere. I recommend installing in your home directory under Z:. Just easier imo.

Providing you manage to get through the install process, navigate to the directory where you installed in a terminal once again.

Use ```
ls
``` to display the contents of this directory. Then ```
wine programlaunchername.exe 
```

If you plan to use this game regularly you may want to make a shell script to do that last bit.

This should launch for you assuming that you don't need to tweak wine in anyway to launch your program. If this doesn't work for you tell me what happens and i'll see if theres any bugs on the wine page for you.

I'm no expert on *any* part of ubuntu or wine, but this is how i got guitar pro 5 to work.

---

### Post by user1397 on 2006-04-17
[quote=GarethMB]Assuming that the installer works with wine try this:

Open a terminal.
Navigate to the directory with the installer you want to use. ```
cd directory_name
``` Then
```
wine installername.exe
``` That should start the installer, everything should be handled just like it would in windows. An important thing to note is that wine creates a virtual C: drive. Which gets hidden away in the files system somewhere. I recommend installing in your home directory under Z:. Just easier imo.

Providing you manage to get through the install process, navigate to the directory where you installed in a terminal once again.

Use ```
ls
``` to display the contents of this directory. Then ```
wine programlaunchername.exe 
``` 
If you plan to use this game regularly you may want to make a shell script to do that last bit.

This should launch for you assuming that you don't need to tweak wine in anyway to launch your program. If this doesn't work for you tell me what happens and i'll see if theres any bugs on the wine page for you.

I'm no expert on *any* part of ubuntu or wine, but this is how i got guitar pro 5 to work.[/quote]
Will definitely try this and get back to you if it works.

P.S. i like your sig. "for all you americans" :)

---

### Post by Sandlst on 2006-04-17
I'm not sure if you have successfully connected to the wine homepage yet, but assuming you havent, I thought I would attach a saved webpage you should be able to view, on installing RA2 as well as an installer script you apparently need, good luck!

---

### Post by user1397 on 2006-04-17
[quote=Sandlst]I'm not sure if you have successfully connected to the wine homepage yet, but assuming you havent, I thought I would attach a saved webpage you should be able to view, on installing RA2 as well as an installer script you apparently need, good luck![/quote]
when I try to run setup.exe, it says: 
"An older version of COMCTL32.DLL exists on your system.  Red Alert 2 requires this file to be updated. Please update this file now.

After updating this file, you will need to reboot your system and rerun the Red Alert 2 Setup program to continue with the installation.

If you continue without updating, you will need to run 401COMUP.EXE
 from the setup directory and reboot your system before running the game."

Then I press continue and it says:

Title: Microsoft COMCTL32.DLL Update
"This system does not need this update."

Then I press okay and then it says:
" You will need to reboot your system before continuing with the Setup program.  You will neeed to rerun the Setup program after restarting your system to continue installing the game.

Would you like to reboot your system now?
        [Yes]       [No]"
Neither button does anything.  By the way if I try to run 401COMUP.EXE in the setup directory, I still get this message:

 Title: Microsoft COMCTL32.DLL Update
"This system does not need this update."

---

### Post by GarethMB on 2006-04-17
from the winehq site.

[b]>  Use this script to install the game (the game's installer does not work)
[http://www.thehandofagony.com/alex/redalert2](http://www.thehandofagony.com/alex/redalert2)[/b]
Crack

The copy protection in Red Alert 2 is very special, as it will blow up all your units after 30 seconds. This can be avoided by doing the following.

    * Update the game to the latest version (if you want to)
    * Make a folder called 'backup' in your RA2 directory and move 'Ra2.exe' and 'Game.exe' to it
    * Download this crack and place the 'game.exe' it contains in the RA2 directory
    * Download this crack and place the 'ra2.exe' found in the 'crack' subfolder of 'ra2_allied_crk.zip' in your RA2 directory
    * If you only intend to use the Allies CD, symlink the mix files from the CD root (run the following command while in your RA2 directory: 'ln -s /mnt/cdrom/*.mix .', substitute /mnt/cdrom with your CD mountpoint). Otherwise, copy all the mix files from your Allies CD root to your RA2 directory, and then symlink ('ln -s /mnt/cdrom/*02.mix .') or copy maps02.mix and movies02.mix from the Soviet CD

You can find more cracks here if you want to experiment on your own.

Network Play

In order to play network games. IPX will have to be enabled in the kernel, and you need some userspace utilities, usually called ipx-utils; and IPX must be started (there should be an initscript). Also note that Red Alert 2's network support is only available when it is run as root.

Ubuntu users can use this command: sudo apt-get install ipx; sudo modprobe ipx; sudo ipx_interface add -p eth0 802.2 0x12345678

---

### Post by user1397 on 2006-04-17
[quote=GarethMB]from the winehq site.

[b][/quote] Don't worry about this anymore.  I don't even want red alert 2 anymore on my system...

---


---
title: "online storage that would mount as drive"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by jord1242 on 2008-02-26
I am looking for online storage that I could mount as a drive in both windows and linux (so I can use this on other people's windows machines). I want to store my firefox data so that I can have the same profile on any machine, and that would save me carrying around an USB stick. Anyway,

It doesn't appear x drive will work, because I don't see anyway in Linux of mounting it as a drive. What options are available to me? I see that I could use an FTP server (I have lots of server space) and mount a drive in Linux to that server, but would I be able to do this in Windows easily? Probably not.

Anyway, just thought if someone had some ideas, I would like to have a central "online" location for my profile information, and then I would rsync that directory to my USB drive (when I plug it in).

Thanks,
JJ

---

### Post by Oldsoldier2003 on 2008-02-26
> **jord1242 said:**
> I am looking for online storage that I could mount as a drive in both windows and linux (so I can use this on other people's windows machines). I want to store my firefox data so that I can have the same profile on any machine, and that would save me carrying around an USB stick. Anyway,

It doesn't appear x drive will work, because I don't see anyway in Linux of mounting it as a drive. What options are available to me? I see that I could use an FTP server (I have lots of server space) and mount a drive in Linux to that server, but would I be able to do this in Windows easily? Probably not.

Anyway, just thought if someone had some ideas, I would like to have a central "online" location for my profile information, and then I would rsync that directory to my USB drive (when I plug it in).

Thanks,
JJ

Samba? You can mount a samba share as a drive and its accessible from Windows...

---

### Post by jord1242 on 2008-02-26
Not sure that would really work for me. I am looking to use x drive (or some other online solution) and they offer a download that makes the x drive appear as a normal drive (say x:\) but that works only for windows. I am looking for a solution that would mount that drive in both a windows and a linux system, so no matter where I am I can mount that drive and use my personal settings.

I am probably not making sense - LONG day. Thanks for the help!

JJ

---

### Post by nilarimogard on 2008-02-26
You can do that with gmail, but i only know how to make it a drive in windows, so if someone knows how to do it in Ubuntu, i'd be great :D

---

### Post by jord1242 on 2008-02-26
I've also looked into a free utility that would map my ftp location for windows and linux, but haven't really found a tool that would mount as a windows drive AND a linux folder. I have server space, I just need a good EASY way to mount that FTP location in both windows and linux.

Thjanks,

JJ

---

### Post by jord1242 on 2008-02-26
> **nilarimogard said:**
> You can do that with gmail, but i only know how to make it a drive in windows, so if someone knows how to do it in Ubuntu, i'd be great :D

That would DEFINITELY be an option, but not sure how to mount it in Linux, so would like to hear if anyone has that working.

---

### Post by Het Irv on 2008-02-26
If the drive was NTFS you it should be no problem to mount in Windows:
XP: right click on My Computer-> Map Network Drive
      Select a free Drive letter, and enter "\\(ipaddress of FTP server)\(name of shared folder)
Example: \\123.123.123.123\music

Procedure the same for Vista.

---

### Post by akadruid on 2008-02-26
This looks like a good hack to get your FTP space mounted as a drive in Windows:
[http://www.astahost.com/info.php/map-ftp-server-as-drive_t7292.html](http://www.astahost.com/info.php/map-ftp-server-as-drive_t7292.html)

Alternativly, Engadget has some software to do it:
[http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/](http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/)

Alternatively see this thread on mounting gmail drives in ubuntu:
[http://ubuntuforums.org/showthread.php?t=232789](http://ubuntuforums.org/showthread.php?t=232789)

hope that helps

aka

---

### Post by kellemes on 2008-02-26
Some random links.. haven't tried it myself.. yet. Very interested though..
[http://ubuntuforums.org/showthread.php?t=596352](http://ubuntuforums.org/showthread.php?t=596352)
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

Can someone confirm this is working?
[https://www.xmailharddrive.com/beta/](https://www.xmailharddrive.com/beta/)

---

### Post by jord1242 on 2008-02-27
> **Het Irv said:**
> If the drive was NTFS you it should be no problem to mount in Windows:
XP: right click on My Computer-> Map Network Drive
      Select a free Drive letter, and enter "\\(ipaddress of FTP server)\(name of shared folder)
Example: \\123.123.123.123\music

Procedure the same for Vista.

It's a Linux server.

---

### Post by jord1242 on 2008-02-27
> **akadruid said:**
> This looks like a good hack to get your FTP space mounted as a drive in Windows:
[http://www.astahost.com/info.php/map-ftp-server-as-drive_t7292.html](http://www.astahost.com/info.php/map-ftp-server-as-drive_t7292.html)

Alternativly, Engadget has some software to do it:
[http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/](http://www.engadget.com/2005/10/25/how-to-map-a-drive-to-your-ftp-server/)

Alternatively see this thread on mounting gmail drives in ubuntu:
[http://ubuntuforums.org/showthread.php?t=232789](http://ubuntuforums.org/showthread.php?t=232789)

hope that helps

aka

Yeah, I saw the windows ones (although when I setup the FTP location in windows it failed to map the drive). In any regard, I am starting to see that there is no EASY way to get an FTP location mapped as a drive in windows and linux, and the gmail FS thing seems fairly non-intuitive to setup if I am over at a friend's house using his Ubuntu box.

I may just have to save the profile stuff on a memory stick, and just carry that around with me. Seems like the most intuitive method, although I wish I didn't have to carry anything around.

Thanks a lot everyone for chiming in, definitely learned some things!

peace,
JJ

---

### Post by halitech on 2008-02-27
If you have a small thumbdrive, you could install a minimal install of Portableapps ( [http://portableapps.com/](http://portableapps.com/) ) and then add firefox and use it to browse from any windows computer. Don't think it will work on a linux box although I haven't actually tried but it would have your profile stuff on it at least.

---

### Post by jord1242 on 2008-02-27
> **halitech said:**
> If you have a small thumbdrive, you could install a minimal install of Portableapps ( [http://portableapps.com/](http://portableapps.com/) ) and then add firefox and use it to browse from any windows computer. Don't think it will work on a linux box although I haven't actually tried but it would have your profile stuff on it at least.

For the longest time that was what I was using. Now what I am envisioning is having the profile on my USB stick, and then having two scripts, one that would run for windows that would do: 

firefox.exe -profilemanager

linux: 

firefox -profilemanager

Then if I am at someone's house or want to set it up, I can just run those scripts and setup a profile for myself. Point it to the location on my USB stick and it would work. Initial testing seems ok.

What I would LOVE is a portable version of firefox for windows/Linux/mac that I could have loaded, and have ONE location for my profile on my stick. Then all I would have to do is run the version for which operating system I am on, and bam, it would work. Much like how Floola works on my iPod, I have three versions of the executable, and depending on which OS I am running under, I just load that up and EVERYTHING just works.

Has anyone come across a way to have three different versions of Firefox running and pointing to the same profile?

JJ

---

### Post by jord1242 on 2008-02-27
UPDATE:
 
So the profile manager thing didn't work so hot. I put my profile on my USB stick. I did the -profilemanager option and setup a new profile to use from the stick (pointing it at the profile folder). It took forever to load. Then upon bringing everything up, it crashed.
 
I am basically back to using the portableapps.com stuff. Does anyone have any GOOD ways of using this in Linux?
 
I would like to use these in Kubuntu, not sure how they would work in Wine if at all. I would imagine some of my Firefox add-ons would NOT work.
 
Any thoughts?
 
Thanks,
JJ

---

### Post by halitech on 2008-02-27
I think you are in way over my head so not really sure, would copying your profile from ubuntu to the thumbdrive work? (I'm strictly guessing here)

---

### Post by Squizz on 2008-02-27
[http://www.foxmarks.com/](http://www.foxmarks.com/)

[I]The Foxmarks Bookmark Synchronizer automatically synchronizes your bookmarks between two or more computers running Firefox. It also lets you access your bookmarks from any computer anytime via my.foxmarks.com. An easy-to-use wizard guides you through the quick startup process. Then Foxmarks works silently in the background to keep your bookmarks up-to-date on all your computers.

Simple. Solid. Free. And ready to use.
[/I]

---

### Post by prensing on 2008-02-27
I have two suggestions.

The first is: try Google Browser Sync. This is a Firefox plugin which stores all your Firefox info (bookmarks, cookies, etc; you can choose) on a Google server. Any time you start up a Firefox session, it syncs to the server, and then updates when you are done.

If you really want do it yourself, look into FUSE. I know there is a FUSE module to mount GMail as a filesystem (called GMailFS). There are a few packages which use FUSE to mount an FTP server. see  [http://gentoo-wiki.com/HOWTO_FTP_Mount](http://gentoo-wiki.com/HOWTO_FTP_Mount).

Hope this helps.

---

### Post by jord1242 on 2008-02-28
> **Squizz said:**
> [http://www.foxmarks.com/](http://www.foxmarks.com/)

[I]The Foxmarks Bookmark Synchronizer automatically synchronizes your bookmarks between two or more computers running Firefox. It also lets you access your bookmarks from any computer anytime via my.foxmarks.com. An easy-to-use wizard guides you through the quick startup process. Then Foxmarks works silently in the background to keep your bookmarks up-to-date on all your computers.

Simple. Solid. Free. And ready to use.
[/I]

That would work great for bookmarks, but leaves out settigns and extensions. Thanks though,

JJ

---

### Post by jord1242 on 2008-02-28
> **prensing said:**
> I have two suggestions.

The first is: try Google Browser Sync. This is a Firefox plugin which stores all your Firefox info (bookmarks, cookies, etc; you can choose) on a Google server. Any time you start up a Firefox session, it syncs to the server, and then updates when you are done.

If you really want do it yourself, look into FUSE. I know there is a FUSE module to mount GMail as a filesystem (called GMailFS). There are a few packages which use FUSE to mount an FTP server. see  [http://gentoo-wiki.com/HOWTO_FTP_Mount](http://gentoo-wiki.com/HOWTO_FTP_Mount).

Hope this helps.

Google Browser Sync actually seems pretty sweet, but I would be left without my extensions. I might try and use a combo of that and FEBE/CLEO to get the extensions synced, then I would only need to get a regular backup of that going to my thumb drive.

---

### Post by UBUSNAFU on 2008-02-28
This may not be anywhere near what you need but windows explorer can log into any ftp site and see it as a network drive. Depending on version it will be called "add network place" or something. You could then possibly synchronise with it calling explorer from the command line. It could also be way too late at night for me but at least I know that I have no idea how to do the same in Linux yet.

---

### Post by jord1242 on 2008-02-28
> **UBUSNAFU said:**
> This may not be anywhere near what you need but windows explorer can log into any ftp site and see it as a network drive. Depending on version it will be called "add network place" or something. You could then possibly synchronise with it calling explorer from the command line. It could also be way too late at night for me but at least I know that I have no idea how to do the same in Linux yet.

Yeah, I see that. The problem being that I need it mounted as a drive in both OS'es. That way I can create a new profile and just point the profile folder to that drive in Firefox.

JJ

---

### Post by calnane on 2008-02-28
1) Find a service that supplies an FTP connection.
2)
  **For Ubuntu**
     1. Click on places in the top bar and select Connect to Server
     2. From the Drop Down list pick FTP (with login)
     3. Type in the details that should be supplied by your hosting service
     4. This should be shown on the Computer Page in Nautilus
  **For Windows**
     1. Go to "My Computer -> Tools -> Map Network drive"
     2. Type in "ftp://[Your Server Here]/
     3. Choose a drive letter and Press Ok

There. Its not too hard

---

### Post by jord1242 on 2008-02-28
> **calnane said:**
> 1) Find a service that supplies an FTP connection.
2)
  **For Ubuntu**
     1. Click on places in the top bar and select Connect to Server
     2. From the Drop Down list pick FTP (with login)
     3. Type in the details that should be supplied by your hosting service
     4. This should be shown on the Computer Page in Nautilus
  **For Windows**
     1. Go to "My Computer -> Tools -> Map Network drive"
     2. Type in "ftp://[Your Server Here]/
     3. Choose a drive letter and Press Ok

There. Its not too hard

I tried the windows one before, and I get: 

---------------------------
Windows
---------------------------
The network path ftp://ftp.{server_name}.com/ could not be found.
---------------------------
OK   
---------------------------

So I gave up on this. I also tried adding my ftp server as a network place, and that worked, but I could not get it to add as a drive.

Thanks,
JJ

---


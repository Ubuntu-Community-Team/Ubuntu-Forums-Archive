---
title: "problem accessing mac HD Ubuntu dual-boot"
date: 2010-06-14
forum: Apple Hardware Users
---

### Post by Colonel Dragoon on 2010-06-14
hey, I'm a new member in this forum and I have moderate experience with generally Linux systems.

this here starts the background of my story, and info about my machine the steps I have taken, if you want to jump to the problem, then it is right after the line-break.

I own a macbook pro 5,5 and I wanted to install Ubuntu 10.04 LTS, so I downloaded the image file .iso and burned it using disk utility on my mac and verified the data, then following the mac ubuntu wiki, did every step in creating a windows partition via bootcamp then booting ubuntu with rEFit, choose try, start gparted delete BOOTCAMP partition then install, went through the installation, but just as it reached 45% exactly it stopped and says [input/output] error, ...due to a faulty CD/DVD or driver.
anyway after investigation and multiple trials, such as choosing the slowest writing speed possible, downloading it again, choosing 32-bit...etc, I found out the problem is with the distro, this error always occurred with mac users trying to install 10.04 LTS, based on the results of my research of course.
so seeing there's no hope for me to get the latest version, I downloaded and installed Karmic Koala, with the same steps and oddly it just installed as simple as it claimed.

________________________________________________________

now here starts the problem, how am I able to access my original files on the Mac HD? I mount it, access it, enter user, but I am unable to go any further because the folders "download, documents, pictures ect.." are unauthorized to enter, and I can't do anything about it because I'm not the author or admin.
seems simple I said, then I booted back to mac (actually several times, back and forth and every time I try something, it doesn't work) and manually checked each folder's from Mac HD to Downloads, document...etc share option and changed their properties to allow all users to write-read on each folders info cards.
of course I also checked the file sharing in system preferences inside "sharing" and enabled everyone (me, users, everyone) to be able to write-read, and I also enabled remote log in for everyone.
I booted back to ubuntu mounted mac HD, tried to access the folders and guess what? it didn't work...

I wanted Ubuntu, the great amount of work put to it, free of charge, I wanted to install it for everyone I know. but I can't use it if I can't access my original folders.

thanks for your time 
-AJ

Ps: I was booting back and forth between mac and ubuntu to see if it worked after each step, but it never did.
I found out everything from burning the image file on a cd/DVD to installing ubuntu and drivers on my own, through this forum and the internet of course; but now I can't seem to find the answer to this particular case ^^;

---

### Post by Frobber on 2010-06-14
I suspect your problem is related to user ID and group ID on the Linux side. The IDs for both sides should match.

OSX uses 501 and 20 respectively, where Linux uses 1001.

Look at my response to this post. 

[http://ubuntuforums.org/showthread.php?t=1502964](http://ubuntuforums.org/showthread.php?t=1502964)

---

### Post by Colonel Dragoon on 2010-06-14
it finally worked, thanks Frobber

---


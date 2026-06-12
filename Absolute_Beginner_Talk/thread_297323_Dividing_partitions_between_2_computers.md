---
title: "Dividing partitions between 2 computers?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by wolfear on 2006-11-10
Ok..I am so totally confused now.
I want to switch both our systems off of XP to Ubuntu.
I did my research and am fairly certain I can save all of our important data, settings and bookmarks from XP and get the one "Windows only" online game (poker) to work.
I have been trying to read up on the docs and the forum all day, but I guess my newbie brain is just not working correctly.
My confusion comes from the whole partition thing and how I would span different hard drives, if I am even understanding this correctly.
We have 2 computers and 4 HDs. I would like the master HD on one system for a desktop, web design tools, online game and server tools (I read about Webmin and I think that'll work). 
The master HD on the second system only needs a desktop and a minimum of apps as it's for my wife who really only needs a browser, IRC/chat(gaim and one or two others should be fine) word processor, and online game, so there should be plenty of space left over for any extras.
One of the slave HDs is LAMP for my web design and testing and, if I can figure it out, eventually allow my partner remote access to current projects (way down the road).
The final slave HD should be for all of the common files and settings. Possibly 3 partitions: 2 user specific (like bookmarks, settings, passwords, etc.) and a final for shared files (music, documents, whatever).
I know I read somewhere how to do 1 HD, but I am not understanding how I could do this across multiple and after reading all day, my brain is mush.
I am probably making this much more difficult than it really is.
I almost forgot:
I do know that in order for the online poker, each of our systems must have a unique IP when connected to the game server.
We currently use a DLink DSS-5+ Ethernet Switch connected to our dsl modem, which seems to work just fine with my current Dapper install, if that helps any.

I am open for ideas, suggestions, links, whatever. I am currently between projects and figure I have about 2 weeks to get us switched over.

Almost forgot: I already have the 6.06 desktop and server downloaded and burned to CDs.

---

### Post by catlett on 2006-11-11
You don't have to cut up your hard drives if you don't want to. You can just seperate data with foldrs if you want. If you are going to install only ubuntu and erase xp then the installs will be easy.
Just run the installation and let ubuntu have the entire master drive. Ubuntu will mount the slave drive automatically. The only difference with you is, one computer will be a server install and the other a dsktop install.
This is about the desktop installation [http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)
This is about a LAMP server install [http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

If you know how many partitions you want (I just checked your post again and it seems you have an idea) I would make the partitions before. Download and burn Gparted Live. It is a boot cd with a partitioner on it. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I suggext making partitions on the slave drives but leave the master drives alone. This will sim[plify installation. Ubuntu can take and format the entire master and it will also  configure the system to mount the slave partitions when you start up. If you make them after, you need to edit the file that moints partitions etc. It is just easier to make them first and let the install automatically mount the partitions.

P.S. Don't forget there are specific areas of the forums. For server issues post here [http://www.ubuntuforums.org/forumdisplay.php?f=7](http://www.ubuntuforums.org/forumdisplay.php?f=7)
For wireless, post here [http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=136](http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=136) 
Of course you can always post in the beginner area but you can get quicker and more informed help by posting in specific areas. The people who know it are browsing in those areas and will see it but may not if it is posted elsewhere.

P.S. I forgot you are using 6.06, here are screenshots for 6.06. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) The installs are similar but there are a few minor differences between 6.06 and 6.10

---

### Post by wolfear on 2006-11-11
Thanks for the input.
I have read elsewhere when gparted was mentioned, but wasn't sure if that was something I needed.
I really only need to cut up one drive since 3 drives would be intact (2 desktops and 1 LAMP)with the one HD for the user and shared files to be divided.
That was the part I couldn't figure out since this spans 2 different computers. 

I'll give it a go once I finish getting all my data backed up.
Looks like I'll use the primary (mine) for a desktop/dev/server admin and subdivide the slave drive, then do a desktop and LAMP on the other system (my wife's) as that one would be using much less processor for anything but our local server most of the time.
I assume that I'll be able to point the second computer to the shared and user data on the first without too much hassle.
Thanks for the help. I'm off to the races...lol

---


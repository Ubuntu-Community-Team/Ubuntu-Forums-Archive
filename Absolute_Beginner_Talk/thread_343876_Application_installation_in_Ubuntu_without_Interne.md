---
title: "Application installation in Ubuntu without Internet"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by robinjives on 2007-01-22
Hi,

I recently installed Ubuntu 6.06LTS on my system and had a couple of queries, needless to say I am a complete newbie to Linux as a whole, my entire knowledge on computers is Windows based which not useful when it comes to Linux :) . My system Configuration is as follows:
          1. Dual Boot with Windows XP
          2. 1BG Ram
          3. 8GB i kept for root and 2GB for Swap file

I do not have any internet connection, I generally download applications and install them from either a CD or USB drive.

My queries are as follows:
         1. How do i install applications which come on cd into Ubuntu is there any graphical way to do this? How do I integrate these applications into Synaptix so I can uninstall them using that tool at a later time?
         2. Where do the applications I install end up in the Ubuntu system, ie. in which folder will I have to install the application?
         3. I heard that Amarok is a very good player for MP3s, when I checked their website they do not any version available for Ubuntu, I saw a version for Kubuntu however. Will Amarok work on Ubuntu since Amarok is meant for KDE enviroment and Ubuntu uses a Gnome enviroment?
        4. Will I be able to use Ubuntu to play video formats such as dat, avi, wmv, 3GP, divx & xvid? Where do I get the Players & codecs for the same? How is Xine, will it be able to handle these formats?
         
Really appreciate yourhelp...

---

### Post by carverj on 2007-01-22
1 & 2 - Have you tried doing a search on howto install programs in Ubuntu?
           Did you use dos terminal in Windows? To become proficient using Linux and to find out how to install things and where they end up in the system, it is crucial to teach yourself how to use the terminal command line. Time and patience and a lot of trial and error
3. You can actually choose between whether or not you want to use KDesktop or Gnome at the beginning of the session. Just choose the one you prefer at the login screen
4. You can play all sorts of files with open source multimedia, but unfortunately for you the internet is very useful for installing, and also troubleshooting problems that may arise.

---

### Post by Kobalt on 2007-01-22
To complete what has been replied to you : 
a KDE application (Kubuntu) will work on Gnome (Ubuntu), and vice versa. Synaptic will install everything you need to get these apps to work. 
If you still want to download a particular applications and yet you don't have a working internet connection on your Ubuntu machine (which would make your learning very easier...) you can download packages here : [http://packages.ubuntu.com](http://packages.ubuntu.com) 
Attention though, you will have to check for dependencies and download them as well... To understand a bit more how installing/removing software works on Ubuntu, read this doc : 
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

I strongly recommend you search these pages before posting here, you will find 80% of what you're searching on help.ubuntu.com

And also : welcome into Ubuntu :rolleyes: !

---

### Post by directcharitycontribution on 2007-01-22
also installing without internet so looking for most effective comprehensive and concise method to install any given package and its dependencies preferably without needing to do cut/paste

---

### Post by mikewhatever on 2007-01-22
To install applications from CD, try opening Synaptic, click Edit, and then Add CD-ROM. I haven't used the function myself, so cant guarantee it will work, also, there may be menu differences, since I have Edgy installed.

To answer your second question, see here [http://users.bigpond.net.au/hermanzone/p5.htm#Where_did_my_new_sofware_go](http://users.bigpond.net.au/hermanzone/p5.htm#Where_did_my_new_sofware_go)

---

### Post by psycosmyth on 2007-01-22
you can go to packages.ubuntu as mentioned or go to packages.debian, I have used both to download to a thumb drive and then install from there. I prefer the default .deb installer for the debian packages cause it's easier. Just check your dependencies as mentioned, some apps will tell you what you need in thier descriptions.




hey we got new smilies!!:lolflag:

---

### Post by directcharitycontribution on 2007-01-22
i got some locking up from using cd as repo.

loss of clock adjustment AND dialog says cannot remove CD from repo without removing ALL other packages!

am sticking to copying file out to desktop and then processing installation.

should report this to development.

---


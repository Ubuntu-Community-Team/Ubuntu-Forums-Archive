---
title: "Installation of tar.gz file in Linux"
date: 2011-09-02
forum: Any Other OS
---

### Post by TheNixObserver on 2011-09-02
I am using LInux Mint 11 as Live Cd and wanted to install flash plugin from Adobe.  I downloaded the file as tar.gz and as rpm and extracted it, What else should I do ? Even after extraction the site I was trying to view doesn't work and gives me the message that plugins are required.  Am I doing things right?

Or do I have to go to the terminal and type out some commands?  If so what should I type?

---

### Post by Perfect Storm on 2011-09-02
Moved to Other OS/Distro Talk.

---

### Post by claracc on 2011-09-02
The common and easiest way is install the packages from the repositories through some synaptic manager or software center (at least in ubuntu, I don't know the name of packages manager in mint or if there is one).

Any case, I have found this thread in linux mint forums: [http://forums.linuxmint.com/viewtopic.php?f=42&t=52104](http://forums.linuxmint.com/viewtopic.php?f=42&t=52104), which explains clearly how to install flash plugin in linux mint.

---

### Post by TheNixObserver on 2011-09-02
Thank You. 

I have already been through that thread.  The first command produced this result below.  What should I do now?  I am an absolute newbie to LInux and have no idea how to decipher these commands.

[COLOR=Blue][I]sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer libnspr4-0d
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts
  ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree libnspr4-0d
0 upgraded, 3 newly installed, 0 to remove and 85 not upgraded.
Need to get 11.3 kB/25.1 kB of archives.
After this operation, 295 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/multiverse flashplugin-installer i386 10.3.181.14ubuntu0.11.04.1
  404  Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse flashplugin-installer i386 10.3.181.14ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse flashplugin-nonfree i386 10.3.181.14ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.3.181.14ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.3.181.14ubuntu0.11.04.1_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.3.181.14ubuntu0.11.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.3.181.14ubuntu0.11.04.1_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I][/COLOR]

---

### Post by claracc on 2011-09-02
> Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/multiverse flashplugin-installer i386 10.3.181.14ubuntu0.11.04.1
404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse flashplugin-installer i386 10.3.181.14ubuntu0.11.04.1
404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/multiverse flashplugin-nonfree i386 10.3.181.14ubuntu0.11.04.1
404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/po....04.1_i386.deb](http://security.ubuntu.com/ubuntu/po....04.1_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/po....04.1_i386.deb](http://security.ubuntu.com/ubuntu/po....04.1_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

These errors indicate system cannot connect with server were required software packages are. Perhaps the server is down?, could you connect these http with your web browser?. Linux mint 11 uses ubuntu natty repositories?

---

### Post by TheNixObserver on 2011-09-02
The first link is working.  This is the page.  I haven't tried the others.

**Index of /ubuntu**

 [IMG]http://archive.ubuntu.com/icons/blank.gif[/IMG][Name]("http://archive.ubuntu.com/ubuntu/?C=N;O=D")[Last modified]("http://archive.ubuntu.com/ubuntu/?C=M;O=A")[Size]("http://archive.ubuntu.com/ubuntu/?C=S;O=A") [IMG]http://archive.ubuntu.com/icons/back.gif[/IMG][Parent Directory]("http://archive.ubuntu.com/")   -  [IMG]http://archive.ubuntu.com/icons/unknown.gif[/IMG][Archive-Update-in-Progress-syowa.canonical.com]("http://archive.ubuntu.com/ubuntu/Archive-Update-in-Progress-syowa.canonical.com")02-Sep-2011 07:39    1  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][dists/]("http://archive.ubuntu.com/ubuntu/dists/")19-Jul-2011 20:10    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][indices/]("http://archive.ubuntu.com/ubuntu/indices/")19-Aug-2011 07:33    -  [IMG]http://archive.ubuntu.com/icons/compressed.gif[/IMG][ls-lR.gz]("http://archive.ubuntu.com/ubuntu/ls-lR.gz")02-Sep-2011 07:29   11M [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][pool/]("http://archive.ubuntu.com/ubuntu/pool/")27-Feb-2010 06:30    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][project/]("http://archive.ubuntu.com/ubuntu/project/")13-Feb-2008 14:39    -    Apache/2.2.14 (Ubuntu) Server at archive.ubuntu.com Port 80



EDIT: The first three are working, the last two I get the 404 error.

---

### Post by claracc on 2011-09-02
Perhaps the problem is that you are working from the live CD and there is some problem to install temporaly flash plugin. 

Any case, there are some addresses that are no accesible so flash plugin won't install in this way.

I don't know, you will have to wait for more expertize advice.

I have find this linux mint documentation, which can be useful:[http://www.linuxmint.com/documentation.php](http://www.linuxmint.com/documentation.php)

---

### Post by MG&amp;TL on 2011-09-02
This probably doesn't help at all, but I was just able to type 'sudo apt-get install ubuntu-restricted-extras' and it worked. I haven't the foggiest why. I was then able to watch flash content. :confused:

---

### Post by ajgreeny on 2011-09-02
Linux mint uses firefox, so get the flash-aid add-on for firefox and you should get flash working without any more problems.

---

### Post by TheNixObserver on 2011-09-02
Used flash aid add-on and it didn't work.

@ MG&TL:  Used the command and downloaded 72 MB out of 76 MB required but the same two links failed again, I get the same error message.

Why do they have to make it so hard to install  a simple plug-in?  I didn't have this problem with the mp3 add-on I had to install.

---

### Post by odiseo77 on 2011-09-02
Have you tried running "apt-get update" before attempting to install the package from the repositories? (I can't access the file from my browser, so they may have upgraded it, and that's why this specific version is not longer available). Try this:

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

If that doesn't work, try installing the package **flashplugin-installer**, instead.

---

### Post by ajgreeny on 2011-09-02
> **TheNixObserver said:**
> Used flash aid add-on and it didn't work.

@ MG&TL:  Used the command and downloaded 72 MB out of 76 MB required but the same two links failed again, I get the same error message.

Why do they have to make it so hard to install  a simple plug-in?  I didn't have this problem with the mp3 add-on I had to install.
I think this is the first time that I have heard of flash-aid not working, so I'm very surprised.

Flash-aid usually makes sure that there are no conflicting applications already installed, and if there are, it removes them.  When you say it did not work, give more details of what you mean.  Did the script not run, or did it run, but flash simply not work for you?

---

### Post by hhh on 2011-09-02
@TheNixObserver, if you are using the Live CD, download the Adobe site tar.gz. Extract it, there is a file called libflashplayer.so, copy it.

~ In your file manager (Nautilus), hit Ctrl+h to make hidden files viewable, in your home directory go to the one named .mozilla. Create a file here named plugins so the contents of .mozilla is extensions, firefox, plugins

~ Paste libflashplayer.so inside of plugins, restart Firefox, done.


The reason people are asking you to install flashplugin-nonfree and others is so that your system will update flash automatically. that's not going to happen on a Live CD.

---

### Post by garvinrick4 on 2011-09-02
#Flashaid does all this below for you when you execute it. Lovinglinux has made it very, very simple for you.
It removes old flashplugins installed. Installs the latest "including the 64 bit beta that works fine" and
keeps you updated when new versions come out.

#I used to tell users to run this below one at a time to install flashplayer, kind of getting obsolete now. (been around a while)
[COLOR=Red]Flash aid will do it for you with the click of a button[/COLOR] [COLOR=Red]and more.[/COLOR]

"Stopping any Firefox that might be running"
sudo killall -9 firefox

 "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

 "Installing Flash Player"
#Download your flash player version from adobe.
cd to directory where flash player download is:
tar zxvf libflashplayer-blah_blah_blah
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

 "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

" now clean up"
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-blah_blah_blah

---


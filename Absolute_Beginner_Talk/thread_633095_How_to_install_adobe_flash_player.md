---
title: "How to install adobe flash player?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by enjtpl on 2007-12-06
I want to way of install in terminal.

---

### Post by kpkeerthi on 2007-12-06
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)

---

### Post by conjur3r on 2007-12-06
# sudo apt-get install flashplugin-nonfree

---

### Post by BLTicklemonster on 2008-01-09
Mine doesn't work. Says it's already installed, too. Tried to install the flash player 9, and it keeps asking me for the install path for mozilla, so I try /usr/lib/mozilla or /bill/home/.mozilla and it won't accept either one.

> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

---

### Post by RomeReactor on 2008-01-09
Hi. See [this thread]("http://ubuntuforums.org/showthread.php?t=636397") regarding the bug in flashplayer-nonfree.

In short, close Firefox, download this [fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), double click it to install, and see if Flash is now correctly recognized by Firefox.

---

### Post by antisocialist on 2008-01-09
go to adobe site, go to download flash player X.XX and download the .tar.gz then follow their instructions, they mostly use the terminal

---

### Post by antisocialist on 2008-01-09
> **BLTicklemonster said:**
> Mine doesn't work. Says it's already installed, too. Tried to install the flash player 9, and it keeps asking me for the install path for mozilla, so I try /usr/lib/mozilla or /bill/home/.mozilla and it won't accept either one.

soz for double post...

it isnt /bill/home/somedir it is /home/bill/somedir

---

### Post by 3rdalbum on 2008-01-09
I believe you need to specify the plugins directory - so /usr/lib/mozilla/plugins, I think.

---

### Post by manmohanpv on 2008-01-09
1. Go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

2. Download the tar.gz file

3. Extract it on the desktop or anywhere

4. Go to the folder through terminal and run sudo ./install_flash_player_9_linux.sh

5. press y (it will ask you to press yes or no)


And do not try sudo apt-get install flashplugin-nonfree because it doesn't work most of the time

-manmohan

---

### Post by misfitpierce on 2008-01-09
I'm hoping the adobe-flashplugin bug will be fixed soon for many new people to keep flash simple as it is a widely used tool. :)

---

### Post by peterwr on 2008-01-09
> **RomeReactor said:**
> Hi. See [this thread]("http://ubuntuforums.org/showthread.php?t=636397") regarding the bug in flashplayer-nonfree.

In short, close Firefox, download this [fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), double click it to install, and see if Flash is now correctly recognized by Firefox.

Tried that, got this:

>   (try: 6 [stopped it there - pwr]) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|88.221.186.70|:80... 
HTTP request sent, awaiting response... No data received.
Retrying.

Still no Flash capability. Any word from Adobe/Ubuntu on when this will be fixed?

---

### Post by RomeReactor on 2008-01-09
Hi. Are you able to browse correctly? perhaps you can try again later. As for when it'll be fixed, keep an eye on [this thread]("http://ubuntuforums.org/showthread.php?t=636397") and the [bug report]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890").

---

### Post by creolbuay on 2008-01-26
This is what I did to get it to work:

   1. [[COLOR="Blue"]Download[/COLOR]]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") the Flash for Linux archive to your desktop
   2. Unpack the archive and extract the file libflashplayer.so
   3. sudo cp libflashplayer.so /usr/lib/firefox/plugins

Restart Firefox and you are good to go.

---

### Post by quaystone on 2008-01-29
So how do you extract the file from the expanded flash package? 'xcuse the "stupid question" -- new user.  thanks, sharon

---

### Post by faintscrawl on 2008-02-02
I'm also having trouble getting adobe flash going.

i tried system>admin>synaptic package manager , then searched and found flashplugin-nonfree, checked it and hit "apply", rebooted (just to be sure), went to npr.org, clicked on some media and it says i need to install flash 8 or better.

---

### Post by jan quark on 2008-02-02
try my easy guide

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by Fechter on 2008-02-02
Download adobe-flash from their site, to your desktop. Download the Tarball. After that right-click and unrar to your desktop. After that enter the untarred folder, run the script in terminal.It worked fine for me.

---

### Post by thiebaude on 2008-02-02
Here is an easy way: [http://launchpadlibrarian.net/107610...untu2_i386.deb](http://launchpadlibrarian.net/107610...untu2_i386.deb)

---

### Post by faintscrawl on 2008-02-02
I did what Romereactor said above and it now works. Many thanks!  One problem solved.  Now I have to find a way to play .wmv files.

---

### Post by RomeReactor on 2008-02-02
> **faintscrawl said:**
> I did what Romereactor said above and it now works. Many thanks!  One problem solved.  Now I have to find a way to play .wmv files.

Hi. To enable WMV playback, add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and then search in Synaptic for **w32codecs**; or download [this package]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu0.7.04.1_i386.deb") and double-click on it to install.

---

### Post by jan quark on 2008-02-02
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

follow this

---

### Post by tad1073 on 2008-02-02
Download adobe-flash from their site, to your desktop. Download the Tarball. After that right-click and extract here to your desktop. After that enter the untarred folder, click on the installer that is included.It worked fine for me.

---

### Post by gandaran on 2008-02-02
the easy way to install flash is go to a web page like youtube, when you get that message flash plugin missing you just click install, you troubles are over, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you prefer,
uninstall any flash, like flashplugin-nonfree or gnash if you tried doe's first.

the ubufox extension will redirect you to install the flashplugin-nonfree 9.0.48, adobe flash is updated now to version 9.0.115 so the link is broken, (all you get installed is an empty /usr/lib/flashplugin-nonfree folder).
 if you use the method above, firefox will install directly from the adobe flash site.

gandaran

---

### Post by Roger Cook on 2008-02-02
I have gone through the hassle of installing flash several times over the past year. I just purchased a AMD 64x2 64 bit machine. I went to Synaptic, searched for Flash, found  it and installed it. It worked first thing after the install. You might need to goto Synaptic delete your version of Flash and then do a reinstall, to get it to work.

:guitar:

---

### Post by nwcowboysfan on 2008-03-25
Just in case people are still finding this post through Google, this is how I got flash player to work (assuming you are using Firefox):

1. Download *.tar.gz file from Adobe's website
2. tar -zxvf *.tar.gz
3. cd into new flash player directory
4. Exit Firefox
5. sudo ./flashplayer-installer
6. Follow prompts and press enter when asked
7. When prompted for installation directory, enter: /usr/lib/**firefox/**
8. Proceed with installation? Yes
9. Another installation? No

That should do it.

---

### Post by noj on 2008-03-26
Download the "Fixed Package"  Make sure that you save it, do not just open the file, then install or reinstall.  Works for me, Im now watching video. Thanks for the help people.

---

### Post by gandaran on 2008-03-27
nothing, my mistake

---

### Post by peterballard on 2008-05-09
> **nwcowboysfan said:**
> Just in case people are still finding this post through Google, this is how I got flash player to work (assuming you are using Firefox):

1. Download *.tar.gz file from Adobe's website
2. tar -zxvf *.tar.gz
3. cd into new flash player directory
4. Exit Firefox
5. sudo ./flashplayer-installer
6. Follow prompts and press enter when asked
7. When prompted for installation directory, enter: /usr/lib/**firefox/**
8. Proceed with installation? Yes
9. Another installation? No

That should do it.

Doesn't work. At step 7 it keeps echoing "WARNING: Please enter a valid installation path." no matter what I type.

---

### Post by peterballard on 2008-05-09
> **jan quark said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

follow this

This worked, i.e. using Synaptic.

Thanks to all who contributed suggestions on this thread.

---

### Post by vilotip on 2008-05-09
manmohan is right...sudo apt-get install flashplugin-nonfree... does not install flashplayer 9...it does however download the installer.

one needs to goto /var/cache , extract it and then run the installer with the terminal

---

### Post by Jheri on 2008-05-19
I've tried the way illustrated on [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) twice, and I keep getting this error:
> E: openjdk-6-jre-headless: subprocess post-installation script returned error exit status 127
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: icedtea-gcjwebplugin: dependency problems - leaving unconfigured

---

### Post by ray_niblock on 2008-06-12
> **nwcowboysfan said:**
> Just in case people are still finding this post through Google, this is how I got flash player to work (assuming you are using Firefox):

1. Download *.tar.gz file from Adobe's website
2. tar -zxvf *.tar.gz
3. cd into new flash player directory
4. Exit Firefox
5. sudo ./flashplayer-installer
6. Follow prompts and press enter when asked
7. When prompted for installation directory, enter: /usr/lib/**firefox/**
8. Proceed with installation? Yes
9. Another installation? No

That should do it.

Yep.  This worked for me also, using Swiftfox.  Just browse to your installation on Swiftfox which is in '/opt/swiftfox', or copy and paste that path and it will install it in an instant.

---

### Post by Johnnie_Walker on 2008-06-15
Could someone tell me how to remove the flashplayer and try to do it some other way, because I installed it exactly as instructed [here]("http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-3"), but it is not working and where it is working players buttons are messed up.

---


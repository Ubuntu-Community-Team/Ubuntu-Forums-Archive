---
title: "Flash+FireFox"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-12-05
Cheers,

I have some issues with Flash in FireFox.  When I go to a site that has some flash animation it doesnt show and that I need to click to download the plugin.

So when I do that, a window appear with 2 options.
Adobe Flash Player
Gnash SWF Player

However, when I select Adobe Flash Player it says that "Package 'flashplugin-nonfree' is already installed"

So whats wrong with this? and how do I fix this.  Any ideas?

Thanks

---

### Post by GSF1200S on 2007-12-05
If you open up add/remove programs and search for flash, does it show the package Ubuntu Restricted Extras installed? If not, install it. If it is, open up synaptic and reinstall the package its saying is already installed. If that doesnt work, can you post the results of:

```
about:plugins
```
(you type this in the address bar of Firefox)

---

### Post by shafin on 2007-12-05
run synaptic and search for flashplugin-nonfree package.See if it's really installed,if it isn't then install it.If you're in 64 bit,hard luck though. You'll have to search and install gnash and firefox-plugin-gnash to get the flash working.

---

### Post by delphiguy on 2007-12-05
in synaptic it says that it is installed.

the output of about:plugins is
```

 Installed plug-ins
 Find more information about browser plug-ins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plug-ins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 DivX Browser Plug-In
 File name:  mplayerplug-in-dvx.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 2007/5/14

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/divx DivX Media Format divx Yes   video/vnd.divx DivX Media Format divx Yes  QuickTime Plug-in 6.0 / 7
 File name:  mplayerplug-in-qt.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 2007/5/14

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/quicktime Quicktime mov Yes   video/x-quicktime Quicktime mov Yes   image/x-quicktime Quicktime mov Yes   video/quicktime Quicktime mp4 Yes   video/quicktime Quicktime - Session Description Protocol sdp Yes   application/x-quicktimeplayer Quicktime mov Yes   application/smil SMIL smil Yes  RealPlayer 9
 File name:  mplayerplug-in-rm.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 2007/5/14

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    audio/x-pn-realaudio RealAudio ram,rm Yes   application/vnd.rn-realmedia RealMedia rm Yes   application/vnd.rn-realaudio RealAudio ra,ram Yes   video/vnd.rn-realvideo RealVideo rv Yes   audio/x-realaudio RealAudio ra Yes   audio/x-pn-realaudio-plugin RealAudio rpm Yes   application/smil SMIL smil Yes  Windows Media Player Plugin
 File name:  mplayerplug-in-wmp.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 2007/5/14

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    application/asx Media Files * Yes   video/x-ms-asf-plugin Media Files * Yes   video/x-msvideo AVI avi,* Yes   video/msvideo AVI avi,* Yes   application/x-mplayer2 Media Files * Yes   application/x-ms-wmv Microsoft WMV video wmv,* Yes   video/x-ms-asf Media Files asf,asx,* Yes   video/x-ms-wm Media Files wm,* Yes   video/x-ms-wmv Microsoft WMV video wmv,* Yes   audio/x-ms-wmv Windows Media wmv,* Yes   video/x-ms-wmp Windows Media wmp,* Yes   video/x-ms-wvx Windows Media wvx,* Yes   audio/x-ms-wax Windows Media wax,* Yes   audio/x-ms-wma Windows Media wma,* Yes   application/x-drm-v2 Windows Media asx,* Yes   audio/wav Microsoft wave file wav,* Yes   audio/x-wav Microsoft wave file wav,* Yes  mplayerplug-in 2007/5/14
 File name:  mplayerplug-in.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 2007/5/14

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/mpeg MPEG mpg,mpeg Yes   audio/mpeg MPEG mpg,mpeg Yes   video/x-mpeg MPEG mpg,mpeg Yes   video/x-mpeg2 MPEG2 mpv2,mp2ve Yes   audio/mpeg MPEG mpg,mpeg Yes   audio/x-mpeg MPEG mpg,mpeg Yes   audio/mpeg2 MPEG audio mp2 Yes   audio/x-mpeg2 MPEG audio mp2 Yes   video/mp4 MPEG 4 Video mp4 Yes   video/3gpp MPEG 4 Video mp4,3gp Yes   audio/mpeg3 MPEG audio mp3 Yes   audio/x-mpeg3 MPEG audio mp3 Yes   audio/x-mpegurl MPEG url m3u Yes   audio/mp3 MPEG audio mp3 Yes   application/x-ogg Ogg Vorbis Media ogg Yes   audio/ogg Ogg Vorbis Audio ogg Yes   audio/x-ogg Ogg Vorbis Audio ogg Yes   application/ogg Ogg Vorbis / Ogg Theora ogg Yes   audio/flac FLAC Audio flac Yes   audio/x-flac FLAC Audio flac Yes   video/fli FLI animation fli,flc Yes   video/x-fli FLI animation fli,flc Yes   video/x-flv Flash Video flv Yes   video/vnd.vivo VivoActive viv,vivo Yes   application/x-nsv-vp3-mp3 Nullsoft Streaming Video nsv Yes   audio/x-mod Soundtracker mod Yes   audio/basic Basic Audio File au,snd Yes   audio/x-basic Basic Audio File au,snd Yes   
 

```

---

### Post by PmDematagoda on 2007-12-05
> **shafin said:**
> run synaptic and search for flashplugin-nonfree package.See if it's really installed,if it isn't then install it.If you're in 64 bit,hard luck though. You'll have to search and install gnash and firefox-plugin-gnash to get the flash working.

Not necessarily, installing Flash on Ubuntu 7.10 x64 has been very much simplified, so it is not much of a problem now.

---

### Post by misfitpierce on 2007-12-05
No, this problem arose for me today as well upon a fresh install on a diff machine. I noticed the 64 bit nspluginwrapper script is not auto working as it should... Luckily I got a fix for you until it gets fixed or fixes itself :( .

Steps to take:

Terminal : wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Untar the libflash.so file... It's the only one you'll need. Untar it to a safe place such as (/home/YOURUSERNAME/.mozilla/plugins/)

Terminal: nspluginwrapper -i /home/YOURUSERNAME/.mozilla/plugins/libflashplayer.so

Restart firefox and test it now... your flash should be working a-ok now.

---

### Post by Johnny3 on 2007-12-05
Try going to Synaptic Package Manager and mark flashplugin-nofree for complete removal. Then do a restart. Go to weather.com and see if it tells you to install Adobe Flash Player. and do it there. That is the way I did it. I use Ubuntu 7.10 64 bit and flash works great. I am new at this use SPM for about ever thing I can. Hope this mite help.
Johnny3
Gainesville Fl

---

### Post by misfitpierce on 2007-12-05
The error thats given upon further looking says md5sum is incorrect or something close to the sort. I believe maybe new flash player for linux and non updated auto flash script may be conflicting? Not 100% on that though.

---

### Post by delphiguy on 2007-12-05
I forgot to mention that I am using Ubuntu 7.10 32bit

---

### Post by misfitpierce on 2007-12-05
maybe take the libflashplayer.so from that location I posted and do this...

Terminal: sudo nautilus /usr/lib/firefox/plugins/
Paste the libflashplugin.so into here and close and try firefox.

---

### Post by mimo74 on 2007-12-05
Hello,

I am new to this forum (as member) but enough old as reader :) I always had Suse as Linux and now changed to ubuntu since ubuntu 7.10 meet my needs and ubuntu is sending a free CD so I don't have to download from internet.

I had your problem (yesterday) about the flash plugin. What I did is to reinstall the plugin using synaptic. I choosed to reinstal the application and after i did reboot the system (it wasen't necessary but in case) and then firefox plugin is working :).

Try the auto-update too, it seem that there is a critical update for the firefox in 7.10.

Good luck.

---

### Post by Johnny3 on 2007-12-05
Do a md5sum check on the ISO file you used to make cd like it says in the Sticky Quickguide. You mite have a bad ISO or cd burn.
Johnny3
Gainesville, Fl

---

### Post by delphiguy on 2007-12-05
> **misfitpierce said:**
> maybe take the libflashplayer.so from that location I posted and do this...

Terminal: sudo nautilus /usr/lib/firefox/plugins/
Paste the libflashplugin.so into here and close and try firefox.

This has fixed my issue, thanks a lot guys.

---

### Post by VON_CAPO on 2007-12-05
SOLVED! thanks. :)

In my case when I tried to use the terminal I had the following error:

fab@desk:~$ sudo wget -c [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
--12:41:53--  [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
           => `get...9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.170.70
Connecting to fpdownload.macromedia.com|88.221.170.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:41:54 ERROR 404: Not Found.

So, I downloaded succesfully using the old method. right click on the link and "Save As" :)

I extracted the file "libflashplayer.so" and I pasted into the folder "/home/fab/.mozilla/plugins" (I have to mention the folder "plugins" did not exist, so, I had to create it).

I restarted Firefox and VOILA!!! Flash is working again.

Thanks a lot. :popcorn:

---

### Post by Kilz on 2007-12-05
> **misfitpierce said:**
> No, this problem arose for me today as well upon a fresh install on a diff machine. I noticed the 64 bit nspluginwrapper script is not auto working as it should... Luckily I got a fix for you until it gets fixed or fixes itself :( .

Steps to take:

Terminal : wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Untar the libflash.so file... It's the only one you'll need. Untar it to a safe place such as (/home/YOURUSERNAME/.mozilla/plugins/)

Terminal: nspluginwrapper -i /home/YOURUSERNAME/.mozilla/plugins/libflashplayer.so

Restart firefox and test it now... your flash should be working a-ok now.

Did you report your problems with flashplugin-nonfree as a bug on launchpad?

Did anyone in this thread with problems report the problem as a bug on launchpad?

---

### Post by VON_CAPO on 2007-12-05
Launchpad links reporting this bug (from july 2007):

---> [https://bugs.launchpad.net/ubuntu/+s...ee/+bug/125131](https://bugs.launchpad.net/ubuntu/+s...ee/+bug/125131)

---> [https://answers.launchpad.net/ubuntu/+question/10061](https://answers.launchpad.net/ubuntu/+question/10061)

---

### Post by delphiguy on 2007-12-05
I just made a launchpad bug report regarding with this issue.
[https://bugs.launchpad.net/ubuntu/+bug/174276](https://bugs.launchpad.net/ubuntu/+bug/174276)

---

### Post by gotmonkey on 2007-12-05
> **misfitpierce said:**
> maybe take the libflashplayer.so from that location I posted and do this...

Terminal: sudo nautilus /usr/lib/firefox/plugins/
Paste the libflashplugin.so into here and close and try firefox.

Thanks, that worked. I have flash working

---

### Post by borisattva on 2007-12-07
> **misfitpierce said:**
> No, this problem arose for me today as well upon a fresh install on a diff machine. I noticed the 64 bit nspluginwrapper script is not auto working as it should... Luckily I got a fix for you until it gets fixed or fixes itself :( .

Steps to take:

Terminal : wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Untar the libflash.so file... It's the only one you'll need. Untar it to a safe place such as (/home/YOURUSERNAME/.mozilla/plugins/)

Terminal: nspluginwrapper -i /home/YOURUSERNAME/.mozilla/plugins/libflashplayer.so

Restart firefox and test it now... your flash should be working a-ok now.

i would like to try this fix, but i dont have a plugins folder in .mozilla. i can make it of course, but i wanted to make sure that this wuld be the folder that a 'working' process would put the file into. is this where the 32 bit version has it?

---

### Post by wolfen69 on 2007-12-07
it seems that there is a problem right now with flash.(in ubuntu restricted extras) alot of people are reporting that flash no longer works in firefox and opera. it didnt work for me on 3 different computers. it has always worked before. i have filed a bug report and hopefully this will be fixed soon.

i installed gnash (in synaptic) and got youtube to work in firefox. that's all i know at this point.

---

### Post by neighborlee on 2007-12-07
> **wolfen69 said:**
> it seems that there is a problem right now with flash.(in ubuntu restricted extras) alot of people are reporting that flash no longer works in firefox and opera. it didnt work for me on 3 different computers. it has always worked before. i have filed a bug report and hopefully this will be fixed soon.

i installed gnash (in synaptic) and got youtube to work in firefox. that's all i know at this point.

It does not work here at all..it says its installed but it is not as flash does not work..I refuse to use gnash as its not stable and I dont therefore trust it.

cheers
nl

---

### Post by melojo on 2007-12-07
> **borisattva said:**
> i would like to try this fix, but i dont have a plugins folder in .mozilla. i can make it of course, but i wanted to make sure that this wuld be the folder that a 'working' process would put the file into. is this where the 32 bit version has it?

I didn't either just create the plugins directory, it worked for me.

---

### Post by borisattva on 2007-12-07
id like to confirm the Gnash experience. the plugin installed smoothly and many sites work fine with it, but many others do not, with bottons either being missing or mispositioned.


> **melojo said:**
> I didn't either just create the plugins directory, it worked for me.

i believe you, i'm sure it works this way and can work in some other ways as well.

i want to make sure that my system works 'the official' way, so that any upgrades/ changes from this point do not break in the future.

is the official plugin (in its current state) broken because THAT file is missing from THAT folder? or is something else breaking it completely, and this is just a work around?

thanks

---

### Post by melojo on 2007-12-07
Here is another link it seems  that a lot of people are having the same problem.
[http://ubuntuforums.org/showthread.php?t=634404&highlight=flashplugin](http://ubuntuforums.org/showthread.php?t=634404&highlight=flashplugin)

I tried Gnash but it ran slow on some sites or wouldn't work at all.

---

### Post by Perpetual on 2007-12-07
I got it to work by uninstalling firefox and installing firefox 3.0...

Not a fix for the problem but it was the only way I could get flash in a browser.

---

### Post by cerealtx on 2007-12-07
i had the same problem, i used automatix to dl the flash, and yah well it didn't work, had to uninstall flash then reinstall using SPM and it worked fine, thats what worked 4 me hope it helps :P

---

### Post by Amstell on 2007-12-07
This worked perfect for me after man try's

Good luck

Installing Flash

   1. download adobe flash by hand
   2. extract libflash.so
   3. cut and paste the .so to /usr/lib/firefox/plugins/
      Code:

      sudo nautilus /usr/lib/firefox/plugins/

   4. make sure the .so is readable by everybody
   5. restart firefox

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by Joeb454 on 2007-12-08
I've not long written a how to workaround this:

[http://ubuntuforums.org/showthread.php?t=635261]("http://ubuntuforums.org/showthread.php?t=635261")

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by DerekVOF on 2007-12-12
> **Amstell said:**
> This worked perfect for me after man try's

Good luck

Installing Flash

   1. download adobe flash by hand
   2. extract libflash.so
   3. cut and paste the .so to /usr/lib/firefox/plugins/
      Code:

      sudo nautilus /usr/lib/firefox/plugins/

   4. make sure the .so is readable by everybody
   5. restart firefox

Finally, worked for me too - after several attempts at installing through Firefox and Synaptic and Add/Remove... 
That's not an acceptable bug :(

---

### Post by Afkpuz on 2007-12-12
See my post here for solution.

[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)


The synaptic version of adobe is broke.  You need to uninstall synaptics version and install the one from adobe.

---

### Post by daradib on 2007-12-12
You can also see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) (which has been updated) for a lot of information on this bug, fixed packages (and how to build own packages- which is a more "correct" way to fix), and information about the fixed packages which have been uploaded to all supported proposed repositories (6.06-7.10). The binary packages should soon be built, but you can use the provided binary packages in that thread, which are compiled versions of the uploaded source packages.

---

### Post by aonegodman on 2007-12-13
> **daradib said:**
> This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

Downloading the package for my 32-bit and installing it finally worked for me in Firefox. I can now watch my "YouTubes".

Thank you so much. This is a great forum community. =D> \\:D/

---

### Post by papuccino1 on 2007-12-13
> **aonegodman said:**
> Downloading the package for my 32-bit and installing it finally worked for me in Firefox. I can now watch my "YouTubes".

Thank you so much. This is a great forum community. =D> \\:D/

You fixed it already I see. But in the future just so you know, all you have to do is download the .tar.gz from Adobe.com (look for the flash plugin), close all firefox windows and install the tar files. Works everytime. 

Good to see you got it fixed.

---

### Post by movrshakr on 2007-12-13
OK, this =is= the Absolute Beginner forum...

So, I dl'ed the .deb file from launchpadlibrarian.net and have it on my desktop.

Now, how do I install it so flash will play inside Firefox?

---

### Post by tombean on 2007-12-13
> **misfitpierce said:**
> maybe take the libflashplayer.so from that location I posted and do this...

Terminal: sudo nautilus /usr/lib/firefox/plugins/
Paste the libflashplugin.so into here and close and try firefox.

thx mate worked for me, but I also had to right-click the link and choose "save location as".

Regards,
-tombean

---

### Post by movrshakr on 2007-12-13
OK, I found some info elsewhere about getting the tar.gz and did so. Extracted. It created a folder containing the installer and an .so file.  Ran the installer as sudo.  It proceeded, but then asked for the installation path of the browser.

That stopped me cold.  I have no idea.

Where is the Easy button?

---

### Post by GSF1200S on 2007-12-13
> **movrshakr said:**
> OK, I found some info elsewhere about getting the tar.gz and did so. Extracted. It created a folder containing the installer and an .so file.  Ran the installer as sudo.  It proceeded, but then asked for the installation path of the browser.

That stopped me cold.  I have no idea.

Where is the Easy button?

Im really not sure on this, but I would think it would be referring to the firefox binary (or executable). Try /usr/bin/

Im not sure past that... I didnt have so many problems with Flash...

---

### Post by daradib on 2007-12-13
> **movrshakr said:**
> OK, this =is= the Absolute Beginner forum...

So, I dl'ed the .deb file from launchpadlibrarian.net and have it on my desktop.

Now, how do I install it so flash will play inside Firefox?

Double-click the package on the desktop and click Install Package. That's all. But if you have 32-bit Ubuntu, you might want to go back to the [thread]("http://ubuntuforums.org/showthread.php?t=636397") as I have linked to the debian package that is currently in the proposed repository.

---

### Post by movrshakr on 2007-12-14
I ended up having to just copy the .so file that was in the downloaded tar.gz into the plugins folder where Firefox was installed (/usr/lib/firefox/plugins).  That did it.  Flash clips now play in Firefox.

---

### Post by AlasdairMacLeod on 2007-12-15
I just downloaded and installed Ubuntu today.  This was the first problem I have encounterd and below is the method that worked for me.

Thanx for your help guys :D

> **Amstell said:**
> This worked perfect for me after man try's

Good luck

Installing Flash

   1. download adobe flash by hand
   2. extract libflash.so
   3. cut and paste the .so to /usr/lib/firefox/plugins/
      Code:

      sudo nautilus /usr/lib/firefox/plugins/

   4. make sure the .so is readable by everybody
   5. restart firefox

---

### Post by krazibone on 2008-01-16
> **AlasdairMacLeod said:**
> I just downloaded and installed Ubuntu today.  This was the first problem I have encounterd and below is the method that worked for me.

Thanx for your help guys :D


 Originally Posted by Amstell  View Post
This worked perfect for me after man try's

Good luck

Installing Flash

1. download adobe flash by hand
2. extract libflash.so
3. cut and paste the .so to /usr/lib/firefox/plugins/
Code:

sudo nautilus /usr/lib/firefox/plugins/

4. make sure the .so is readable by everybody
5. restart firefox




The above method works i can see most sites so far except [www.symantec.com](www.symantec.com), there is a big blank page that it tries to load which doesn't do anything. Anyone know a way around it or a way to disable it?

---

### Post by philinux on 2008-01-16
This is the flash deb file - easier to to install.

Just click the link to dowload to desktop. double click to install. 

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)

---

### Post by daradib on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) has packages for all supported Ubuntu releases (although I doubt the packages for Ubuntu 6.06 and 6.10 will work) and for both 32-bit and 64-bit architectures.

---


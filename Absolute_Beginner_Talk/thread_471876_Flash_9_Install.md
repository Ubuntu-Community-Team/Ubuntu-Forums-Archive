---
title: "Flash 9 Install"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Sig_ZA on 2007-06-12
I downloaded the .tar.gz from Adobe and I have gotten this far after using sudo -i

> Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.
Adobe Flash Player 9 for Linux
Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.
Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.
To cancel the installation at any time, press Control-C.

NOTE: Please exit any browsers you may have running.

Press ENTER to continue...

**Please enter the installation path of the Mozilla**, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): 

What path do I enter please?

---

### Post by Happy_Man on 2007-06-12
Uhh.... you don't need to do that. Simply enter ```
sudo apt-get install ubuntu-restricted-extras
``` to install flash with no hassle. (and stuff like java, codecs, etc. too! :D)

---

### Post by Sig_ZA on 2007-06-12
Thanks. :KS

How does one receive or is notified of updates for these products?

---

### Post by Crafty Kisses on 2007-06-12
> **Sig_ZA said:**
> Thanks. :KS

How does one receive or is notified of updates for these products?

It should just come up in the Synaptic Packet Manager.

---

### Post by Sig_ZA on 2007-06-13
I'm still having a problem. 

Typed in this command: sudo apt-get install ubuntu-restricted-extras

> root@Linux-PC:~# sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libdvdread3 
  libid3tag0 liblame0 libltdl3 libmad0 libmpeg2-4 libsidplay1 msttcorefonts
  odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin unixodbc
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs equivs libdvdcss2 debhelper 
  fakeroot sidplay-base xsidplay sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed: 
  cabextract flashplugin-nonfree gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libdvdread3
  libid3tag0 liblame0 libltdl3 libmad0 libmpeg2-4 libsidplay1 msttcorefonts 
  odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin
  ubuntu-restricted-extras unixodbc
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.

Started firefox, about : plugins and flash wasn't listed nor did any flash content work.

Opened Synaptic, searched for Flash. It was not ticked so I ticked it and tried to install.
Got an error pop-up, something about type in "dpkg --configure -a" at the konsole.

So I did.

> root@Linux-PC:~# dpkg --configure -a
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

root@Linux-PC:~# 

But flash still isn't working. :(

---

### Post by deadgobby on 2007-06-13
It should work. However, lets try the super cow powers of apitude.

sudo aptitude install ubuntu-restricted-extras

Or try this link

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by mig96 on 2007-06-13
See the addon thing that pops up on top?  I installed Flash in 15 seconds with that...

---

### Post by Sig_ZA on 2007-06-13
Thanks. Fixed it.

Seems than when I first ran "sudo apt-get install ubuntu-restricted-extras" something went wrong in the process.

I tried the command again and it mentioned an error about an incomplete install of java and that I should go to Synaptic to fix it.
In Synaptic it was highlighted for re-install, which I did.
After this I ran apt-get again and this time it finished without any errors and flash is now working.

What I really liked here with Ubuntu is that it just doesn't fail. It gives you a tip on how to proceed. Very nice. :KS

---

### Post by mhenriday on 2007-06-24
Whether by skill or by luck, **Sig_ZA**, you're doing a far better job than I ; I've never managed to install **Flash Player** on my machine ! **Adobe**'s instructions read as follows :>    1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.
Downloading and saving the .tar.gz.file to my desktop is done with a click ; a couple more and it is unpacked I have the **install_flash_player_9_linux** directory on my desktop. It is thereafter that my calvary begins - when I open my terminal and type in ```
cd /install_flash_player_9_linux
```I get the following less than elucidating response :```
bash: cd: /install_flash_player_9_linux: Filen eller katalogen finns inte  
```I e, the file or directory does not exist ! Thus I don't even have a chance to run the installer from my terminal. If I double-click on the (according to my terminal, non existent) **install_flash_player_9_linux** directory on my desktop in the file browser, however, it opens up to reveal four items, among which one with the intriguing title **flashplayer-installer**. Alas, it is locked, so that when I double-click on it and am asked whether I want to open the directory or run it or run it in a terminal, the last two alternatives are not available to me....

What am I missing here ? Surely it can't be this complicated to download and install **Adobe**'s tarball ? I am running the 64-bit version of **Feisty**, but if that is what is gumming up the works, I'd expect a notice to that effect....

Henri

---

### Post by Happy_Man on 2007-06-24
> **mhenriday said:**
> Whether by skill or by luck, **Sig_ZA**, you're doing a far better job than I ; I've never managed to install **Flash Player** on my machine ! **Adobe**'s instructions read as follows :
Downloading and saving the .tar.gz.file to my desktop is done with a click ; a couple more and it is unpacked I have the **install_flash_player_9_linux** directory on my desktop. It is thereafter that my calvary begins - when I open my terminal and type in ```
cd /install_flash_player_9_linux
```I get the following less than elucidating response :```
bash: cd: /install_flash_player_9_linux: Filen eller katalogen finns inte  
```I e, the file or directory does not exist ! Thus I don't even have a chance to run the installer from my terminal. If I double-click on the (according to my terminal, non existent) **install_flash_player_9_linux** directory on my desktop in the file browser, however, it opens up to reveal four items, among which one with the intriguing title **flashplayer-installer**. Alas, it is locked, so that when I double-click on it and am asked whether I want to open the directory or run it or run it in a terminal, the last two alternatives are not available to me....

What am I missing here ? Surely it can't be this complicated to download and install **Adobe**'s tarball ? I am running the 64-bit version of **Feisty**, but if that is what is gumming up the works, I'd expect a notice to that effect....

Henri
No, you're entering your commands wrong. If it's on the desktop...
```
cd ~/Desktop/install_flash_player_9_linux
```

And go from there..... 

Alternatively, if you are on Feisty, you can always use ```
sudo apt-get install flashplugin-nonfree
``` to get Flash.

---

### Post by mhenriday on 2007-06-25
Thanks a lot, **Happy_Man** ! I knew I was missing something very basic, but I was unable to see it unaided ; thanks to your help, however, I now realise what it was - I had assumed that because my home directory was called «mhenriday@mhenriday-desktop», that I was, in fact, in my desktop directory by default. So, obviously, was not the case....

What happened then, when I attempted to follow your instructions ? Take a look at the following comedy of errors :```
mhenriday@mhenriday-desktop:~$ cd ~/Desktop/install_flash_player_9_linux
mhenriday@mhenriday-desktop:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
``` As usual, 64-bit computer owners get the shaft ! But not being one to give up easily, I then tried the alternative procedure you had presented :```
mhenriday@mhenriday-desktop:~$ sudo apt-get install flashplugin-nonfree
```with the following result :```

Password:
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser in tillståndsinformation... Färdig
Paketet flashplugin-nonfree är inte tillgängligt, men ett annat paket hänvisar till det. 
Detta betyder vanligen att paketet saknas, har blivit föråldrat eller
bara är tillgängligt från andra källor
E: Paketet flashplugin-nonfree har ingen installationskandidat
```I e, the **flashplugin-nonfree** package is unavailable and there is no candidate for installation ! Where do I go from here ? All the alternativesI on my **Ubuntu** repositories page  - main, universe, restricted, and multiverse - are checked off. Should I attempt to use the «Add» button at the bottom of the page to add **Flash Player**'s download page - [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash»](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash») to my list of third party repositories ? But wouldn't this lead me back to the unsupported x86_64 architecture dilemma ? Do I have to go **Kilz's** route and [install **32-bit Firefox**]("http://ubuntuforums.org/showthread.php?p=1174435") to install the latest **Linux** version of **Flash** on my 64-bit machine ? And is it really necessary - I have already installed all the **Flash**-related programmes from **Synaptic** and the videos I've hitherto encountered that require **Flash Player** seem to work on my machine ; is that not sufficient, or are there videos out there that require the latest 9,0,31,0 version ?...

Henri

---

### Post by Happy_Man on 2007-06-25
Kilz's route..... Adobe hates 64 bits, and tries to make their lives difficult.

---

### Post by mhenriday on 2007-06-25
> **Happy_Man said:**
> Kilz's route..... Adobe hates 64 bits, and tries to make their lives difficult.

Afraid of that. But **Adobe** seems to be far from the only firm that dislikes - or at least, doesn't support - 64-bit computing. At the same time, we are told that - for obvious reasons - 64 bits is the future of computing. Go figure !...

Henri

---


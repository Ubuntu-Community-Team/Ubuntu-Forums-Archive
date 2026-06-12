---
title: "Automatix: Automated Graphical Installer and Tweaker (look here first!)"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by arnieboy on 2005-10-21
**_Introduction_:**
This is a graphical interface for installation of a lot of apps on **UBUNTU BREEZY (DOES NOT WORK ON Warty, Hoary or Dapper)** and for tweaking a few things to get your Ubuntu box up and working in full throttle in the quickest possible timespan.

[COLOR="Blue"]**For a KUBUNTU BREEZY version of Automatix go to [this thread]("http://ubuntuforums.org/showthread.php?t=105343")**[/COLOR]

**_Features_:**
**a)** Shoots up gnome-terminal for almost all downloads (giving u a good idea about the status of your download ,etc)
**b)** deletes all downloaded files (except those downloaded by apt-get) automatically after installation.
**c)** automatix does not overwrite anything without making a date_and_time_based backup.
**d)** When u install a new version of automatix, it automatically uninstalls the last version.

**_Capabilities_:**
1) Installs multimedia codecs
2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
3) Installs RAR, ACE and UNRAR archive support
4) Installs skype
5) Installs Acrobat reader 7 and firefox plugin for the same.
6) Installs Gnomebaker (CD/DVD burning s/w for GNOME)
7) Installs gftp (FTP client for GNOME with ssh capability)
8) Installs DC++ , amule and Limewire (file sharing progs)
9) Installs Frostwire (GPL clone of Limewire)
10) Installs multimedia editors (Audacity (audio), Kino (video), EasyTag (ID3))
11) Installs DVD (dvdrip) ripper 
12) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
13) Installs totem-xine, VLC and Beep Media Player (with docklet)
14) Installs Opera Browser
15) Installs Debian Menu (shows all installed applications) ([COLOR="Blue"]**this kills and restarts your gnome-panel without warning u but its a completely harmless operation!**[/COLOR])
16) Installs Bittornado and **Azureus** (Bittorrent clients)
17) Installs Avidemux (Video editing tool) **(New version 2.1.0)**
18) Enables Numlock on (turns numlock on Gnome startup)
19) Installs Programming Tools (Anjuta (C/C++ IDE), Bluefish (HTML editor) and Screem (Web Development Env.))
20) Install GnomePPP (Graphical Dial up connection tool) 
21) Installs MS true type fonts 
22) Configures ctrl-alt-del to start gnome-system-monitor (*aka* windows)
23) Installs Streamripper and Streamtuner
24) Installs NON-FREE audio and dvd codecs
25) Installs ndisgtk (WiFi configurator Graphical user interface) 
26) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer. (**no support for AMD64 and ppc packages**) 
27) Adds 3 nautilus scripts (open any file with gedit as root; open a nautilus window as root in any folder; open gnome search tool in any folder (Right click in a nautilus window and look under "scripts")
28) Installs SUN'S JAVA JRE version 1.5
29) Installs SUN'S JAVA JDK version 1.5
30) Installs wine ** (u need to run *winecfg* manually after installation)**
31[COLOR="Red"]*[/COLOR]) Installs firestarter (GNOME firewall frontend) and adds firestarter to GNOME startup
32[COLOR="Red"]*[/COLOR]) installs gdesklets (GNOME eyecandy) and adds gdesklets to GNOME startup
33[COLOR="Red"]*[/COLOR]) Gamepads (Makes USB gamepads work)
34[COLOR="Red"]*[/COLOR]) Turns DMA ON on Intel and AMD machines **(needs a restart)**
35[COLOR="Red"]*[/COLOR]) NVIDIA cards (Detects Nvidia cards and installs drivers) **(Needs a restart)**
36[COLOR="Red"]*[/COLOR]) Adds midi capability to your Ubuntu box [B](test by playing a midi file with timidity or pmidi from terminal)
37[COLOR="Red"]*[/COLOR]) Installs Firefox 1.5 and its plugins**(themes and extensions are not retained, bookmarks need to be copied from backup folder)**

[COLOR="Red"]*[/COLOR] --> [COLOR="Blue"]**These options require manual intervention and clicking. Please stand by!**[/COLOR]

**_Where to find it?_**
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by fut21 on 2005-10-23
Is it balckdown java or sun java i installe with automatix ?

---

### Post by ykpaiha on 2005-10-23
thanks, looks like a very good idea but, 
sorry I do not find any link to your automatix ?
where  is it please

---

### Post by arnieboy on 2005-10-23
[QUOTE=fut21]Is it balckdown java or sun java i installe with automatix ?[/QUOTE]
Sun's Java 1.5

---

### Post by arnieboy on 2005-10-23
[QUOTE=ykpaiha]thanks, looks like a very good idea but, 
sorry I do not find any link to your automatix ?
where  is it please[/QUOTE]
look just above the "quote" button on the first post (bottom right corner) on [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by wiseguy on 2005-10-23
Nice work!

I noticed keyes has included the w32codecs. Wondering why the legalities are not an issue with Easy Ubuntu and they are with Automatix?

---

### Post by bored2k on 2005-10-23
> 12) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
Why the old mozilla mplayer plugin? 3.11 rocks.
[http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

---

### Post by wiseguy on 2005-10-23
Gotcha. :D

Thanks.

---

### Post by Brando569 on 2005-10-25
one suggestion to make it more automatic, could you remove the "app here"installed successfully notification? i have a slow connection here at college and i set this up assuming it would go through everything sequentially so i left for two or so hours and came back it was at the end of the first thing! :( just a suggestion...

---

### Post by dudinatrix on 2005-10-25
Ok, this is a n00b question....

When starting for the first time, it prompts you to hit OK if you "have not set your root password yet".  Is the root password different from using sudo?  Not sure to hit OK or Cancel.

---

### Post by arnieboy on 2005-10-25
[QUOTE=dudinatrix]Ok, this is a n00b question....

When starting for the first time, it prompts you to hit OK if you "have not set your root password yet".  Is the root password different from using sudo?  Not sure to hit OK or Cancel.[/QUOTE]
yes root password is different(which u have to set with automatix). ur sudo password is your user password.

---

### Post by herot on 2005-10-26
arnieboy, how can i tell what prelinking is doing?? like as its actually doing it
does it get put inside a log file somewhere?

---

### Post by arnieboy on 2005-10-26
[QUOTE=herot]arnieboy, how can i tell what prelinking is doing?? like as its actually doing it
does it get put inside a log file somewhere?[/QUOTE]
[http://www.crast.us/james/articles/prelink.php](http://www.crast.us/james/articles/prelink.php)

---

### Post by funkenstein on 2005-10-27
Hi there, I posted this in [_here_](http://ubuntuforums.org/showthread.php?t=66563&page=41) before I saw this thread, so here goes again.... sorry for the repost, but I really want to get opera running on my 64bit breezy:
```

me@ubuntu:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.50-20050916.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
``` 
What to do now??? :'(

---

### Post by Tm_T on 2005-10-27
This might sound a bit stupid but... how you prevent that not break system if it does install anything using --force-all flag?! I've heard several complains from newbies when automatix break their X or something else as crucial.

I'm just wondering...

---

### Post by arnieboy on 2005-10-27
[QUOTE=fut21]Is it balckdown java or sun java i installe with automatix ?[/QUOTE]
the latest version of automatix (2.13) has sun java 1.5

---

### Post by Nano on 2005-10-28
It works great, indeed!
However, this time I also installed the midi support and I think it's slowing down the performances of my laptop.

What's the best way to uninstall it?

---

### Post by arnieboy on 2005-10-28
[QUOTE=Nano]It works great, indeed!
However, this time I also installed the midi support and I think it's slowing down the performances of my laptop.

What's the best way to uninstall it?[/QUOTE]
read "autoscript" and undo whatever it does for adding midi capability.
In a later version, I will automate "undo" for all options.

---

### Post by kakashi on 2005-10-29
can i get the hoaray version please.
i really don't want to move to breezy cuz when i did it gave me a lot of problems

---

### Post by arnieboy on 2005-10-29
[QUOTE=kakashi]can i get the hoaray version please.
i really don't want to move to breezy cuz when i did it gave me a lot of problems[/QUOTE]
sorry but I have to rewrite the whole thing for hoary.. and thats quite a bit of work.. if I do get time however, I will try and do it for u.

---

### Post by kakashi on 2005-10-29
[QUOTE=arnieboy]sorry but I have to rewrite the whole thing for hoary.. and thats quite a bit of work.. if I do get time however, I will try and do it for u.[/QUOTE]


is this written in python. if so please tell what changes need to be made and i'll make them myself. 
also i see there was a hoaray version. can i have a copy of that.

ok don't mind me. i just looked at the code and it seems to be in bash. 
i can still edit it a bit.

---

### Post by kelean on 2005-10-30
Arnieboy thank you very much.  Your Automatix program is very cool. You have saved me a lot of time setting up my new breezy install.  Java has never been so easy to install.  The only problem I had was that annoying error popup for the motif lib-3 missing.  I just check don't show message again and its all good.

Thanks again, Kelean

---

### Post by arnieboy on 2005-10-30
[QUOTE=kakashi]is this written in python. if so please tell what changes need to be made and i'll make them myself. 
also i see there was a hoaray version. can i have a copy of that.

ok don't mind me. i just looked at the code and it seems to be in bash. 
i can still edit it a bit.[/QUOTE]
its a bash script. I myself dont have a copy of the hoary version.. I think its on one of the posts in the automatix thread.

---

### Post by germex on 2005-11-01
Thanks, pal. Excellent. I already had installed most of the codecs, AMule and a few other things, but I was having problems watching DVDs. After I ran Automatix I tried the DVD and works great i Guess I was missing a codecs or had a wrong one. I wanted to install gnomebaker and now i have it and works great. I am relatively new to linux, i tried Red Hat a few years ago. And a few weeks ago I installed Breezy. 
Thanks for the help, really appreciated.

---

### Post by arnieboy on 2005-11-03
**UPDATE (11/03/2005 07:22 PM ET): [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") updated to version 3.0 Please redownload and reinstall**
Latest version (**3.0**) has the following NEW features:
[B]a) wine repositories added. now u get the latest version of wine from the wine headquarters.
b) ndisgtk added (WiFI configurator Graphical user interface)[/B]

---

### Post by arnieboy on 2005-11-03
If someone could make a debian package out of Automatix version  3.0, it would be awesome!

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=arnieboy]**UPDATE (11/03/2005 07:22 PM ET): [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") updated to version 3.0 Please redownload and reinstall**
Latest version (**3.0**) has the following NEW features:
[B]a) wine repositories added. now u get the latest version of wine from the wine headquarters.
b) ndisgtk added (WiFI configurator Graphical user interface)[/B][/QUOTE]


This warrents a change in the title of the thread.

---

### Post by BLTicklemonster on 2005-11-05
Hey arnieboy, can't you make it where it either only adds the repositories to what I already have, or have it replace the repositories I had once it's done?

---

### Post by ishtvan222 on 2005-11-05
Very nice program, I think it would be a good idea to seperate the flash plugin from the java tho. I have Java SDK installed and when i select the plugins it also installs j2re. Just my opinion tho.

Thanks for making such a nice script

---

### Post by arnieboy on 2005-11-05
[QUOTE=ishtvan222]Very nice program, I think it would be a good idea to seperate the flash plugin from the java tho. I have Java SDK installed and when i select the plugins it also installs j2re. Just my opinion tho.

Thanks for making such a nice script[/QUOTE]
u might have java SDK installed, but most people wudnt have it. and java and its plugin is a core part of FF plugins.

---

### Post by kakashi on 2005-11-06
[QUOTE=BLTicklemonster]Hey arnieboy, can't you make it where it either only adds the repositories to what I already have, or have it replace the repositories I had once it's done?[/QUOTE]


you could do some of the work your self. 
before runing the script. 
```
 
cp /etc/apt/sources.list $HOME/sources.list

```
later you can do this. 
```

mv $HOME/sources.list /etc/apt/

```

---

### Post by bugmenot on 2005-11-06
Could you add the Ooo2 thumbnailer?

[http://www.ubuntuforums.org/showthread.php?t=76566](http://www.ubuntuforums.org/showthread.php?t=76566)

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=bugmenot]Could you add the Ooo2 thumbnailer?

[http://www.ubuntuforums.org/showthread.php?t=76566](http://www.ubuntuforums.org/showthread.php?t=76566)[/QUOTE]

That is an awesome hack.

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=kakashi]you could do some of the work your self. 
before runing the script. 
```
 
cp /etc/apt/sources.list $HOME/sources.list

```
later you can do this. 
```

mv $HOME/sources.list /etc/apt/

```[/QUOTE]
(I meant make IT do it for ME... like automating... like ... you know automatix)

---

### Post by syphix on 2005-11-07
Am I the only one who can't get Acrobat Reader to install on this?  It stalls on "Installing Acrobat Reader and plugin required for Firefox", never getting installed.

---

### Post by arnieboy on 2005-11-07
[QUOTE=syphix]Am I the only one who can't get Acrobat Reader to install on this?  It stalls on "Installing Acrobat Reader and plugin required for Firefox", never getting installed.[/QUOTE]
it will get installed if u give it time. acrobat reader is a 15 MB download. if ur net speed sucks.. therez nuthing much automatix can do abt it.

---

### Post by syphix on 2005-11-07
Hadn't noticed the net activity.  Thanks, I'll give it mre time.

---

### Post by Navyblue on 2005-11-07
I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?

---

### Post by silentQ on 2005-11-07
hey guys... just installed automatix...
now when i load azureus   it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above  same with bitcomet :confused:

---

### Post by Navyblue on 2005-11-07
After installing the fonts, my openoffice2 failes to start now. But I am not sure if it is automatix related. But apeart from automatix I did nothing to my system. The error message is:

```

I18N: X Window System doesn't support locale "en_GB"
I18N: X Window System doesn't support locale "en_US"
I18N: X Window System doesn't support locale "C"
Qt: Locales not supported on X server
*** glibc detected *** free(): invalid next size (fast): 0x080def10 ***
KCrash: Application 'soffice.bin.real' crashing...
/usr/lib/openoffice2/program/soffice: line 224: 10397 Alarm clock             "$sd_prog/$sd_binary" "$@"

```

I have used dpkg-reconfigure locales to enable the locale mentioned but the outcome is the same.

---

### Post by pioni on 2005-11-08
Does this support Quicktime? I installed Easy Ubuntu a while ago and at least it doesn't have Quicktime support, or at least it didn't allow me to view Quicktime trailers at apple.com/trailers (Totem said it couldn't find suitable plugin).

---

### Post by arnieboy on 2005-11-08
[QUOTE=pioni]Does this support Quicktime? I installed Easy Ubuntu a while ago and at least it doesn't have Quicktime support, or at least it didn't allow me to view Quicktime trailers at apple.com/trailers (Totem said it couldn't find suitable plugin).[/QUOTE]
check out version 3.1 of automatix.
install mplayer plugin and AUD-DVD codecs
that should solve ur problem.

---

### Post by Navyblue on 2005-11-09
[QUOTE=Navyblue]I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?[/QUOTE]

Can someone please help me with this?

---

### Post by Bonarges on 2005-11-09
Oh.. My... God...

If this thing does half of what it says it does, you may have my first born (if you exercise the option before I find a woman to impregnate).  This is amazing.  I'm a total linux noob and just want to get this up to a running level so i can tinker and learn how to really do it.

Thanks for this.

CM

---

### Post by kakashi on 2005-11-09
[QUOTE=Bonarges]Oh.. My... God...

If this thing does half of what it says it does, you may have my first born (if you exercise the option before I find a woman to impregnate).  This is amazing.  I'm a total linux noob and just want to get this up to a running level so i can tinker and learn how to really do it.

Thanks for this.

CM[/QUOTE]

wow this guy must really like  Automatix.
also if you want to learn then don't use automatix.
if you want a system up and running in no time then automatix is for you.

---

### Post by arnieboy on 2005-11-09
[QUOTE=Navyblue]I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?[/QUOTE]
yes I will help u out on this and fix this midi bug in the next release of automatix. herez what u have to do:
```
gedit .bashrc
```
add the following lines:
> export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0

```
gedit .gnomerc
```
add the following lines:
> export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0

that shd get u all set. test by running the following:
```
timidity file.mid
```
where file.mid will be replaced by the name of the mid file u are trying to play.

---

### Post by trash on 2005-11-09
Just wondering if a comic book reader can be added for reading .cbr files...

[http://ubuntuforums.org/showthread.php?t=81180&highlight=.cbr](http://ubuntuforums.org/showthread.php?t=81180&highlight=.cbr)
[http://www.jcoppens.com/soft/cbrpager/index.en.php](http://www.jcoppens.com/soft/cbrpager/index.en.php)

---

### Post by Navyblue on 2005-11-09
[QUOTE=arnieboy]yes I will help u out on this and fix this midi bug in the next release of automatix. herez what u have to do:
```
gedit .bashrc
```
add the following lines:

```
gedit .gnomerc
```
add the following lines:


that shd get u all set. test by running the following:
```
timidity file.mid
```
where file.mid will be replaced by the name of the mid file u are trying to play.[/QUOTE]


Thanks a heap, MIDI works now. :)

---

### Post by arnieboy on 2005-11-09
[QUOTE=Navyblue]Thanks a heap, MIDI works now. :)[/QUOTE]
u are welcome. I have also released a bug fix version of automatix (version 3.1.1) in which midi will now work out of the box :)

---

### Post by silentQ on 2005-11-10
hey i posted before, didnt get an answer 
heres the original post

"hey guys... just installed automatix...
now when i load azureus it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above same with bitcomet "

---

### Post by Mr_J_ on 2005-11-10
This should be included with Ubuntu.
It's great!
My instalation before I couldn't get videos to play in firefox, and now on this one it works like normal!

This is great!

---

### Post by arnieboy on 2005-11-10
[QUOTE=silentQ]hey i posted before, didnt get an answer 
heres the original post

"hey guys... just installed automatix...
now when i load azureus it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above same with bitcomet "[/QUOTE]
the answer is in this post on the other thread:
[http://ubuntuforums.org/showpost.php?p=478713&postcount=636](http://ubuntuforums.org/showpost.php?p=478713&postcount=636)
hope this helps.

---

### Post by silentQ on 2005-11-10
i'll try it now thanx :)

---

### Post by neymac on 2005-11-12
When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?

---

### Post by BLTicklemonster on 2005-11-12
[QUOTE=neymac]When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?[/QUOTE]
That's what I meant when I posted about it automatically putting things back. I don't understand why repository settings are not able to just keep adding and adding and why you should comment out some when using new ones, and vice versa.

Hint: when you finally get your originals back, save them in /home/you/ as repository original, then each others you get, save them by a name you will remember. I'm going to do this one of these days.

I think, though, that you can go to synaptic, and then reset your repositories in there the way you would have set up extra reps originally. Settings>repositories> make sure they are all checked, and press okay. Maybe I'm wrong, but I think I did that once, and it set me back to normal. (like I can be normal, riiiight)

---

### Post by arnieboy on 2005-11-12
[QUOTE=neymac]When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?[/QUOTE]
its simple enough.. delete your existing sources.list and rename the backup file as sources.list in /etc/apt/ (that will replace the one which automatix creates).

---

### Post by neymac on 2005-11-12
[QUOTE=arnieboy]its simple enough.. delete your existing sources.list and rename the backup file as sources.list in /etc/apt/ (that will replace the one which automatix creates).[/QUOTE]

Thank's, Arnieboy. I did it.

By the way, is there any possibility of before you leave the Automatix it renames both files, like it did at the begining, restoring the previous sources.list? 
(It renames /etc/apt/sources.list as backup and created a new one)

---

### Post by jrincon87 on 2005-11-12
I installed, among other things, the MIDI support and now I have no sound at all.
Any clue?

---

### Post by arnieboy on 2005-11-12
[QUOTE=jrincon87]I installed, among other things, the MIDI support and now I have no sound at all.
Any clue?[/QUOTE]
when u say no sound at all.. u need to gimme some more info.. 
do this from terminal:
```
mplayer <filename>
```
where filename is a mp3 file.
paste the terminal out put here.

---

### Post by jrincon87 on 2005-11-13
When I say I have no sound at all, I mean it. I can't hear any system sound, I try to play something with XMMS and I don't hear anything, I prove it with another output (like OSS), and nothing happens. The XMMS seems to be playing the file, but I don't hear anything.

---

### Post by arnieboy on 2005-11-13
[QUOTE=jrincon87]When I say I have no sound at all, I mean it. I can't hear any system sound, I try to play something with XMMS and I don't hear anything, I prove it with another output (like OSS), and nothing happens. The XMMS seems to be playing the file, but I don't hear anything.[/QUOTE]
u probably need to check ur volume settings (or whether ur speakers are properly attached to the sound output of your computer).. if xmms is playing a file that means there shdnt be anything wrong with the sound server.

---

### Post by arnieboy on 2005-11-14
[B] Automatix Version 3.3 released!
Please redownload and reinstall.[/B]

Latest version (**3.3**) has the following new update:
[B]a)Done away with the plf repos (They freaked me out a couple of days back) and replaced them with the seveas repos.
The seveas repos rock! They have all that the plf repos have and much more. They backport quite a few apps from the dapper repos to the breezy repos! That means u will get periodical updates to quite a few of your favorite apps with backports!
b) Added a separate section for sun's java 1.5 JRE and SDK!
c) Added freenx (and a howto on how to configure it)
d) Options 29 to 35 require manual intervention and clicking and hence have been taken to the end. The first 28 options install without any user input.[/B]

---

### Post by jrincon87 on 2005-11-14
> u probably need to check ur volume settings (or whether ur speakers are properly attached to the sound output of your computer).. if xmms is playing a file that means there shdnt be anything wrong with the sound server.

Sorry, this is what happened. I have two sound cards. It seems that during the installation of the Midi support, the default output has been changed. Now, how do I set Ubuntu to output sound through a determinate sound card? (The sound card I want the output is hw:1,0).
Thanks.

---

### Post by tig4 on 2005-11-15
Where's the link?

---

### Post by arnieboy on 2005-11-15
**Automatix is back! Sorry about the downtime...**

[B]Automatix updated to version 3.3.1 Please redownload and reinstall.

Latest version (3.3.1) has the following new bugfix:
a)Minor bugfix in java script and severe juggling with seveas and plf repos to get everything right.everything seems to be fine now but I still have my fingers crossed till I get confirmation from users.[/B]

---

### Post by Zhukov on 2005-11-15
---

---

### Post by arnieboy on 2005-11-15
[QUOTE=Zhukov]Hello ArnieBoy!
Dunno if you remember me (i made a automatix-based app, IT oriented, with ns2, jsdk and so on), and i was wondering if you want to merge my progress with automatix (the DEIUCbuntu online is NOT the new version). I could also get  you the host i was about to receive for my project. What do you think?[/QUOTE]
I think u need to elaborate more on what u mean by "upgrading to OO2 made my laptop unusable". Thats a tall claim and u better support it with some good arguments and data.

---

### Post by Zhukov on 2005-11-15
Easy! Dont take it so deep! I was just saying what happened to me! I upgrade to 002 using automatix and shutdown, all went fine (i only did that). When i rebooted, i opened a ppt using oo2 and gnome-panel crashed and kept on crashing ever since! Since the only thing i did was run automatix and install oo2 i was just trying to see if someone else experienced the same problems! geez...

---

### Post by arnieboy on 2005-11-15
[QUOTE=Zhukov]Easy! Dont take it so deep! I was just saying what happened to me! I upgrade to 002 using automatix and shutdown, all went fine (i only did that). When i rebooted, i opened a ppt using oo2 and gnome-panel crashed and kept on crashing ever since! Since the only thing i did was run automatix and install oo2 i was just trying to see if someone else experienced the same problems! geez...[/QUOTE]
u are the one who needs to take it easy buddy!
there is no way automatix affected anything in the gnome panel (it did not even install an applet). u probably screwed it up in some other way which u dont have the faintest idea of and are merrily attaching the blame to automatix which I dont quite appreciate. "making my laptop unusable" is a very strong statement and it expresses a lot of disdain if u arent already aware of it. this is the last post of yours I am replying to. The last thing I am going on to here is a trollish flame war. 
In future try to avoid making sweeping statements if u dont want to earn the disapproval of the members of this community who give a lot of time and effort in order to make the lives of millions of dummies easier.

---

### Post by Zhukov on 2005-11-15
Nobody wants a flame war and please do not see none of my posts as an attempt to start one! Automatix is great, no doubt! And since you say there is no chance automatix screwed my gnome-panel i do believe in you and my post was edited (you can check it). I started my "claim" saying "maybe it just me". I had no intention of insult your work or something similar! Everyone is gratefull for your work. Maybe my words were harsh, and if they were i apologize. I was merely trying to help.

---

### Post by souled on 2005-11-15
How can I remove the Debian Menu? A suggestion for Automatix - maybe there can be a uninstall function to uninstall previously installed items by Automatix.

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]How can I remove the Debian Menu? A suggestion for Automatix - maybe there can be a uninstall function to uninstall previously installed items by Automatix.[/QUOTE]
```
sudo apt-get remove menu menu-xdg pdmenu
killall gnome-panel
```
I dont like the idea of automating removal of software.. its something every user shd do manually... its justmy own philosophy.
I am planning to start a thread in the automatix forum on how to remove all the options that automatix installs. that shd help.

---

### Post by souled on 2005-11-15
[QUOTE=arnieboy]```
sudo apt-get remove menu menu-xdg pdmenu
killall gnome-panel
```
I dont like the idea of automating removal of software.. its something every user shd do manually... its justmy own philosophy.
I am planning to start a thread in the automatix forum on how to remove all the options that automatix installs. that shd help.[/QUOTE]

I see... That idea would be very helpful. I'm trying out the newest version, and when the repos were updating or whatever.... it got stuck at 99% said it was downloading headers. In synaptic, I hit reload... and it's pretty much frozen at Download 34 of 35. Is there something wrong with one of the repos?

Edit: After I hit cancel in Synaptic I got a message saying it could not download all of the repository indexes. And these repos listed:
```
http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg: Connection failed
http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release
```

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]I see... That idea would be very helpful. I'm trying out the newest version, and when the repos were updating or whatever.... it got stuck at 99% said it was downloading headers. In synaptic, I hit reload... and it's pretty much frozen at Download 34 of 35. Is there something wrong with one of the repos?[/QUOTE]
u shd never run automatix and synaptic simultaneously. repos can be slow at times. u shd be a little patient.. if they dont respond for 2minutes or so, cancel and try again.

---

### Post by souled on 2005-11-15
What I meant was I canceled Automatix then I opened up Synaptic. Sorry for the confusion.

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]What I meant was I canceled Automatix then I opened up Synaptic. Sorry for the confusion.[/QUOTE]
np. the seveas repos seem to be down at the moment. I did an **apt-get update** myself to confirm. wait awhile and try later.

---

### Post by phanboy_iv on 2005-11-15
Geat idea, arnieboy. Fills Ubuntu's cracks.
Every thing worked fine except now flash animations won't play or play very slowly in Firefox. I tried uninstalling all the flash packages with synaptic, deleting the "pluginreg.dat" files, and reinstalling the flash plugins, but the problem remains.

Great tool, though. Keep at it.

---

### Post by lameiro on 2005-11-15
I am installing it and I already loving it!
Great!

[http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl)

I saw some problems with it but now I think the server is up again...
and the webpage is also up:)

---

### Post by arnieboy on 2005-11-15
[QUOTE=phanboy_iv]Geat idea, arnieboy. Fills Ubuntu's cracks.
Every thing worked fine except now flash animations won't play or play very slowly in Firefox. I tried uninstalling all the flash packages with synaptic, deleting the "pluginreg.dat" files, and reinstalling the flash plugins, but the problem remains.

Great tool, though. Keep at it.[/QUOTE]
flash on linux has a gazillion problems.
try this thread and see if it works for u or not:
[http://ubuntuforums.org/showthread.php?t=89827](http://ubuntuforums.org/showthread.php?t=89827)

---

### Post by xavierh on 2005-11-16
do I need to set additional repositories in my sources.lst in order for the script to work?

---

### Post by arnieboy on 2005-11-16
Automatix 3.4 is pretty much a stable and final version for the time being. I will not be adding any new functionality to automatix in the near future (of course firefox 1.5 final version and gaim 2.0 being exceptions). I will however be releasing bugfix versions if and when needed. Hope u all enjoy automatix and ubuntu as such. :)
-Arnie

---

### Post by cstudent on 2005-11-16
[QUOTE=arnieboy]Automatix 3.4 is pretty much a stable and final version for the time being. I will not be adding any new functionality to automatix in the near future (of course firefox 1.5 final version and gaim 2.0 being exceptions). I will however be releasing bugfix versions if and when needed. Hope u all enjoy automatix and ubuntu as such. :)
-Arnie[/QUOTE]

bout time you took a break

---

### Post by arnieboy on 2005-11-17
**Automatix updated to version 3.4.2 because of repository issues.. please download and reinstall.**

---

### Post by h0bbe on 2005-11-19
Automatix removed Splashy from my system, why?

---

### Post by h0bbe on 2005-11-19
I noticed another thing after a reboot. Instead of the standard sound when the login-screen appears I hear a beep. The beep occurs once again when I start Firefox (I guess). I had none of this before I ran Automatix :confused:

Hope anyone can help me!

---

### Post by arnieboy on 2005-11-19
[QUOTE=h0bbe]Automatix removed Splashy from my system, why?[/QUOTE]
if u are running breezy.. it doesnt have splashy.. it uses usplash. and automatix does nothing to remove that.

---

### Post by arnieboy on 2005-11-19
[QUOTE=h0bbe]I noticed another thing after a reboot. Instead of the standard sound when the login-screen appears I hear a beep. The beep occurs once again when I start Firefox (I guess). I had none of this before I ran Automatix :confused:

Hope anyone can help me![/QUOTE]
the sound server probably got tunred off.. but even that automatix did not do.
go to system -->preferences--> sound and make sure u have "enable sound server at startup" and "enable sound for events" checked.

---

### Post by bfonseca on 2005-11-19
> **arnieboy]**_Introduction_:**
This is a graphical interface for installation of a lot of apps on **UBUNTU BREEZY (DOES NOT WORK ON Warty, Hoary or Dapper)** and for tweaking a few things to get your Ubuntu box up and working in full throttle in the quickest possible timespan.

**_Features_:**
**a)** Shoots up gnome-terminal for almost all downloads (giving u a good idea about the status of your download ,etc)
**b)** deletes all downloaded files (except those downloaded by apt-get) automatically after installation.
**c)** automatix does not overwrite anything without making a date_and_time_based backup.
**d)** When u install a new version of automatix, it automatically uninstalls the last version.

**_Capabilities_:**
1) Installs multimedia codecs
2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
3) Installs RAR, ACE and UNRAR archive support
4) Installs skype
5) Installs Acrobat reader 7 and firefox plugin for the same.
6) Installs Gnomebaker (CD/DVD burning s/w for GNOME)
7) Installs gftp (FTP client for GNOME with ssh capability)
8) Installs DC++ , amule and Limewire (file sharing progs)
9) Installs multimedia editors (Audacity (audio), Kino (video), EasyTag (ID3))
10) Installs DVD (dvdrip) ripper 
11) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
12) Installs totem-xine, VLC and Beep Media Player (with docklet)
13) Installs Opera Browser
14) Installs Debian Menu (shows all installed applications) ([COLOR="Blue"]**this kills and restarts your gnome-panel without warning u!**[/COLOR])
15) Installs Bittornado and **Azureus** (Bittorrent clients)
16) Installs Avidemux (Video editing tool)
17) Enables Numlock on (turns numlock on Gnome startup)
18) Installs Programming Tools (Anjuta (C/C++ IDE), Bluefish (HTML editor) and Screem (Web Development Env.))
19) GnomePPP (Graphical Dial up connection tool) 
20) Installs MS true type fonts 
21) Configures ctrl-alt-del to start gnome-system-monitor (*aka* windows)
22) Installs Streamripper and Streamtuner
23) Installs NON-FREE audio and dvd codecs
24) Installs ndisgtk (WiFi configurator Graphical user interface) 
25) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer. (**no support for AMD64 and ppc packages**) 
26) Adds 3 nautilus scripts (open any file with gedit as root said:**
> *[/COLOR]) Installs firestarter (GNOME firewall frontend) and adds firestarter to GNOME startup
30[COLOR="Red"]*[/COLOR]) installs gdesklets (GNOME eyecandy) and adds gdesklets to GNOME startup
31[COLOR="Red"]*[/COLOR]) Gamepads (Makes USB gamepads work)
32[COLOR="Red"]*[/COLOR]) Turns DMA ON on Intel and AMD machines **(needs a restart)**
33[COLOR="Red"]*[/COLOR]) NVIDIA cards (Detects Nvidia cards and installs drivers) **(Needs a restart)**
34[COLOR="Red"]*[/COLOR]) Adds midi capability to your Ubuntu box ** (test by playing a midi file with timidity or pmidi from terminal)**

[COLOR="Red"]*[/COLOR] --> [COLOR="Blue"]**These options require manual intervention and clicking. Please standby!**[/COLOR]

**_Where to find it?_**
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
thanks arnieboy for Automatix. I installed it and it fixed alot of problems. I have recommended this to a few friends aswell.
Brian

---

### Post by h0bbe on 2005-11-20
It was Splashy I had, I installed it. And I also saw Automatix say "removing splashy" but I don't want to argue with you. Both the sound options were checked but I still have the beep and the only thing I've done is to run Automatix. Maybe I should have mentioned that I'm running Ubuntu on a laptop.

I just wanted to tell you what happened to me when I ran Automatix arnieboy, not blame you, apart from those things I think it's great!

---

### Post by ameerirshad on 2005-11-20
1,2,3 testing, running and enjoying it! Very nice tool, easy and fast!

thnx

---

### Post by Zill on 2005-11-20
A newbie question as I have not yet installed Ubuntu...

Does Automatix install the additional packages in the same way as other apt-get/synaptic packages are installed?

eg.  would they then be upgraded automatically with all the other installed applications?

Many thanks.

---

### Post by cstudent on 2005-11-20
[QUOTE=Zill]A newbie question as I have not yet installed Ubuntu...

Does Automatix install the additional packages in the same way as other apt-get/synaptic packages are installed?

eg.  would they then be upgraded automatically with all the other installed applications?

Many thanks.[/QUOTE]

Automatix is essentially a bash script. It will backup your current sources.list and install a new one. Then it will use apt to download software you select and install it. Once finished all the software you install with it will get updated through synaptic because synaptic will use that same sources.list. It's very simple and very slick IMO.

Bill

---

### Post by Maniak on 2005-11-21
Cheers arnieboy - fantastic job making a lot of work very easy. It is guys like you that bring me back to linux over and over again. Thanks.

---

### Post by ezphilosophy on 2005-11-22
This is just fantastic.  Just install Breezy, load automatix, and finished.  It's this kind of thing that will make people switch over.  

-keeping the power of linux for those who can use it, but having the simplicity for those who need it.  That's ezphilosophy.

Well done.

---

### Post by robotgeek on 2005-11-23
This is based on automatix. I  contacted the author of automatix with the corrections, but he refused to correct the bugs in automatix which I've listed below. I hope the original author does correct the mistakes in his original program.I want to make it clear that I have intention of claiming arnieboy's program or anything, but i just fixed what i felt what wrong with it. 

1. Creating the root user

The root user is disabled in ubuntu. It should not be enabled by someone who does not know his way around linux.  

2. The use of --force-yes in apt-get

This is a very dangerous option that should not be enabled. This is what 'man apt-get' says:

> 
--force-yes
Force yes; This is a dangerous option that will cause apt to continue without prompting if it is doing something potentially harmful. It should not be used except in very special situations. Using force-yes can  potentially destroy your system! 

Hence, the entire script has been modified to correct these defects. Also a few packages have been disabled, because they were not meant for breezy or where other sutiable packages are available in the repos. Please refer to the changelog file for details.

---

### Post by jadugarr on 2005-11-23
> 1. Creating the root user

2. The use of --force-yes in apt-get


I don't want to get envolved in flame war but I will have to agree that those are not bugs by definition.

---

### Post by deNoobius on 2005-11-23
All Kudos, Arnieboy!!  I'm a newbie, and your script saved me a world o' pain and frustration!

Installing Ubuntu:  Free.

Getting everything to work:  Free but difficult and annoying.

Starting automatix and getting a cup of coffee to return and find out everything's done:  PRICELESS!

---

### Post by Nu-Buntu on 2005-11-23
The fact that Automatix can be studied and decyphered means that it is easy to see how the features work and how they are used. While derivatives can be improvements, I don't see that being the case here. If anyone wants to disable root again after running automatix, they can do so. If you don't trust the script or its author, study the script or install everything manually. I for one appreciate the research and effort required to put such a useful tool together for the Ubuntu community. I think the author has shown his willingness to keep the script updated and current. Perhaps the author of the so-called "safer" version should build his own program rather than piggybacking on the work of someone who he seems to want to bash.

---

### Post by rohandhruva on 2005-11-23
Hi,

I dont want to be part in a flame war. But i request the original author, arnieboy, to please not enable the root account. Going through the script, not thoroughly, i dont find anything that cannot be done by "sudo" or "sudo su -".
It is against the ubuntu "philosophy" :) 

--force-yes is not a problem. I have done it hundreds of times when i want to install lots of software during the night, when i am sleeping. If arnie considers, and releases a version that does not enable root, i will surely use AutoMatix.

Thanks,
Rohan.

---

### Post by apokryphos on 2005-11-23
[QUOTE=rohandhruva] or "sudo su -".[/QUOTE]
sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)

---

### Post by rohandhruva on 2005-11-23
[QUOTE=apokryphos]sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)[/QUOTE]
Oops, never knew that :) I stand corrected.

---

### Post by Pablo_Escobar on 2005-11-23
Arnieboy, don't be discouredged by someone having other view on things as You. Even if it's dead wrong.
Please do not leave the great work You're doing.

---

### Post by rohandhruva on 2005-11-23
We all realize that it feels bad to have your work ripped off by other people, and being discredited. However, by taking automatix down, you have stolen opportunity from many new users who anyway dont care whether root is enabled, or --force-yes is used. 

For their sake, i request you to put it back on. And i think that automatix and automatix-proper can both learn from each other, and in the end, provide us wit h a new automatix that combines + points of both.

Consider,
Rohan.

---

### Post by az on 2005-11-23
Is automatix proprietary?

---

### Post by deNoobius on 2005-11-23
[QUOTE=apokryphos]sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)[/QUOTE]

Try doing that when launching a program that only allows itself to be run fromt the X11 environment, as happened to me recently.  It won't work.  I would have had to enable root login--or I could use Automatix's right-click to open that particular item as root from the GUI.  Of the two alternatives, the Automatix-provided one was clearly better.

Anyone who doesn't like it--don't select that option.  But don't criticize someone who has spent what I have to guess is hundreds of hours providing the rest of us with a great installer that saves hours of work.  Frankly, when I realized that tool was available via Automatix, I breathed a sigh of relief because it solved a knotty problem for me that I don't yet have the skills to solve myself.

---

### Post by imagine on 2005-11-23
[QUOTE=deNoobius]Try doing that when launching a program that only allows itself to be run fromt the X11 environment, as happened to me recently.  It won't work.  I would have had to enable root login--or I could use Automatix's right-click to open that particular item as root from the GUI.[/QUOTE]Are you speaking of Gnome's gksudo or kdesu on KDE? They should be used for X applications instead of sudo and are installed by default in (K)Ubuntu.

---

### Post by deNoobius on 2005-11-23
[QUOTE=apokryphos]Go find out what "troll" actually means, instead of sounding nonsensical and using it as a person who simply disagrees with you. I suggest you grow up.

GUI applications shouldn't be run with a direct sudo; this is more detrimental in KDE applications, but GNOME applications too can suffer from it. That's why there's gksudo (patched gksu) and kdesu (again, patched specifically for Kubuntu), in order for a user to run GUI applications as root; generally not a good idea in many cases, but it's the safest bet.[/QUOTE]

I wasn't aware of gksudo, but I'm not sure how that's different from the right-click script.  Don't both allow an item to be opened or run as root?  

BTW, do all the other distros discourage root access as well? I find that hard to believe.  My reading so far, as little as it is, leads me to believe that this is more of a Ubuntu thing, to make sure the distro was as foolproof as possible for as many people as possible.  I didn't think you could actually damage your system unless you make a mistake as root, like deleting a critical file.

---

### Post by jadugarr on 2005-11-23
[QUOTE=arnieboy]**Automatix has been taken down till all trolls and their posts pertaining to automatix are taken care of by mods/admins.**[/QUOTE]

Please don't let comments from a few people discourage you.  Most of the people really appreciate the work that you have done.  Sure it sucks that someone said that the code you spent clearly a lot of time writing and testing  has bugs (when they are clearly not), changed a few lines of your code and redistributed it without your consent.  It doesn't make your work any less appreciated by the rest of us though.

---

### Post by BLTicklemonster on 2005-11-23
I know I speak for the entire community (well except for* him*) when I say thank you for your hard work on Automatix, Arnieboy. You have provided an invaluable tool for so many newcomers. Please reconsider and leave it up for the newbs. Rant all you want, but Automatix has become the first thing people get when they install ubuntu. Without it, people are going to have a harder time getting what they need. We all read the post, and know that automatix is unimpeachable, that fellow isn't doing anything but making himself look bad. Let him, but you hold the higher ground and keep automatix up and don't let this get to you.

Thanks for your hard work.

oh, and please. :D

---

### Post by arnieboy on 2005-11-23
**Until the "safer automatix" thread and all similar ones are hard deleted, I will not bring automatix up.. Period.**

---

### Post by BLTicklemonster on 2005-11-23
Looks like you won, it's gone, bro. :p

---

### Post by arnieboy on 2005-11-23
yeah.. automatix is up again.. thanks for standing by.

---

### Post by Black Moon on 2005-11-23
Thanks for all the work it took make such a great program arnieboy. It really made my transition to linux alot smoother

---

### Post by deNoobius on 2005-11-23
I feel the same.  Thanks.

---

### Post by BLTicklemonster on 2005-11-23
[QUOTE=arnieboy]yeah.. automatix is up again.. thanks for standing by.[/QUOTE]
LMAO, LIKE I COULD SIT DOWN DURING ALL THAT?

---

### Post by darkmatter on 2005-11-23
People...if you want to argue....keep it in IRC or the Backyard...and try to be more 'civil'...not in the support/tech areas....

Continue this discussion elsewhere.

---

### Post by arnieboy on 2005-11-23
**Automatix updated to version 3.4.4 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")**

---

### Post by arnieboy on 2005-11-23
one more thing.. guys I have a request..
If u want to make a real fork of automatix, please do that (like porting it to some fancy python GUI with lots of options) or some other fancy stuff.. but please abstain from changing two lines and claiming it to be safe or whatever (cuz I have had thousands of users worldwide using automatix happily minus any complaints).. The name Automatix from henceforth is trademarked, so even if u come up with any such "2 lines changed" fork , u need to change the name to something else.

If u have any issues with the code, pm me personally, and I will explain stuff to u. u dont need to be rude or take it upon urself to malign me...  cuz really I have done all this for free.. in the true spirit of Ubuntu..

---

### Post by henriquemaia on 2005-11-23
I have just tried Automatix and the ideia is great.

Thanks Arnieboy!

---

### Post by Tosa on 2005-11-24
Thanks for the Automatix.
It really makes life easier for newbies!

Regards,
Tosa.

---

### Post by Zhukov on 2005-11-24
Once again i come here requesting for your authorization to continue with my automatix clone, with some small extras, giving you full credit for the work, as i did so far. I know you're probably 180% feed up with automatix licensing problems, thats why im asking again.

---

### Post by arnieboy on 2005-11-24
[QUOTE=Zhukov]Once again i come here requesting for your authorization to continue with my automatix clone, with some small extras, giving you full credit for the work, as i did so far. I know you're probably 180% feed up with automatix licensing problems, thats why im asking again.[/QUOTE]
I have replied to your question on the main automatix thread.

---

### Post by Tails on 2005-11-26
Just asking... will this works in 64-bit Ubuntu??? :D

cheers!

---

### Post by arnieboy on 2005-11-26
[QUOTE=Tails]Just asking... will this works in 64-bit Ubuntu??? :D

cheers![/QUOTE]
if it has AMD64 bit kernel and packages, it wont work. if it is running an i386. then it will.

---

### Post by quietglow on 2005-11-27
This app ROCKS! I can do all this stuff sans script, but it sure is heck is nice to have it automated. When we start doing installs for people as part of our linux group's work, it will be a real life saver.

Thanks for all your hard work!

---

### Post by Strangerdave on 2005-11-27
I am new to this and followed the install instructions, yet nothing seemed to happen.  I don't have limewire, can't seem to find easytag, as well as the other applications that I selected to be installed.

I downloaded the installer, opened it in the home directory, and it seemed to download things, then it asked for a password and I typed in my root, then it all shut down.

Anyone else experience this?

-SD-

EDIT**Just realized that one must install them individually, it seems to work now.

---

### Post by n0ah on 2005-11-30
I'm really hoping this doesn't kill my 64-bit ubuntu, I used it twice at work (yes I convinced my boss to switch from WinXP to Ubuntu) today and it went very very smoothly, but it's bitching and moaning about the 64-bit, but we'll see how it goes.. hopefully it doesn't kill my install.. if so oh well.. i'll just re-install Breezy fresh, instead of this semi-broken copy i have from updating from Hoary.

I never knew having amd64 would be such a pain in the a$$...

---

### Post by n00blar on 2005-11-30
Great script!!!
This one did wonders on my PC and on my laptop as well.

I do have a question, since I messed something up when I ran it on my laptop.
How do I turn off numlock? I turned it ON for my laptop (I don't know what I was thinking :p ).

Thanks.

---

### Post by arnieboy on 2005-11-30
[QUOTE=n0ah]I'm really hoping this doesn't kill my 64-bit ubuntu, I used it twice at work (yes I convinced my boss to switch from WinXP to Ubuntu) today and it went very very smoothly, but it's bitching and moaning about the 64-bit, but we'll see how it goes.. hopefully it doesn't kill my install.. if so oh well.. i'll just re-install Breezy fresh, instead of this semi-broken copy i have from updating from Hoary.

I never knew having amd64 would be such a pain in the a$$...[/QUOTE]
please bear in mind that automatix DOES NOT support AMD64/ppc packages. if u are running an x86 kernel on an AMD64, then alone will it be fully supported.

---

### Post by arnieboy on 2005-12-01
[QUOTE=n00blar]Great script!!!
This one did wonders on my PC and on my laptop as well.

I do have a question, since I messed something up when I ran it on my laptop.
How do I turn off numlock? I turned it ON for my laptop (I don't know what I was thinking :p ).

Thanks.[/QUOTE]
here is how to do it:
first from terminal do:
```
sudo apt-get remove numlockx

```
now do the following:
Go to **/etc/X11/gdm/Init/** as root (use the "open as root nautilus" script which comes with automatix) and delete the file called "**Default**". 
Now look for a file which looks like: **Default_backup200512010316** (the numbers at the end is the date and time when u ran automatix to install numlockx, it will be different for u). 
**Rename** this file as "**Default**" (minus quotes). now log out of gnome and log back in. numlock wont start up again.

---

### Post by JazzCrazed on 2005-12-01
I also wanted to take a quick moment to thank you for this extremely useful installer. I really appreciate your hard work!

---

### Post by tlc on 2005-12-01
Another shout of thanks here! I can't believe I lived with gentoo for two years... :razz: 

This is all so painless! Cheers!

---

### Post by runlevel0 on 2005-12-02
[QUOTE=arnieboy]Sun's Java 1.5[/QUOTE]
Coool!!
Nice work!

---

### Post by runlevel0 on 2005-12-02
[QUOTE=tlc]Another shout of thanks here! I can't believe I lived with gentoo for two years... :razz: 

This is all so painless! Cheers![/QUOTE]

Hey, me too X'D

I was really tired of having the home-page of my browser set to [http://bugs.gentoo.org](http://bugs.gentoo.org), ROFLMAO

---

### Post by ewtesterman@cox.net on 2005-12-02
I have to thank you it worked great and is very helpful. I setup quite a few systems for people and this saves a lot of time. I have only one comment outside of that. Please do not take this as negative feed back. I had to use Easy Ubuntu to install my ATI driver, it would have been nice to have been able to just use Automatix all the way around. Again please do not take that the wrong way I am very impressed with your work. I have noticed as I looked through the repositories that there are tools to build your own distro CD I think that I would like to see how difficult it would be to add Automatix to the Ubuntu install CD, maybe we would lose less newbies that way.

---

### Post by arnieboy on 2005-12-02
[QUOTE=ewtesterman@cox.net]I have to thank you it worked great and is very helpful. I setup quite a few systems for people and this saves a lot of time. I have only one comment outside of that. Please do not take this as negative feed back. I had to use Easy Ubuntu to install my ATI driver, it would have been nice to have been able to just use Automatix all the way around. Again please do not take that the wrong way I am very impressed with your work. I have noticed as I looked through the repositories that there are tools to build your own distro CD I think that I would like to see how difficult it would be to add Automatix to the Ubuntu install CD, maybe we would lose less newbies that way.[/QUOTE]
currently there is one project working on the automatix CD:
[http://ubuntuforums.org/showthread.php?t=87382](http://ubuntuforums.org/showthread.php?t=87382)
as for ATI drivers, there are some complications in installing these drivers which cannot all be automated. Easy Ubuntu merely installs the fglrx package available for ATI cards. However, u wud need to refer to the following thread to know what I am talking about regarding the complications with this package and ATI cards in general:
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

---

### Post by nppro on 2005-12-02
hello -- on most commands I enter I get this 

root@ubuntu:/home/nppro# apt-get update
E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)


and was wondering why and how to fix it -- really want to install this program .. but these obstacles are keeping me from it :) 

help appreciated

---

### Post by nppro on 2005-12-03
nevermind got it -- had to copy paste a exisity source list.

---

### Post by KermitJr on 2005-12-03
Just some feedback, but pmidi stops to ask for Root passwd.

---

### Post by arnieboy on 2005-12-03
[QUOTE=KermitJr]Just some feedback, but pmidi stops to ask for Root passwd.[/QUOTE]
if u mean midi installation and configuration by automatix, yes it will ask for your root password, but when playing a file with pmidi alone, it will not ask for your root password.
play a file with pmidi in the following way:
```
pmidi <filename>
```
Also make sure that u have read permissions on the folder from which u are trying to play the file.

---

### Post by j813 on 2005-12-04
64bit not yet fully or officially supported?
Thanks

---

### Post by arnieboy on 2005-12-04
**Automatix updated to version 3.4.6 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")**
[B]
Please download and install version 3.4.6.[/B]
Automatix has the new features:
[B]a) Added Ubuntu Backports
b) Removed the --force-yes switch to avoid any further controversy[/B]

---

### Post by arnieboy on 2005-12-04
[QUOTE=j813]64bit not yet fully or officially supported?
Thanks[/QUOTE]
not fully supported.

---

### Post by arnieboy on 2005-12-05
**Automatix updated to version 3.4.7 with the General Public License**

The **automatix license** ceases to be effective for the present and all future versions of automatix starting now.

---

### Post by poofyhairguy on 2005-12-05
[QUOTE=arnieboy]**Automatix updated to version 3.4.7 with the General Public License**

The **automatix license** ceases to be effective for the present and all future versions of automatix starting now.[/QUOTE]


Well thats that.

---

### Post by kalos on 2005-12-05
[QUOTE=arnieboy]Automatix updated to version 3.4.6 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")[/quote]

Is there a reason I am not allowed to view the licence? I click your [link](http://ubuntuforums.org/showthread.php?t=94310) and I get this:

[quote=vBulletin Message]
kalos, you do not have permission to access this page. This could be due to one of several reasons:

   1. Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
   2. If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.[/quote]

-kalos

---

### Post by kassetra on 2005-12-05
[quote=kalos]Is there a reason I am not allowed to view the licence? I click your [link]("http://ubuntuforums.org/showthread.php?t=94310") and I get this:
-kalos[/quote]

That's because it has been re-released under the gpl.

---

### Post by veehell on 2005-12-06
I just install Automatix; executed, run very nice, thanks for this. Really help me to install some firefox and multimedia stuff (codecs and mplayer and plugins). 
No any problems during the run. Thanks!

---

### Post by Jenda on 2005-12-08
I'm glad to see that this thread has been unlocked (if indeed ever locked?).
Now automatix has ceased to exist. If you're looking for an up-to date version, you will not find it.
However, the project has been forked, and this new project has recently merged with the original project from which even Automatix was forked: EasyUbuntu.
You can download the current version here: easybreezy.robotgeek.org

I hope the forums administration doesn't mind me posting this, since I intend to give a solution to the people looking for Automatix.

---

### Post by arnieboy on 2005-12-08
Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.

---

### Post by poofyhairguy on 2005-12-08
[QUOTE=arnieboy]Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.[/QUOTE]

excellent

---

### Post by xyz on 2005-12-08
[QUOTE=poofyhairguy]excellent[/QUOTE]
I second that!and thanks for a great job.

---

### Post by noelferg on 2005-12-08
[quote=arnieboy]Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.[/quote] 
Hi Arnieboy, You have done a fantastic job with Automatix. Hope the problems can be resolved. Automatix is one of the main reasons I recommend Ubuntu to Linux newbies. (I am not that experienced with it, myself.)

---

### Post by blakamin on 2005-12-08
Just one thing... remind laptop owners not to install numlock.... I couldn't for the life of me work out why my password wasn't working.....:p 
(I installed it out of habit)

---

### Post by Lem on 2005-12-09
Useful script there.. saves a lot of finger-twidling in terminal to get things set-up.

Cheers! :)

---

### Post by starscalling on 2005-12-10
Setting up gdesklets-data (0.35.2-2) ...

cat: /home/nekostar/.gnome2/session-manual: No such file or directory
/usr/local/automatix/autoscript: line 494: 19485 Terminated              zenity --progress --pulsate --title "Automatix" --text "Installing gdesklets"
cat: /home/nekostar/.gnome2/session-manual: No such file or directory
mv: cannot stat `/home/nekostar/.gnome2/session-manual': No such file or directory
tail: cannot open `/home/nekostar/.gnome2/session-manual_backup' for reading: No such file or directory
expr: syntax error
expr: syntax error
gawk: /num_clients/{gsub(//,)};{print}
gawk:                       ^ syntax error
gawk: fatal: 0 is invalid as number of arguments for gsub
gawk: {sub(/0/,);print}
gawk:          ^ syntax error
gawk: fatal: 0 is invalid as number of arguments for sub
Multimedia codecs|Firefox Plugins|MS TTF Fonts|Archives|Skype|Acrobat Reader|gftp|Ctrl-Alt-Del|Ripper and Tuner|File Sharing|Multimedia Editing|DVD Ripper|Mplayer with plugin|Media Players|Opera Browser|Debian Menu|Bittorrent Clients|Avidemux|Numlock ON|Programming Tools|AUD-DVD codecs|Open Office|Nautilus Scripts|SUN JAVA 1.5|Wine|Gdesklets


er it hiccuped?

---

### Post by arnieboy on 2005-12-10
please paste the results of the following command:
```
cat ~/.gnome2/session-manual
```

---

### Post by starscalling on 2005-12-10
i dont get any reply.. sorry it took me so long.. everything ive tried as of yet works fine though :) contents of that directory:
~/.gnome2$ ls
accels              gnomebaker            panel2.d        totem-addons
backgrounds.xml     gnome-volume-control  rhythmbox       totem_config
file-roller         keyrings              session
gedit-2             main                  session-manual
gedit-metadata.xml  nautilus-scripts      share

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]i dont get any reply.. sorry it took me so long.. everything ive tried as of yet works fine though :) contents of that directory:
~/.gnome2$ ls
accels              gnomebaker            panel2.d        totem-addons
backgrounds.xml     gnome-volume-control  rhythmbox       totem_config
file-roller         keyrings              session
gedit-2             main                  session-manual
gedit-metadata.xml  nautilus-scripts      share[/QUOTE]
so gdesklets works as well?

---

### Post by starscalling on 2005-12-10
eh just tried it and heck no :P
let me grab an error here.... ::
eh it wont even start now.. i tried to run one a minute ago and it gave me some error... sorry i knew i should have wrote it down... *checks top*
i dont see it running.. yeah so that doesnt work sorry :/

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]eh just tried it and heck no :P
let me grab an error here.... ::
eh it wont even start now.. i tried to run one a minute ago and it gave me some error... sorry i knew i should have wrote it down... *checks top*
i dont see it running.. yeah so that doesnt work sorry :/[/QUOTE]
alright just paste the results of
```
cat ~/.gnome2/session-manual
```

---

### Post by starscalling on 2005-12-10
nekostar@ubuntu:~$ cat ~/.gnome2/session-manual
nekostar@ubuntu:~$

heh exactly nothing !_!

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nekostar@ubuntu:~$ cat ~/.gnome2/session-manual
nekostar@ubuntu:~$

heh exactly nothing !_![/QUOTE]
interesting.. try doing the following:
go to system -->preferences-->sessions-->startup programs and add **gdesklets**. log out of gnome and log back in.

---

### Post by starscalling on 2005-12-10
nope nothing.. still doesnt open.. im sure i broke something somewhere....

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nope nothing.. still doesnt open.. im sure i broke something somewhere....[/QUOTE]
try doing the following:
```
sudo apt-get install gdesklets gdesklets-data
```
after the installation ends, log out of gnome and log back in again.

---

### Post by starscalling on 2005-12-10
nekostar@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
gdesklets is already the newest version.
gdesklets-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should i " sudo apt-get remove --purge gdesklets gdeksklets-data " then reinstall?

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nekostar@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
gdesklets is already the newest version.
gdesklets-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should i " sudo apt-get remove --purge gdesklets gdeksklets-data " then reinstall?[/QUOTE]
no try running gdesklets from terminal by doing the following:
```
gdesklets
```

---

### Post by starscalling on 2005-12-10
now that is interesting :P
gdesklets
Starting gdesklets-daemon...
Connected to daemon in 226 microseconds.

i still dont see it in top.. under root or nekostar [current user]
and the gui for it doesnt come up either [thanx for all the help btw]

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]now that is interesting :P
gdesklets
Starting gdesklets-daemon...
Connected to daemon in 226 microseconds.

i still dont see it in top.. under root or nekostar [current user]
and the gui for it doesnt come up either [thanx for all the help btw][/QUOTE]
do u have window notification applet added to any of your panels?
if not add that, and run gdesklets from applications-->accessories
u will see a blue gdesklets icon in ur notification area and a startup screen which will let u go on to gdesklets main screen where u can add whichever gdesklets u want. add them and close the main window. log out of gnome and logback in.
u shd see gdesklets start up every time with the chosen desklets starting up automatically.

---

### Post by starscalling on 2005-12-10
yup sure enough your right as rain!!!!!
/gg :P
thanx and keep up the awesome work...
what i dont understand is _why_ it was pissy lol.. though im gonna have to look into gdesklets some more.. *imagines running openbox + gdesklets - gnome-panels* ;)

---

### Post by MicroChris on 2005-12-11
This program....is amazing..

---

### Post by starscalling on 2005-12-11
yeah i agree.. this is gonna make it a bit easier to convert a couple of friends and collegues

---

### Post by arnieboy on 2005-12-11
Thanks for the support guys.. I hope to start working on automatix again in a few days. This thread will become the active support thread.

---

### Post by Gray. on 2005-12-11
Glad to see that Automatix is being worked on again.

---

### Post by Jenda on 2005-12-11
Arnieboy: Any chance of pooling efforts with Easy Ubuntu - now that both projects are GPL'd?

---

### Post by arnieboy on 2005-12-11
[QUOTE=Jenda]Arnieboy: Any chance of pooling efforts with Easy Ubuntu - now that both projects are GPL'd?[/QUOTE]
NO. Automatix will remain independent of all forks and precedents. However, if anyone with sufficient programming skills is interested in contributing to Automatix, he is welcome to contact me.

---

### Post by chrishan on 2005-12-11
arnieboy, you are my hero! thanks for making automatix, and thanks for starting again!

---

### Post by LeTon on 2005-12-11
Hi Arnieboy...
Funny thing happens, or rather does not happen with Automatix.
I followed how-to as per this thread [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
I get a msg that automatix has been installed in Applications - sys. tools....
But it is not there!
And terminal announces that command not found!
Confused.
Thank you in advance.

---

### Post by nix4me on 2005-12-11
I doesn't show up in my menu either.

I start it fine from the terminal though.

nix4me

---

### Post by arnieboy on 2005-12-11
Leton and nix4me do the following:
download the file to your home folder. then from terminal do the following:
```
tar xzf automatix-ubuntu_v3.4.8.tar.gz
cd Automatix
./install
```
this will install Automatix in Applications --> System Tools

---

### Post by LeTon on 2005-12-11
Indeed it did:)
It just makes me wonder...how these things happen:D
Thank you.
Sure I would love to ask millions of other how-to-get-this-done kinda questions...:)

---

### Post by UbunT00L on 2005-12-11
Any chance of automating the Nvidia TV-out support?

---

### Post by arnieboy on 2005-12-11
[QUOTE=UbunT00L]Any chance of automating the Nvidia TV-out support?[/QUOTE]
If u mean this one:
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)
then, No I wont automate it because it involves editing **/etc/X11/xorg.conf** which Automatix has a strict policy of not touching except in the case of installing the nvidia drivers which is done indirectly.

---

### Post by arnieboy on 2005-12-12
Alright, The [Automatix thread]("http://ubuntuforums.org/showthread.php?t=66563") is open once again for support and development. I would be happy to take all your questions and suggestions there once again. Please try and avoid discussions of past controversies here or on [that thread]("http://ubuntuforums.org/showthread.php?t=66563"). if u feel you still have any outstanding issues regarding these past controversies, please take it to the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") to be effectively handled by the admins.
Thanks,
Arnie

---

### Post by bored2k on 2005-12-12
[Avidemux 2.1 **Final]("http://www.ubuntuforums.org/showpost.php?p=564380&postcount=19") ** for the x86 architecture.

Possible requirements: libfaac0 liba52-0.7.4 libsmjs1 (on the repositories).

---

### Post by sabredog on 2005-12-13
Thanks for this app, I am looking forward to running it after I install Breezy later this month.

first time Linux user :)

One question though, Does Automatix ask you and then set up a root password change?

Sorry, it is probably a silly question but I have not used a non Windows OS since my Unix days running MOSS design software 14 years ago.

---

### Post by UbunT00L on 2005-12-13
One small annoyance.  When automatix asks you for your root password, the focus is set on the cancel button.  So unknowingly, you type in your password, and press enter, which will cancel the entire process.  It almost seems as though the process gets completed because it doesn't ask you if you are sure if you want to cancel, it just cancels the entire process without a word.  I think setting the focus to the terminal when it asks for your password would be less confusing for some of the newer users.

---

### Post by arnieboy on 2005-12-16
**Automatix updated to version 3.5 with the General Public License**
[B]Automatix 3.5 has the following new features:
a) Finally bringing to an end a long standing controversy, Automatix no longer uses the root user (su). No need to set root password.
b) Ubuntu release check has been reworked on.[/B]

I sincerely hope this pacifies the group of people who were much against the use of root in Automatix.

---

### Post by robotgeek on 2005-12-16
[QUOTE=arnieboy]
a) Finally bringing to an end a long standing controversy, Automatix no longer uses the root user (su). No need to set root password.

I sincerely hope this pacifies the group of people who were much against the use of root in Automatix.[/QUOTE]

Great!

---

### Post by karma 23 on 2005-12-17
How do I run this on Xubuntu?  I downloaded the file but when I double-click on it, nothing happens.  Worked fine on Ubuntu (GNOME).

---

### Post by arnieboy on 2005-12-18
[QUOTE=karma 23]How do I run this on Xubuntu?  I downloaded the file but when I double-click on it, nothing happens.  Worked fine on Ubuntu (GNOME).[/QUOTE]
it is not made for xubuntu.. or Kubuntu

---

### Post by arnieboy on 2005-12-18
**[Automatix-Kubuntu 1.0]("http://ubuntuforums.org/showthread.php?t=105343") released! (This is only meant for Kubuntu Users (not for Ubuntu or Xubuntu users)**

---

### Post by dabear on 2005-12-18
Arnieboy: I believe the url should be [http://ubuntuforums.org/showthread.php?t=105343](http://ubuntuforums.org/showthread.php?t=105343)

---

### Post by arnieboy on 2005-12-18
Thanks! edited.

---

### Post by karma 23 on 2005-12-18
[QUOTE=arnieboy]it is not made for xubuntu.. or Kubuntu[/QUOTE]

Well, that would explain why.  Thanks!

---

### Post by Nu-Buntu on 2005-12-18
Arnie,

I used your Firefox 1.5 script on my desktop machine and it worked great. I used it on my laptop and it destroyed my firefox, and when I try to start firefox, it says in the toolbar, "Starting Firefox Web Browser" and the wait icon is spinning. Both then disappear with no firefox.

I used Automatix to install Opera which I am using at the moment on this laptop. I saw you added Firefox 1.5 to Automatix 4, so I ran it from there, and it said it installed. Still I get the same results in trying to start firefox. Any ideas?

Thanks!

---

### Post by arnieboy on 2005-12-18
[QUOTE=Nu-Buntu]Arnie,

I used your Firefox 1.5 script on my desktop machine and it worked great. I used it on my laptop and it destroyed my firefox, and when I try to start firefox, it says in the toolbar, "Starting Firefox Web Browser" and the wait icon is spinning. Both then disappear with no firefox.

I used Automatix to install Opera which I am using at the moment on this laptop. I saw you added Firefox 1.5 to Automatix 4, so I ran it from there, and it said it installed. Still I get the same results in trying to start firefox. Any ideas?

Thanks![/QUOTE]
try opening up terminal, and run
```
firefox
```
and paste the results here

---

### Post by Nu-Buntu on 2005-12-18
> randy@UbuntuLaptop:~$ firefox
randy@UbuntuLaptop:~$


It just goes back to a prompt.

---

### Post by arnieboy on 2005-12-18
[QUOTE=Nu-Buntu]It just goes back to a prompt.[/QUOTE]
ok try this:

```
mv ~/.mozilla ~/.mozilla-backup1
```
and restart firefox

---

### Post by Nu-Buntu on 2005-12-18
Arnie, you remain my hero! Thanks friend. This asked about importing settings, gave me the chrome error, but after that it works. 

I appreciate your help greatly.

---

### Post by Fibre on 2005-12-19
Thanks Arnie boy,

I keep finding moments where I see how helpful this is. As a Newbie I can't thank you enough for the time you've spent on getting this thing up and running.

The more I understand what extra stuff has been installed, the more I appreciate the time and effort put into to it. I plan on installing a lot of computers with it through volunteer work and also use Ubuntu to learn about linux based O/S and networking etc to eventually make a living.

You've saved me a hell of a lot of time. At least a week of headache's maybe probably more because of got no idea or very little now.

---

### Post by etchesketch on 2005-12-19
This is the most ingenious tool I have come across for linux.  (But I am a newbie, so that's not saying much.)  However, I have one problem with the NVIDIA driver installation.  I want to use the NVIDIA driver installation which is included in Automatix, but my video card is obviously undetectable if it is not connected.  If I insert my PCI NVIDIA FX5700LE, X will not boot.  X will only boot if I remove the video card and connect my monitor to the onboard video, to which the system defaults.  Is there a way to temporarily disable the video card while it is inserted, so that I can boot to X and use Automatix to install the drivers?  Or, is there a way to install the drivers from the command line while I am using the video card?  I hope I am being clear enough.

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]Leton and nix4me do the following:
download the file to your home folder. then from terminal do the following:
```
tar xzf automatix-ubuntu_v3.4.8.tar.gz
cd Automatix
./install
```
this will install Automatix in Applications --> System Tools[/QUOTE]
Hi Arnie

I'm trying to run Automatix 4.0 on Ubuntu 5.10
I followed the installation instructions and got the Automatix folder created but it doesn't show up in Applications > System Tools
So then I followed the instructions you gave here (substituting v4.0 of course) - again it creates the folder but still no menu entry
Any ideas?
Thanks

Andy

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]Hi Arnie

I'm trying to run Automatix 4.0 on Ubuntu 5.10
I followed the installation instructions and got the Automatix folder created but it doesn't show up in Applications > System Tools
So then I followed the instructions you gave here (substituting v4.0 of course) - again it creates the folder but still no menu entry
Any ideas?
Thanks

Andy[/QUOTE]
u need to go into the folder and run the install script from there.
the tar command unzips the tar.gz file.
the cd command takes u to the automatix folder
the ./install command installs automatix in /usr/local/automatix and creates an entry in Application --> System Tools
Please dont try to run Automatix from your home folder. run it only from applications --> system tools
or from terminal as
```
automatix
```

---

### Post by arnieboy on 2005-12-19
[QUOTE=etchesketch]This is the most ingenious tool I have come across for linux.  (But I am a newbie, so that's not saying much.)  However, I have one problem with the NVIDIA driver installation.  I want to use the NVIDIA driver installation which is included in Automatix, but my video card is obviously undetectable if it is not connected.  If I insert my PCI NVIDIA FX5700LE, X will not boot.  X will only boot if I remove the video card and connect my monitor to the onboard video, to which the system defaults.  Is there a way to temporarily disable the video card while it is inserted, so that I can boot to X and use Automatix to install the drivers?  Or, is there a way to install the drivers from the command line while I am using the video card?  I hope I am being clear enough.[/QUOTE]
Automatix merely installs the nvidia driver package in the official breezy repos and enables the nvidia drivers when it detects that the card is nvidia.
Your issue is one with dual cards. I think u should do the following:
1) take ur nvidia card off.
2) plug ur monitor into the integrated card.
3) boot into X.
4) make a back up of xorg.conf as follows:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
5) edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and look for the word "**nvidia**" under the "**Devices**" section
change "**nvidia**" to "**nv**".
6) Save xorg.conf and exit and shut down your comp.
7) Now plug in your nvidia card and restart your comp. X should boot up fine but u wont get 3D acceleration.
8) Now use automatix to install your nvidia drivers.
9) Restart your comp.
Have fun.

---

### Post by HandyAndy on 2005-12-19
Hi Arnie

Thanks for your reply. That's what I'm doing, but when I click the install script in the Automatix folder in Home it doesn't create the folder in usr/local/ or create the entry in Applications > System.

What I get is the text editor opening up with this:

#!/bin/bash
# Licence GPL, see gpl.txt
# Written by arnieboy
# Automatix is copyrighted by arnieboy
# Automatix is released under the General Public License (Please refer to GPL.txt)

gksudo -t "Installing Automatix" "rm -rf /usr/local/automatix"
sudo mkdir /usr/local/automatix
sudo cp conf/Automatix.desktop /usr/share/applications/
sudo cp -R * /usr/local/automatix/
sudo rm -rf /usr/bin/automatix
sudo ln -s /usr/local/automatix/Automatix /usr/bin/automatix
zenity --info --title "Automatix" --text $"Automatix has been installed in Applications-->System Tools !"

Doing it by the command line doesn't work either

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]Hi Arnie

Thanks for your reply. That's what I'm doing, but when I click the install script in the Automatix folder in Home it doesn't create the folder in usr/local/ or create the entry in Applications > System.

What I get is the text editor opening up with this:

#!/bin/bash
# Licence GPL, see gpl.txt
# Written by arnieboy
# Automatix is copyrighted by arnieboy
# Automatix is released under the General Public License (Please refer to GPL.txt)

gksudo -t "Installing Automatix" "rm -rf /usr/local/automatix"
sudo mkdir /usr/local/automatix
sudo cp conf/Automatix.desktop /usr/share/applications/
sudo cp -R * /usr/local/automatix/
sudo rm -rf /usr/bin/automatix
sudo ln -s /usr/local/automatix/Automatix /usr/bin/automatix
zenity --info --title "Automatix" --text $"Automatix has been installed in Applications-->System Tools !"

Doing it by the command line doesn't work either[/QUOTE]
u need to double click the install script and hit run..

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]u need to double click the install script and hit run..[/QUOTE]
I don't get any option to 'run' - just the text editor

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]I don't get any option to 'run' - just the text editor[/QUOTE]
ok open terminal, 
```
cd Automatix
./install
```
what errors do u get?

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]ok open terminal, 
```
cd Automatix
./install
```
what errors do u get?[/QUOTE]
That did it
It asked for my password and when I gave it, it worked
Now I've got the menu entry and the automatix folder in usr/local/

Thanks a lot, Arnie
Any idea why my system should respond differently? It's only a couple of weeks old and pretty much unmodified from the install defaults.

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]That did it
It asked for my password and when I gave it, it worked
Now I've got the menu entry and the automatix folder in usr/local/

Thanks a lot, Arnie
Any idea why my system should respond differently? It's only a couple of weeks old and pretty much unmodified from the install defaults.[/QUOTE]
you possibly made your executable scripts default to text editor. On a default Ubuntu install, one gets the option to read it, run it etc. but u possibly overrode them with a check on "dont ask me again"

---

### Post by joewilliams on 2005-12-19
Hey Arnie,

It worked great for me on a fresh 5.10 install with AMD Sempron 2800 and nvidea video card. Thanxs for all your hard work. I was considering upgrading to the 686 or K7 kernel. Do you know if this will create any problems with any of the packages Automatix installed...especially the nvidia drivers?



thanks,
Joe

---

### Post by arnieboy on 2005-12-19
[QUOTE=joewilliams]Hey Arnie,

It worked great for me on a fresh 5.10 install with AMD Sempron 2800 and nvidea video card. Thanxs for all your hard work. I was considering upgrading to the 686 or K7 kernel. Do you know if this will create any problems with any of the packages Automatix installed...especially the nvidia drivers?



thanks,
Joe[/QUOTE]
should not create a problem..

---

### Post by arnieboy on 2005-12-19
[COLOR="Navy"]I have created a debian package for automatix. I need someone to host it for me (someone with sufficient bandwidth and a 24/7 reliable server). file is just 32 KB.
Please send me a pm if you are interested.
Thanks,
Arnie[/COLOR]

---

### Post by etchesketch on 2005-12-20
[QUOTE=arnieboy]Automatix merely installs the nvidia driver package in the official breezy repos and enables the nvidia drivers when it detects that the card is nvidia.
Your issue is one with dual cards. I think u should do the following:
1) take ur nvidia card off.
2) plug ur monitor into the integrated card.
3) boot into X.
4) make a back up of xorg.conf as follows:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
5) edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and look for the word "**nvidia**" under the "**Devices**" section
change "**nvidia**" to "**nv**".
6) Save xorg.conf and exit and shut down your comp.
7) Now plug in your nvidia card and restart your comp. X should boot up fine but u wont get 3D acceleration.
8) Now use automatix to install your nvidia drivers.
9) Restart your comp.
Have fun.[/QUOTE]

My xorg.conf does not have an entry for my nVidia card.

I went into bios and set it to boot using onboard video.  This way my computer can still see the nVidia card without trying to use it.

lspci gives me a line about *Unknown device 0343*:

```
0000:02:0b.0 VGA compatible controller: nVidia Corporation: Unknown device 0343 (rev a1)
```

EDIT: I have gotten my NVIDIA card to work now, using the instructions I found here:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by arnieboy on 2005-12-20
[B]Please Note: Automatix is now available as a deb package for easier installation (read the installation instructions for details).

A BIG WOOT to [beerorkid]("http://ubuntuforums.org/member.php?u=9536") for hosting Automatix![/B]

To install Automatix do the following:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

To uninstall automatix do the following:
```
sudo apt-get remove automatix
```

---

### Post by kuru on 2005-12-20
I'm going to try automatix on edubuntu-5.10. It is based on ubuntu-5.10. 
I think the installed apps will work ok for the clients, and automatix will be installed by the main user , so the icon should not be available to clients to change things.
I'll let you know as soon as my dd of the drive finishes so I can test it.

cheers
kuru

---

### Post by r4ik on 2005-12-21
Got my system back up and runnin in less than an hour.(smashed the command-line just a little to hard)
Thanks Arnieboy keep up the good work !

---

### Post by kuru on 2005-12-22
Just a note about my Automatix install on Edubuntu. The deb worked fine.
I selected a couple of the packages, since alot of them were already installed,
and away the script went . Fetching packages and installing. It's a good thing theres a check right at the startup for sudo, otherwise a client could launch the app from remote. 
To paraphrase some one wise >     Just works!

I had a couple of errors, but it was a missing gthumb-logo.png. Not sure which package it popped up from. It wasn't an Automatix error.

off-topic note: I know some people frown on Totem player, but somehow it's the only player installed on this system that can launch an avi & play it remotely via a client from clicking on a networked server. Sadly sound is not available to clients, not yet anyway.

cheers and thanks for a very nifty app.
kuru

---

### Post by n0ah on 2005-12-22
It installed -most- of the stuff just fine, but a bunch of them crapped out.. as I expected.. Opera being one of the most notable ones.. (damn them all to hell for not creating x64 version already!)

oh well.. i'm ditchin the x64 ubuntu and throwing it on my old machine and throwing win2k back on.. *ducks* i miss my games and there aren't enough programs for x64 yet that i want.. i'll be back.. that's for damn sure.. just not till x64 becomes more mainstream though

---

### Post by Styles on 2005-12-22
Just an FYI I mirrored the deb file as well

[http://www.linuxsystems.net/automatix-ubuntu_4.0-1_i386.deb](http://www.linuxsystems.net/automatix-ubuntu_4.0-1_i386.deb)

Cheers,

Eric



[QUOTE=arnieboy][B]Please Note: Automatix is now available as a deb package for easier installation (read the installation instructions for details).

A BIG WOOT to [beerorkid]("http://ubuntuforums.org/member.php?u=9536") for hosting Automatix![/B]

To install Automatix do the following:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

To uninstall automatix do the following:
```
sudo apt-get remove automatix
```[/QUOTE]

---

### Post by tagg3rx on 2005-12-22
WOW -

I have been trying to install things mannualy tracking down walk through after walk through banging my head agianst the linux wall.  On more than one occasion saying linux is still no where near user friendly....

Then I found automatix

WOW

Arnieboy you have done well

now i can get on to using my computer not trying to get it working.

Rock ON!

---

### Post by PYR on 2005-12-22
there is a possible bug with automatix. 

when using the "install firefox 1.5 and plugins" option i ran into a problem, after the task was complete i could no longer open links from gaim, irssi, etc. when i clicked on a link nothing happened, so i went to system->pref->preferred apps and found that my preferred web browser had changed from firefox %s to mozilla-firefox %s (which is a binary that does not exist), to remedy the problem i just changed it back to firefox and now everything works.

---

### Post by jasongrieves on 2005-12-23
[QUOTE=PYR]there is a possible bug with automatix. 

when using the "install firefox 1.5 and plugins" option i ran into a problem, after the task was complete i could no longer open links from gaim, irssi, etc. when i clicked on a link nothing happened, so i went to system->pref->preferred apps and found that my preferred web browser had changed from firefox %s to mozilla-firefox %s (which is a binary that does not exist), to remedy the problem i just changed it back to firefox and now everything works.[/QUOTE]

Good catch.  Same over here

---

### Post by nix4me on 2005-12-24
Arnieboy,

I just tried your script and Firefox 1.5 is not working.  I had Firefox installed in /opt before so I went ahead and removed it.

Re-ran Automatix, still no good.  Opened Synaptic and removed Firefox altogether, re-ran Automatix, no good.  1.07 keeps opening.

How do I get back to square 1.

nix4me

---

### Post by nix4me on 2005-12-24
This is what i see in the Automatix terminal.

cp: cannot stat `/home/nix4me/firefox': No such file or directory
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
mv: cannot stat `/home/nix4me/.mozilla': No such file or directory
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
dpkg-divert: `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu' clashes with `local diversion of /usr/bin/firef to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists
./autoscript: line 603:  9710 Terminated              zenity --progress --pulsate --title "Automatix" --text "Installing Firefox 1.5"


nix4me

---

### Post by WackToMack on 2005-12-24
How can I tell which version of Automatix I have?

---

### Post by Aero-Z on 2005-12-24
[QUOTE=WackToMack]How can I tell which version of Automatix I have?[/QUOTE]
Open up Synaptic and search for Automatix

---

### Post by WackToMack on 2005-12-24
Oh... cool... thanks.  But then why didn't Automatix install Firefox Version 1.5?  That is the latest version, right?  I'm still using 1.0.7...  Does Automatix remove older programs and then install the newer versions, does it just overwrite them, or does it skip installing programs that are already installed?

---

### Post by Aero-Z on 2005-12-24
[QUOTE=WackToMack]Oh... cool... thanks.  But then why didn't Automatix install Firefox Version 1.5?  That is the latest version, right?  I'm still using 1.0.7...  Does Automatix remove older programs and then install the newer versions, does it just overwrite them, or does it skip installing programs that are already installed?[/QUOTE]
Search the forum for the Firefox issue.There are more people who have problems intalling Firefox 1.5 with Automatix

---

### Post by nix4me on 2005-12-25
The only way I get Firfox 1.5 to work is by using the Wiki instructions and install it to /opt.  Works fine.

On my Debian box, there is already a Firefox 1.5 in the unstable repositories.

nix4me

---

### Post by tseliot on 2005-12-25
[QUOTE=Aero-Z]Search the forum for the Firefox issue.There are more people who have problems intalling Firefox 1.5 with Automatix[/QUOTE]
No problems whatsoever here (Firefox 1.5 installed with Automatix)

---

### Post by Aero-Z on 2005-12-25
[QUOTE=tseliot]No problems whatsoever here (Firefox 1.5 installed with Automatix)[/QUOTE]
No problems with Firefox 1.5 and Automatix here also. I had somekind of error when I ran Firefox 1.5 the first time, but after that everything seems to work fine.

---

### Post by azteech on 2005-12-26
[quote=Aero-Z]No problems with Firefox 1.5 and Automatix here also. I had somekind of error when I ran Firefox 1.5 the first time, but after that everything seems to work fine.[/quote] 
While I have no problems with installing firefox 1.5, using automatix, I am not able to get the firefox 1.5 to recognize the java plugin that is downloaded by automatix. Has anyone else experienced this, and is there a solution?
If it helps, I 1st downloaded/installed firefox 1.5 using automatix, then after restarting the system, I downloaded the plugins. during download/install I did not note any error messages.

Edit: corrected misspellings

---

### Post by arnieboy on 2005-12-26
[QUOTE=azteech]While I have no problems with installing firefox 1.5, using automatrix, I am not able to get the firefox 1.5 to recognize the java plugin that is downloaded by automatrix. Has anyone else experienced this, and is there a solution?
If it helps, I 1st downloaded/installed firefox 1.5 using automatrix, then after restarting the system, I downloaded the plugins. during download/install I did not note any error messages.[/QUOTE]
the following will solve your java problem:
[http://ubuntuforums.org/showpost.php?p=594437&postcount=223](http://ubuntuforums.org/showpost.php?p=594437&postcount=223)
now please be nice enuf to help others with the same problem and give them this link. I will correct this bug in automatix in a few days (I am on vacation right now).


and please spell it right.. lol.. its automatix.

---

### Post by azteech on 2005-12-26
[quote=arnieboy]the following will solve your java problem:
[http://ubuntuforums.org/showpost.php?p=594437&postcount=223]("http://ubuntuforums.org/showpost.php?p=594437&postcount=223")
now please be nice enuf to help others with the same problem and give them this link. I will correct this bug in automatix in a few days (I am on vacation right now).


and please spell it right.. lol.. its automatix.[/quote] 
Thank you arnieboy. That did the trick. 
Have a great vacation and Happy Holidays.

BTW, sorry for the misspelling of automatix. ...

---

### Post by Nu-Buntu on 2005-12-27
Arnie,

I noticed there is an update to OOo, version 2.0.1 available. It appears to be more than a minor bug fix, as it adds some new capabilities. You might want to take a look for the next version of Automatix.

---

### Post by Sokraates on 2005-12-28
[QUOTE=Nu-Buntu]Arnie,

I noticed there is an update to OOo, version 2.0.1 available. It appears to be more than a minor bug fix, as it adds some new capabilities. You might want to take a look for the next version of Automatix.[/QUOTE]

To update OOo from 2.0 to 2.0.1 we will first need debs and a repo where Automatix can get it from. AFAIK there are none yet.

Once we've got them, I'm sure arnieboy will update Automatix ASAP.

---

### Post by huh? on 2005-12-28
having trouble with the public.planetmirror.com link...is it broken ?

---

### Post by Sokraates on 2005-12-28
[QUOTE=huh?]having trouble with the public.planetmirror.com link...is it broken ?[/QUOTE]

Yup ... again. Guess arnieboy will have to remove the repo after all (see post #1232 [here](http://ubuntuforums.org/showthread.php?t=66563&page=124)).

---

### Post by arnieboy on 2005-12-29
planetmirror removed and java firefox issue fixed in version 4.1

---

### Post by nimd4 on 2005-12-29
Hi, from what I can see, automatix offers to install OoO 2.0 while version 2.0.1 is available and besides, Ubuntu does come with Office anyway .. the whole issue seems a little confusing; just a heads-up, plz don't bother with my observation :)

Vladimir

---

### Post by arnieboy on 2005-12-29
[QUOTE=nimd4]Hi, from what I can see, automatix offers to install OoO 2.0 while version 2.0.1 is available and besides, Ubuntu does come with Office anyway .. the whole issue seems a little confusing; just a heads-up, plz don't bother with my observation :)

Vladimir[/QUOTE]
ubuntu comes with version 1.9x . automatix upgrades it to 2.0. version 2.0.1 is available yes, but its still not been made into reliable debs. once thats done, automatix will also get them for u.

---

### Post by nimd4 on 2005-12-30
Thanks for following up on that. I am finding my way extremely difficult around this (desktop) Linux, there seems to be a lot to discover and learn since I am a first-time user. Thanks again.

Vladimir

---

### Post by canadianwriterman on 2005-12-30
[QUOTE=nimd4]Thanks for following up on that. I am finding my way extremely difficult around this (desktop) Linux, there seems to be a lot to discover and learn since I am a first-time user. Thanks again.

Vladimir[/QUOTE]

Keep at it, nimd4. I spent about two months figuring out how everything works in Ubuntu and Linux. While I'm no expert yet, I have got Ubuntu working perfectly for me and customized just the way I want. These forums are an excellent way to navigate your way through that learning phase.

---

### Post by nimd4 on 2005-12-30
I will :) The forums are awesome and so are the people, thanks for the *words of encouragement* :D

---

### Post by corefile on 2005-12-31
Arnieboy, are you still insiting on messing up this great script you have created (with the help of others) by using the NON OPENSOURCE license that you unforunatly decide to use?

---

### Post by cjm5229 on 2005-12-31
Arnieboy,
  I have a question, My son's computer (an old Compaq Presario). He's 10 yrs old and thinks he's a computer expert, so we give him the old one to break. Gstreamer and Skype will not install from either Automatix or Easy Ubuntu. He just wiped his Windows completely and put Ubuntu in to it. Could it be a sound card issue? I would rell you what the errors were, but he is busy adding a second harddrive right now to put Win back on as a Dual boot until he gets these problems solved. I might get to catch him between computer dismantleings and find out if he has the errors. If so I will add an edit to this. I really appreciate what you do for Ubuntu, With out Automatix and the Howto's that you have written I would have thrown up my hands a long time ago. I hardly ever have to go to my Windows partition anymore, when I get the rest of my files transferred, I might just remove windows completely. If it weren't for you and a few of the others on this forum I would probably have gone back to fighting virii and spyware for kicks.:smile:  
Carl

---

### Post by philetus on 2006-01-04
Thanks for the tool, Arnieboy.
MS has got to be squirming.

---

### Post by ausm on 2006-01-04
Hi Arnieboy,

I really appreciate all your hard work with this awesome graphical Installer. It made my transition from Windows soooo much easier. I have tried many flavors of Linux but none of them offer a tool as handy as the one you created or have such a large,helpful and FRIENDLY community as this one.

Keep up the great work!

Ausm

---

### Post by jeepmanjr on 2006-01-06
See Above

---

### Post by jeepmanjr on 2006-01-06
See Above

---

### Post by jeepmanjr on 2006-01-06
WOW...three posts!  How'd that happen?!


OUTSTANDING script!!  Loaded without a hitch.  I recently installed Breezy and manually loaded quite a bit of software.  It took me more than FOUR DAYS of sitting in front of my 'puter researching, downloading and attempting installs...one after the other.  While I did manage to get most everything up 'n running, I was still missing a bunch of stuff.  Now I have it.  If you've been there/done that, you will absolutely love this script.

Manually installing packages is a very good learning experience for a noob (like me) and everyone should take a stab at it.  You'll learn a whole lot in the process.

This script replaces countless hours of installation effort.  Arnieboy deserves a bottomless beer from the Ubuntu community for this fine peice.  If you utilize his work, please take the time to give him a shout and express your appreciation.  It's the least we could do.

Arnieboy, my hat is off to you sir....

:cool:  Mike

---

### Post by arnieboy on 2006-01-06
[QUOTE=jeepmanjr]WOW...three posts!  How'd that happen?!


OUTSTANDING script!!  Loaded without a hitch.  I recently installed Breezy and manually loaded quite a bit of software.  It took me more than FOUR DAYS of sitting in front of my 'puter researching, downloading and attempting installs...one after the other.  While I did manage to get most everything up 'n running, I was still missing a bunch of stuff.  Now I have it.  If you've been there/done that, you will absolutely love this script.

Manually installing packages is a very good learning experience for a noob (like me) and everyone should take a stab at it.  You'll learn a whole lot in the process.

This script replaces countless hours of installation effort.  Arnieboy deserves a bottomless beer from the Ubuntu community for this fine peice.  If you utilize his work, please take the time to give him a shout and express your appreciation.  It's the least we could do.

Arnieboy, my hat is off to you sir....

:cool:  Mike[/QUOTE]
Thank you sir :) I really appreciate this overwhelming appreciation :)

---


---
title: "[SOLVED] Problem with sound on Ubuntu 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by TaoBoogie on 2007-08-06
Hello, I have just installed Ubuntu 7.04 for the first time and really like what I am seeing. I don't like what I am hearing though, which is nothing :(
I have a AMD64 bit dual processor on an Abit KN9 Ultra MoBo with a GeForce 7600GT Video card, 2Gig of RAM. The sound card is onboard.
The sound worked perfectly under windows but now that I have changed to Ubuntu I cannot hear any of my music MP3, WMA, or streamed, I can't access any video either streamed or otherwise. I have tried all the players that come packaged with the install and I also have tried to update the codecs but I still have been unsuccessful.
When I go to System>Pref'>Sound I can very faintly hear a tone when testing the first three test buttons ( Sound Events, Music and Movies and I only hear a tone in Audio Conferencing  "Sound playback" but nothing with "Sound Capture")

This is my first time using Ubuntu so I am only just feeling my way around. I have used "ENVY" to get my Video card working but I'm not sure if I have to do something similar to get my sounds working again. I've never used the Terminal Window before but at least I know where to find it should I need to use it.

I hope I have given enough background information.
Thanks for any help given.
Tao

---

### Post by jnorthr on 2007-08-06
Many of us have found the same situation when using sound for the first time. Since several of the formats you name, such as .mp3, are not public domain, they have not been included in the standard ubuntu install. You will need to go to alternate sites to download the missing codecs to play dvd's, mp3
Check [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) as a starting poiint. After reading that you will be in a better position to ask further questions which we will be glad to help you with.
;)

---

### Post by TaoBoogie on 2007-08-06
My word that was quick, thanks for the reply jnorthr I'm off to follow that link now :)

---

### Post by leo_rockway on 2007-08-06
if you still have problems after enabling propietary codecs, then run the following in terminal:

> lspci | grep -i audio

copy the output and it paste here.

---

### Post by armandh on 2007-08-06
I found that after install [or even live] the GUI to down load codex popped up the first time I tried to play an unsupported file. got it going well and quick.

once however, when I tested the install on a small hard drive this function didn't.

---

### Post by jnorthr on 2007-08-06
Perhaps the sound drivers and logic are better at discovering the necessary bits, while hard drives etc are completely different animals and their drivers may not be so 'smart'. Remember that some drives may not be supported 'out-of-the-box' in ubuntu. They may need special drivers. What kinda drive is it ?
Also keep in mind that ubuntu is developed by a variety of souls around the planet and some may be more familar with the terrain they cover and hence may make some features easier to use.

---

### Post by TaoBoogie on 2007-08-06
Ok well I hecked the page you linked to jnorthr and downloaded what I hope was the correct  repositories. Then I tried to play an MP3 by double clicking on it, the Totem movie player opened but there is still no sound. I have of course checked all connections btw.
Here is the output from the terminal window:
> tao@tao-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
Password:
--14:34:43--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

100%[====================================>] 233           --.--K/s             

14:34:43 (10.07 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [233/233]

tao@tao-desktop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Then I installed "the package using APT"

>  sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mplayer gstreamer0.10-pitfdll
The following NEW packages will be installed
  w32codecs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3MB of archives.
After unpacking 34.4MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  w32codecs
Install these packages without verification [y/N]? y
Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free w32codecs 20061022-0medibuntu1+build1 [14.3MB]
Fetched 14.3MB in 55s (255kB/s)                                                
Selecting previously deselected package w32codecs.
(Reading database ... 112990 files and directories currently installed.)
Unpacking w32codecs (from .../w32codecs_20061022-0medibuntu1+build1_i386.deb) ...
Setting up w32codecs (20061022-0medibuntu1+build1) ...

 I can see the player looking like it is playing the MP3 with the time status bar moving, but still slince.
Should I be using another player perhaps?
I hope i have provided the correct information for your consideration.  Thanks for all the replies.
Tao

---

### Post by leo_rockway on 2007-08-06
provide output for lspci | grep -i audio pls

---

### Post by TaoBoogie on 2007-08-06
Whoops I forgot to say my hard drive is a 400 gig Hitachi SATA 300 (ATA2)

leo_rockway, I'm sorry I do not know how to provide output for lspci | grep -i audio. How would I go about doing that? Please bare in mind that this is the first time I have used this operating system. Well the  last two days anyway :)

---

### Post by TaoBoogie on 2007-08-06
Unless this is what you mean.
> tao@tao-desktop:~$ lspci | grep -i audio
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
tao@tao-desktop:~$ 


---

### Post by leo_rockway on 2007-08-06
> **TaoBoogie said:**
> Whoops I forgot to say my hard drive is a 400 gig Hitachi SATA 300 (ATA2)

leo_rockway, I'm sorry I do not know how to provide output for lspci | grep -i audio. How would I go about doing that? Please bare in mind that this is the first time I have used this operating system. Well the  last two days anyway :)

ok, you are in that black screen w/ white letters, right? it should say smth like ~@ubuntu
if you're not there then press ctrl+alt+F1

now, type this in exactly as i put it:

> lspci | grep -i audio

and then post your result...

and i'm going to tell you what that command does.

"ls" shows all files/folders inside the folder you are (just like "dir" in the DOS command line, in case you are familiar with that)

by analogy, lspci shows all the pci devices your comp has.

grep find patterns.

-i searches inside a database in particular, instead of the whole pci database.

so... lspci | grep -i audio looks into your pci devices and looks for the database that has the pattern "audio" in its name. basically what it will do is spit out the information on your sound card so we can help you set it.

for instance, my lspci | grep -i audio information says: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

once you tell us what audio card you have we can search online and see if together we can find you a solution.

---

### Post by leo_rockway on 2007-08-06
> **TaoBoogie said:**
> Unless this is what you mean.

exactly what i meant...

---

### Post by leo_rockway on 2007-08-06
what do you get when you type in

> amixer

and

> cat /proc/asound/modules

?

EDIT

type this one in too...

> aplay -l

---

### Post by TaoBoogie on 2007-08-06
Sorry for the delay I did not notice that the thread had progressed to a second page I was still refreshing the first one....
I typed ctrl+alt+F1 and got the black screen but the machine did not recognise the command "lspci | grep -i audio". Is that five letters (ispci) - space - pipe - space - four letters (grep) - space minus sign - space then i - space - audio?
Also how do I get out of the black screen? I had to force a restart.

The second command "amixer" ran at least a screenful of text perhaps more I can copy it down but I can not scroll the black screen to see if I have missed any information.

Can I do any of this in a terminal window like I could in a DOS box in windows?
Sorry again for the delay

---

### Post by TaoBoogie on 2007-08-06
I went ahead and tried the Terminal window :)
Here are the results af all the commands you listed above:

> tao@tao-desktop:~$ lspci | grep -i audio
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
tao@tao-desktop:~$ amixer
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [-4.50dB] [on]
  Front Right: Playback 28 [90%] [-4.50dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
tao@tao-desktop:~$ cat /proc/asound/modules
 0 snd_hda_intel
tao@tao-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tao@tao-desktop:~$ 


---

### Post by TaoBoogie on 2007-08-06
I still cannot hear any sound and I was wondering if there is a preffered software for playing back music files? The device that opens when I select a track is Totem Movie Player.

---

### Post by leo_rockway on 2007-08-06
another app still shouldnt work since you dont have sound...

this is what i found: [http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

basically you have to recompile alsa which you can download from their page. to compile it you need to extract it and then go like this in terminal from the folder you extracted your files to:

> sudo ./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install

---

### Post by TaoBoogie on 2007-08-06
Thanks  so much for the time you have taken on this, it really is appreciated. I have visites the ALSA page here [http://www.alsa-project.org/](http://www.alsa-project.org/) but what is it that i am downloading? I am at a bit of a loss. There are so many things to download on that page> # Driver
# Library
# Lib-plugins
# Utilities
# Tools
# Firmware
# PyALSA
# OSS Compat. Librar

---

### Post by TaoBoogie on 2007-08-06
Just wanted to BUMP this as I do not know what it isI am supposed to download from the site [http://www.alsa-project.org/](http://www.alsa-project.org/) There is no one link to download ALSA further help appreciated.

---

### Post by TaoBoogie on 2007-08-06
I tried to run the command > sudo ./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install From the directory that I downloaded the current driver from the page linked to.
Unfortunately I got these error messages

install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
The sound is still not working.
Any further advice?

---

### Post by leo_rockway on 2007-08-07
> **TaoBoogie said:**
> I tried to run the command  From the directory that I downloaded the current driver from the page linked to.
Unfortunately I got these error messages

install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
The sound is still not working.
Any further advice?

sorry for not answering before, i wasn't at my house...

you have to do the ./configure thing from the directory you extracted the alsa-drivers to... the tar.gz files (or tar.bz2) are compressed files.

you need to get alsa-drivers, alsa-lib and alsa-utils. you decompress all of them (i use ark from X, never liked using terminal to decompress)

then in the drivers directory type

> sudo ./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install

for utils and libs you can just compile the usual way (from their directories):

> ./configure
> make
> sudo make install

after you're done w/ all that you need to type this in

> modprobe snd-intel8x0 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

and then run the alsamixer command and unmute everything and raise the volume (using the M key and the up arrow on your keyboard).

> alsamixer

just to let you know... i'm not guaranteeing your sound will work after this... i'm just following normal procedure and it will def not hurt having the latest alsa drivers.

---

### Post by TaoBoogie on 2007-08-31
Sorry tech problems crashed me out of the online world for quite a while, but I'm back now (with the same lack of sound :( ) with a fresh install of ubuntu 7.04 with the updates and I've just installed my NVidia driver with Envy.

I'm now re-reading through this thread again to follow all the advice given and will post after that with my progress so far.
I have downloaded a linux driver from the sound card makers site RealTek but I have not attempted to install it yet (as I don't know how) untill I try the other procedures. If it may help here is the text file that came with the package "realtek-linux-audiopack":

> The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC880
ALC882
ALC883

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.9b_1.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.9b_1.
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
	       snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 

---

### Post by leo_rockway on 2007-08-31
at first sight it seems like the drivers you got are in fact an older version of the alsa drivers.

if the newer ones didn't work for you i don't think an older version will help.

btw, i entered the realtek site, which version of the drivers did you download? the ones that say "other"?

---

### Post by TaoBoogie on 2007-08-31
When you say
> you have to do the ./configure thing from the directory you extracted the alsa-drivers to... the tar.gz files (or tar.bz2) are compressed files.

you need to get alsa-drivers, alsa-lib and alsa-utils. you decompress all of them (i use ark from X, never liked using terminal to decompress)

Do you mean I open the folder with the extracted files in. and then I open a terminal window from Applications>Accessories>Terminal ? Because when I do that the terminal window still says > ged@ged-desktop:~$ ./install
bash: ./install: No such file or directory
ged@ged-desktop:~$ 

I really don't want to mess up this install by playing around with things I have no idea how to use, I've re-installed three times already. :)

---

### Post by leo_rockway on 2007-08-31
the terminal (afaik) always opens at "$HOME" which is the same as "~" which is also the same as /home/yourusername.

you need to enter the folder you extracted the tar to. if you extracted it to, let's say, "/home/yourusername/alsa-utils/" then just type in "cd alsa-utils" (idk if you're familiar with basic terminal commands like cd, ls, rm, cp, etc...) if you're not, i recommend looking for a guide (i don't know of any, otherwise i would provide you with a link)

after you are in that directory (or folder, or however you call them) then you can do ./configure (or ./install if you are planning to use the realtek ones)

---

### Post by TaoBoogie on 2007-08-31
thank you for still being there leo.
I tried to follow your steps. Opened the terminal window and typed ;
> ged@ged-desktop:~$ cd realtek
bash: cd: realtek: No such file or directory
ged@ged-desktop:~$ cd alsa-driver-1.0.14
bash: cd: alsa-driver-1.0.14: No such file or directory
ged@ged-desktop:~$ 
there is a folder on my desktop where I extracted the tar files to called "realtek" and "alsa-driver-1.0.14" but as you can see the terminal did not recognise the folder?
I shall keep on trying and looking for more info on the terminal commands.
I am fairly familial with the old DOS commands so I thought this wold work. I bet I'm missing something really basic.

---

### Post by TaoBoogie on 2007-08-31
The realtek page I downloaded from is here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)
and the driver is the Linux one called Linux(Kernel version 2.2.14 or 2.4)

---

### Post by TaoBoogie on 2007-08-31
I don't know how but it seems I've messed up my installation **again** I think I am trying to do too many things at once. My browsers have lost the top bar funtionality where the menus are. There is no bar of colour there and I can not move the windows or close them except from the panal at the bottom of the screen by alt clicking. If I can't  restore the normal windows I'll have to re-install.

---

### Post by TaoBoogie on 2007-08-31
Ok I have just completed the re-install. Now I am going to try to tread very carefully only installing the things I really need one at a time. The first thing is my NVidia driver I do not know whether to use the "System>Administration>Restricted Drivers Manager" or if I should  use "Envy" do you have any thoughts on that I wonder?
Now as for the lack of sound, what do you think should be my first steps? The last time I tried to load/update from ALSA I got it wrong it seems by installing out of date drivers.
I am going to search the forums for answers but I would also appreciate your advice greatly.
Tao
[edit] I also found this resource for the terminal commands I thought you may like to look at:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[/edit]

---

### Post by TaoBoogie on 2007-09-01
I went ahed amd installed my NVidia drive with Envy and (fingers crossed) things seem to be running OK.
I've been re-reading through this thread and I noticed with this output from the terminal:
> tao@tao-desktop:~$ lspci | grep -i audio
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
tao@tao-desktop:~$
Does this mean that I should be looking to nVidia for a sound driver and not RealTek?
When I open the Volume Control: HDA NVidia (Alsa mixer) and go to File>Change Device I have a choice of two. "HDA NVidia (Alsa mixer)" and Realtek ALC883 (OSS Mixer) The "HDA nVidia" is the one already selected. Is this the correct/normal configuration?

I have not yet tried to install the driver file (realtek-linux-audiopack-3.5-6) I got from the RealTek site as I feel that I need to complete this step first before I move on to another.

---

### Post by TaoBoogie on 2007-09-01
I downloaded the ALSA drivers "1.0.14" and typed in terminal;
> sudo ./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install
I got the message "ALSA modules were successfully compiled." but after that there were about 70 lines of text all saying;
> install: cannot create regular file `/usr/include/sound': Permission denied

In the ALSA Lib folder "alsa-lib-1.0.14a" I ran;
> ./configure
> make
> sudo make install

In the ALSA utilites folder "alsa-utils-1.0.14" I tried
> ./configure
and I got this message at the end;
> checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
I did some digging and found [this page]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
So I then typed this into the terminal;
> sudo apt-get install libncurses5-dev
and that seemed to go ok so I re-tried 
> ./configure
make
sudo make install
and it seemed to run ok.

Next I ran
> modprobe snd-intel8x0 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

but I got this message;
> tao@tao-desktop:~$ modprobe snd-intel8x0 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting ac97_bus (/lib/modules/2.6.20-16-generic/kernel/sound/ac97_bus.ko): Operation not permitted
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Operation not permitted
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-intel8x0.ko): Operation not permitted
tao@tao-desktop:~$ 
This is where I am up to at the moment.
As it stands I still can not hear sounds. I shall have another search though the forum before I try anything else and hopefully that will give you time to read through my recent posts .

---

### Post by TaoBoogie on 2007-09-01
**[CENTER]O M G[/CENTER]**
I can hear music, I am so happy. The sound is not very loud ( the same track plays a lot louder in  windows) but I think I can live with that.
If you think you can help me get the sound louder I would love that, I have all the sliders up to the max, but this is indeed a vast improvement.
Thank you very much for your help leo_rockway you have been a star. :guitar:

---

### Post by oliwally on 2007-09-02
> **TaoBoogie said:**
> **[CENTER]O M G[/CENTER]**
I can hear music, I am so happy. The sound is not very loud ( the same track plays a lot louder in  windows) but I think I can live with that.
If you think you can help me get the sound louder I would love that, I have all the sliders up to the max, but this is indeed a vast improvement.
Thank you very much for your help leo_rockway you have been a star. :guitar:

So, how did you fix it in the end? In your previous post it still wasn't working.

---

### Post by TaoBoogie on 2007-09-02
It was all the steps taken in post #31 that cured the problem. I don't know why I did not hear anything immediatly after that, but on re-start the there was music in my ears ;)

---


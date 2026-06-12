---
title: "Can't get sound to work in ubuntu 7.04"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by TaoBoogie on 2007-08-30
Hello there
My system is AMD 64 bit although I am only running it as 32bit. I have an ABIT KN9 Ultra MoBo with an on-board sound card (RealTek HD).
I am dual booting on separate drives with XP Pro. The sound card work while in XP but I can't get any sound/music to work in ubuntu.
When I go to System>Sound and test the "Sound Events" "Music and Movies" and "Audio Conferencing" I can hear a faint tone sound on test.
I cannot hear any of my music or video files.
I have visited the RealTek website and downloaded the "RealTek-Linux-Audiopack -3.5-6 but I'm not sure if:
A) It is the right driver.
B) How to install it.
I am **very**  new to ubuntu so these instructions that came in a text file with the audio pack don't really help me, as I do not understand the directions. There is an installer file in the pack but I've been warned against installing software this way.
Any help to get me back on the Boogie Woogie would be joyfully received.
Thanks
Tao

[edit]
here is the contents of the "read me" file included in the Audio pack.

The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
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
[/edit]

---

### Post by Ben Lumley on 2007-08-30
I'm also struggling with this but I'm not dual booting!

Running with an Acer Aspire 5050

---

### Post by jrlii on 2007-08-30
Is the audio muted?

The volume icon is near the upper right corner of the gnome screen.

I haven't figured out why, but it seems to frequently default to mute.

At least you have something reasonably standard. I had to struggle through building the driver for my Layla card.

---

### Post by TaoBoogie on 2007-08-30
I should have mentioned that sorry. No the sound is not muted

---

### Post by TaoBoogie on 2007-08-31
I just want to bump this.
The problem is unresolved.

---

### Post by TaoBoogie on 2007-08-31
A la bump

---

### Post by mpospisil on 2007-08-31
> **TaoBoogie said:**
> Hello there
My system is AMD 64 bit although I am only running it as 32bit. I have an ABIT KN9 Ultra MoBo with an on-board sound card (RealTek HD).
I am dual booting on separate drives with XP Pro. The sound card work while in XP but I can't get any sound/music to work in ubuntu.
When I go to System>Sound and test the "Sound Events" "Music and Movies" and "Audio Conferencing" I can hear a faint tone sound on test.
I cannot hear any of my music or video files.
I have visited the RealTek website and downloaded the "RealTek-Linux-Audiopack -3.5-6 but I'm not sure if:
A) It is the right driver.
B) How to install it.
I am **very**  new to ubuntu so these instructions that came in a text file with the audio pack don't really help me, as I do not understand the directions. There is an installer file in the pack but I've been warned against installing software this way.
Any help to get me back on the Boogie Woogie would be joyfully received.
Thanks
Tao

[edit]
here is the contents of the "read me" file included in the Audio pack.

The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
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
[/edit]

I don't know if it is the correct driver or not for your sound card but according to the readme that is posted the installation is simple.  In a terminal you change to the folder that the driver you downloaded is in.  Most likely it downloaded to your Desktop.  So change directories to the Desktop and then to the driver folder. Ater that type in the command ./install like it says.

---

### Post by beap on 2007-09-02
the device can be seen on alsaconf but still alsa cant load it during boot process. ive been trying to recompile/reinstall again and again. still no luck :(

---- alc880;realtek

---

### Post by musikgoat on 2007-09-13
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				taoboogie:  in terminal
```
lsmod | grep snd_hda_intel
```

if you get:
snd_hda_intel         <somevalue> <someothervalue> 

you may be experiencing the same problem I had when I stumbled upon your post.

I have a realtek audio card, but also an intel HD audio add-on (which i never used)
later, with some help from nickrud in IRC,   I fixed the issue with info from this bug report.
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

in terminal:
```
sudo nano /etc/modprobe.d/snd-hda-intel
```
in the blank file type:
```
options snd-hda-intel model=auto
```
and hit ctrl+x and yes to save the file.
reboot and see if your sound issue is fixed.

hope that helps you.

---

### Post by ]Nbx*cmD[ on 2007-09-18
Worked perfectly, thanks!

---

### Post by maryjanua on 2007-09-19
i just fixed this problem in my pc
check out this thread around page11 all credit to vadi and mali2297
[http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)
hope this helps ya 
regards
mj:)

---

### Post by Tteddo on 2007-10-06
This just fixed the sound on my Acer Aspire 5050. Cool!

---


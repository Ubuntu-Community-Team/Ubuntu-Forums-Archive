---
title: "quick mythtv question"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-25
ok i am setting up mythtv with a hauppauge pvr 150 and have gotten everything up to the backend configuration working fine. Using this guide here: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

I set up the drivers for my card first using this guide: [http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150](http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150)
and then started using the other guide. My question is when I get to the input connections scrren, there are no options available. I set up the card following the guide, and then hit escape to go back instead of finish. Either one doesn't seem to save the changes but thats what the guide says to do. Any idea what I am doing wrong? The card works just fine in xp and vista and when I did the mplayer test found in the first guide, video played. Mythtv reports the card as well in the probe section. Why no inputs? The cable is firmly in there.

Also, the guide says to select mpeg 2 encoder which I am doing, should I be using something else?

---

### Post by tgm4883 on 2007-05-25
You didn't need to use the other guide as the PVR-150 support is built into feisty

In the capture card section, under (New Capture Card) and both delete options, is your PVR-150 listed

---

### Post by jba6511 on 2007-05-25
no it is not listed in there. just the 3 options are listed.

---

### Post by tgm4883 on 2007-05-25
Then thats why it isn't showing up, you need to add the card there first and be sure to hit finish when you do otherwise it wont add

---

### Post by jba6511 on 2007-05-25
ok, will try and report back in a min.

---

### Post by jba6511 on 2007-05-25
ok tried it and no luck. It says the video card is on /device/video0. How do I check and make sure this is correct? Once I chose the mpeg 2 whatever for hauppauge and click finish, it does not save it. Also, I have tuner1 selected. I am just using regular cable tv as well.

---

### Post by tgm4883 on 2007-05-25
hmm it really should be saving when you hit finish, are you doing it as an mpeg 2 encoder card?

---

### Post by jba6511 on 2007-05-25
yeah. I am going to boot over to windows real quick and make sure it is still working there in case it came loose earlier today when I installed a NIC. By the way, were you able to get your DS3 board to work with the onboard Marvel NIC?

---

### Post by tgm4883 on 2007-05-25
Yes and no, last time i checked it i kept getting freezes (what i believe was that it was due to it being a gigabyte card hooked up to a 10/100 router).  I have since put in a second NIC and disabled the onboard one.

Also you could test it in tvtime to see if it works (and to see what device it is)

also, are you sure it says /device/video0 and no /dev/video0?

---

### Post by jba6511 on 2007-05-25
works fine in windows. Is there an equivalent in linux to device manager so that I can make sure ubuntu recognizes the card. Is there a way to remove the drivers I installed using that guide if you think that might be the problem.

---

### Post by tgm4883 on 2007-05-25
Post the output of lspci in terminal

---

### Post by jba6511 on 2007-05-25
0:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:02.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

---

### Post by tgm4883 on 2007-05-25
also, install tvtime

---

### Post by jba6511 on 2007-05-25
i just marked mythtv package for reinstall and went to do the editing of the mysql part. HOwever, the changes were already saved from before and i got this message:

* Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Do I need to redo this file? How would that be done?

---

### Post by jba6511 on 2007-05-25
what does tvtime do?

---

### Post by tgm4883 on 2007-05-25
we can use tv time to make sure that it works in linux

---

### Post by jba6511 on 2007-05-25
when I run tv time I get an error on the bottom left that says:

ivtv: invalid argument
cannot open capture device /dev/video0

from searching the forums it seems tvtime does not work with ivtv anyways and the hauppauge cards.

---

### Post by fenian on 2007-05-25
TVTime doesn't work with hardware encoders (ivtv).To see if the card is working use mplayer.To install mplayer do..
> 
sudo apt-get install mplayer

then check the card from the terminal enter...

> mplayer /dev/video0

this may bring up a window that is all static thats ok we can change the tuner channel,open a separate terminal window and enter...

> ivtv-tune -c # -d /dev/video0 

change the # to the channel you want (if you are hookig up  to a cable box that would be 3 if your cable goes directly to the card enter a real channel #).

---

### Post by jba6511 on 2007-05-25
works fine doing it that way. sound and video. It is like the changes are not sticking in mythtv backend setup. Is there a way to completely remove and reinstall? I treid this in syanptic to all the packages, but when I uninstall them, restart, and then reinstall, I do not get the popups with the genrated password and what not.

---

### Post by fenian on 2007-05-25
Try this first...

> sudo apt-get remove --purge mysql-server-5.0 mythtv-database

then...
> 
sudo apt-get install mythtv-database mysql-server-5.0 

then do mythtv-setup agaim.

---

### Post by jba6511 on 2007-05-25
did the first part, will reinstall and try again then report back. Thanks for all of the help so far

---

### Post by jba6511 on 2007-05-25
well that worked and now mythtv sees my card and saves the changes. Now, however, when I get to the input source screen, everything is listed like in the guide, but they all say (none) beside them instead of cable like the tuner should.
gotta eat dinner real quick and will be back in like 20 - 30.

---

### Post by fenian on 2007-05-25
In the capture card setup screen did you set the default input to match how you are conncting to your cable to the card (svideo,composite or tuner)?Also be sure to set  the card type to mpeg2 encoder card.

---

### Post by tgm4883 on 2007-05-25
Sweet some extra help.  I was leaning toward a purge of the database, just needed the right command.

---

### Post by jba6511 on 2007-05-25
i just double checked and it is set up as tuner1 in the capture card and tuner 1 in the input screen still has a none by it. I am connecting cable into the back of the card directly. Any ideas why the tv tuner option in the input and all of the other options list none?

---

### Post by tgm4883 on 2007-05-25
> **jba6511 said:**
> well that worked and now mythtv sees my card and saves the changes. Now, however, when I get to the input source screen, everything is listed like in the guide, but they all say (none) beside them instead of cable like the tuner should.
gotta eat dinner real quick and will be back in like 20 - 30.

Are you talking about the input connections?  You need to select the tuner 1 on the /dev/video0 card.  The reason it says cable on there (and yours says none) is because that is where the video source is listed from the previous step.  Once you select that tuner, go in and set the video source to whatever the right one is that you setup in step 3 (Video Sources).  Once you set that up, then it will no longer say none and instead say the name of your video source.

---

### Post by fenian on 2007-05-25
In the capture card setup screen is the video device set to /dev/video0?

---

### Post by jba6511 on 2007-05-25
ok guys almost there. I get the video source working and it found all of my channels and they now appear in the channel editor. I got this after running the database manager update it asks you to do when exiting:

2007-05-25 21:26:21.064 Upgrading to schema version 1158
2007-05-25 21:26:21.079 Upgrading to schema version 1159
2007-05-25 21:26:21.096 Upgrading to schema version 1160
2007-05-25 21:26:21.104 Database Schema upgrade complete, unlocking.
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-25 21:30:06.032 Using runtime prefix = /usr
2007-05-25 21:30:06.051 New DB connection, total: 1
2007-05-25 21:30:06.055 Connected to database 'mythconverg' at host: localhost
2007-05-25 21:30:06.058 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-25 22:06:50.771 Using runtime prefix = /usr
2007-05-25 22:06:50.791 New DB connection, total: 1
2007-05-25 22:06:50.794 Connected to database 'mythconverg' at host: localhost
2007-05-25 22:06:50.796 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-25 22:24:08.576 Using runtime prefix = /usr
2007-05-25 22:24:08.617 New DB connection, total: 1
2007-05-25 22:24:08.624 Connected to database 'mythconverg' at host: localhost
2007-05-25 22:24:08.626 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-25 22:28:31.672 Using runtime prefix = /usr
2007-05-25 22:28:31.705 New DB connection, total: 1
2007-05-25 22:28:31.709 Connected to database 'mythconverg' at host: localhost
2007-05-25 22:28:31.711 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.
2007-05-25 22:29:19.182 Using runtime prefix = /usr
2007-05-25 22:29:19.201 New DB connection, total: 1
2007-05-25 22:29:19.205 Connected to database 'mythconverg' at host: localhost
2007-05-25 22:29:19.207 Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

And running this  ps -p `cat /var/run/mythtv/mythbackend.pid`
I only see the header with no info.

---

### Post by jba6511 on 2007-05-25
changing the address from 127.0.0.1 to my real private addy fixed this. Pressing on...

---

### Post by fenian on 2007-05-25
-snip-

---

### Post by jba6511 on 2007-05-25
well i am glad to say that everything is up and running. However, I did notice the sound comes in a little low, even with the sound turned all the way up from the speaker icon in ubuntu and on my speakers. Any idea how to fix this and any quick tips for making my hauppauge remote work that came with the card with mythtv? Thanks guys, could not have done it without your help.

---

### Post by tgm4883 on 2007-05-25
You need to install lirc.  There is a guide in the same place as the feisty mythtv guide.

The sound is another problem.  What i'm told is there is not much you can do.  If everything is already turned up, then the next thing to do is get an external amplifier.

---

### Post by fenian on 2007-05-25
To bump up  the volume go to utilities/setup on the main myth screen ,choose setup on the next screen,choose general and advance to the third screen (audio) turn up the master mixer volume and the pcm mixer volume then keep hitting next until your back to the setup screen.

---


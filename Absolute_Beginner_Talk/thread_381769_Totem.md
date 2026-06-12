---
title: "Totem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-03-11
Totem could not play 'mms://63.250.205.11/b02r01/011/yahoomovies/14/33266007.wmv?StreamID=33266007=003FFAC339475E001E5588A40245F41588=
1551890=182488=1809276825=y=0000061e1ab1945f41587=c=1'.


I get this when trying to play a movie trailer on yahoo or a music selection sample from amazon.com
How do I get Totem to perform?

---

### Post by nudnik on 2007-03-11
> **rosswmcgee said:**
> Totem could not play 'mms://63.250.205.11/b02r01/011/yahoomovies/14/33266007.wmv?StreamID=33266007=003FFAC339475E001E5588A40245F41588=
1551890=182488=1809276825=y=0000061e1ab1945f41587=c=1'.


I get this when trying to play a movie trailer on yahoo or a music selection sample from amazon.com
How do I get Totem to perform?

Remember, Ubuntu earned its mascot honestly : ) (see below) 

Make sure you have all the necessary codecs and software installed before venturing into Multimedia Land. See the Ubuntu documentation regarding this, and in particular, the wikki articles on Restricted Formats. 

As far as I can gather, it appears you were attempting to play a WMV file, which, for one thing, requires the WIN32 codecs. These are available in a Debian package. 

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

---

### Post by rosswmcgee on 2007-03-11
I did this but no change, what is next?
    *

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

### Post by houstonbofh on 2007-03-11
> **rosswmcgee said:**
> I did this but no change, what is next?
    *

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Might want to change ogle to ogle-mmx, unless you like slow DVDs.  Here is my simple install script, AFTER enabling all the builtin Ubuntu repositories, and disabling the CD repository.
```

#!/bin/sh
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
# Universe, multiverse and backports must be on,
# and CDs must be off.
#
# Note: Sudo must be enabled for this to work.
# Type 'sudo ls' and your password before running
#
# DHCP Client
# /etc/dchp3/dhclient.conf
#
# NTP Config
#

# Add extra repositories

# Medibuntu
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european flashplugin-nonfree sun-java5-plugin faad ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 liboggflac3 libquicktime0 libsidplay1 libswfdec0.3 libungif4g libwavpack0 libxine-extracodecs libxine-main1 libxvidcore4 libxvmc1 mjpegtools ntp ntp-simple sox vorbis-tools libdvdcss2 w32codecs msttcorefonts

```

---

### Post by rosswmcgee on 2007-03-11
bash: DHCP: command not found



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

this is where I stalled.I ma using Ubuntu 6.10

---

### Post by houstonbofh on 2007-03-12
That is a broke package.  Run 'sudo dpkg --configure -a' and follow directions.  Then run Synaptic, and "Fix Broken Packages."  Reload the repositories, and exit.  Now start again.

Also, that shell is run on a stock ubuntu gnome system.  DHCP is commented, and should not be a command.  So I am not sure where you are.  If you are also unsure, post a screenshot of your repositories.  (3rd party especially)

---

### Post by ronbrooks on 2007-03-12
Well I am getting the same message and under that message it has you may not have permission  to use this file. I have been trying to figure out what I don't have permission to use. but I don't know what file to look for to see if I have the right permission.

---

### Post by drs305 on 2007-03-12
I can't help you get Totem to play mms files, but I have learned how to play mms audio file links on the Internet. 

I am a big NHL fan and finally got mms audio streams to play by using Firefox and installing MediaPlayerConnectivity. Once that was installed, I changed the preferences of MediaPlayerConnectivity to use VLC as the program to open every type of file. That got mms files working on my computer. When I click on an audio link, the add-on displays a symbol like a film clip. I click on that and the file opens with the player I selected for that type of file (VLC). 

You might be able to open mms links directly with VLC but I've always opened them via Firefox.

---

### Post by relambert on 2007-03-12
I've seen people in slam Automatix2 in these posts, but installing it and then installing the mutilmedia codecs enabled me to play wmv files. Oh, you might want to install MPlayer and the Firefox plugin as well. Just follow this link to Automatix, [http://www.getautomatix.com/](http://www.getautomatix.com/). Click on installation and follow along. Hope that helps you like it did me.

---

### Post by rosswmcgee on 2007-03-12
I did down load media connectivity, where is stored? can not find it?

---

### Post by relambert on 2007-03-12
Not sure what you mean by "media connectivity".:confused:  You have to get Win32 codecs to play any wmv file, and the only way I've found to get ones that work are through Automatix, and go figure, I just went to their sight, and it isn't working. So much for me talking them up. I had many trial and error sessions trying to get Windows streams to play. After I installed Mplayer and then the multimedia codecs from Automatix, I was able to see wmv streams from many web sights. I'm not sure if Mplayer is required, but I saw many posts that said to install it, so I did. All wmv files seem to open in Totem anyway. In my opinion though, flash  video seems to work better on Ubuntu then Windows media. There's just so much media player stuff out there. I'm by no means an expert here, but I was able to get them to work on my system.

---

### Post by drs305 on 2007-03-13
> **rosswmcgee said:**
> I did down load media connectivity, where is stored? can not find it?

The short answer to whether MediaPlayerConnectivity is installed:
In Firefox, click on Tools, Add-ons, and you should see it listed in the Add-on window.

Here are the detailed instructions on how to install it if you are not familiar wtih Firefox add-ons/extensions/plug-ins:

If you are using Firefox 2, here is how to install MediaPlayerConnectivity:
Open Firefox.
Select Tools, Add-ons.
Click on the link for Get Extensions (lower right)
At the bottom of the new screen, type MediaPlayerConnectivity in the search box and enter.
Click on the green Install Now box. This is on page: [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
The plug-in should install. 
Once it is finished (it should only take a few seconds), restart Firefox.
You can see if it is installed by going to Tools, Add-ons, and seeing if MediaPlayerConnectivity is listed.

[Pardon the interruption, I'll have to exit this thread to restart Firefox.]

Okay, I'm back. To set the preferences in MediaPlayerConnectivity:
Tools, Add-ons.
You should see MediaPlayerConnectivity listed. Click on the Preferences box inside the MPC box.
You now have options for various types of audio/video files.
I have all mine set to VLC (assuming you have the VLC program installed).
My VLC program is listed in /usr/bin, so I used the browse button to go to File System usr/bin and clicked on VLC
Once I've done that, the entry for the file type (example) Windows Media is checked, and in the panel it displays:  /usr/bin/vlc
As I mentioned, I have all file types checked and set to VLC because I wasn't sure which file type MMS referenced.
Once you have the file types checked and associated with the VLC app, click Apply and/or OK and you should be set.

Now when I click on a link that uses an MMS stream, I get a new window and I click on the 'film clip' icon. This launches the VLC player. Sometimes it takes a minute or so after the VLC program starts before I actually get the audio to start playing.

Good luck.

PS: This is a good example of why so many people prefer Linux. Look at all the steps necessary to get to the end. With many/most Linux programs, we could have arrived there with one entry in a command line instead of having to do all of the above...

---

### Post by relambert on 2007-03-13
drs305, that's the best solution I've seen yet.:)

---

### Post by rosswmcgee on 2007-03-13
I have installed automatix and vlc but when I try to play a sample video from yahoo movies I still get the mms msg totem can not play. How do I get totem out of the picture?

---

### Post by drs305 on 2007-03-13
I eliminated all references to Totem via Synaptic Package Manager. 

System, Administration, Synaptic Package Manager. 
Type in your root password.
I type totem in the search box to find all installed references to totem.
I deselected all references to totem originally but now have totem-xine and libtotem-plparser1 and the mms stream still is played by VLC. On my system, if totem had anything to do with MMS it wouldn't work...

Other than de-installing totem, the only other system-wide things that might help are having the "w32codecs" installed. While you have Synaptic open, you can do a search for w32codecs to see if they are installed (and install them if not).

Keep asking questions if you still are having problems.

---

### Post by rosswmcgee on 2007-03-13
Voila! ok it woiks! The changes you recomended r/e media player connectivity did the job. On the other hand I did every thing others recommeded, Sudo this and that, I also downloaded automatix. Is there a reason to keep automatix? It installed fine,but I am not sure which takes over automatix or snyaptic package manager or how to operate them. Thank you so much for helping and every one else a thank you as well for this thread!
Ross

---

### Post by drs305 on 2007-03-13
Ross,

Glad you got the mms files to work.

I am still an Ubuntu newbie and started with Automatix and moved on to Synaptic. Synaptic provided a lot more apps. You can use either program but cannot have them both open at the same time (you will get an error message). Eventually you will probably prefer direct command line installations, which are by far the easiest if you can get the command line entry figured out.

Enjoy Ubuntu.

Dave

---

### Post by relambert on 2007-03-14
I tried to play movie trailers from Yahoo movies and got the same error message. Got vlc and got the media extension for Firefox. Now the movie trailers play as well. Good job!

---

### Post by rosswmcgee on 2007-03-14
It is satisfying to learn new things. I have been a  linspire user for years, lindows before that,ubuntu is very fast. Now ubuntu will offer cnr from linspire so I am running both systems for the time being.

---


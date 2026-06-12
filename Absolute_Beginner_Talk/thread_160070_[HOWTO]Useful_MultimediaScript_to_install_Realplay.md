---
title: "[HOWTO]Useful MultimediaScript to install Realplayer/VidPlayers/codecsWithoutEfforts!"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-14
[HOWTO]Useful MultimediaScript to install Realplayer/VidPlayers/codecsWithoutEfforts!
For Breezy and Dapper
-------------------------
Hi, 
    
Then, just run this script with root rights :
```

cd /tmp
wget -N http://patrick295767.sitesled.com/miniram/multimedia.sh
sudo sh /tmp/multimedia.sh
```

Installations after the installation configuration (you choose what you need) : 
 **  codecs, mplayer, totem ... xvidcap (record ur screen), realplayer, e17 enlightenment, mupen, skype, ...**
-------------------
script multimedia.sh [here]("http://patrick295767.sitesled.com/miniram/multimedia.sh") 

No needs to worry about /etc/apt/sources.list 
The script do everythg by itself without changing your own & personal : /etc/apt/sources.list 
   
Greetings, 

Patrick

---

### Post by meatbites on 2006-04-14
Thanks for this Patrick. I can see this being damn useful for many. :)

Just a suggestion: unless I overlooked something, you might want to offer a list of the required lines that need to be added to the sources.list file.

---

### Post by patrick295767 on 2006-04-14
[QUOTE=meatbites]Thanks for this Patrick. I can see this being damn useful for many. :)

Just a suggestion: unless I overlooked something, you might want to offer a list of the required lines that need to be added to the sources.list file.[/QUOTE]
  
Thank you !
I edited the first post of this thread & added the sources.list.
  
Greetings, Patrick

---

### Post by patrick295767 on 2006-04-14
And shit !!
  
I think I have been kicked by multimania, for having realplayer files ... and deb files...   certainly too much visits,  
OR the multimania is very unstable :mad: 
  
Plz could someone tell me where I could have a stable webhosting without any problems & better than multimania ?? (with ftp uploading) or maybe a login/password under our Ubuntu website (admin guys) ;) ??
  
Thank you very much !!
  
Patrick

---

### Post by patrick295767 on 2006-04-18
New version (new webhosting) 

Multimedia.sh 
----vers 0.3--- :
```
#!/bin/bash
#############" multimedia, codecs, xvidcap
## juke box
echo "Please enter your main user of this computer ?" 
read userpatname
#
apt-get -f -y install xmms
apt-get -f -y install juk


### codecs and so on
cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer

##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "/home/$userpatname/.mplayer/config       to get zoom=yes in .mplayer/config"
echo "zoom=yes" >> "/home/$userpatname/.mplayer/config"




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin

cd /root
wget http://patrick295767.sitesled.com/miniram/real.bin
chmod 777 /root/real.bin
chmod +x /root/real.bin
./real.bin
#You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

###################### Installing xvidcap xvidcap_1.1.3-p7_i386.deb############""
cd /root
wget http://patrick295767.sitesled.com/miniram/xvidcap_1.1.3-p7_i386.deb
#echo "  " >> /etc/apt/sources.list
#echo "## libavcodec1 " >> /etc/apt/sources.list
#echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
#apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
dpkg -i xvidcap_1.1.3-p7_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"
echo "** Patrick295767 **"
```

---

### Post by macdo on 2006-04-18
Cool! But I have a suspicion that you need to repost your sources.list :) 

I'm willing to mirror the lot on a free.fr website, if that would help...
Email me at macdo10nospamplease\at\free.fr if you're interested.

---

### Post by patrick295767 on 2006-04-19
I updated a bit the script, now,  version 0.4 (first post of this thread).
 (I am adding now this script in my signature)
  
Thank you MacDo !! We can amsn or gaim each other, to stay in contact !
              
Greetings            
         
Patrick  
=====

---

### Post by macdo on 2006-04-19
OK, I sent you a Gmail chat invite...

---

### Post by patrick295767 on 2006-04-20
My version 0.5 multimedia.sh :
```
#############" multimedia, codecs, xvidcap
## multimedia link : http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Player_.28MPlayer.29_with_Plug-in_for_Mozilla_Firefox
##
### multimedia script

echo "Please enter your main user of this computer ?"
read userpatname
#$(echo userpatname)


apt-get update
apt-get -y upgrade



## if one day, xvid and gvidcap are in repos
apt-get -f -y install xvidcap
apt-get -f -y install gvidcap
## utils apps videos player
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install mplayer-386
apt-get -f -y install digikam
apt-get -f -y install kaffeine
apt-get -f -y install guitar
apt-get -f -y install xine
apt-get -f -y install sed
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install  gxine
apt-get -f -y install audacity
## stream radio online tuner via internet
apt-get -f -y install streamripper
apt-get -f -y install streamtuner
apt-get -f -y install rhythmbox
## like realplayer
apt-get -f -y install hxplay
## stream tv online
apt-get -f -y install xawtv
apt-get -f -y install kdetv
#apt-get -f -y install xdtv
apt-get -f -y install xmltv
# camera stuffs
apt-get -f -y install camorama
## sound sound
apt-get -f -y install alsamixergui
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim
########### tv stuffs
apt-get -f -y install xawtv
apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install

# Music Organizer: Cowbell
apt-get -f -y install cowbell
# ID3 Tag Editor (EasyTAG)
apt-get -f -y install easytag
# Video Editor (Kino)
apt-get -f -y install kino
apt-get -f -y install kinoplus
apt-get -f -y install kino-timfx
apt-get -f -y install kino-dvtitler
apt-get -f -y install

## juke box
apt-get -f -y install amarok
apt-get -f -y install xmms
apt-get -f -y install xmms-skins
apt-get -f -y install juk
#wget -c http://easylinux.info/uploads/xmms-wma_1.0.4-2_i386.deb
cd /root
wget http://patrick295767.sitesled.com/miniram/xmms-wma_1.0.4-2_i386.deb
dpkg -i /root/xmms-wma_1.0.4-2_i386.deb

cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list
rm -f /tmp/defaults.*

### codecs and so on

apt-get -f -y install xine-ui
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
rm -f /usr/share/applnk/Multimedia/xine.desktop
ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list


cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla

sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs
apt-get -f -y install libdvdcss2
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer
#gedit /etc/mplayer/mplayer.conf
#Find this line 
#vo=x11,         # To specify default video driver (see -vo help for
#Replace with the following line 
#vo=xv,         # To specify default video driver (see -vo help for
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
 
##never forget this for all the users
echo "/home/$(echo userpatname)/.mplayer/config       to get zoom=yes in .mplayer/config"
echo "zoom=yes" >> "/home/$(echo userpatname)/.mplayer/config"




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin

cd /root
##wget http://membres.lycos.fr/patrick295767/miniram/packages/realplayer10gold.bin
wget http://patrick295767.sitesled.com/miniram/real.bin
chmod 777 /root/real.bin
chmod +x /root/real.bin
./real.bin
#You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup


cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup


###################### Installing xvidcap ############""
cd /root
#wget http://membres.lycos.fr/patrick295767/miniram/packages/xvidcap_1.1.3-1_i386.deb
#wget http://patrick295767.sitesled.com/miniram/xvidcap_1.1.3-p7_i386.deb
wget http://patrick295767.sitesled.com/miniram/xvidcap_1.1.3-1_i386.deb
#echo "  " >> /etc/apt/sources.list
#echo "## libavcodec1 " >> /etc/apt/sources.list
#echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
#apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"



```

---

### Post by jms830 on 2006-04-20
This is very a very helpful script. Just a question though: is it just me or does it install alot of KDE apps, and might be better suited for Kubuntu than Ubuntu with gnome?

---

### Post by patrick295767 on 2006-04-21
[QUOTE=jms830]This is very a very helpful script. Just a question though: is it just me or does it install alot of KDE apps, and might be better suited for Kubuntu than Ubuntu with gnome?[/QUOTE]
  
Indeed there is gnome and KDE apps too. There is the most useful apps for multimedia, and you can choose your favourite. 
  
The idea is to be sure that everthg multimedia is working ! (or most of it at >90 percent).:D 

Thanks 

Greetings !!

---

### Post by adamkane on 2006-04-21
Please give the user the option to install mplayer-686 or mplayer-k7.

You should add the latest ffmpeg as well:
[http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb]("http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb")

Takis repository:
  deb [http://issaris.be/breezy]("http://issaris.be/breezy") ./

EDIT:
Due to unstability of the server that previously hosted the repository, Takis has moved the Ubuntu Breezy repository. The new line to add to your /etc/apt/sources.list would be:
 deb [http://alpha.uhasselt.be/takis.issaris/breezy/]("http://alpha.uhasselt.be/takis.issaris/breezy/") ./

---

### Post by jms830 on 2006-04-24
how do i uninstall realplayer after using this script? (I still want to be able to play realmedia files of course, just don't want the realplayer program).

---

### Post by adamkane on 2006-04-24
Because you asked (I don't want to interrupt the thread.):

How to play streaming realmedia without realplayer:
[http://www.ubuntuforums.org/showthread.php?t=158337]("http://www.ubuntuforums.org/showthread.php?t=158337")

You can play non-streaming realmedia with beep-media-player or totem, if you have mplayer installed.

---

### Post by patrick295767 on 2006-04-24
[QUOTE=adamkane]Please give the user the option to install mplayer-686 or mplayer-k7.

You should add the latest ffmpeg as well:
[http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb](http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb)[/QUOTE]
  
I will provide you an update as soon as possible (one or 2 days) to satisfy you with it !  *

Thank you !!!

Patrick

---

### Post by patrick295767 on 2006-04-24
[QUOTE=jms830]how do i uninstall realplayer after using this script? (I still want to be able to play realmedia files of course, just don't want the realplayer program).[/QUOTE]
  
I will add in the begininng of the script some choices for the users ...  (i.e. Realplayer too )
This week, another version will be released !! :-)
  
Thank you for your comments and ideas !! 
  
Patrick
  
===
therefore, to be continued in this thread ! :-)

---

### Post by jms830 on 2006-04-24
Sorry, what I meant was I already have used the script and realplayer is installed. But I no longer want it installed, so how would I remove it now? Most of the other stuff I know I can apt-get remove if I chose... but this realplayer is installed differently. Thanks

Btw, good work Patrick, I think this will be very popular with more prompts and options

EDIT: Because I don't want to further interrupt this thread, I'll just add this.  The link in the post below said to "sudo apt-get remove realplay", however after using this script one will find that does not work.  Instead, my best guess to remove it is the commands:
sudo rm /usr/bin/realplay
sudo rm /usr/lib/realplay
sudo rm -rf /root/RealPlayer
sudo rm /usr/share/applications/realplay.desktop
sudo rm /usr/share/gnome-app-install/realplayer.desktop

---

### Post by adamkane on 2006-04-24
Uninstall realplayer:
[http://www.ubuntuforums.org/showthread.php?t=151125](http://www.ubuntuforums.org/showthread.php?t=151125)

---

### Post by patrick295767 on 2006-04-27
Hi,

So now there is a release version 0.8 :
You can now install : 

> Codecs for multimedia,
multimedia players, 
...
realplayer, 
skype, 
e17 enlightenment 
....


  
This program is meant Effortless !
  
Enjoy !
  
Patrick

---

### Post by quincyjones on 2006-04-27
Sorry but could someone please tell me *exactly* how to run Patrick's script?
I reaally am a beginner!
;)

Also, 
1) do you think it can sort out my problems with playing quicktime 7 movies
2) WMA playing jittery and jerky
3) Is it a problem that I have some of the programs and codecs installed already?

Thanks!

---

### Post by Jagot on 2006-04-27
Download the script in Patrick's first post, then in the terminal:

[QUOTE=patrick295767]
Root rights :
```
sudo bash
```
    
Then, just run this script with root rights :
```
./multimedia-v0.8.sh 
```[/QUOTE]

With the last part just go to wherever you saved the script to, so if it's the desktop then:

```
~/Desktop/multimedia-v0.8.sh 
```

---

### Post by quincyjones on 2006-04-27
Hey Jagot, 
Thanks for the reply but this is what I get:

```
clint@192:~$ sudo bash
Password:
root@192:~# ~/Desktop/multimedia.sh
bash: /home/clint/Desktop/multimedia.sh: **Permission denied**
root@192:~#

```

The file from Patrick's first post is saved on my desktop as "multimedia.sh"
:confused: 
I even tried rebooting in case another program somehow had the permissions

You probably wouldn't have noticed the edit at the end of my other post so I'm going to stick it in again:
[I]Also,
1) do you think it can sort out my problems with playing quicktime7 movies
2) WMA playing jittery and jerky
3) Is it a problem that I have some of the programs and codecs installed already?[/I]

---

### Post by patrick295767 on 2006-04-27
[QUOTE=quincyjones]Hey Jagot, 
Thanks for the reply but this is what I get:

```
clint@192:~$ sudo bash
Password:
root@192:~# ~/Desktop/multimedia.sh
bash: /home/clint/Desktop/multimedia.sh: **Permission denied**
root@192:~#

```

The file from Patrick's first post is saved on my desktop as "multimedia.sh"
:confused: 
I even tried rebooting in case another program somehow had the permissions

You probably wouldn't have noticed the edit at the end of my other post so I'm going to stick it in again:
[I]Also,
1) do you think it can sort out my problems with playing quicktime7 movies
2) WMA playing jittery and jerky
3) Is it a problem that I have some of the programs and codecs installed already?[/I][/QUOTE]
  
  
I would recommand from konsole or xterm to type (in the order ) this : 
(maybe that could maybe be easier) (no need of mozilla-firefox )
as normal user :
   
```
sudo bash                    # you'll have to enter the root password for installations....
cd /root
wget [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
chmod 777 /root/multimedia.sh                      # not necessary at all, but by precaution ...?
chmod +x /root/multimedia.sh
./multimedia.sh
```
   
And, you then can reply the questions, and choose what you'd like to install 
  
I hope this will help you !  
  
Let us know about your progress, and do not hesitate to ask questions, we 'll be glad to help you !
  
Greetings, 

Patrick

---

### Post by quincyjones on 2006-04-27
Another question, if I use Patrick's script to install apps (assuming that I get it to work) or for that matter, automatix, then can I remove programs with Synaptic?
Are automatix and this script "compatible"?
Shouldn't automatix include all the stuff in this script (not a complaint, just a question)?

---

### Post by patrick295767 on 2006-04-27
[QUOTE=quincyjones]Another question, if I use Patrick's script to install apps (assuming that I get it to work) or for that matter, automatix, then can I remove programs with Synaptic?
Are automatix and this script "compatible"?
Shouldn't automatix include all the stuff in this script (not a complaint, just a question)?[/QUOTE]
  
Yes yes, In order to remove apps, you may use synaptics ... or 
apt-get remove yyyyyyyy
 
for instance: ```
apt-get remove gedit
apt-get remove streamtuner 
....

```
  
See ya', Patrick

---

### Post by quincyjones on 2006-04-27
Hey Patrick,
Thanks so much for the reply, I wasn't expecting it from the author himself!
But, I don't know what I'm doing wrong, this is what happened in my terminal:

> clint@192:~$ sudo bash
root@192:~# cd /root
root@192:/root# wget [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
--22:44:42--  [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
           => `multimedia.sh'
Resolving patrick295767.sitesled.com... 8.6.90.150
Connecting to patrick295767.sitesled.com|8.6.90.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13,699 (13K) [application/x-sh]

100%[====================================>] 13,699        19.02K/s

22:44:43 (19.00 KB/s) - `multimedia.sh' saved [13699/13699]

root@192:/root# chmod 777 /root/multimedia.sh
root@192:/root# chmod +x /root/multimedia.sh
root@192:/root# ./multimedia.sh
: command not foundne 9: clear
************************************************************
************************************************************
**** Welcome !                                          ****
**** multimedia.sh script by patrick295767 version 0.8  ****
**** April 2006 - Ubuntu Linux     (for Breezy)         ****
************************************************************
************************************************************
  Automatic Installation script for several applications
  Please choose your applications you would like to install effortless ! :-)
  I would recommand you to launch this script from konsole

./multimedia.sh: line 25: syntax error near unexpected token `('
./multimedia.sh: line 25: `echo " Please enter your main username (your mainly u 'ed session login) ?"
root@192:/root#


Hope you (or someone) can help, again!

---

### Post by patrick295767 on 2006-04-27
[QUOTE=quincyjones]Hey Patrick,
Thanks so much for the reply, I wasn't expecting it from the author himself!
But, I don't know what I'm doing wrong, this is what happened in my terminal:
Hope you (or someone) can help, again![/QUOTE]
 
 I wrote it in Windows environment today ... and Windows Chars are there bugging our LInux life.... 
I am removing them !! 
type vi multimedia.sh
  and you'll see the result of windows ...! (even notepad2)
  
So, I am workign on it !!
Sorry, and in few minutes, taht will be okay !! to do : wget http ... bla bal
  
Regards, 

Patrick
=========
Ok, now, it's done : it's corrected !! :)
  
but since, 
I have problem with my intennet provider... so I cant make correction in re-uploading the script:
...

---

### Post by human on 2006-04-27
fixed it:

just remove parenthesis on the 25th line w/ gedit and it works!

---

### Post by patrick295767 on 2006-04-30
Thank you !! 
 
(Line 25 in my previous post fixed)
  
Installations after the installation configuration (you choose what you need) :
codecs, mplayer, totem ... xvidcap (record ur screen), realplayer, e17 enlightenment, mupen, skype, ...
-------------------
script multimedia.sh [here ]("http://patrick295767.sitesled.com/miniram/multimedia.sh")
version 1.2
  
to run the script:
> sudo bash                    # you'll have to enter the root password for installations....
cd /root
wget [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
chmod 777 /root/multimedia.sh                      # not necessary at all, but by precaution ...?
chmod +x /root/multimedia.sh
./multimedia.sh

---

### Post by j0eb0b on 2006-05-03
Patrick,

Thanks for the clear instructions and useful script.  Everything works for me up until when the script attempts to contact [Http://issaris.be](Http://issaris.be) and retrieve ffmpeg at which the script enters a timeout loop.  Looks like the site is up but maybe is suffering from congestion.  Should I just let the script run overnight to see if I can download this package?  

Is there an alternative location to go to?

Thanks,
joe

---

### Post by j0eb0b on 2006-05-03
Further to my earlier post, leave the script running and it will eventually get through.  The various video formats now seem to play.  next order of business is to figure out how to get some control over my Nvidia graphics card.

Patrick, thanks for helping the newbies

---

### Post by patrick295767 on 2006-05-04
[QUOTE=j0eb0b]Patrick,

Thanks for the clear instructions and useful script.  Everything works for me up until when the script attempts to contact [Http://issaris.be](Http://issaris.be) and retrieve ffmpeg at which the script enters a timeout loop.  Looks like the site is up but maybe is suffering from congestion.  Should I just let the script run overnight to see if I can download this package?  

Is there an alternative location to go to?

Thanks,
joe[/QUOTE]

Issaris location site down :(  Thank you for the information .... It seems I have to get the deb file, to make it into the script. 
If you have the deb file, plz send it to me  to my gmail address.

Greetings,

---

### Post by j0eb0b on 2006-05-04
Patrick,

I think I got everything last night.  as far as the deb file is concerned can you tell me the full file name and where you think I might find it?  If I have it i will certainly send it to you.    I am a rank amatuer with Unbuntu and am having some diffculty finding my way around the operating system.

Related to that, is there an unbuntu command reference posted anywhere?  i have one for Redhat but some of the commands in Ubuntu seem to be different.

Thanks,
Joe

---

### Post by patrick295767 on 2006-05-05
[QUOTE=j0eb0b]Patrick,

I think I got everything last night.  as far as the deb file is concerned can you tell me the full file name and where you think I might find it?  If I have it i will certainly send it to you.    I am a rank amatuer with Unbuntu and am having some diffculty finding my way around the operating system.

Related to that, is there an unbuntu command reference posted anywhere?  i have one for Redhat but some of the commands in Ubuntu seem to be different.

Thanks,
Joe[/QUOTE]
  
The file is : ffmpeg_0.20060410T134157_i386.deb
I looked a bit yesterday but couldnt find it in my folder...
I ll have to look somewhere else ... :-(
 
Normallly, the linux command are always similar with other linux distro.
(for standard cmd's)
  
I would recommand you this link  : [http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)
It's nice website to begin with good bases with command line & scripts ...
 
Thank you,
  
Greetz

---

### Post by patrick295767 on 2006-05-06
Now if you want to have engage (mac os x type bar with icons) your ur BREEZY :
  
Just type this : 
```
 sudo su
cd /root
wget http://patrick295767.sitesled.com/miniram/engage_only_install.sh
chmod +x engage_only_install.sh
./engage_only_install.sh
```

---

### Post by BobSongs on 2006-05-08
Patrick: thanks for the script. However the download doesn't appear to be working. Since it is a fairly short script and you've quoted the entire thing in previous posts, would you kindly quote the most current version again. This way I can paste it into a blank document and run the script.

Thanks!

Bob

---

### Post by patrick295767 on 2006-05-08
The link is there : 
[http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
 
   or I just copied it there also : 
[http://patrick295767.sitesled.com/fvwm/multimedia.sh](http://patrick295767.sitesled.com/fvwm/multimedia.sh)
  
I checked the sitesled webhosting and it appears to be down for the moment :-(
  Try later or PM me ...
(If you know better webhosting, plz do not hesitate to let me know and informed ! :-) )  

(Also please check at the beginning in the script that version 1.2 is written.)
  
Kind regards, 

Patrick

---

### Post by patrick295767 on 2006-05-09
[QUOTE=BobSongs]Patrick: thanks for the script. However the download doesn't appear to be working. Since it is a fairly short script and you've quoted the entire thing in previous posts, would you kindly quote the most current version again. This way I can paste it into a blank document and run the script.

Thanks!

Bob[/QUOTE]

The webhosting is now workign again :-) 

You can download the script !! (look my signature)
The link is there : 
[http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
  
Greetings !

Patrick

---

### Post by LCC on 2006-07-20
Patrick, i installed your script, but couldn`t open the web the mms a tv via internet, mms://80.84.129.169/telesur45; and I don`t understand much of Linux yet, but how does it work, your script allowed me to run things on Ubuntu 5.10 but I was using the 6.06 version and it the linux was downgraded to an early version, how do I "log back" to ubuntu 6.06, should I uninstall the script, if so how do I do it? 

Thanks

---

### Post by patrick295767 on 2006-07-20
> **LCC said:**
> Patrick, i installed your script, but couldn`t open the web the mms a tv via internet, mms://80.84.129.169/telesur45; and I don`t understand much of Linux yet, but how does it work, your script allowed me to run things on Ubuntu 5.10 but I was using the 6.06 version and it the linux was downgraded to an early version, how do I "log back" to ubuntu 6.06, should I uninstall the script, if so how do I do it? 

Thanks

with gedit, you can remove the line 82 (cp sources.list_extended02 "/etc/apt/sources.list")
(check quickly)
and it should work for dapper too ;
you can get a sources.list for dapper there:
[http://patrick295767.sitesled.com/miniram/sources.list-dapper](http://patrick295767.sitesled.com/miniram/sources.list-dapper)
  
Concerning the website, could you post the www address ?
  Thx
  
Enjoy, greetz

---

### Post by LCC on 2006-07-20
Patrick

[http://www.telesurtv.net/](http://www.telesurtv.net/) and it should be a link on the left upper coner

one more thing, when I open the programs like vlc or mplayer I cannot close them afterwards, why is tha, and how do i go back to the 6.06 ubuntu, because it seems like the whole system became 5.10, it might be a silly question, but I set Ubuntu up only 2 days ago

ok, deleted line 82, what do I do with the dapper list? and do I run the sript again or just save without line 82 ant it should work?
Thanks a lot.


LOL now I saw what might be wrong, I put the mms adress in the wrong place, but still I cannot get the video only the sound, and it doesn`t work for to long, I have to keep pressing play, any sugestion

---

### Post by patrick295767 on 2006-07-21
Hi, 

I reviewed the script that was only for Breezy and is now for Breezy and Dapper.
I hope that can help you for you dapper installation.
(updated first post, how to run the script)
 
(to be continued)
(script to be updated and next feature : engage exige )

---

### Post by LCC on 2006-07-21
Thanks a lot Patrick, perhaps you could add wine to the script. See ya!

---

### Post by kris2pe on 2006-07-21
How do I configure this? MY os still play gxine & its quite annoying coz it pop up another window!!!

---

### Post by patrick295767 on 2006-07-21
> **kris2pe said:**
> How do I configure this? MY os still play gxine & its quite annoying coz it pop up another window!!!

I will as soon as possible add thnigs to solve gxine and wine ... Maybe next week... (vacations time)
  
Greetings

---

### Post by LCC on 2006-07-22
Patrick, have a good time.
Do you know why I cannot get the video on the vcl, or should i use other program to play mms, especifically mms://80.84.129.169/telesur45  I think it is some kind of Windows codec, cause after the script I can hear the sound(not for too long) but no video at all. Thanks again

---

### Post by patrick295767 on 2006-08-01
> **LCC said:**
> Patrick, have a good time.
Do you know why I cannot get the video on the vcl, or should i use other program to play mms, especifically mms://80.84.129.169/telesur45  I think it is some kind of Windows codec, cause after the script I can hear the sound(not for too long) but no video at all. Thanks again

 
The codecs link was not available for downloading anymore.
 
I updated the script. 
Check :
```
ls /usr/lib/win32
```
To see if your codecs are there. 
  
Concerning the fact you dont like gxine, you can do:
	```
	apt-get -y remove totem-xine
	apt-get -y remove gxine
	apt-get -y remove gnome-xine
	apt-get -f -y install totem-gstreamer
	apt-get -f -y install mozilla-mplayer
	apt-get -f -y install 
```

I also prefer mozilla-mplayer for the firefox.

Greetz
(I'll try to update the script soon)

---

### Post by patrick295767 on 2006-08-01
> **LCC said:**
> Patrick

[http://www.telesurtv.net/](http://www.telesurtv.net/) and it should be a link on the left upper coner

one more thing, when I open the programs like vlc or mplayer I cannot close them afterwards, why is tha, and how do i go back to the 6.06 ubuntu, because it seems like the whole system became 5.10, it might be a silly question, but I set Ubuntu up only 2 days ago

ok, deleted line 82, what do I do with the dapper list? and do I run the sript again or just save without line 82 ant it should work?
Thanks a lot.


LOL now I saw what might be wrong, I put the mms adress in the wrong place, but still I cannot get the video only the sound, and it doesn`t work for to long, I have to keep pressing play, any sugestion

I tried your link 

I have the italian internet TV now ... I dont understand much.
[http://80.84.129.169/telesurdsl](http://80.84.129.169/telesurdsl)

(I think that was because of the fact that the downloading link was down. I updated the script.)

Enjoy Linux !!

---


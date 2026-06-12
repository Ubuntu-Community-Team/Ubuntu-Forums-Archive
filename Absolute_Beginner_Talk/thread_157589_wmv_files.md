---
title: "wmv files?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-09
where can i get a plugin for wmv files?

---

### Post by bitoiu on 2006-04-09
Hi,

[http://www.ubuntuforums.org/showthread.php?t=157000&highlight=wmv+files](http://www.ubuntuforums.org/showthread.php?t=157000&highlight=wmv+files)

This tipic let's you know how.

---

### Post by Bloch on 2006-04-09
mplayer plays wmv files on my system.
I installed it using automatix, which automatically adds all the codecs.  Download automatix (do a google search) and install it by going to the dircetory where the .deb file is and entering
dpkg -i ***.deb
wher you replace ***.deb with the name of the file.
Now automatic will be in your menu. When you run it you can tick off the goodies you want to install - most are not open source and so cannot be included in standard ubuntu.
A word of caution - I don't think it's a good idea to tick off everything in automatix and let it rip. Just choose a couple of things you really need. You can always go back later and install the others as and when you need them.  

VLC also can play many things that Totem won't. There are licencing issues here, and using these codecs without the right licence might be illegal in your country.

---

### Post by dylonium on 2006-04-09
Thanks!

---

### Post by patrick295767 on 2006-04-09
run this script and you'll be solved of lot of time consuming... 
  
```
#############" multimedia
## juke box
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
echo "zoom=yes" >> ~/.mplayer/config




######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin       #You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup
```


=========
to run teh script: 
```
sudo bash
apt-get -f -y install gedit 
echo " " > /root/myscriptydpdict.sh
gedit /root/myscriptydpdict.sh
```
  
u can then copy paste the script code...
then:

```
chmod +x  /root/myscriptydpdict.sh 
cd /root
./myscriptydpdict.sh 
```
  
Greetings

patrick

---

### Post by Sonlc on 2006-04-09
Sterling work Patrick, this was very useful.

---

### Post by patrick295767 on 2006-04-09
[QUOTE=Sonlc]Sterling work Patrick, this was very useful.[/QUOTE]
  
You're welcome !!

Pleasure to help linux community

ahh, you have to place the realplayer in the /root
if you inform me where i can have more than 50 Mb ftp account (like free.fr ...)
(uploadable via ftp gftp or kbear)
I can make it automatic the script
(my ftp is full ...)

Greetings, 

Patrick

---

### Post by rorschach on 2006-04-09
What repositories are you using - I have been trying to 'fix' my video and audio playback for a while now, and there are still a number of files I just can't see due to lack of codecs (specifically, I believe I am missing xvid, divx, and later wmv codecs, as well as the necessary libraries for DVD playback).

I've been battling this for around a week, and I was quite happy last weekend when I found the ubuntuguide.org, but, w32codecs, divx4linux and libdvdcss2 just don't seem to exist anymore in the repositories.

I haven't tried these packages:
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
so I'll give them a shot.

To be honest, though, it's getting frustrating installing one set of codecs, and finding that *some* of my music and videos will play, then trying to fix the others and breaking the other playback as a result. Then, when I try to undo what I have done, nothing works](*,) 

I'm just glad that the basic install of Breezy takes so little time.

Suggestions?

---

### Post by dylonium on 2006-04-09
Thanks patrick!

---

### Post by rorschach on 2006-04-09
OK, just got done going through and installing:
avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4
(libdvdnav4 and libdvdread3 were already at the newest versions)

I now have access to ... I would say 80% of my video files - but there are still a few that cause totem to freak out and pop up three "Internal GStreamer error: negotiation problem: file a bug" notices.

any other suggestions? what am I missing?

---

### Post by patrick295767 on 2006-04-10
Hi, 

I have never found any problems with reading videos... try my script, with the sources.list (in my signature)

  
That will certainly work. This script needs to be updated with new codecs, and so on, but I am very sorry, I have not much time for the moment to update it better ... 

Check it with the sources.list and let me informed which videos is not working!!
  
Greetings, 

Patrick

---

### Post by xyz on 2006-04-10
[QUOTE=Sonlc]Sterling work Patrick, this was very useful.[/QUOTE]

I second that Patrick...Golden work! Shit man, some people just know what they are doing.
I'm light years away but you are an encouragement.Thanks.

> Check it with the sources.list and let me informed which videos is not working!!
I'll be sure to let you know if need be!

One last thing!I'm a beginner but I guess something didn't work as it should have.Could you give me a hand as what I should do to resolve it.Thanks again.

> ./myscriptydpdict.sh: line 54: /home/th/.mplayer/config: No such file or directory
chmod: cannot access `/root/RealPlayer10GOLD.bin': No such file or directory
./myscriptydpdict.sh: line 64: ./RealPlayer10GOLD.bin: No such file or directorymv: cannot stat `mplayerplug-in-rm.xpt': No such file or directory
mv: cannot stat `mplayerplug-in-rm.xpt': No such file or directory

---

### Post by patrick295767 on 2006-04-10
Hi, 
  
For the moment:
  
Please find the version_02 working better:
To install, run this script:
(you then may reply to the questions & accept with Enter key...)
   
As soon as I have more time, I'll update it & with fixes too...
  
Let me know if you encounter problems.

Greetings, 

Patrick

The multimedia.sh script:
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
wget http://membres.lycos.fr/patrick295767/miniram/packages/realplayer10gold.bin
chmod 777 /root/realplayer10gold.bin
chmod +x /root/realplayer10gold.bin
./realplayer10gold.bin
#You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

###################### Installing xvidcap ############""
cd /root
wget http://membres.lycos.fr/patrick295767/miniram/packages/xvidcap_1.1.3-1_i386.deb
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
echo "** Patrick295767 **"


```
 
My /etc/apt/sources.list [here ]("http://membres.lycos.fr/patrick295767/miniram/data/sources-breezy.list")

---

### Post by rorschach on 2006-04-10
Okiedokey
First off - thank you Patrick - you've got a great resource here.
Second - when I run sudo apt-get update after grabbing your sources list, I get a couple of errors about GPG errors for [www.kadu.net](www.kadu.net) and ftp.nerim.net, which I think is causing some of the problems I mention below.

Now, when I ran the script (first version 1, then version 2 after I read your update) I ran into a number of errors.
I manually installed the w32codecs package when I saw the error below, however, I am unable to find most of the others when I try to manually sudo apt-get install <package> (ie libdivx4linux). Right now, there are a few avi files that won't play - at least two of which I am sure are divx encoded 
```

derrick@rorschach:~$ ./multimediascript
Please enter your main user of this computer ?
derrick
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mv: cannot stat `libtotem_mozilla.a': No such file or directory
mv: cannot stat `libtotem_mozilla.la': No such file or directory
mv: cannot stat `libtotem_mozilla.so': No such file or directory
mv: cannot stat `libtotem_mozilla.xpt': No such file or directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
Password:
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  w32codecs
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 13.2MB of archives.
After unpacking 31.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  w32codecs
E: There are problems and -y was used without --force-yes
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
Reading package lists... Done
Building dependency tree... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree... Done
sox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libavcodeccvs51 libavutilcvs49 libfaac0 libfaad2-0 libmp4v2-0 libxvidcore4
The following NEW packages will be installed:
  libavcodeccvs51 libavutilcvs49 libfaac0 libfaad2-0 libmp4v2-0 libxvidcore4
The following packages will be upgraded:
  ffmpeg
1 upgraded, 6 newly installed, 0 to remove and 4 not upgraded.
Need to get 2719kB of archives.
After unpacking 2679kB disk space will be freed.
WARNING: The following packages cannot be authenticated!
  libxvidcore4 libavutilcvs49 libavcodeccvs51 ffmpeg
E: There are problems and -y was used without --force-yes
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  aalib1 gcc-3.3-base libmjpegtools0 libquicktime0 libstdc++5 libsvga1 slang1
Suggested packages:
  toolame mpeg2dec a52dec
The following NEW packages will be installed:
  aalib1 gcc-3.3-base libquicktime0 libstdc++5 libsvga1 slang1
The following packages will be upgraded:
  libmjpegtools0 mjpegtools
2 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 1662kB/2108kB of archives.
After unpacking 3236kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libquicktime0 libmjpegtools0 mjpegtools
E: There are problems and -y was used without --force-yes
Reading package lists... Done
Building dependency tree... Done
vorbis-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
--18:30:54--  http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
           => `essential-20050412.tar.bz2'
Resolving www2.mplayerhq.hu... 193.225.187.202
Connecting to www2.mplayerhq.hu|193.225.187.202|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,349,060 (8.9M) [application/x-tar]
essential-20050412.tar.bz2: Permission denied

Cannot write to `essential-20050412.tar.bz2' (Permission denied).
mkdir: cannot create directory `/usr/lib/win32': Permission denied
tar: essential-20050412.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `essential-20050412/*': No such file or directory
/home/derrick/.mplayer/config       to get zoom=yes in .mplayer/config
./multimediascript: line 58: /home/derrick/.mplayer/config: No such file or directory
--18:30:55--  http://membres.lycos.fr/patrick295767/miniram/packages/realplayer10gold.bin
           => `realplayer10gold.bin'
Resolving membres.lycos.fr... 212.78.204.20
Connecting to membres.lycos.fr|212.78.204.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,789,348 (5.5M) [application/octet-stream]
realplayer10gold.bin: Permission denied

Cannot write to `realplayer10gold.bin' (Permission denied).
chmod: cannot access `/root/realplayer10gold.bin': No such file or directory
chmod: cannot access `/root/realplayer10gold.bin': No such file or directory
./multimediascript: line 72: ./realplayer10gold.bin: No such file or directory
mv: cannot stat `mplayerplug-in-rm.so': No such file or directory
mv: cannot stat `mplayerplug-in-rm.xpt': No such file or directory
--18:30:56--  http://membres.lycos.fr/patrick295767/miniram/packages/xvidcap_1.1.3-1_i386.deb
           => `xvidcap_1.1.3-1_i386.deb'
Resolving membres.lycos.fr... 212.78.204.20
Connecting to membres.lycos.fr|212.78.204.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,501,062 (1.4M) [text/plain]
xvidcap_1.1.3-1_i386.deb: Permission denied

Cannot write to `xvidcap_1.1.3-1_i386.deb' (Permission denied).
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
dpkg: requested operation requires superuser privilege
./multimediascript: line 91: /root/xvid.sh: Permission denied
chmod: cannot access `/root/xvid.sh': No such file or directory
chmod: cannot access `/root/xvid.sh': No such file or directory
./multimediascript: line 94: /root/xvid.sh: Permission denied
if you wanna make a avi file of ur screen, run sh /root/xvid.sh
u can move this little script, where you want & need
** Greetz' **
** Patrick295767 **

```

---

### Post by patrick295767 on 2006-04-11
sthg is wrong when u run the script: 
1/ reboot the pc   (to be sure there is no process apt or kill them ...  ps -A  ... kill -9 )
2/ do : 
sudo bash

or 

sudo ./script.sh

Greetz

---

### Post by patrick295767 on 2006-04-11
a bit more time now : 
i can read : 
> derrick@rorschach:~[COLOR="Black"][SIZE="4"][SIZE="6"]$ [/SIZE][/SIZE][/COLOR]./multimediascript
Please enter your main user of this computer ?
derrick
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to loc
  
This is meaning you are not root.
  
try then : 
```
sudo ./multimediascript
```
  
or 
  
```
su
```

or 
  
```
su bash
 ./multimediascript
```
  
The target is thaat you are root
soo then you'll see the $ is replaced by a # (when u are root)
  
you can also type : 
```
whoami 
```

Greetings

---

### Post by rorschach on 2006-04-12
So sorry for the delayed response.
I got a bit frustrated the other day and tried a different distro, now I'm back.

Anyway - upon clean install, I tried your script after updating the sources list - yes, this does work **much** better when it is run via sudo.
It seems that everything is now working - Thank you!

I think this should be appended or updated to a how-to - Does Ubuntu have a Wiki? or is the old ubuntuguide for 5.04 the only resource besides the forums?

---

### Post by aktiwers on 2006-04-12
Thanks! This worked out painless!

Thanks alot :cool:

---

### Post by patrick295767 on 2006-04-14
[QUOTE=rorschach]So sorry for the delayed response.
I got a bit frustrated the other day and tried a different distro, now I'm back.

Anyway - upon clean install, I tried your script after updating the sources list - yes, this does work **much** better when it is run via sudo.
It seems that everything is now working - Thank you!

I think this should be appended or updated to a how-to - Does Ubuntu have a Wiki? or is the old ubuntuguide for 5.04 the only resource besides the forums?[/QUOTE]
  
I am glad it worked !!
:-) 

and realplayer is also installed, that's very cool too !
did you see you can record ur screen with xvidcap too..? 
  
Greetz 

Pat'

---

### Post by patrick295767 on 2006-04-18
Multimedia.sh vers.0.3
-------------
New webhosting & thus script re-working :-) : 
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

### Post by patrick295767 on 2006-04-20
--- 
script deleted

---

### Post by rez on 2006-04-24
Awesome work - just what I've been looking for.  Feel the <3 :-D

---

### Post by quincyjones on 2006-04-27
Hi, I ran Patrick'scode but I had some trouble. This is the code from my terminal:

[PHP]clint@192:~$ sudo bash
Password:
root@192:~# apt-get -f -y install gedit
Reading package lists... Done
Building dependency tree... Done
gedit is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
root@192:~# echo " " > /root/myscriptydpdict.sh
root@192:~# gedit /root/myscriptydpdict.sh
root@192:~# chmod +x  /root/myscriptydpdict.sh
root@192:~# cd /root
root@192:/root# ./myscriptydpdict.sh
Reading package lists... Done
Building dependency tree... Done
xmms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libakode2 libtunepimp-bin libtunepimp2c2
Suggested packages:
  khelpcenter libtunepimp2-dev
The following NEW packages will be installed:
  juk libakode2 libtunepimp-bin libtunepimp2c2
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 1090kB of archives.
After unpacking 2994kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libtunepimp2c2 0.3.0-2ub untu7 [183kB]
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy/main libakode2 2.0-0ubuntu0breezy1 [ 94.7kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main libtunepimp-bin 0.3.0-2u buntu7 [21.5kB]
Get:4 [http://kubuntu.org](http://kubuntu.org) breezy/main juk 4:3.5.1-0ubuntu0breezy1 [79 1kB]
Fetched 1090kB in 2s (505kB/s)

Preconfiguring packages ...
Selecting previously deselected package libakode2.
(Reading database ... 74945 files and directories currently installe d.)
Unpacking libakode2 (from .../libakode2_2.0-0ubuntu0breezy1_i386.deb ) ...
Selecting previously deselected package libtunepimp2c2.
Unpacking libtunepimp2c2 (from .../libtunepimp2c2_0.3.0-2ubuntu7_i38 6.deb) ...
Selecting previously deselected package libtunepimp-bin.
Unpacking libtunepimp-bin (from .../libtunepimp-bin_0.3.0-2ubuntu7_i 386.deb) ...
Selecting previously deselected package juk.
Unpacking juk (from .../juk_4%3a3.5.1-0ubuntu0breezy1_i386.deb) ...
Setting up libakode2 (2.0-0ubuntu0breezy1) ...

Setting up libtunepimp2c2 (0.3.0-2ubuntu7) ...

Setting up libtunepimp-bin (0.3.0-2ubuntu7) ...
Setting up juk (3.5.1-0ubuntu0breezy1) ...

mv: cannot stat `libtotem_mozilla.a': No such file or directory
mv: cannot stat `libtotem_mozilla.la': No such file or directory
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
gstreamer0.8-lame is already the newest version.
gstreamer0.8-ffmpeg is already the newest version.
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
lame is already the newest version.
sox is already the newest version.
ffmpeg is already the newest version.
mjpegtools is already the newest version.
vorbis-tools is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins-multiverse is already the newest version.
The following extra packages will be installed:
  libavifile-0.7
Suggested packages:
  avifile-player avifile-utils avifile-mjpeg-plugin
  avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin
The following NEW packages will be installed:
  avifile-divx-plugin avifile-mad-plugin libavifile-0.7
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 1691kB of archives.
After unpacking 4592kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe libavifile-0.7 1:0.7 .43.20050224-1ubuntu6 [1625kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse avifile-divx-plugi n 1:0.7.43.20050224-1ubuntu6 [960B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe avifile-mad-plugin 1 :0.7.43.20050224-1ubuntu6 [65.5kB]
Fetched 1691kB in 3s (495kB/s)

Preconfiguring packages ...
Selecting previously deselected package libavifile-0.7.
(Reading database ... 75021 files and directories currently installe d.)
Unpacking libavifile-0.7 (from .../libavifile-0.7_1%3a0.7.43.2005022 4-1ubuntu6_i386.deb) ...
Selecting previously deselected package avifile-divx-plugin.
Unpacking avifile-divx-plugin (from .../avifile-divx-plugin_1%3a0.7. 43.20050224-1ubuntu6_i386.deb) ...
Selecting previously deselected package avifile-mad-plugin.
Unpacking avifile-mad-plugin (from .../avifile-mad-plugin_1%3a0.7.43 .20050224-1ubuntu6_i386.deb) ...
Setting up libavifile-0.7 (0.7.43.20050224-1ubuntu6) ...

Setting up avifile-divx-plugin (0.7.43.20050224-1ubuntu6) ...
Setting up avifile-mad-plugin (0.7.43.20050224-1ubuntu6) ...
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin
0 upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 108kB of archives.
After unpacking 360kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe avifile-mjpeg-plugin  1:0.7.43.20050224-1ubuntu6 [10.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe avifile-vorbis-plugi n 1:0.7.43.20050224-1ubuntu6 [7064B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse avifile-win32-plug in 1:0.7.43.20050224-1ubuntu6 [89.8kB]
Fetched 108kB in 0s (168kB/s)

Preconfiguring packages ...
Selecting previously deselected package avifile-mjpeg-plugin.
(Reading database ... 75072 files and directories currently installe d.)
Unpacking avifile-mjpeg-plugin (from .../avifile-mjpeg-plugin_1%3a0. 7.43.20050224-1ubuntu6_i386.deb) ...
Selecting previously deselected package avifile-vorbis-plugin.
Unpacking avifile-vorbis-plugin (from .../avifile-vorbis-plugin_1%3a 0.7.43.20050224-1ubuntu6_i386.deb) ...
Selecting previously deselected package avifile-win32-plugin.
Unpacking avifile-win32-plugin (from .../avifile-win32-plugin_1%3a0. 7.43.20050224-1ubuntu6_i386.deb) ...
Setting up avifile-mjpeg-plugin (0.7.43.20050224-1ubuntu6) ...
Setting up avifile-vorbis-plugin (0.7.43.20050224-1ubuntu6) ...
Setting up avifile-win32-plugin (0.7.43.20050224-1ubuntu6) ...
Reading package lists... Done
Building dependency tree... Done
libdvdnav4 is already the newest version.
libdvdread3 is already the newest version.
The following NEW packages will be installed:
  avifile-xvid-plugin libdvdplay0
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 25.8kB of archives.
After unpacking 152kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse avifile-xvid-plugi n 1:0.7.43.20050224-1ubuntu6 [914B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe libdvdplay0 1.0.1-6 [24.9kB]
Fetched 25.8kB in 0s (53.4kB/s)

Preconfiguring packages ...
Selecting previously deselected package avifile-xvid-plugin.
(Reading database ... 75078 files and directories currently installe d.)
Unpacking avifile-xvid-plugin (from .../avifile-xvid-plugin_1%3a0.7. 43.20050224-1ubuntu6_i386.deb) ...
Selecting previously deselected package libdvdplay0.
Unpacking libdvdplay0 (from .../libdvdplay0_1.0.1-6_i386.deb) ...
Setting up avifile-xvid-plugin (0.7.43.20050224-1ubuntu6) ...
Setting up libdvdplay0 (1.0.1-6) ...

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gst-register-0.8
Reading package lists... Done
Building dependency tree... Done
mplayer-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
mplayer-fonts is already the newest version.
flashplayer-mozilla is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
Reading package lists... Done
Building dependency tree... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
sox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
mjpegtools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
vorbis-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
acroread is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
flashplayer-mozilla is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
mozilla-acroread is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package mplayerplug-in is a virtual package provided by:
  mozilla-mplayer 3.17-1ubuntu1~breezy1
You should explicitly select one to install.
E: Package mplayerplug-in has no installation candidate
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  totem-xine-firefox-plugin
The following packages will be REMOVED:
  totem-gstreamer totem-gstreamer-firefox-plugin
The following NEW packages will be installed:
  totem-xine
0 upgraded, 1 newly installed, 2 to remove and 4 not upgraded.
Need to get 0B/837kB of archives.
After unpacking 24.6kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 75089 files and directories currently installe d.)
Removing totem-gstreamer-firefox-plugin ...
dpkg: totem-gstreamer: dependency problems, but removing anyway as y ou request:
 totem depends on totem-gstreamer (= 1.2.1-0ubuntu1~breezy1) | totem -xine (= 1.2.1-0ubuntu1~breezy1); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
Removing totem-gstreamer ...
Selecting previously deselected package totem-xine.
(Reading database ... 74970 files and directories currently installe d.)
Unpacking totem-xine (from .../totem-xine_1.2.1-0ubuntu1~breezy1_i38 6.deb) ...
Setting up totem-xine (1.2.1-0ubuntu1~breezy1) ...

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  m4
Recommended packages:
  mozilla-browser mozilla-browser-snapshot mozilla-browser-cvs
  mozilla-firefox
The following packages will be REMOVED:
  mozilla-acroread
The following NEW packages will be installed:
  m4 mozplugger
0 upgraded, 2 newly installed, 1 to remove and 4 not upgraded.
Need to get 45.4kB/155kB of archives.
After unpacking 754kB disk space will be freed.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe mozplugger 1.7.1-1 [ 45.4kB]
Fetched 45.4kB in 0s (87.0kB/s)

Preconfiguring packages ...
(Reading database ... 75089 files and directories currently installe d.)
Removing mozilla-acroread ...
Selecting previously deselected package m4.
(Reading database ... 75074 files and directories currently installe d.)
Unpacking m4 (from .../archives/m4_1.4.3-1_i386.deb) ...
Selecting previously deselected package mozplugger.
Unpacking mozplugger (from .../mozplugger_1.7.1-1_i386.deb) ...
Setting up m4 (1.4.3-1) ...

Setting up mozplugger (1.7.1-1) ...
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libflash0c2
The following NEW packages will be installed:
  libflash-mozplugin libflash0c2
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 77.4kB of archives.
After unpacking 348kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe libflash0c2 0.4.13-1 ubuntu1 [64.5kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe libflash-mozplugin 0 .4.13-1ubuntu1 [12.9kB]
Fetched 77.4kB in 0s (129kB/s)

Preconfiguring packages ...
Selecting previously deselected package libflash0c2.
(Reading database ... 75128 files and directories currently installe d.)
Unpacking libflash0c2 (from .../libflash0c2_0.4.13-1ubuntu1_i386.deb ) ...
Selecting previously deselected package libflash-mozplugin.
Unpacking libflash-mozplugin (from .../libflash-mozplugin_0.4.13-1ub untu1_i386.deb) ...
Setting up libflash0c2 (0.4.13-1ubuntu1) ...

Setting up libflash-mozplugin (0.4.13-1ubuntu1) ...

Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer-mad
Reading package lists... Done
Building dependency tree... Done
beep-media-player is already the newest version.
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
--20:34:37--  [http://www2.mplayerhq.hu/MPlayer/releases/codecs/essen](http://www2.mplayerhq.hu/MPlayer/releases/codecs/essen) tial-20050412.tar.bz2
           => `essential-20050412.tar.bz2'
Resolving www2.mplayerhq.hu... 193.225.187.202
Connecting to www2.mplayerhq.hu|193.225.187.202|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9,349,060 (8.9M) [application/x-tar]

100%[========================>] 9,349,060    606.67K/s    ETA 00:00

20:34:57 (468.71 KB/s) - `essential-20050412.tar.bz2' saved [9349060 /9349060]

mkdir: cannot create directory `/usr/lib/win32': File exists
chmod: cannot access `/root/RealPlayer10GOLD.bin': No such file or d irectory
./myscriptydpdict.sh: line 63: ./RealPlayer10GOLD.bin: No such file or directory
mv: cannot stat `mplayerplug-in-rm.xpt': No such file or directory
mv: cannot stat `mplayerplug-in-rm.xpt': No such file or directory
root@192:/root#[/PHP]


Does anyone know how I can fix this?
The reason I am trying to use this code is that I can't watch Quicktime 7 movies and also when I watch WMA via firefox, it's kind of jittery and jerky!
Realplayer is (or was) fine.
So any other ideas would also be much appreciated.

---

### Post by idjut on 2006-05-01
Amazing scripts Patrick! Thanks a lot. Gonna try that E17 script when I have time for sure. :KS :KS

---

### Post by MegaBill on 2006-05-02
Wow, I'm glad you took some time to make this. It should help solve some of the playback problems I've been having.  One quick question, is Totem supposed to be able to play MP3's after installing everything from this script?  I use xmms regardless, but I'm just curious.

Now I just need to find a .mov codec/plugin for Totem.

Thanks!

---

### Post by patrick295767 on 2006-05-02
Thank you !!
  
Both totem & xmms are working after this script.  

I made a version 1.2 of the script...  And made some corrections in it & improved it... 
as soon as I have more time, I"ll  add the QT codec...
 script [here]("http://patrick295767.sitesled.com/miniram/multimedia.sh")
  
 Greetings, 

Patrick
===
to run the script:
> sudo bash                    # you'll have to enter the root password for installations....
cd /root
wget [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh)
chmod 777 /root/multimedia.sh                      # not necessary at all, but by precaution ...?
chmod +x /root/multimedia.sh
./multimedia.sh

---

### Post by tstreit on 2006-05-03
Awesome script Patrick, I am new Ubuntu and not very good scripts but you sure made it easy!  Thanks again!

---

### Post by patrick295767 on 2006-05-03
[QUOTE=tstreit]Awesome script Patrick, I am new Ubuntu and not very good scripts but you sure made it easy!  Thanks again![/QUOTE]
  
Anytime !! Glad it helped you. 
If you find some programs/apps or some deb's that can be useful or you'd like to add, plz do not hesitate to let me know :) 
  
Patrick

---

### Post by tstreit on 2006-05-04
Patrick,

I don't know if this is because I am behind a firewall or what, but this part of the script does not work right for me.  I think the site has been taken down.  Just wanted to let you know so that you may update your script, or let me know if it is on my side.

Cheers!

```
cd /root/miniram
wget http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb
dpkg -i install ffmpeg_0.20060410T134157_i386.deb
```

---

### Post by patrick295767 on 2006-05-04
I'll try to look today about this site down ... I should have a backup somewhere I guess ... 
  
Nice Video link about programs & apps : [http://mdk.fit2.bur.st/Video.phtml](http://mdk.fit2.bur.st/Video.phtml)

Greetz

---

### Post by auxiliary.chipmunk on 2007-08-26
> **rorschach said:**
> What repositories are you using - I have been trying to 'fix' my video and audio playback for a while now, and there are still a number of files I just can't see due to lack of codecs (specifically, I believe I am missing xvid, divx, and later wmv codecs, as well as the necessary libraries for DVD playback).

I've been battling this for around a week, and I was quite happy last weekend when I found the ubuntuguide.org, but, w32codecs, divx4linux and libdvdcss2 just don't seem to exist anymore in the repositories.

I haven't tried these packages:
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
so I'll give them a shot.

To be honest, though, it's getting frustrating installing one set of codecs, and finding that *some* of my music and videos will play, then trying to fix the others and breaking the other playback as a result. Then, when I try to undo what I have done, nothing works](*,) 

I'm just glad that the basic install of Breezy takes so little time.

Suggestions?
Hi Rorschach,

Try Medibuntu, 

[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

This is where all the restricted software has been placed, things like WMV support and DVD playback. The names have remaned very similar (if not the same) but they have been put here so that Ubuntu is legal and free out of the box.

Please check that it is legal for you to install before proceeding and if this note is passed on ensure to note this disclamer to who you pass the infomation to.

---

### Post by patrick295767 on 2007-08-26
did you try the w32codecs ([http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)) ?
 
wmv have some key encription for some of them

---

### Post by Jasethemuss on 2008-04-21
Hi Patrick, 

Do you have a link for the latest version of your script? The link [http://patrick295767.sitesled.com/miniram/multimedia.sh](http://patrick295767.sitesled.com/miniram/multimedia.sh) seems to be dead. Or should I theoretically still be ok using the old script?

Thanks!

---


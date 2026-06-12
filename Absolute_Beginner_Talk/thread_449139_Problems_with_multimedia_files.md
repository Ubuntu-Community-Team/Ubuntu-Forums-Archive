---
title: "Problems with multimedia files"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by blue-gum on 2007-05-19
I have been reading the forum for days on this but unable to resolve my problems.  

I apparently do not have appropriate plugins for audio files that I wish to either listen to or download (particularly from ABC Radio National, here in Australia).   When I click 'listen now' (to radio) on internet, window opens prompting download of RealPlayer (for Windows).

Second example of the problem:   Mplayer plugin 'embedded video for mozilla' opened, displayed the file name - which was xxx.rm and then displayed 'stopped'.

Third example:   When I click 'download audio' from radio National website, I get an error msg "Totem could not play 'fd://0' "

I have followed advice from other posts re multimedia and have checked Add/Remove Sound & Video Applications and find I have
gstreamer extra plugins
gstreamer ffmpeg video plugin 

but I don't have
"GStreamer plugins for aac, xvid, mpeg2, faad"
"GStreamer plugins for mms, wavpack, quicktime, musepack"
and don't know where to find or how to install these.   

In Add/Remove - Other I don't have Ubuntu restricted extras.
Error msg above indicates totem plugins are also involved in my failures!

 Advice would be appreciated.

---

### Post by tchoklat on 2007-05-19
Hi neighbour. Go to getautomatix.com and install automatix2. You can use it to domwload all the multimedia codecs you need!

---

### Post by bobplano on 2007-05-19
also if you have the medibuntu repositories enabled you should be able to find the codec you need in synaptic

---

### Post by fenian on 2007-05-20
Download and install the w32 codecs with these commands...
> 
wgethttp://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

also download and install these...

> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

for streaming audio/video with mplayer do this...
> 
sudo apt-get install mozilla-mplayer

to play encrypted dvds do this...

> wget [http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb

---

### Post by blue-gum on 2007-05-20
Thanks for responses.

I updated medibuntu repositories by editing /etc/apt/sources.list following sticky on multimedia.  Still could not see what I wanted in synaptic.

Then ran code given by Fenian.   First 'quote' failed, 2nd and 3rd okay, 4th had Error 404.  Will try this again later.

The details of failed code:  
hxx@hxxs:~$ wgethttp://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb
bash: wgethttp://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb: No such file or directory
hxx@hxxs:~$ sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb
dpkg: error processing w32codecs_20061022-0medibuntu1+build1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20061022-0medibuntu1+build1_i386.deb

Note that I edited Fiesty to Edgy as I thought this might be the reason for the failure of install.
Can you see reason for 'no such file or directory'?  I don't know what to do next - somewhat out of my depth here!!

---

### Post by bobplano on 2007-05-20
there needs to be a space:
wget [http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
just an honest typo

---

### Post by Bachstelze on 2007-05-20
> **blue-gum said:**
> 
hxx@hxxs:~$ wgethttp://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb


Try

```
wget http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb
```

---

### Post by blue-gum on 2007-05-20
Hey... a typo.   I feel bad because even a newbie should have been able to see that!  Thanks for the help.

Anyway, ran with the correction and got Error 404, medibuntu not responding, so I will try again later.

---

### Post by blue-gum on 2007-05-20
I can get to medibuntu site via Firefox but not through wget command.   I am assuming that the error msg is that the Medibuntu server is not responding.  Is my thinking on this correct?

hxx@hxxs:~$  wget [http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
--15:24:29--  [http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb)
           => `w32codecs_20061022-0medibuntu1+build1_i386.deb'
Resolving medibuntu.sos-sts.com... 88.191.13.100, 88.191.26.58, 88.191.30.43, ...
Connecting to medibuntu.sos-sts.com|88.191.13.100|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:24:30 ERROR 404: Not Found.

---

### Post by Bachstelze on 2007-05-20
No, it's just the address of the file that is bad. Which Ubuntu version are you running ?

---

### Post by AlanD on 2007-05-20
In all honesty, automatix 2 makes things much easier than the medibuntu repositories still, in my opinion. [www.getautomatix.com](www.getautomatix.com) has a link to the install deb, all you need to do is download and install the package by double clicking. It then shows up in system tools. Just check off all the codec stuff and it takes care of the rest, including the codecs needed for dvd, mpeg2, etc. The .rm file is a real player file, and automatix also allows for easy installation of realplayer along with a variety of other things like VLC :)

---

### Post by Bachstelze on 2007-05-20
Yep, it makes it much easier to break your system, that's for sure !

---

### Post by blue-gum on 2007-05-20
Ubuntu 6.10

---

### Post by Bachstelze on 2007-05-20
Here you go :

```

cd
wget http://medibuntu.sos-sts.com/repo/pool/edgy/non-free/i386/w32codecs_20061022-0medibuntu1_i386.deb
sudo dpkg -i w32codecs_20061022-0medibuntu1_i386.deb
```

---

### Post by blue-gum on 2007-05-20
I installed Real Player today.   I still cannot download the audio files from the website.  I already have Automatix installed, but did not know what it was for.  I looked at Codec stuff there and found  Sun Java JRE and Swiftfox plugins listed.   I googled Swiftfox and found out that it is a browser.   I don't want another browser, currently using Firefox.   Not sure that I want JRE yet. 

Still thinking that Medibuntu files are what I am needing but something not right in the wget code?

---

### Post by blue-gum on 2007-05-20
HymnToLife.  Many thanks.

Used your code to download medibuntu and install.   It was big download on a slow connection.  Terminal confirmed 'setup w32 codecs'.  Then checked Add/Remove.  Ran it's update.   Got an error msg:
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I don't know what this means.   
I still can't download audio files - still getting same error msg on download attempt: 
"Totem could not play 'fd://0' "

Is there something else I should be doing following the install?
Any thoughts?

---

### Post by Bachstelze on 2007-05-20
Nope, the problem you get in Totem does not seem codec-related. It seems like Totem is trying to play from a floppy disk... Can't help you with that, I'm afraid.

---


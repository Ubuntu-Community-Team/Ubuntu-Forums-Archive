---
title: "newbie cannot play video or flash"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2007-10-28
Hi.
I'm a complete newbie but have been quite pleased with my progress so far, I've installed 7.10 64x in a dual boot with Vista 64x.
 
I can now listen to music and view images from Vista in Ubuntu, browse the web, send messages to my friends etc but am stuck with anything involving a moving image.

I have enabled mplayer, totem, vlc, gxine and xine but when I stick a dvd into the pc I get "an error occurred could not read from this resource".
This is from totem but it is a similar message from all of them- I think gxine suggested I need plugins but when I followed the link I got to a BBC News Error 404 Page Not Found.

When I browse with Stumbleupon 90%+ of flash video clips don't play and some of them appear corrupted with jagged boxes across the small screens. A small number of them play ok.

I'm obviously missing something fundamental from the outset here. Can anyone help?

Thanks, John Williams

---

### Post by sayuki288 on 2007-10-28
sudo install flashplugin-nonfree

---

### Post by Qwerty_ on 2007-10-28
To watch DVD's you have to install some special software.

[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd)

---

### Post by limac on 2007-10-28
Watching clips from youtube and stuff should be fulfilled by installing the flashplugin-nonfree.

And also what browser do u use?

If it's firefox, if you go to sites such as youtube and try to play a video and it'll probably say something like "You have to install the latest flashplayer" and from that link you can do it.

Hope that helps!

---

### Post by johnwillyums on 2007-10-28
Hi. Thanks for the input.

I looked through installed stuff in synaptic and I seem to have all the lib instructions except libdvdcss2.

I ran a search fort it in synaptics and it appeared in the left hand column but I could not find a way to install it.

Also followed the link suggested by Qwerty and tried typing 
"sudo/usr/share/doc/libdvdread3/install-css.sh" into the terminal and this gave "no such command".

Any further suggestions.

Also have clicked on "install plugin" suggestions on youtube etc and they don't do anything.

Thanks, John Williams

---

### Post by johnwillyums on 2007-10-28
I'm still not getting anywhere.
Ubuntu really appeals to me on a philosophical basis but so far all I can do is browse, send emails amd access my music and pics  from  Vista.
I just tried to print something and, although my Canon printer is recognised it won't print a document.
I can't watch videos and I can't watch flash clips on Digg or Metacafe etc. If I try to download plugins it just doesn't happen.
I don't want to give up but this is not much use to me as I keep having to go back to Vista for most simple things.
John Williams

---

### Post by pashashome on 2007-10-28
Hi John,
Lets work on getting movies and such to work first. Try installing the ubuntu-restricted-extras package. To do this go to System/Administration/Synaptic Package Manager. Click the search button and search for ubuntu-restricted-extras. Install that and see if the movies you would like to watch are watchable.  Hope that helps.

---

### Post by daimaru on 2007-10-28
to get dvds running you have to add medibuntu repository to your apt sources.list
just go to medibuntu.org and follow the howto for adding repository after that you can install dvd support realplayer skype acrobat reader etc by following the instructions on medibuntu.

---

### Post by philinux on 2007-10-28
Have you checked through this sticky for installing multimedia.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by johnwillyums on 2007-10-28
> **pashashome said:**
> Hi John,
Lets work on getting movies and such to work first. Try installing the ubuntu-restricted-extras package. To do this go to System/Administration/Synaptic Package Manager. Click the search button and search for ubuntu-restricted-extras. Install that and see if the movies you would like to watch are watchable.  Hope that helps.

Thanks but I may have a bigger problem. When I opened synaptic I got this:
:
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Not sure what this means. As I said I'm a complete newbie.

John Williams

---

### Post by johnwillyums on 2007-10-28
I just tried to open Adept Manager following the thread that Philinux suggested and got this:

Could Not Open Cache-Adept-Manager

The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in Terminal and see if it helps resolve the problem.

So I opened Terminal and typed apt-setup and pressed enter and I got-
 bash:apt-setup:command not found

I'm deeply stuck here folks.
John Williams

---

### Post by johnwillyums on 2007-10-28
Now I've got an update problem. Update Manager tells me the following:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the "update-manager" package and include the following message:
"E: Malformed line 52 in source list/etc/apt/sources.list (dist parse), The list of sources could not be read"

This is the same message I get if I try and open Synaptic.

What now?
John Williams

---

### Post by philinux on 2007-10-28
> **johnwillyums said:**
> Thanks but I may have a bigger problem. When I opened synaptic I got this:
:
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Not sure what this means. As I said I'm a complete newbie.

John Williams

open a terminal and type gksudo gedit /etc/apt/sources.list 

Select Edit prefs and check line numbers. got to line 52 and post what it says.

It's probably a typo.

Attached is my sources list mind you I'm on 386 version.

---

### Post by eapache on 2007-10-28
All of these install and update problems are being caused by a corrupt file (I'd check the cd before using it for any more installs). This file (/etc/apt/sources.list) is what Ubuntu uses to check the list of programs available.

Please browse to that file and copy/paste the contents into a post so we can figure out how it got corrupted and how to fix it.

---

### Post by johnwillyums on 2007-10-28
Philinux.

Thanks for replying . I did as you suggested but it turned into a disaster. 
In an attempt to cut and paste lines 52 and 53 into this reply I've accidently deleted them!

Help.
John Williams

---

### Post by philinux on 2007-10-28
seeing as it had an error the simplest thing is this just pick your systemfrom the drop downs.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by johnwillyums on 2007-10-28
Ok hopefully this is my sources list-

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as togksudo gedit /etc/apt/sources.list

## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



deb [http://mirror3.ubuntulinux.nl/dapper-seveas](http://mirror3.ubuntulinux.nl/dapper-seveas) freenx

As you can see there are 2 lines missing just before the final one.

Philinux, I tried what you suggested and got a very short list which looks nothing like this one at all.
Assuming it's the right one what should I do with it?

Thanks for the help, John Williams

---

### Post by eapache on 2007-10-28
Just replace what is currently there with the new list. The reason it looks different is because it has different lines beginning with # which are just comments and not actually important.

---

### Post by johnwillyums on 2007-10-28
Ok. This is the new list from source-o-matic:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse


Firstly how do I get rid of the current list and do I just copy and paste this lot into the window?

Thanks, John

---

### Post by eapache on 2007-10-28
To get rid of the current list, just put your cursor in the window, ctrl-A to select all, then backspace. Then you can just copy/paste the newly generated list in and save.

When that is done, open synaptic (System>Administration>Synaptic Package Manager) and click on reload at the top.

---

### Post by SpinningAround on 2007-10-28
:)

---

### Post by johnwillyums on 2007-10-28
Great. That seems to have worked. At least my update package would now download.
Instead of having 52 lines in my source list I now have 30.

Do I now have to go back and enable repositories etc to get my dvd and flash  working?
Should I now follow the instructions in your (Philinux) earlier link?

Thanks for your tremendous support, John Williams

---

### Post by oldos2er on 2007-10-28
You still need to enable the Medibuntu repositories if you want libdvdcss (and other goodies). See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by johnwillyums on 2007-10-28
Hello again. I seem to have added medibuntu repository and enabled all the necessary  things.
I now have libdvdcss showing in synaptic as installed.

However I still can't play dvds in totem or any of the other players I've installed.

I just tried a pop concert dvd that was free with a newspaper today. I can hear the music but if I go to menu and try to play the dvd I get a cannot read from this source message with a request to install plugins.

I've looked at the link suggested which is Gstream or something and cannot find a way to download the plugins either from them or sourceforge. 
Also they all seem to be for 32 bit architecture.

Whilst I seem to be back on course after this afternoons disasters ie I can now open synaptic etc.
I'm no further forward in my attempt to play dvds in Ubuntu.

i have to go to bed shortly. Thanks for all your help. I shall try again tomorrow night so please make any suggestions you can to help me get this os operating

John Williams

PS I just went into Digg and cannot get any of their flash videos to play either. Basically I haven't achieved anything for a few hours work. Quite depressing.

---

### Post by johnwillyums on 2007-11-01
Well I think I've tried everything that has been suggested and then some.
I installed Automatix and this seems to have enabled me to play videos and I can now view flash videos on YouTube as well.

However I cannot find a way to view flash on Metacafe, Colege Humour, Revision3 etc.

Why is this? I've enabled/installed everything in synaptic that was suggested and there all there but still no result.

This certainly spoils the fun on Stumbleupon or Digg so I have to go back to Vista 64x.
I should'nt have to do that, it's a pity because I'd hoped to gradually phase out Vista.

John Williams

---

### Post by philinux on 2007-11-01
Some sites require cookies enabled.

What about looking at ```
about:plugins
```

post what you've got in there

---

### Post by johnwillyums on 2007-11-01
Thanks for that but I'm not sure how to access that
.
Do you mean type" code:about:plugins" into terminal?

I imagine not because if I do that I get "command not found"

Please elaborate, John


Don't know the smiley got there, supposed to be a colon

---

### Post by philinux on 2007-11-01
you type it into the address bar of firefox

---

### Post by eapache on 2007-11-01
Type it in the firefox address bar (no http or www or anything).

---

### Post by johnwillyums on 2007-11-01
Ok. Thanks to you both-This is what I have-

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.7 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.7.0_00 	IcedTea 	class,jar 	Yes
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6c Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.40

    File name: mplayerplug-in.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes


As yoy can see everything here seems to be enabled. 

Something crucial missing?

Cheers, John Williams

---

### Post by eapache on 2007-11-01
You're using gnash, which is an open-source version of flash. Unfortunately, it doesn't quite support the latest flash version, so newer sites won't work (while older sites will).```
sudo apt-get install flash-nonfree
```to get the full, copyright-protected version.

---

### Post by philinux on 2007-11-01
I think you go two many the vlc plugin and mplayer will cause a conflict so that no embedded video will play. Choose one and uninstall the other.

---

### Post by dreamsR4living on 2007-11-01
I don't know if it was mentioned before, because I don't have the time to read the whole post. But the most plugins like flash and java don't work because you are on a AMD 64 computer (like myself). For example Adobe did write a free flash plugin for i386, but not for AMD 64. In the following posts you can read more about installing programs and plugins on AMD 64;

[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)
[http://ubuntuforums.org/showthread.php?t=185303](http://ubuntuforums.org/showthread.php?t=185303)

If you like to install the Firefox browser which fully supports Flash and Java, you should read this thread; 

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

You should follow the guide about installing the 32 bit firefox on AMD 64. First install Firefox. Somewhere in the bottom of the Thread you should find how to make your 32 bit firefox your default browser. After that install the Flash and Java plugins. In the guide you will be asked to download the Flash and Java files, which you are going to install by command line. Make sure you update the new versions of the files after you pasted a command from the guide into the terminal.

This guide helped me a lot.

To make your AMD 64 Ubuntu work is a lot harder than the i386 version, but I hope Ubuntu will be working for you soon, so Vista don't have to be in your mind anymore :)

---

### Post by johnwillyums on 2007-11-01
Hello.

I uninstalled mplayer  through synaptic and then attempted to install the flash-nonfree plugin by typing

"sudo apt-get install flash-nonfree" into terminal and I got-

"[sudo] password for johnwillyums:"

So I put in my password but it did not display. I then got-

Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package flash-nonfree:
johnwillyums@johnwillyums-desktop:~$

So that's where I'm at. Will try browsing and see if removing mplayer has achieved anything.

Cheers, John

Edit nope, still only plays YouTube

---

### Post by Maestro23 on 2007-11-01
> **johnwillyums said:**
> Hello.

I uninstalled mplayer  through synaptic and then attempted to install the flash-nonfree plugin by typing

"sudo apt-get install flash-nonfree" into terminal and I got-

"[sudo] password for johnwillyums:"

So I put in my password but it did not display. I then got-

Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package flash-nonfree:
johnwillyums@johnwillyums-desktop:~$

So that's where I'm at. Will try browsing and see if removing mplayer has achieved anything.

Cheers, John

Edit nope, still only plays YouTube

Make sure all your Repositories are enabled: Universe/Multiverse, 3rd-Party, etc...  Then try the install again.

System>>Admin>>Software Sources (Check your sources)

Correct apt-get command:

> sudo apt-get install flashplugin-nonfree

---

### Post by eapache on 2007-11-01
Sorry, I forgot the plugin bit, use Maestro's command.

---

### Post by johnwillyums on 2007-11-01
Ok. I did that and got the following-

johnwillyums@johnwillyums-desktop:~$  sudo apt-get install flashplugin-nonfree
[sudo] password for johnwillyums:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
johnwillyums@johnwillyums-desktop:~$ 

I then tried some flash clips on Digg. Still won't play.

I also followed dreamsR4living@s suggestion and installed a 32 bit version of Firefox but this doesn't play flash either.
Perhaps I am misunderstanding the howto he suggested and need some plugins for that.

I just wish it would work.

John

---

### Post by johnwillyums on 2007-11-01
Have to sleep now. will try again tomorrow. thanks to you all for the support and I hope I get it all going in the end.
 haven't even tried my DVB-TD stick yet or downloading RAW files from my camera.

I get the feeling this is going to be a long process, John

---

### Post by Scratches on 2007-11-01
> **johnwillyums said:**
> Ok. Thanks to you both-This is what I have-

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
GCJ Web Browser Plugin (using IcedTea) 1.4

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes


Should he get rid of the above, then do:

```
sudo aptitude install sun-java6-jre
```

then make a symbolic link in firefox's plugin directory to /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so ?

Tom

---

### Post by johnwillyums on 2007-11-03
Can anyone help me to play flash in either my 64x Firefox or the 32 bit version.

I've tried everything suggested with the 64x version but am unsure where to look for plugins for the 32 bit one.

I appreciate Scratches input but I don't really understand it.

Thanks, John Williams

---

### Post by johnwillyums on 2007-11-03
Hi folks.

I seem to have solved the problem by installing swiftweasel via automatix.
I can now browse and view flash inserts from all sites.
Can't think why no one suggested this.
Is this a safe procedure?

Cheers, John Williams

---

### Post by johnwillyums on 2007-11-25
Hello again all,

I've been happily using Swiftweasel 32 bit for the last few weeks and it plays flash fine.

I installed the new 64 bit version a few days ago and it won't play flash at all.

I'm happy to carry on using the 32 bit version but surely a brand new 64bit  application should be able to do the business in every way?

Strange stuff this 64 bit computing.

John

---

### Post by daflame on 2007-11-27
> **johnwillyums said:**
> Hello again all,

I've been happily using Swiftweasel 32 bit for the last few weeks and it plays flash fine.

I installed the new 64 bit version a few days ago and it won't play flash at all.

I'm happy to carry on using the 32 bit version but surely a brand new 64bit  application should be able to do the business in every way?

Strange stuff this 64 bit computing.

John

If you want to resolve your 64bit woes I would suggest doing a search for nspluginwrapper.  It wraps certain 32bit plugins in a layer to make them 64bit compatible.  It takes a couple minutes to set up, but I believe Gutsy has this in its multiverse repo. I can't remember the commands offhand, but I think there are only a couple steps.

---

### Post by johnwillyums on 2007-11-28
Hi Daflame,thanks for your input. I checked in synaptic and I already have nspluginwrapper enabled.
As I say I can get flash on my 32 bit Swiftweasel but not on my 64 bit install. 
It works really well in all other ways and I think it has a slight speed advantage over the 32 bit version.
Therefore I think it's pity that a brand new 64 bit browser is limited in this way.
Or am I doing something wrong?
Cheers, John

---

### Post by daflame on 2007-11-28
> **johnwillyums said:**
> Hi Daflame,thanks for your input. I checked in synaptic and I already have nspluginwrapper enabled.
As I say I can get flash on my 32 bit Swiftweasel but not on my 64 bit install. 
It works really well in all other ways and I think it has a slight speed advantage over the 32 bit version.
Therefore I think it's pity that a brand new 64 bit browser is limited in this way.
Or am I doing something wrong?
Cheers, John

You may have nspluginwrapper installed, but it may not do anything for you until you execute the
command at the prompt to create the symlinks necessary to wrap the 32bit plugins.
For example:
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

that will setup the plugin to be wrapped by nspluginwrapper.
If it works ok, it will return to the prompt without any messages.

in the folder .mozilla/plugins/ in our /home we can see the file &#8220;npwrapper.libflashplayer.so&#8221;, created from the previous command.

Copy it into the folder /usr/lib/mozilla/plugins/
and create a link (or copy it) into the folder /usr/lib/mozilla-firefox/plugins/

Now, it should work, so try going on [http://www.youtube.com/](http://www.youtube.com/) and watch a video.
If you right click the video it should bring up a context menu with the last item being "About Adobe Flash Player 9..."
otherwise Flash is not installed properly.  As for Java it always crashes on me when I install Sun Java 6 and you can't
wrap a 32bit library for java sadly.  It's good for me that I rarely use it (since most everything is Flash now).

(These installation instructions are a modified excerpt of: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727))

---

### Post by johnwillyums on 2007-11-29
Hi Daflame, thanks for your suggestions.

I have just been browsing sites using Stumblupon with my 64x Swiftweasel install.

I find that Youtube stuff will play but other flash inserts on regular sites won't.
Also sites such as Metacafe, Collegehumor, Dailymotion, Liveleak and b3ta won't show flash.

What happens is I either get a message saying "buffering" or "loading" but nothing happens or I just get a blank box where the video is supposed to play.

I don't get any prompts to download a plugin.
On one of these sites I thought I'd try the command you suggested anyway and I got this:

johnwillyums@johnwillyums-desktop:~$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin
johnwillyums@johnwillyums-desktop:~$

So I get youtube but nothing else. Also some sites with mouse-activated animations won't work either.

Not sure where I go from here. Thanks for listening, John

---

### Post by daflame on 2007-11-30
> **johnwillyums said:**
> Hi Daflame, thanks for your suggestions.

I have just been browsing sites using Stumblupon with my 64x Swiftweasel install.

I find that Youtube stuff will play but other flash inserts on regular sites won't.
Also sites such as Metacafe, Collegehumor, Dailymotion, Liveleak and b3ta won't show flash.

What happens is I either get a message saying "buffering" or "loading" but nothing happens or I just get a blank box where the video is supposed to play.

I don't get any prompts to download a plugin.
On one of these sites I thought I'd try the command you suggested anyway and I got this:

johnwillyums@johnwillyums-desktop:~$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin
johnwillyums@johnwillyums-desktop:~$

So I get youtube but nothing else. Also some sites with mouse-activated animations won't work either.

Not sure where I go from here. Thanks for listening, John

Make sure you uninstall Gnash and any other flash plugins.  These plugins may override the adobe flash player plugin.

```
sudo apt-get remove libflash-mozplugin
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove flashplugin-nonfree
sudo apt-get intall flashplugin-nonfree
```

That sequence should fix it.  If you still have troubles please reply with the output of:
```
ls -l /etc/alternatives/mozilla-flashplugin
ls -l /usr/lib/mozilla/plugins
```

This problem occurs when Gnash or any other flash plugin is used prior to installing flashplugin-nonfree.  If this doesn't work I'll give you the code for manually setting /etc/alternatives/mozilla-flashplugin.  This seems to be the way it's expected to be done now.

---

### Post by johnwillyums on 2007-12-01
Hello daflame.

I did as you suggested and it all seemed to go as planned. Lots of things removed. Re-installed flashplugin- nonfree.
I then tried browsing a few sites including metacafe and several others.
They don't play but youtube still does.

So I copied and pasted your second two lines into terminal and got this:

johnwillyums@johnwillyums-desktop:~$ ls -l /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 32 2007-12-01 19:57 /etc/alternatives/mozilla-flashplugin -> /usr/lib/gnash/libgnashplugin.so
johnwillyums@johnwillyums-desktop:~$ ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2007-10-23 07:14 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 26 2007-10-26 02:11 gxineplugin.so -> ../../gxine/gxineplugin.so
lrwxrwxrwx 1 root root 39 2007-10-27 17:49 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
johnwillyums@johnwillyums-desktop:~$ 

In the text the following are bright pale blue:


 /etc/alternatives/mozilla-flashplugin

 gxineplugin.so

libjavaplugin.so 

 /etc/alternatives/mozilla-flashplugin

Thanks a lot for your continued support, any ideas where I go from here?

Cheers, John

---

### Post by SunnyRabbiera on 2007-12-01
yeh if you have a 64bit system this kind of thing can happen.
the flash issue might be more from those sites though as the flash on linux is different then the one in windows
are you still having DVD issues by the way?
if its stuff you got off your DVD camera or something it might help if you finalize your disks if you have not done so...
I have no idea on how to work a DVD camera so you will have to check your instruction manual but normally if you dont finalize your disks they wont play in any player unless the dvd camcorder and the player you have are made by the same company and were made in the same year.

---

### Post by johnwillyums on 2007-12-01
SunnyRabiera, thanks for your reply.

I got over the dvd problem. I think with xine. I'm not sure anymore because I've only had this machine for a few weeks and am dual booting 64x Vista and 64x Ubuntu 7.10. It's all been a bit of a blur as I'm trying to learn how to use 2 different systems at once.

Anyway, it wasn't home made dvd that was the problem (I don't have a dvd camera either). Just dvd in general. Rented movies, copies etc.

As I say that problem is now fixed.

I have several problems:   a WinTV-NOVA-TD dual tuner that won't work, a Canon i9950 that won't print and this problem with flash in my browser.

I have the Firefox install that came with the 7.10 package, a 32x Firefox install, a 32x Swiftweasel install and a 64x Swiftweasel install.

I can play flash in the 32x installs. (youtube seems to work in all of them 64/32x)

Back in Vista I can only play flash in Firefox 32x or Opera 9.5 beta.

I'm pretty much a newbie in every way so I thought I'd try and deal with things one by one.

A guy ( I think) called wieman01 really tried hard to help me with the dvb stick in a thread called:

HOWTO: Kaffeine & (Hauppauge) WinTV-Nova-T Stick [Feisty Fawn]
which is in forums under Hardware and Laptops

As I say he tried all sorts of things to get my stick working but ended up by suggesting that I start again in the 64x threads (rather than Absolute Beginners)
I haven't had the heart for that yet so I thought I'd try to get the flash problem fixed first but so far I'm not getting anywhere.

Any suggestions would be welcome, John

---

### Post by daflame on 2007-12-04
> **johnwillyums said:**
> Hello daflame.

I did as you suggested and it all seemed to go as planned. Lots of things removed. Re-installed flashplugin- nonfree.
I then tried browsing a few sites including metacafe and several others.
They don't play but youtube still does.

So I copied and pasted your second two lines into terminal and got this:

johnwillyums@johnwillyums-desktop:~$ ls -l /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 32 2007-12-01 19:57 /etc/alternatives/mozilla-flashplugin -> /usr/lib/gnash/libgnashplugin.so
johnwillyums@johnwillyums-desktop:~$ ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2007-10-23 07:14 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 26 2007-10-26 02:11 gxineplugin.so -> ../../gxine/gxineplugin.so
lrwxrwxrwx 1 root root 39 2007-10-27 17:49 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
johnwillyums@johnwillyums-desktop:~$ 

In the text the following are bright pale blue:


 /etc/alternatives/mozilla-flashplugin

 gxineplugin.so

libjavaplugin.so 

 /etc/alternatives/mozilla-flashplugin

Thanks a lot for your continued support, any ideas where I go from here?

Cheers, John

Here is the problem:
> ohnwillyums@johnwillyums-desktop:~$ ls -l /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 32 2007-12-01 19:57 /etc/alternatives/mozilla-flashplugin -> /usr/lib/gnash/libgnashplugin.so

Flash is still tied to gnash, when it should be using flashplugin-nonfree.

First open up your package manager and do a search for gnash.  Remove all the packages related to that.  Then execute the following:
```
sudo dpkg-reconfigure flashplugin-nonfree
```
Follow the prompts.  If that doesn't solve it try the following:
```
sudo rm -f /etc/alternatives/mozilla-flashplugin
sudo ln -s /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so /etc/alternatives/mozilla-flashplugin
```

---

### Post by johnwillyums on 2007-12-04
Hey daflame!

That worked. I uninstalled a couple of gnash items and pasted your reconfigure plugin command and it seems to have worked. 
I just looked at some video sites and they are working well so thank you very much for your patience and well done.
I've now got to go to a couple of other threads and tell them that my problem is solved, one in the 64x forum and also reply to Ubuntu helpline where a couple of people have been trying to help.
They didn't seem to have heard of Swiftweasel and were suggesting I should get rid of it as that was my problem.
Well I'm glad they were wrong because I think it's great and now it's fully functional for my needs.
Just another couple of important issues and half a dozen little ones and I'll have very little reason to go into Vista.

I'm amazed. Both by how good Ubuntu is and how supportive and helpful people are. Makes me feel good and you too I hope so thanks once again, John Williams

---

### Post by daflame on 2007-12-05
> **johnwillyums said:**
> Hey daflame!

That worked. I uninstalled a couple of gnash items and pasted your reconfigure plugin command and it seems to have worked. 
I just looked at some video sites and they are working well so thank you very much for your patience and well done.
I've now got to go to a couple of other threads and tell them that my problem is solved, one in the 64x forum and also reply to Ubuntu helpline where a couple of people have been trying to help.
They didn't seem to have heard of Swiftweasel and were suggesting I should get rid of it as that was my problem.
Well I'm glad they were wrong because I think it's great and now it's fully functional for my needs.
Just another couple of important issues and half a dozen little ones and I'll have very little reason to go into Vista.

I'm amazed. Both by how good Ubuntu is and how supportive and helpful people are. Makes me feel good and you too I hope so thanks once again, John Williams

Hurray for another problem solved and I must thank you for your patience with Ubuntu.  It is getting better every day, but there are still a few wrinkles to sort out.  I'm just glad to have people like yourself who are willing to stick it out.

Now after all this hassle, in retrospect, I should have pointed you to the galternatives package.  This give you a graphical interface with the options to choose which package does what.  It would allow you to choose flashplugin-nonfree over gnash and it's a whole lot friendlier than the console.  Sorry about that.

---


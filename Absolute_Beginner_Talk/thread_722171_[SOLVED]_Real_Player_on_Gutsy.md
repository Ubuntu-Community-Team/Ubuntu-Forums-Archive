---
title: "[SOLVED] Real Player on Gutsy"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-12
hello everyone,

does anyone know what am I supposed to do toI install Real Player on Gutsy? I've got Helix, but it doesn't seem to be helpful at all when I try to play BBC videos - plz notice that (I think, might be wrong) - I'm probably ok with codecs and the like (I can play virtually anything else including youtube and online videos from other sources except for BBC), but of course you never know.

Many thanks!

---

### Post by jonnywombat on 2008-03-12
Hi mate...

what vids you trying to watch?? and are you in the uk??

A lot of content is currently drm'd and will not play on linux (well anything that ain't windows really).. tho the government has stepped in and told the beeb they must be platform neutral in a couple of year or so...

Non drm'd content will play by selecting the windows media player option.. assuming you have the mplayer plugin installed in firefox (and u are in the uk)


Jonny

---

### Post by manishtech on 2008-03-12
Get the real player from
[http://fileforum.betanews.com/detail/RealPlayer_for_Linux/959031648/2](http://fileforum.betanews.com/detail/RealPlayer_for_Linux/959031648/2)

Its a bin file, hope you know how to install. Install it as root user. Better use sudo :)
first give it execute permissions and then use **sudo ./realplayer**

---

### Post by jan quark on 2008-03-12
> Get the real player from
[http://fileforum.betanews.com/detail...ux/959031648/2](http://fileforum.betanews.com/detail...ux/959031648/2)

is there a difference between these versions ?
[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by Arkenzor on 2008-03-12
The difference is that last time I checked, the official RealPlayer site link didn't even work...

But here's an "official" link through the Helix community mirror: [https://helixcommunity.org/projects/player/files/download/2478](https://helixcommunity.org/projects/player/files/download/2478)

---

### Post by mikeyphi on 2008-03-12
> **al.adab said:**
> hello everyone,

does anyone know what am I supposed to do toI install Real Player on Gutsy? I've got Helix, but it doesn't seem to be helpful at all when I try to play BBC videos - plz notice that (I think, might be wrong) - I'm probably ok with codecs and the like (I can play virtually anything else including youtube and online videos from other sources except for BBC), but of course you never know.

Many thanks!

Download from here: [https://player.helixcommunity.org/2004/downloads/index.html](https://player.helixcommunity.org/2004/downloads/index.html)

take the RealPlayer 10.0.0 Gold  linux/x86 "installer" file - save to desktop.

Look at the read me file on the same site - it describes how to install RealPlayer10

Ask again if you don't understand the instructions!

---

### Post by geekcliff on 2008-03-12
> **al.adab said:**
> hello everyone,

does anyone know what am I supposed to do toI install Real Player on Gutsy? I've got Helix, but it doesn't seem to be helpful at all when I try to play BBC videos - plz notice that (I think, might be wrong) - I'm probably ok with codecs and the like (I can play virtually anything else including youtube and online videos from other sources except for BBC), but of course you never know.

Many thanks!

Get the deb file from here: [http://archive.canonical.com/ubuntu/pool/partner/r/realplay/](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/) the one at the bottom of the list then just double click it.:guitar:

---

### Post by manishtech on 2008-03-12
> **jan quark said:**
> is there a difference between these versions ?
[http://www.real.com/linux](http://www.real.com/linux)

This is the reason why I gave an alternate link, hope you got the reply above. I too installed RealPlayer from the unofficial site. But it works properly.
Though I still dont think getting bins and using it for installing is a right way. It defeats the whole purpose of having a packaging system.

---

### Post by ibizatunes on 2008-03-12
Real player wont play your bbc stuff in linux! U need to get VLC and VLC mozilla plug in,
go to system > admin > repo > search for "VLC" and "vlc mozilla" install that, and the bbc will play!
If u want video u need adobe flash install as well

---

### Post by manishtech on 2008-03-12
> **geekcliff said:**
> Get the deb file from here: [http://archive.canonical.com/ubuntu/pool/partner/r/realplay/](http://archive.canonical.com/ubuntu/pool/partner/r/realplay/) the one at the bottom of the list then just double click it.:guitar:

Thanks man! I didnt know that it was in the partner repos....
I got Opera by enabling the partner repos. Didnt knew about real to be in it... :-P

---

### Post by manishtech on 2008-03-12
> **ibizatunes said:**
> Real player wont play your bbc stuff in linux! U need to get VLC and VLC mozilla plug in,
go to system > admin > repo > search for "VLC" and "vlc mozilla" install that, and the bbc will play!
If u want video u need adobe flash install as well

Adobe Flash plugin? Is it required?
There was a problem with Flash plugin of firefox earlier " Some MD5 checksum mismatch"
I sorted it out by installing **Flash 8 Update 3** plugin instead of **Flash 8 Update 4** which was buggy...




Manish

---

### Post by geekcliff on 2008-03-12
> **manishtech said:**
> Thanks man! I didnt know that it was in the partner repos....
I got Opera by enabling the partner repos. Didnt knew about real to be in it... :-P
It Dont show up in synaptic , even with partner repo enabled, so i just go there and steal it.:lolflag:

---

### Post by geekcliff on 2008-03-12
> **ibizatunes said:**
> Real player wont play your bbc stuff in linux! U need to get VLC and VLC mozilla plug in,
go to system > admin > repo > search for "VLC" and "vlc mozilla" install that, and the bbc will play!
If u want video u need adobe flash install as well

Iwatch click with real player, thats bbc?:popcorn:

---

### Post by ubuntu-freak on 2008-03-12
> **ibizatunes said:**
> Real player wont play your bbc stuff in linux! U need to get VLC and VLC mozilla plug in,
go to system > admin > repo > search for "VLC" and "vlc mozilla" install that, and the bbc will play!
If u want video u need adobe flash install as well

 
Wrong! Maybe you haven't set things up properly.
 
My how-to includes intructions for installing RealPlayer, and a fix incase it stutters and freezes while playing. You should remove any packages that will clash with it's plugin also. It's all explained in part 2 of my how-to, there's a link to it in my sig.
 
Nathan

---

### Post by ibizatunes on 2008-03-12
BBC player uses flash, because the iPlayer has DRM protection, and is only windoze compaitiable! Flash is the only way to watch programs....

---

### Post by geekcliff on 2008-03-12
> **ibizatunes said:**
> BBC player uses flash, because the iPlayer has DRM protection, and is only windoze compaitiable! Flash is the only way to watch programs....

Sorry, didn't know you were talking about bbc iplayer, the program i watch uses win media player or real player. :lolflag:

---

### Post by ubuntu-freak on 2008-03-12
> **ibizatunes said:**
> BBC player uses flash, because the iPlayer has DRM protection, and is only windoze compaitiable! Flash is the only way to watch programs....

 
It's still incorrect to say RealPlayer doesn't work. You didn't mention iPlayer in your original post. I use Adobe Flash, MPlayer and RealPlayer to watch/listen to content on the BBC.
 
Nathan

---

### Post by ibizatunes on 2008-03-12
the iplayer is going to do all of the bbc stuff sortly.... read it on the site somewhere..... so u need flash

---

### Post by jis on 2008-03-13
> **geekcliff said:**
> It Dont show up in synaptic , even with partner repo enabled, so i just go there and steal it.:lolflag:

There are realplay packages meant for Feisty, Edgy and Dapper. Is there any alternative package for Gutsy?

---

### Post by manishtech on 2008-03-13
I checked, its not in repos in Gutsy, its there in Dapper, check this link
[http://packages.ubuntu.com/dapper/net/realplayer](http://packages.ubuntu.com/dapper/net/realplayer)

And please make a note of the first paragraph of that link, it says
> RealNetworks does not allow redistribution of their software. Therefore, this package requires the user to fetch the real player archive separately from their web site. When you install this package you will be guided through that process.

So why worry to install from the repos? Install it explicitly...

---

### Post by geekcliff on 2008-03-13
> **jis said:**
> There are realplay packages meant for Feisty, Edgy and Dapper. Is there any alternative package for Gutsy?

The feisty one is the one to use, it works ok and it is the latest version. there wasn't one for gutsy.

---

### Post by jis on 2008-03-13
> **manishtech said:**
> 
So why worry to install from the repos? Install it explicitly...

Maybe removing the package is easier if you use a deb file / repository.

---

### Post by jis on 2008-03-13
> **geekcliff said:**
> The feisty one is the one to use, it works ok and it is the latest version. there wasn't one for gutsy.

I installed it, and it plays, but there is no sound.

---

### Post by ubuntu-freak on 2008-03-13
> **jis said:**
> I installed it, and it plays, but there is no sound.

This is a quote from the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), could be your problem;

**1.** If your RealPlayer's playback is terrible (mine was) you have to do some manual editing. First of all, install "alsa-oss" (added to "Essential" in Part 1). Now you need to copy and paste these commands into the Terminal and do some manual editing;

**gksudo gedit /usr/bin/realplay**

Find the line "echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\"" and underneath "fi" paste these two lines;

[B]LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD[/B]

Save and close. Also, open RealPlayer's preferences and go to "Transport" and select "Use specified transport". Then go into the two configure options beneath that and untick everything except "http". You can also select your connection speed in preferences and tell RealPlayer not to send connection info back to real.com.

It's worth checking out the rest of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) as well.

Nathan

---

### Post by jis on 2008-03-13
My package management system has been odd lately. It does not find alsa-oss package, for example. The output of 'sudo apt-get update' is like this:
> Get:1 [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy Release.gpg [191B]
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/main Translation-en_US                                             
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/restricted Translation-en_US                                       
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                                         
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/web Translation-en_US                                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Get:3 [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release.gpg [189B]                
Ign [http://www.claws-mail.org](http://www.claws-mail.org) ./ Translation-en_US                   
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/universe Translation-en_US         
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/multiverse Translation-en_US       
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Get:5 [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates Release.gpg [191B]       
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/main Translation-en_US                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                      
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release                             
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/restricted Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/web Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/universe Translation-en_US 
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/multiverse Translation-en_US
Get:6 [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports Release.gpg [191B]     
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/main Translation-en_US   
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/universe Translation-en_US
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Packages                            
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/multiverse Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/web Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Get:7 [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security Release.gpg [191B]
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/main Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/web Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/universe Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/multiverse Translation-en_US
Get:8 [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed Release.gpg [191B]
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/restricted Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/main Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/multiverse Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/universe Translation-en_US
Ign [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/web Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy Release
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates Release                      
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports Release
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security Release
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed Release
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/main Sources    
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/restricted Sources
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/main Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy/restricted Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/main Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-updates/restricted Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/main Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/restricted Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/universe Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-backports/multiverse Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/main Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-security/restricted Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/restricted Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/main Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/multiverse Packages
Hit [http://www.nic.funet.fi](http://www.nic.funet.fi) gutsy-proposed/universe Packages
Fetched 8B in 2s (3B/s)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy/Release](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-updates/Release](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-backports/Release](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-security/Release](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-proposed/Release](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/dists/gutsy-proposed/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Do you mean the two lines you mentioned should be pasted between "echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\"" and the "fi"?

How do you tell RealPlayer not to send connection info back to real.com?

---

### Post by ubuntu-freak on 2008-03-13
I said underneath "fi". 
 
Connection info option is in preferences, surely you can see it there?
 
Are you running the 64-Bit Ubuntu version? Someone else said alsa-oss was missing in 64-Bit. If that's not it, you may have a currupt apt list. There is a command in part 1 of my how-to which should fix that, in the "did you have errors" section. 
 
If you're running a 64-Bit system, you're better off using the MPlayer plugin to stream Real Media, or you could install the 32-Bit Ubuntu version (I would do the latter). 
 
Nathan

---

### Post by jis on 2008-03-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/202170](https://bugs.launchpad.net/ubuntu/+bug/202170) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I suppose you mean "Supply connection-quality data to RealServers" item at Internet tab.

I am running 32bit version of (X)ubuntu 7.10.There was noting in /var/lib/apt/lists/partial/.

> $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Still I can not install mplayer by " sudo apt-get install mplayer":
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages


---

### Post by ubuntu-freak on 2008-03-14
Ouch! Did you try this command as well?

**sudo dpkg --configure -a**

Might be worth posting a new thread stating that you have packages missing and you think something is currupt or broken somewhere.

Nathan

---

### Post by jis on 2008-03-14
I tried the command now, but it didn't help.I opened a new [thread]("http://ubuntuforums.org/showthread.php?p=4514402"). Thanks for help.

---

### Post by jis on 2008-03-15
> **reassuringlyoffensive said:**
> This is a quote from the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833), could be your problem;

**1.** If your RealPlayer's playback is terrible (mine was) you have to do some manual editing. First of all, install "alsa-oss" (added to "Essential" in Part 1). Now you need to copy and paste these commands into the Terminal and do some manual editing;

**gksudo gedit /usr/bin/realplay**

Find the line "echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\"" and underneath "fi" paste these two lines;

[B]LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD[/B]

Save and close. Also, open RealPlayer's preferences and go to "Transport" and select "Use specified transport". Then go into the two configure options beneath that and untick everything except "http". You can also select your connection speed in preferences and tell RealPlayer not to send connection info back to real.com.


I overcame the problems with my repositories. Now I could install alsa-oss. It helped together with editing /usr/bin/realplay like you told. Thanks. I wonder why realplay does not dependend or recommend alsa-oss. I didn't change the "Transport" preferences. What kind of benefit do you get by changing them?

---

### Post by jamaas on 2008-03-15
Thanks All,

Stumped here, realplayer keeps telling me that it cannot connect to the audio device and that it may be busy .... but it isn't.

Coincidentally, xmms works fine and plays mp3s just fine, just can not connect  to bbc using realplayer ?

Suggestions and thanks

Jim

---

### Post by ubuntu-freak on 2008-03-15
> **jamaas said:**
> Thanks All,

Stumped here, realplayer keeps telling me that it cannot connect to the audio device and that it may be busy .... but it isn't.

Coincidentally, xmms works fine and plays mp3s just fine, just can not connect  to bbc using realplayer ?

Suggestions and thanks

Jim

 
Did you install alsa-oss and try the fix I posted?
 
Nathan

---

### Post by ubuntu-freak on 2008-03-15
> **jis said:**
> I overcame the problems with my repositories. Now I could install alsa-oss. It helped together with editing /usr/bin/realplay like you told. Thanks. I wonder why realplay does not dependend or recommend alsa-oss. I didn't change the "Transport" preferences. What kind of benefit do you get by changing them?

 
Only a few have that issue with RealPlayer. Tis a bit strange though, and some think alsa-oss should be installed by default.
 
The transport settings helped some with odd errors, but if you'r not having anymore issues you shouldn't worry about it.
 
Nathan

---


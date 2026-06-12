---
title: "Help with Multimedia Files which are on a Networked Drive"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2007-01-21
[FONT="Comic Sans MS"][COLOR="Indigo"][/COLOR][/FONT]I need help with my multimedia files which are located on a networked drive.  I can view the files but I cannot execute them.  Audio as well as Video files just buffer for about 3 seconds then nothing happens.  It does not seem to matter which audio/video player that is used.  As long as I can direct the player to the networked folder.  If I move to one of the local drives they work seamlessly.  Any suggestions?  I have a big library of media and would like to make play lists.

Thanx,

           Hillbilly

---

### Post by jvc26 on 2007-01-21
Have you installed the necessary codecs to open the files? It may be that you don't have the media codecs - Ubuntu doesnt come with proprietary codecs, such as those for .mp3s and the like. To sort them out, either:

Install automatix 2, and select the bits which are relevant to your codecs:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

Or go here and install most of the codecs separately:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Il

---

### Post by medley on 2007-01-21
> **Hillbilly Tilley said:**
> [FONT="Comic Sans MS"][COLOR="Indigo"][/COLOR][/FONT]I need help with my multimedia files which are located on a networked drive.  I can view the files but I cannot execute them.  Audio as well as Video files just buffer for about 3 seconds then nothing happens.  It does not seem to matter which audio/video player that is used.  As long as I can direct the player to the networked folder.  If I move to one of the local drives they work seamlessly.  Any suggestions?  I have a big library of media and would like to make play lists.

Thanx,

           Hillbilly

This isn't a codec problem; this is a bug/limitation in samba I believe. The fact that you can copy them locally and then play them means that your codecs are OK. I have the same problem, and I've read somewhere that this is a bug that is on the record. Sucks, but that's the joys of open source.

---

### Post by Hillbilly Tilley on 2007-01-21
I believe that medley is on to something.  When I check the permissions on the files when they are on the networked drive the "allow executing file as program" toggle is off when I check the permissions on a local file the toggle is on.  I have tried to change the permissions on the files on the network but I get the error cannot change permissions.

Hillbilly

---

### Post by Efros on 2007-01-21
I had this problem when I first installed Ubuntu Edgy,  I followed this guide [http://www.ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb](http://www.ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb)

---


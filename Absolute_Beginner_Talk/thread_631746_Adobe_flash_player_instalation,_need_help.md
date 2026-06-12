---
title: "Adobe flash player instalation, need help"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by justinclark on 2007-12-04
I need the newer version of flash player and these are the install instructions they give [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

How do I know which one to download and how do I navigate through the terminal?  I have Gutsy if that helps.  Thanks

---

### Post by ZipoTe on 2007-12-04
Hi!!

You have to download de .tar.gz file and extract it. Just follow the instructions, they're clear :popcorn:

---

### Post by PeterJS on 2007-12-04
> **justinclark said:**
> I need the newer version of flash player and these are the install instructions they give [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

How do I know which one to download and how do I navigate through the terminal?  I have Gutsy if that helps.  Thanks


Just ignore those, that's the hard way.

The easy way is to first enable the universe and multiverse repositories as shown here:
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Then open Synaptic and install *flashplugin-nonfree* and you're good to go.

---

### Post by ZipoTe on 2007-12-04
By the way, as you requested:

> How do I know which one to download and how do I navigate through the terminal?

This may help you. The basics about terminal are in this post:
[http://ubuntuforums.org/showthread.php?t=618806&highlight=useful+linux+commands]("http://ubuntuforums.org/showthread.php?t=618806&highlight=useful+linux+commands")

---

### Post by justinclark on 2007-12-04
According to Synaptic I have flashplugin nonfree.  Also I dont have what that 2nd to last link shows, I believe it was software sources.

---

### Post by PeterJS on 2007-12-04
> **justinclark said:**
> According to Synaptic I have flashplugin nonfree.
Hmm, then it should work. Do you have noscript installed? That would also block flash.

> 
Also I dont have what that 2nd to last link shows, I believe it was software sources.

Yeah they only update the images with the LTS releases, so that's a couple releases old, by the synaptic method does still get you to the right place.

---

### Post by justinclark on 2007-12-04
Well flash has been working untill today, youtube and whatnot say I dont have the latest.  


AH HA!  I got it, for some reason java was disabled.  Im a genius!  Thanks for the help guys

---

### Post by ZipoTe on 2007-12-04
:lolflag: great!

---


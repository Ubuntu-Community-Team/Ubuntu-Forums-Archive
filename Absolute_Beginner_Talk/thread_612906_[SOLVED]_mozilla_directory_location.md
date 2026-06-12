---
title: "[SOLVED] mozilla directory location"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-11-14
"Flash Player
Versions: 9.0r31
SeaMonkey 1.1a: Supported
Firefox 2.0: Supported
FAQ: Flash Player FAQ

   1. Download Flash Player 9.0.
   2. Decompress it, then copy libflashplayer.so to your Mozilla plugins directory and flashplayer.xpt to your Mozilla components directory.

Note: Upgrading to Flash Player 9.0 is strongly suggested, even if only for ALSA support." 

These are instructions I got from another post. Where do I find my Mozilla plugins directory and  Mozilla components directory?
Thanks in advance.:)

---

### Post by Inxsible on 2007-11-14
it should be in your home folder. press ctrl + h to show you the hidden folders and then i think its .mozilla or .firefox. One or the other :)

---

### Post by tehet on 2007-11-14
The place for plug-ins is /usr/lib/mozilla/plugins and a bunch of other dirs that store plugins. But why not install it from the repositories?

---

### Post by FuturePilot on 2007-11-14
There should be an install script in there as well. cd to the uncompressed directory then
```
sudo ./flashplayer-installer
```
Follow the directions. The directory you want is
```
/usr/lib/firefox
```

---

### Post by jryprt on 2007-11-14
> **FuturePilot said:**
> There should be an install script in there as well. cd to the uncompressed directory then
```
sudo ./flashplayer-installer
```
Follow the directions. The directory you want is
```
/usr/lib/firefox
```

Hi sorry to jump in but I want the flash player to.
What is cd to the directory?
How do you cd to the directory?
I have the  uncompressed tar.gz on the desttop now what.

---

### Post by Inxsible on 2007-11-14
> **jryprt said:**
> Hi sorry to jump in but I want the flash player to.
What is cd to the directory?
How do you cd to the directory?
I have the  uncompressed tar.gz on the desttop now what. cd is the command to go into the directory.

Its the same as the cd command in DOS.

---

### Post by jryprt on 2007-11-14
> **Inxsible said:**
> cd is the command to go into the directory.

Its the same as the cd command in DOS.

So how do I get the flash player

---

### Post by FuturePilot on 2007-11-14
I'm not sure what you mean. Did you already install it?

---

### Post by jryprt on 2007-11-14
> **FuturePilot said:**
> From here
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
You want the tar.gz package.

Got it on the desktop how do I install it .
How do I do a tar.gz .

---

### Post by FuturePilot on 2007-11-14
Right click on it and select Extract Here.
Then open a terminal Applications>Accessories>Terminal and
```
cd /home/USER/Desktop/Extracted-Folder-Here
```
Replace USER with your user name and replace Extracted-Folder-Here with the name of the folder that was created when you extracted the archive
Then follow my other post.

---

### Post by jryprt on 2007-11-14
> **FuturePilot said:**
> Right click on it and select Extract Here.
Then open a terminal Applications>Accessories>Terminal and
```
cd /home/USER/Desktop/Extracted-Folder-Here
```
Replace USER with your user name and replace Extracted-Folder-Here with the name of the folder that was created when you extracted the archive
Then follow my other post.


Got it Thanks the help

---

### Post by powder on 2007-11-14
Just use the repositories.  It is much easier this way.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by skyjacker on 2007-11-15
Thanks for everyone's help. This forum has been a  GREAT help to me. Hope I can help others that need it.:)

---


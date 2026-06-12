---
title: "no audio on youtube"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by fenixfox on 2008-01-09
So I get audio on all of the programs I currently have. When I go to youtube I get no sound and the volume control graphic at the bottom of the movie on youtube is pixelated. How do I fix this?

---

### Post by supertails on 2008-01-09
Did you download flash?

---

### Post by esva on 2008-01-10
I absolutely don't understand why it doesn't work. I installed gnash and/or flash and it still didn't work. This was in firefox. So I tried kazehakaze or somethign no luck either.
So I tried opera, no luck either. It did work, but with opera 9.50, that is still not the official stabe version, but is available in the site. It works pretty well, sometimes it just stops working, then I have to restart the browser. But it runs smooth, In firefox the videos were like you describe in your post. Dunno.

---

### Post by billgoldberg on 2008-01-10
Remove flash using synaptic.

Go to their download page. (adobe flash!)

download the .tar.gz file

right-click and choose extract here.

Open the folder

look for the installer and run it in terminal.

look at the text and install it for all you webbrowsers.

This should do the trick.

---

### Post by philinux on 2008-01-10
If you dont want to bother with the command line then just download this deb file to your desktop and double click it

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)

---

### Post by wolfen69 on 2008-01-10
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.(remove gnash also)

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by fenixfox on 2008-01-10
> **billgoldberg said:**
> Remove flash using synaptic.

Go to their download page. (adobe flash!)

download the .tar.gz file

right-click and choose extract here.

Open the folder

look for the installer and run it in terminal.

look at the text and install it for all you webbrowsers.

This should do the trick.

I extracted it to desktop the typed /flashplayer-installer in terminal here is my reply. bash: /flashplayer-installer: No such file or directory
What do I do now? (I'm still really new at this. I have to say though after loading compiz and emerald my fiance' now wants ubuntu for the effects and customization!)

Thank you to the others who provided links. However I am using 64 bit ubuntu i686 architecture so i386 wont work. Thank you though!

---

### Post by GavinZac on 2008-01-10
> **fenixfox said:**
> I extracted it to desktop the typed /flashplayer-installer in terminal here is my reply. bash: /flashplayer-installer: No such file or directory
What do I do now? (I'm still really new at this. I have to say though after loading compiz and emerald my fiance' now wants ubuntu for the effects and customization!)

Thank you to the others who provided links. However I am using 64 bit ubuntu 686 architecture so i386 wont wrok. Thank you though!

if its on the desktop then the correct directory is /home/<yourname>/Desktop/flash-installer

---

### Post by fenixfox on 2008-01-10
> **GavinZac said:**
> if its on the desktop then the correct directory is /home/<yourname>/Desktop/flash-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
; ;

---

### Post by GavinZac on 2008-01-10
> **fenixfox said:**
> ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
; ;

do they supply a 64bit version?

---

### Post by fenixfox on 2008-01-10
they have a x86 plug in for solaris, here's the link. [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)
it's all the way at the bottom. I am using firefox it says it has support for 32 bit browsers. Alas nothing for 64. Here is a link for anyone else crying like me over the problem. [http://kb.adobe.com/selfservice/viewContent.do?externalId=6b3af6c9&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=6b3af6c9&sliceId=2)

---

### Post by Jammy4041 on 2008-04-18
It says you have to install a 32 bit browser. Then installing flash should work

---


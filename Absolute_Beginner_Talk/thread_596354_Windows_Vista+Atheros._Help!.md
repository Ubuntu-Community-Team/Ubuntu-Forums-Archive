---
title: "Windows Vista+Atheros. Help!"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by raizen24 on 2007-10-29
So ok this is the situation. I brought a Samsung laptop which came with the Windows Vista and with the ATI privative drivers. I downloaded the 7.04 version of Ubuntu and managed to install it and to fix the graphics. I can't download 7.10, it gives me too much trouble (don't know why). The thing is everything works now but the wifi. My card is an Atheros AR5007EG. I suppose I can't get the NDIS wrapper to work if I have Windows Vista, can I? I tried it anyway. I was following this:

[http://ubuntuforums.org/showthread.php?=521828](http://ubuntuforums.org/showthread.php?=521828)

When I tried to download the drivers I couldn't. I suppose because of my system. What should I do? It cost me a lot to fix the graphics and I'm afraid that if I install Windows XP, the drivers might be missing. I'm afraid of not being able to repeat the process too...I don't know. Maybe you know a save way of doing this? I also heard from madwifi but I don't really understand how it works. Please help! I am a newbie!:(

---

### Post by pizzutz on 2007-10-29
You can still use ndiswrapper to get an ar5007eg chip to work.  It doesn't care whether or not you have vista installed, as long as you d/l the XP driver for it.  Your link was broken, I assume you followed this thread:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

What do you mean when you say you couldn't d/l the drivers?  I checked, and they seem to be there.

cheers

---

### Post by raizen24 on 2007-11-03
Sorry, I made mistake. What I can't do is extracting the archives. It all worked fine until I introduced the order 
tar xvf ndiswrapper-newest.tar.gz 
Then the terminal said:
tar: ndiswrapper-newest.tar.gz No se puede open : No existe el fichero ó directorio
tar: el error no es recuperable: salida ahora
My Linux is in spanish so more or less:
No se puede open= It can't be opened
No existe el fichero ó directorio= The file or directory doesn't exist
el error no es recuperable: salida ahora= the mistake isn't recoverable: exit now
Any ideas of what's happening here?

---

### Post by jw5801 on 2007-11-03
That comand is attempting to extract the ndiswrapper source code. What was the filename of the tarball you downloaded? ndiswrapper-newest.tar.gz isn't what it would have been called. It was most likely ndiswrapper-1.49.tar.gz since that's the most recent.

---

### Post by i_TheDevil_i on 2007-11-03
u simpy have to install "ndisgtk", then download dirver for your adapter from [here]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1")
then unzip the driver to some dir, and go to "System>Administration>Windows Wireless Drivers". then choose to install new driver, and browse to dir where u unzipped the inf/sys files of driver. and that's all.
more info is [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") <- this HowTo is very powerful =))) i got my wifi working after reading it

---

### Post by raizen24 on 2007-11-05
Thanks jw5081! With your name I could carry on the configuration fine. But I have another problem now. When I restarted my laptop offered me the possibility to connect by Vitoria and Alberto. I chose Vitoria which is my net. I introduced my keyword. However instead of connecting it keep asking me the keyword over and over again. What's the problem now?

---

### Post by jw5801 on 2007-11-06
Hmm... Well I don't think that's a driver issue. Have you tried any other network managers to see if they have more success? Try wicd or wifi-radar, you will need to be connected to the net to get them though, so if you have a wired connection give it a spin. Else there's an Ubuntu site that has all the .debs that are in the repositories around somewhere which I don't have a link for with me at the moment, but it shouldn't be too hard to find.

---

### Post by tubasoldier on 2007-11-06
if it has an atheros chipset then try madwifi before you go mucking about with ndiswrapper.
it will show up as ath0.

```
sudo apt-get isntall madwifi
```

You may also want to disable NetworkManager and use Wifi-radar or Wlassistant.

---


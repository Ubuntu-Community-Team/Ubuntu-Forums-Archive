---
title: "Azureus Problem"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by MugenDraco on 2007-05-02
I'm using Azureus, and on startup it gives me a Warning error about Azureus not shutting down tidily.  It did the same thing the last time I installed Ubuntu, but this time it won't let me hide the error message.  And the error message is blocking my desktop switcher.

---

### Post by kvonb on 2007-05-02
Download the one from their website, the Azureus in the repos is rather old!

I lived in Pensacola for a few years, on Blount St and also Desert Street :D.

Couldn't stand the humidity!

---

### Post by starcraft.man on 2007-05-02
> **MugenDraco said:**
> I'm using Azureus, and on startup it gives me a Warning error about Azureus not shutting down tidily.  It did the same thing the last time I installed Ubuntu, but this time it won't let me hide the error message.  And the error message is blocking my desktop switcher.

Gah, I remember having this problem too when I was using Azureus, I'm still not sure why that is... can I suggest Ktorrent, its not java based and runs really well :) Its in the main repos too easy to get.

---

### Post by MugenDraco on 2007-05-03
thanx, i'll try both suggestions.  and yeah kvonb, the heat and humidity sux over here.  unfortunately i love the ocean, and there's no better place in the US for diving and doing underwater research than Florida.

---

### Post by MugenDraco on 2007-05-03
couldn't get Azureus installed from the official site, but KTorrent is working out great.  thanx.

---

### Post by Griff on 2007-05-03
> **MugenDraco said:**
> couldn't get Azureus installed from the official site, but KTorrent is working out great.  thanx.
I used Automatix to install Azureus: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Automatix will also, if you choose to, install a plethora of other useful codecs, programs, etc.

-Griff

---

### Post by therandman on 2007-05-03
> **starcraft.man said:**
> Gah, I remember having this problem too when I was using Azureus, I'm still not sure why that is... can I suggest Ktorrent, its not java based and runs really well :) Its in the main repos too easy to get.

Thanks, too, I was lookin for an alternative to Azureus! :)

---

### Post by medya on 2007-05-03
Azureus sucks simply because it uses Java !
I recommedn Ktorrent , if u still want a faster thing (but ugly) you may try Deluge BitTorrent Client

---

### Post by kvonb on 2007-05-04
> **medya said:**
> Azureus sucks simply because it uses Java !
I recommedn Ktorrent , if u still want a faster thing (but ugly) you may try Deluge BitTorrent Client

Yes, I have to agree with you there medya, it uses a lot of resources and has quite a few "quirks".

I use it because it runs on my server 24/7 and it has a lot of flexibility, ie you can select individual files in a torrent, rather than downloading the whole thing, and I can control it remotely.

If you want to use the Azureus from their site, download the 2.5.0.4 .tar.gz, unzip it into your home or working folder, install JRE 5 from the repos, you will need to make an icon to start it.

Just right click on the desktop and select "create launcher", for the command, browse to the folder that you unzipped Azureus into and pick up "azureus", it also has an icon in that same folder.

You also need to tell it which version of Java to use,  open a terminal and type:

```
sudo update-alternatives --config java 
```

It will give you a choice of detected versions, you will figure it out!

Another way is to directly edit the file "azureus" in the Azureus folder, it is a shell script.  At the top of the file it has the default location and also the location of the java bin file, change them to your settings.

Here is the top of my file if it helps:

```
#!/bin/bash

######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR=" /usr/lib/jvm/java-1.5.0-sun/jre/bin/"                # use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
PROGRAM_DIR="/home/kev/azureus"    # use full path to Azureus bin dir
#######################################




######## YOU PROBABLY DO NOT WANT TO TOUCH ANYTHING BELOW! ########

MSG0="Loading Azureus:"
MSG1="Starting Azureus..."
```

Oh, and I love your sig medya, good on you!

:)

---


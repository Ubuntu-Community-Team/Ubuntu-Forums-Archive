---
title: "Just installed Ubuntu"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by LEDZO on 2007-07-07
Hi, I have the version before feisty fawn installed, but im downloading kbuntu right now for feisty fawn. i have some very general questions.

1.I have a wireless linsky router and i believe ubuntu is detecting it but i dont know how to check and i dont know how to configure it.
2.I need a 56k modem i know will work with ubuntu, if anyone has any recommendations, i would be thankful.
3.my sound card worked with the live version but after i installed it, it no longer worked. i know it detects the sound card from the device manager.

I'm not totally new to linux so i can do more than just little things.

Thanks

---

### Post by BarfBag on 2007-07-07
As far as your router goes, you can probably access it by opening up Firefox, and typing 192.168.1.1.  If you've never used it before, the default user name and password is probably admin.

---

### Post by KIAaze on 2007-07-07
> **LEDZO said:**
> 
2.I need a 56k modem i know will work with ubuntu, if anyone has any recommendations, i would be thankful.


Altough you might have already been there, here are some essential sites for 56k modems on GNU/Linux:
[http://linmodems.org/]("http://linmodems.org/")
[http://tldp.org/HOWTO/Modem-HOWTO.html]("http://tldp.org/HOWTO/Modem-HOWTO.html")

I still haven't gotten my 56k modem to work.
I ran the scanmodem tool, but I didn't go further than that since the rest of the procedure seemed quite complicated and I didn't really need to get the modem to work.

> **LEDZO said:**
> 
3.my sound card worked with the live version but after i installed it, it no longer worked. i know it detects the sound card from the device manager.

I don't know exactly what to do, but usually it has to do with alsa and esd packages...
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=feisty&release=all")

I know that simply running the "alsaconf" command once solved all my sound problems. :)
Sometimes it's also simply the PCM output that's too low. Run "alsamixer" to increase it to 100%.

---

### Post by KIAaze on 2007-07-07
double post error

---

### Post by p_quarles on 2007-07-07
> 1.I have a wireless linsky router and i believe ubuntu is detecting it but i dont know how to check and i dont know how to configure it.

Are you using the wireless to connect to it, or are you using a cable? The difference is important. If it's wireless, you'll need to make sure you have the correct driver installed for your machine's wireless card, and that you know the WEP/WPA key for the router. If you need to configure it first, it will be a lot easier to hook up by ethernet, and then follow BarfBag's instructions (erm, did that sound weird? :-) ).

Good luck.

---

### Post by KIAaze on 2007-07-07
3) One more thing about the sound:
I don't remember where I got this script from, but it runs everytime at startup on my PC:

startesd:
```
#!/bin/sh
APP="/usr/bin/esd"
ARGS="-nobeeps"
if [ `pidof $APP` ]; then
#Do Nothing - already running
return
else
$APP $ARGS&
fi;

```

Save it as "~/bin/startesd".

Then go into "System->Preferences->Sessions" and click on "Add...".
Fill out as follows:
> Name: startesd
Command: ~/bin/startesd
Comment: sound daemon


It makes sure that "esd" is running everytime.
Maybe it'll work for you.

You'll have to make sure that "esd" is installed of course. The package to install to have it is ["esound"]("http://packages.ubuntu.com/feisty/sound/esound").

"alsamixer" is in "alsa-utils" by the way.
I can't seem to find where to get "alsaconf" but I know that it does exist. Maybe it has been replaced by something else now.
You can still install it from source otherwise:
[http://www.alsa-project.org/alsa/ftp/driver/alsaconf/]("http://www.alsa-project.org/alsa/ftp/driver/alsaconf/")

---

### Post by LEDZO on 2007-07-17
I have updates.
Wireless
I can find it in device manager, but i dont think the drivers work because alot of the information isnt filled out and the internet doesnt work.

I like that in feisty it allows you to go into roam because i have no access to a hardline, i can't get high speed internet at my house :-(.

Is there anything like the linksys wireless thing where i can scan for all the networks in range, or even see if i am getting signal?

I also couldn't get any commands to work and i dont think i understand how to run commands very well because nothing i try works.

Sound- now it plays sometimes when i start it up but if i go to a music player it doesnt work. I also dont know how to save the script, and i couldnt get any of the alsa stuff to work

Modem-is there a certain brand that has a good reputation?

---

### Post by RomeReactor on 2007-07-17
Hi. What wireless card do you have? If you don't know/are unsure, try this from the terminal (Applications->Accessories->Terminal):
```
sudo lshw -class network
```
and post the output here. Also, your wireless card may already have drivers, but is not correctly configured; try this:
```
iwconfig
```
and if one of the devices gives information about its wireless extensions, (e.g. wlan0), then try this:
```
sudo iwlist wlan0 scan
```

If you're having trouble entering the commands, try copying/pasting in the terminal, and post the output of the commands..

---

### Post by KIAaze on 2007-07-18
> **LEDZO said:**
> 
I also dont know how to save the script, and i couldnt get any of the alsa stuff to work

[LIST]
[*]Installing esound and alsa-utils
```
sudo aptitude install esound
sudo aptitude install alsa-utils

```

Try running alsamixer to see if the PCM level is high enough:
```
alsamixer
```

[*]Installing and running alsaconf:
```
wget http://www.alsa-project.org/alsa/ftp/driver/alsaconf/alsaconf-0.4.3b.tar.gz
tar -xzvf alsaconf-0.4.3b.tar.gz
cd alsaconf-0.4.3b/
./alsaconf

```

Maybe it's necessary to run it as root. In that case:
```
sudo ./alsaconf
```

[*]Creating and saving the script:
```
mkdir ~/bin
gedit ~/bin/startesd

```

Copy-paste this code into it:
```
#!/bin/sh
APP="/usr/bin/esd"
ARGS="-nobeeps"
if [ `pidof $APP` ]; then
#Do Nothing - already running
return
else
$APP $ARGS&
fi;
```

Save it (File->Save).

Then go into "System->Preferences->Sessions" and click on "Add...".
Fill out as follows:
> Name: startesd
Command: ~/bin/startesd
Comment: sound daemon

[/LIST]

---


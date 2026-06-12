---
title: "No sound on YouTube or Google video!"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by NirvanaRush2112 on 2006-12-29
there is no sound...and i just installed Ubuntu 6.06 last night and i am very new with it...the video also runs slow and skips abit...i used Automatix2 and it failed to install Flash on there...i dont know how i got flash now...how do i check what version i have? i also used EasyUbuntu...no luck...so can some one help me out here?
is it...
FireFox?
Flash?
ubuntu????

---

### Post by Perfect Storm on 2006-12-29
in the browser box you write **about : plugins** (without the spaces in between)to see which version you have of flash.
You need flash 9 to YourTube and Google video.

---

### Post by ComplexNumber on 2006-12-29
check that you're using the correct sound card. see screenshot. then check the volume.

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> in the browser box you write **about : plugins** (without the spaces in between)to see which version you have of flash.
You need flash 9 to YourTube and Google video.

where do i find it...i typed it like this (aboutplugins) and this is what came up.. [http://wiki.apache.org/nutch/AboutPlugins](http://wiki.apache.org/nutch/AboutPlugins)

---

### Post by Perfect Storm on 2006-12-29
You forgot the **:** in between of aboutplugins. I have do it this way because when you put : and p next to eachother a smiley shows up (bummer, going have to talk with U-G about this).

---

### Post by NirvanaRush2112 on 2006-12-29
> **ComplexNumber said:**
> check that you're using the correct sound card. see screenshot. then check the volume.

sound works...i was riping cd's and downloading music off of frostwire

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> You forgot the **:** in between of aboutplugins. I have do it this way because when you put : and p next to eachother a smiley shows up (bummer, going have to talk with U-G about this).
ooo my bad dude....here is what came up...

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by pissedoffdude on 2006-12-29
> **NirvanaRush2112 said:**
> ooo my bad dude....here is what came up...

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I had the same problems when i was using adobe flash 7.  Try getting flash 9 beta 2 and manually extracting it into the /usr/lib/firefox/plugins folder

---

### Post by Perfect Storm on 2006-12-29
You have version 7 I see. uninstall the flash first.

flash 9 - [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html) save to **Desktop**.

```
cd ~/Desktop
tar zxfv FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/mozilla/plugins
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/mozilla-firefox/plugins
```

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> You have version 7 I see. uninstall the flash first.

flash 9 - [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html) save to **Desktop**.

```
cd ~/Desktop
tar zxfv FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/mozilla/plugins
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/mozilla-firefox/plugins
```

how do i uninstall it? sorry im being a total noob :D

---

### Post by pissedoffdude on 2006-12-29
> **NirvanaRush2112 said:**
> how do i uninstall it? sorry im being a total noob :D

If you installed it through synaptic then you can just search for flash using synaptic.  You can also try "sudo apt-get remove flashplugin-nonfree" (without quotes) or a "sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt" (without quotes once again)

---

### Post by Frak on 2006-12-29
It happens often on all linux flash 9 beta plugins, I got over it by using Crossover to install Flash 9 for Windows, much more stable, but since linux is such a small demographic, don't count on Adobe fixing it soon.

---

### Post by Frak on 2006-12-29
> **NirvanaRush2112 said:**
> how do i uninstall it? sorry im being a total noob :D
You shouldn't have to uninstall, it upgrades when installing, and just untar the archive and open the folder and double-click flash 9 install (or something equivilent) and a box should come up, choose open in terminal, and it automatically installs itself into firefox files.

---

### Post by Perfect Storm on 2006-12-29
Never had any issue with flash 9 beta on linux and stability. Maybe I'm lucky ;) Both YouTube and GoogleVideos ran perfectly everyime, but again I'm using Epiphany browser which is more stable than Edgy firefox.

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> Never had any issue with flash 9 beta on linux and stability. Maybe I'm lucky ;) Both YouTube and GoogleVideos ran perfectly everyime, but again I'm using Epiphany browser which is more stable than Edgy firefox.

i tryed what you told me but it didnt do anything...i still have flash 7...how do i install the other way?...i have the file sitting on ym desktop

---

### Post by Perfect Storm on 2006-12-29
In **places** tab there's a search options. Make a search on **flashplayer.so** make sure you set it to search in **system** (or something similiar I'm at work away from my ubuntu computer). PLease ost the outcome

---

### Post by Frak on 2006-12-29
> **Artificial Intelligence said:**
> In **places** tab there's a search options. Make a search on **flashplayer.so** make sure you set it to search in **system** (or something similiar I'm at work away from my ubuntu computer). PLease ost the outcome
Do you mean **filesystem**.

---

### Post by Perfect Storm on 2006-12-29
Aye, we don't have any linux system where I'm at. So it's from my memory, but it was close :rolleyes:  :mrgreen:

---

### Post by NirvanaRush2112 on 2006-12-29
> **Frak said:**
> Do you mean **filesystem**.

i have the file but how do i install it now?

---

### Post by Frak on 2006-12-29
> **NirvanaRush2112 said:**
> i have the file but how do i install it now?
Did you follow the instructions I gave, or did that not work for you?

---

### Post by Perfect Storm on 2006-12-29
can you please post where it's installed. Then we have to remove it and place it with flashplayer.so version 9

---

### Post by pissedoffdude on 2006-12-29
to uninstall: ```
sudo apt-get remove flashplugin-nonfree
``` or ```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
```

to install flash 9:  go here [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html") and download tar.gz.  Then open up a terminal and ```
cd Desktop
tar zxfv FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/firefox/plugins 

```

---

### Post by Frak on 2006-12-29
Wait, why didn't we reccoment automatix2, it does all that automatically.

---

### Post by pay on 2006-12-29
> **Frak said:**
> Wait, why didn't we reccoment automatix2, it does all that automatically.Because you will never learn howto do it yourself. Automatic doesn't have every program. Anyway try this ```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

```and change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```

---

### Post by Perfect Storm on 2006-12-29
Does it include flash 9? I'm not into these easy installers, I'm a manually guy and want full control ;)

But if it have flash 9 I see no why.

---

### Post by NirvanaRush2112 on 2006-12-29
> **Frak said:**
> Did you follow the instructions I gave, or did that not work for you?

i double clicked the file and it brought up the package installer and it gave an error saying it was corrupted or somthing...its happend with most files ive downlaoded like limewire..but i got it installed some how lol

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> can you please post where it's installed. Then we have to remove it and place it with flashplayer.so version 9

i took the libflashplayer9.so out of the folder and put it on the desktop

---

### Post by Frak on 2006-12-29
> **Artificial Intelligence said:**
> Does it include flash 9? I'm not into these easy installers, I'm a manually guy and want full control ;)

But if it have flash 9 I see no why.
Yep, just click miscelleneous and click Install Flash, and as long as you aren't running another apt-process, it should go without a hitch.

---

### Post by Perfect Storm on 2006-12-29
Which path did it had? (you can't remove/move/edit by moving it without admin permission)

---

### Post by NirvanaRush2112 on 2006-12-29
> **pissedoffdude said:**
> to uninstall: ```
sudo apt-get remove flashplugin-nonfree
``` or ```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
```

to install flash 9:  go here [http://labs.adobe.com/downloads/flashplayer9.html]("http://labs.adobe.com/downloads/flashplayer9.html") and download tar.gz.  Then open up a terminal and ```
cd Desktop
tar zxfv FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/firefox/plugins 

```

i put the last one in to install and it just said what was in the folder...

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> Which path did it had? (you can't remove/move/edit by moving it without admin permission)

path...you mean like /home/matt/Desktop ?

---

### Post by Perfect Storm on 2006-12-29
Aye, the flashplayer.so you are looking for should be in /usr/lib/~

---

### Post by Frak on 2006-12-29
Make sure you use GKsudo, because in the end its going to be graphical.

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> Aye, the flashplayer.so you are looking for should be in /usr/lib/~

ahh i see now...ya i dnt have permission

---

### Post by NirvanaRush2112 on 2006-12-29
> **Frak said:**
> Make sure you use GKsudo, because in the end its going to be graphical.

huh? wow im sorry guys this is so new to me...i mean im just trying to install flash 9 lol

---

### Post by Frak on 2006-12-29
> **NirvanaRush2112 said:**
> huh? wow im sorry guys this is so new to me...i mean im just trying to install flash 9 lol
Instead of the sudo command, use the gksudo command, unless your using Kubuntu which would be Kdesu.

---

### Post by Perfect Storm on 2006-12-29
> **NirvanaRush2112 said:**
> huh? wow im sorry guys this is so new to me...i mean im just trying to install flash 9 lol

No problem. We have all been newbie once ;)
Well I'll be more help when I get home. I need to be infront of my machine.

---

### Post by NirvanaRush2112 on 2006-12-29
> **Frak said:**
> Instead of the sudo command, use the gksudo command, unless your using Kubuntu which would be Kdesu.

ooo ok...i dnt have that installed so let me do that

---

### Post by NirvanaRush2112 on 2006-12-29
> **NirvanaRush2112 said:**
> ooo ok...i dnt have that installed so let me do that

what whoa....i thought somthing different lol

---

### Post by NirvanaRush2112 on 2006-12-29
> **Artificial Intelligence said:**
> No problem. We have all been newbie once ;)
Well I'll be more help when I get home. I need to be infront of my machine.

ok...may i ask when u get home lol

---

### Post by NirvanaRush2112 on 2006-12-29
> **pay said:**
> Because you will never learn howto do it yourself. Automatic doesn't have every program. Anyway try this ```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

```and change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```

i tryed that last night..no luck

---

### Post by pissedoffdude on 2006-12-29
are you running a 64-bit ubuntu

---

### Post by NirvanaRush2112 on 2006-12-29
> **pissedoffdude said:**
> are you running a 64-bit ubuntu

no im not

---

### Post by NirvanaRush2112 on 2006-12-29
bump.....

---

### Post by NirvanaRush2112 on 2006-12-29
bump again :(

---

### Post by xpod on 2006-12-29
IF you got that "libflashplayer9.so " on your desktop or somewhere all you need to do is copy it over to "/usr/lib/firefox/plugins".......

As someone suggested Automatix2 would sort all this out for you plus it also has many other useful applications & utilities...

Havent read all the thread so sorry if you already know this much..
Good luck

---

### Post by NirvanaRush2112 on 2006-12-30
> **xpod said:**
> IF you got that "libflashplayer9.so " on your desktop or somewhere all you need to do is copy it over to "/usr/lib/firefox/plugins".......

As someone suggested Automatix2 would sort all this out for you plus it also has many other useful applications & utilities...

Havent read all the thread so sorry if you already know this much..
Good luck

i tryed that but it said i dont have permission...and it keeps stoping when i use automatix2

---

### Post by pissedoffdude on 2006-12-30
> **NirvanaRush2112 said:**
> i tryed that but it said i dont have permission...and it keeps stoping when i use automatix2

has this happened with everything that you have tried to install using automatix or just the flash plugin

---

### Post by Perfect Storm on 2006-12-30
> **NirvanaRush2112 said:**
> i tryed that but it said i dont have permission...and it keeps stoping when i use automatix2

You need to do 

sudo cp -r libflashplayer9.so /usr/lib/firefox/plugins

---

### Post by Frak on 2006-12-30
> **NirvanaRush2112 said:**
> i tryed that but it said i dont have permission...and it keeps stoping when i use automatix2
Did you follow the instructions off of getautomatix.com ?

---

### Post by NirvanaRush2112 on 2006-12-30
> **Frak said:**
> Did you follow the instructions off of getautomatix.com ?

ya but when it says downloading flash from adobe it just stops there and doesint continue

---

### Post by NirvanaRush2112 on 2006-12-30
> **pissedoffdude said:**
> has this happened with everything that you have tried to install using automatix or just the flash plugin

flash and java the 1st time i tryed it

---

### Post by nickoli on 2006-12-30
I had a similiar situation with a differant plugin earlier today. I installed the wrong plugin. I just used the rm command to delete the directory that the program installed and then the links that I placed in the mozilla plugin folder. Maybe this will work for you.

---

### Post by NirvanaRush2112 on 2006-12-30
> **nickoli said:**
> I had a similiar situation with a differant plugin earlier today. I installed the wrong plugin. I just used the rm command to delete the directory that the program installed and then the links that I placed in the mozilla plugin folder. Maybe this will work for you.

whoa what is that? how do i do that? eh?

---

### Post by pissedoffdude on 2006-12-31
> **NirvanaRush2112 said:**
> whoa what is that? how do i do that? eh?

try using automatix to install swiftfox and the swiftfox plugins so you can get a working flash using swiftfox

---

### Post by NirvanaRush2112 on 2006-12-31
> **pissedoffdude said:**
> try using automatix to install swiftfox and the swiftfox plugins so you can get a working flash using swiftfox

swiffox is what ive been using...and ill try the pluggins again i guess

---


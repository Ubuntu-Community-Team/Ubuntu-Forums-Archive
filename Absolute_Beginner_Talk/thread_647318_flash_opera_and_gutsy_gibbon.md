---
title: "flash opera and gutsy gibbon"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-12-22
I have a 32 bit intel system and gutsy gibbon.
I used apt to get flash - it downloaded and installed ok. It works with firefox.

The plugin does not work with opera. I visit the test flash page and it says to install plugin.

What can I do (gnash has similar problems.)

---

### Post by steve-shinn on 2007-12-22
I had the same problem....if you are using flash 9.0.115 with Opera 9.24 or 9.25 it won't work.

What worked for me was installing Opera 9.50 beta.

---

### Post by njaneardude on 2007-12-22
[BUMP]
Until 9.50 develops the lock problem (me), just did a Opera 9.50 uninstall/reinstall, still broke.
Looks like I'll have to downgrade and live without Opera /Flash/

:(

---

### Post by yeehi on 2007-12-22
I should have said I have opera 9.5 beta.

I remember seeing that there was a workaround, for version 2 of the 9.5 beta. But i downloaded again, and still had the 9.5 version 1 beta.

So, I am still stuck...

---

### Post by usergroup81 on 2007-12-22
Try installing flash 7 for Opera for now until they release a newer version that will work. It's working for me. Here is the link to get older Flash versions:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266]("http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266")

Extract the file and then go into folder r73 which is the latest version of 7.
Extract install_flash_player_7_linux_r73.tar.gz.

cd into the folder containing: flashplayer.xpt      flashplayer-installer      libflashplayer.so
something like this
```

cd /home/t/fp7_archive/r73/install_flash_player_7_linux

sudo ./flashplayer-installer

```

follow the installation when ask the directory for opera plugin, use this: /usr/lib/opera/plugins.
Now you have to go to Tools > Preferences > Advanced > Content > Plugin-Options  and check to see if flash 7 is listed. You might have to change path so as to only have flash 7 as listed instead of flash 9.
Sorry if it's difficult to understand, I'm still new to Linux.

---

### Post by njaneardude on 2007-12-23
Appreciate the tip, except now I can't get Opera to open at all!  Major bummer, that and no sound after a reboot, complete bummer.

I'm going to try to uninstall/reinstall Opera again but already did it 3 times and get a lock error whenever I try to open it.

Well back to the hair pulling!

Ubuntu noob here!

Merry Christmas!

~n

---

### Post by aonegodman on 2007-12-26
Thought I'd give Opera a try over Firefox since I was having some problems with it.

Installed Opera(latest in repositories) came up fine.

Went straight to YouTube -  NO Flash Player.  Bummer!!!

Just got Flash installed and fixed in Firefox, although it stops and stutters a little from time to time.

You know if Ubuntu/Linux can just get the multimedia things worked out that we all seem to have problems with - lookout Microsoft. DONE.

---

### Post by LaRoza on 2007-12-26
Here is what I did. I use Flash and Opera with no problems in Gutsy.

First remove flashplugin-nonfree and Opera (you can save your .opera directory to keep your settings)

Then [http://www.opera.com/download/linux/?ver=9.50b](http://www.opera.com/download/linux/?ver=9.50b) Install it.

It is beta, yes, but it works.

Now go to System->Administration->Software Sources and go to the Updates tab. Click "Pre Release...."

Run these commands:

```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

Unless I am unique, it should work just as well for you as it did for me.

---

### Post by jesesc6 on 2007-12-26
:popcorn:


Didnt Opera Update  9.50 a while ago

---

### Post by LaRoza on 2007-12-26
> **jesesc6 said:**
> 
Didnt Opera Update  9.50 a while ago

9.25 is the latest version, 9.50b is beta.

---

### Post by s0l1dsnak3123 on 2007-12-27
it works! Thanks alot LaRoza. There is only one slightly worrying error I got when installing flash:

> 
 2750K .......... .......... .......... .......... .......... 94%   57.60 KB/s
 2800K .......... .......... .......... .......... .......... 96%   57.16 KB/s
 2850K .......... .......... .......... .......... .......... 97%   57.47 KB/s
 2900K .......... .......... .......... .......... .......... 99%   58.96 KB/s
 2950K .......... ....                                       100%   55.03 KB/s

11:25:27 (57.83 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

snak3@snak3-desktop:~$ 


but it does work on flash so - who cares :) thanks again LaRoza.

---

### Post by jalirious on 2008-01-02
Cheers LaRoza - worked a treat!

---

### Post by Madvil on 2008-01-06
I had the same report as s0l1dsnak3123 did and didn't worked for me...

:mad::mad:

---

### Post by yeehi on 2008-01-06
Like the previous poster, I got the same error message and flash still does not work on my machine.

I now also have to work out whether to install other "proposed" code onto my system from the auto updater...

---

### Post by ray1claw on 2008-01-22
i did install the 9.50b but it was all crashing n ****... it crashed when i opened random sites... totally random... ones which hav flash content n those that dont... so i switched bak to 9.25 for gud... but now i realize again that i lost the flash again... GOD i wanna cry!!

---


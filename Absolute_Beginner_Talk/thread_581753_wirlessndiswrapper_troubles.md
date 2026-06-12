---
title: "wirless/ndiswrapper troubles"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by froggger on 2007-10-19
ok, so complete begginer here(duh) and i'm having troubles with ndiswrapper.
i have it installed and i get a response from modinfo, but when i try to use any ndiswrapper command, it says no ndiswrapper utils found.

It did install kinda weird. i followed the webiste instructions and it didn't work, but then terminal gave me a suggestion to install it and i did that. Then it asked for my gusty gibbon disc so i gave it to it and now it should be installed, but its not responding to commands. 

Keep in mind, complete noob here, everything i've done is from googling and testing it out.

I'm using a dwl-g132 108mb/s adaptor and 7.10 gutsy gibbon.

Any help would be greatly appreciated!

---

### Post by maverick_mach on 2007-10-19
same problem here...
im tryin to install my netgear wireless WG311v3 card but cant install ndiswrapper eve,...
as written in the install file provided with th ndiswrapper package wen am typing
make install
though it is doin somethin but in th end finishes with 2 errors an lots of warnings...many errors are implicit declaration of some functions..
tryin :
sudo apt-get install ndiswrapper 
  says ndiswrapper not found..

any1 pl help me out...i cant use my net thru ubuntu an i hav to migrate to windows to do it...

---

### Post by Daveth on 2007-10-19
where are you sourcing the program from? In the feisty repository at least all the necessary parts in in Synaptic. Look in system/admin/synaptic package manager. Then give your root password and type in ndiswrapper. Should bring up what you need and then get all your dependencies. Assuming they haven't entirely changed everything!!!

---

### Post by froggger on 2007-10-19
acutally, check this post, because i found something else that i'm trying.
[http://ubuntuforums.org/showthread.php?t=581854](http://ubuntuforums.org/showthread.php?t=581854)

please help there!

---

### Post by Onay on 2007-10-19
Ha, I use dwl-g132. Try this for me, I'll write you a little tutorial...

1. Boot up Gutsy
2. Insert the Live install CD for Gutsy.
3. Open of the command prompt and execute the following
```
sudo apt-get install build-essential
```
4. Allow it to install the build tools from the cd.
5. Download the ndiswrapper source code to the desktop
[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.48.tar.gz?modtime=1190227517&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.48.tar.gz?modtime=1190227517&big_mirror=0)
6. Here are the commands. Execute these all in the terminal by pressing enter at the end of each line. Lines with /* are comments, DO NOT execute them
```
/* Change directory to the desktop
cd ~/Desktop

/* Untar the ndiswrapper source code
tar zxvf ndiswrapper-1.48.tar.gz

/* Change to ndiswrapper directory
cd ndiswrapper-1.48

/* Uninstall anything existing and compile the source code
make uninstall
make && sudo make install

/* once that compiles correctly, you need to install your drivers.
/* change directory to the one with the driver(s) and run the command using YOUR DRIVERS..
sudo ndiswrapper -i drivername.inf

/* activate the wireless
sudo depmod -a
sudo modprobe ndiswrapper

```

Then, if all works execute the following after logging into the network
```
sudo ndiswrapper -m
```

---

### Post by froggger on 2007-10-19
ok, thanks, i'll try that and get back to you!
is this permanent?

thanks!

---

### Post by Onay on 2007-10-19
Well, you can always uninstall ndiswrapper, but then you would have internet again. My advice is to stick with ndiswrapper, it's your best chance.

It took me a very long time to figure out how to get it working, and I seem to have reached a strong middle ground. Anyway, the drivers you should be looking for are named below, you can get them at the D-link website for the dwl-g132.

athfmwdl.inf
NetA5AGU.inf

You need those, plus the sys files, bin file, pretty much everything that comes when you download the drivers all in one folder to install.

---

### Post by froggger on 2007-10-19
so i'll have to do this step
```
/* change directory to the one with the driver(s) and run the command using YOUR DRIVERS..
sudo ndiswrapper -i drivername.inf
```twice, once with each inf file?
thanks for your helpon this too!

so i have the ndiswrapper tar.gz, the drivers, and your tut on a floppy so i should be good to go.  Yea, i know, a floppy....

and one last thing, if i have the inf files in a folder called drivers on my desktop, the command to go to that folder would be ```
cd ~desktop/drivers/
``` right?

---

### Post by froggger on 2007-10-19
ok, so i did all that and entered my connection details , then after i hit ok or whatever, my computer froze!
so it wouldn't respond at all, not even moving the cursor. so i held the power button and it turned off.
then i booted back up and it did a disk check and all that, then it got to a point and it froze, in the middle of startup. so i repeated the procedure and turned it off.
then i turned it back on and it did a disk check, now i stopped to see what it was froze at.
its froze at something to do with ndiswrapper.  I can copy down all the numbers and letters is you need them.

Can anybody help me with me with this?

BTW, i can still boot into windows(i have it on dual-boot) if that helps.

---

### Post by maverick_mach on 2007-10-20
Well i got my ndiswrapper got working perfect now...
ANd now th trouble is lying with th installation of my wireless drivers...
I got this in one of Ubuntu topics

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29")
$ ndiswrapper -l
is also showing my wireless card with th device Id...But wen im trying:
$ iwconfig
it is not showing any details about wlan0 ...An in networking also wireless network is still not there...
I'd try to post th output of ndiswrapper -l an iwconfig asap...
But i need urgent help coz im dried of switchin OSs b/w Xp an Ubuntu/...LOLz..

---

### Post by maverick_mach on 2007-10-20
Well....i hav got it working...
thanks anyways...,,

---


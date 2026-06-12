---
title: "GUI not loading"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by skydancer on 2006-09-30
need help
just loaded Ubuntu onto my computer
but the GUI screen doesn't show up
a blue screen shows up which tells me the X server loading had failed 
i am stuck in the command line argument and i have no idea how to start of with anything...help..

---

### Post by bigken on 2006-09-30
give this a shot boot into single user mode and type sudo dpkg-reconfigure xserver-xorg ;)

---

### Post by skydancer on 2006-09-30
tried that but it ain't working it leads me through a setup process to detect my monitor , keyboard and mouse and then returns to the command line prompt ..rebooting doesn't help either..

---

### Post by bigken on 2006-09-30
what is your grahpics card

---

### Post by skydancer on 2006-09-30
ATI RADEON X300 ..onboard..

---

### Post by bigken on 2006-09-30
ok so when you run the  sudo dpkg-reconfigure xserver-xorg select ati as your driver and if that dont work run the dpkg again and select vesa as your driver this will at least get you running ;)

---

### Post by skydancer on 2006-09-30
no luck
the screen terminates after my monitor configuration 
*"overwriting possibly customized configuration file; backup in /etc/x11/xorg.config.200609302026"*
then i am back to bash



ps: while loading Ubuntu the following error message shows up
"[I] synchronizing clock to ntp.ubuntulinux.org failed
error : Temp failure in name resolution[/I]" 
Dunno if ths causin da error

---

### Post by bigken on 2006-09-30
sorry cant help anymore :-k

---

### Post by skydancer on 2006-09-30
well thnx nyways

---

### Post by podunk on 2006-09-30
ATI cards are just hell in Linux. ATI is a MS/Intel running dog lackey! I swear it looks like they do everything they can to keep us locked into Windows.

This is the way I get mine to work when the driver gets messed up

```
sudo nano /etc/X11/xorg.conf
```

Use the <CTRL> <V>  keys to go down the page to
Section "Device"
and there should be the name of some sort of video and you will see
	Driver  	<”something”> 

change this to 

	Driver	            “ati”

Hit the keys
<CTR>  <X>

It will ask if you want to save – type Y then hit Enter, then hit enter again.

Type
```
 sudo shutdown  - r now
```

and see if you get to the GUI

if not then change the driver from 
“ati”
to
“vesa”

If you are using a LCD there is a good chance you will get an out of sync error. If you do post back and I'll give you my LCD settings to enter in.

Hope this helps!

---

### Post by skydancer on 2006-09-30
k i thnk tht worked changed my driver to vesa 
but now Ubuntu starts up n my screen reads
                       [I]out of range
                       46.4khz/87hz[/I]
                      
i have a 17" lcd  ..

---

### Post by Rui Pais on 2006-09-30
Hi,
have you tried [those instructions here]("https://help.ubuntu.com/community/RadeonDriver") for the open source radeon driver?

or [this one here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") for the binary (proprietary) driver?

You must install and configure one of those first.


Don't worry about the:
> synchronizing clock to ntp.ubuntulinux.org failed
error : Temp failure in name resolution...thats nothing to do with your driver. 
It fails to connect to an internet server that provide local time for your computer clock (you can configure that later).

---

### Post by skydancer on 2006-10-01
k by now i have tried all tht but the x server fails to load unless i use vesa 
even then my lcd screen reads "out of range"..so im still stuck...

---

### Post by Rui Pais on 2006-10-01
try to boot from the liveCD (the installer CD) and check if it works there. Usually autodetection on ubuntu liveCD is very good.

If it works there you can copy the xorg.conf to your /etc/X11/xorg.conf

---

### Post by slimdog360 on 2006-10-01
have a look in the manual which came with your screen for the VertRefresh and HorizSynch values. If they arnt in there or you cant find the manuals plug these numbers in your xorg.conf file just look for the monitor heading and replace the numbers. Make a backup first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

HorizSynch 31.5-48.5
VertRefresh 40-70

change it the same way as before using nano and make sure you save it. Hit ctrl+alt+backspace. If it still doesnt load tell me what it says about the xserver not loading.

and dont worry its not always this hard.

---

### Post by Rui Pais on 2006-10-01
another simple way of do it is simply comment out (put a # in the beginning of the line of HorizSynch and VertRefresh) Those values are set automatically now by the X server, usually with less errors  than user's hand made.

---

### Post by skydancer on 2006-10-01
bingo! im in thnx a lot 
k now can someone help me get the internet started im like a lost puppy in there..

---


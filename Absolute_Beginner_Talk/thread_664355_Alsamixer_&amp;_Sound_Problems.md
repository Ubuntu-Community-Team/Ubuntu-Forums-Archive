---
title: "Alsamixer &amp; Sound Problems"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by kristeng on 2008-01-11
**Computer:** Toshiba Satellite A210 (was running Vista until the system "could not load Windows")
**The terminal said this about my soundcard:**
description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel


I've recently gotten Ubuntu (today, actually) and I'm having problems with sound. I've been looking all over the forums and I've tried as much as I am possible (being new to Linux), but am unable to find anything that works. Yes, I have checked to make sure it's not on mute, and I've also tried putting two different sets of headphones in.

This site here: [http://linux.iuplog.com/default.asp?item=9463](http://linux.iuplog.com/default.asp?item=9463) has information about how to troubleshoot the issue and looked very promising. I think it would work for me but I'm having problems with alsamixer.

I go into the alsamixer boot and change Caller I and Off-hook to on, and change "View" to All like so: [http://img132.imageshack.us/img132/116/screenshotkristenkristess0.png](http://img132.imageshack.us/img132/116/screenshotkristenkristess0.png)
Then I press escape, type in *sudo alsactl store*. My sound didn't work, even after reboot, so I went back into the alsamixer boot and it changed back to what it was originally: [http://img132.imageshack.us/img132/9122/screenshotkristenkristeqp3.png](http://img132.imageshack.us/img132/9122/screenshotkristenkristeqp3.png)

I can't figure out why this is changing, I'm typing everything right (unless the site has it wrong?). Could someone please help? I really love Ubuntu but I need sound!

Any links to a very basic step-by-step troubleshoot would be helpful!

---

### Post by HermanAB on 2008-01-11
It is easy to fix most Linux sound problems - turn the volume up - really!

The audio is muted by default and it can be controlled in at least three different ways. If any one of those is turned down, then you won't hear anything.

The kmix utility should be on the task bar - turn everything up till the sound works. Another way is to run aumix.

When all else fails, go to the ALSA Project web page and start reading: [http://www.alsa-project.org](http://www.alsa-project.org).

Also, do ensure that you have that little cable between the CDROM drive and the mother board plugged in...

---

### Post by balaknair on 2008-01-11
Detailed guide for step by step instructions on troubleshooting
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

guide on hda-intel
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

A simpler fix for hda-intel modules(based on what worked for me from both the above links)
open a terminal and enter the following commands
```
aplay -l
```
```
lspci -v
```
These will give info about whether your card is loaded and detected
now
```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

in that page find your card model and check the details given
eg ```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)

```

select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type
```
sudo nano /etc/modprobe.d/alsa-base
```

Paste this into the _last line_ of the file
```
options snd-hda-intel model=MODEL
```

replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.

If this doesn't work you can also edit the probemask(look at the hda-intel howto page, it's towards the end)

If your problem is fixed, please reply and post just what worked for you, and please don't forget to mark the thread as solved

Wishing you luck

---

### Post by kristeng on 2008-01-11
**Herman**: The speaker in the task bar has a tiny red x beside it, and when I try to open it I get an error. The first thing I checked was to see if the sound was low/muted.
I tried to make it clear that I'm *extremely* new to Linux. I don't know what aumix is.
Also, I'm trying to run music on my system directly, not from a CD. However, the sound had worked fine until Vista crapped on my computer.

**Balaknair**: *aplay -l* 
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

*lspci -v*
It was a list of everything I have on my computer, I think, but everything said "access denied" at the end. Is that right?

Also, for my soundcard: 
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Toshiba America Info Systems Unknown device ff0a
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

After doing *cat /proc/asound/card0/codec#* | grep Codec*
```
Codec: Generic 11c1 Si3054
Codec: Generic ffff ID ffff
```

I wasn't able to find "Generic 11c1 Si3054" on the kernel documentation page, so I googled it and it says it's a codec. This is where I get confused. I know enough about computers to work my way around them, and I can follow directions usually but I'm really confused with this.

And thank you very much for your help, I appreciate it.

---

### Post by balaknair on 2008-01-11
don't worry about the access denied part, that's normal
and Generic 11c1 Si3054 is a codec for the modem
from a web search I think you HDA codec should be Realtek ALC268
Could you please copy paste this in a terminal
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'`

I'll wait for a reply

---

### Post by balaknair on 2008-01-11
the next logical step is to reinstall alsa with latest stable version 1.0.15 which has some fixes for ALC268.
first you'll need to install the necessary tools and files. In a Terminal
```
sudo aptitude install build-essential libncurses5-dev gettext linux-headers-`uname -r`
```

Download these files from the alsa-project site
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

Save them to a folder named downloads in your home directory

Then in terminal, type the following commands to
make installation directory
```
sudo mkdir -p /usr/src/alsa
```
open the target folder
```
cd /usr/src/alsa
```
Copy the downloaded archives over from your home directory
```
sudo cp ~/downloads/alsa* .
```
Extract each of the archives
```
sudo tar xjf alsa-driver*.bz2
```
```
sudo tar xjf alsa-lib*.tar.bz2
```
```
sudo tar xjf alsa-utils*.tar.bz2
```

Now compile and install the drivers with the following steps
```
cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```
Do the same for the lib and utils
```
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
```
```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```

Reboot

Now you have the latest Alsa drivers
Back to the earlier steps
 to check your codec
```
cat /proc/asound/card0/codec#* | grep Codec
```

now insert the codec model
```
sudo nano /etc/modprobe.d/alsa-base
```
```
options snd-hda-intel model=toshiba
```

reboot


If this doesn't work, the linux kernel may need a patch
More info and tips at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) (method E)

Lotsa luck

---

### Post by kristeng on 2008-01-11
```
bash: awk{print $}: command not found
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
```

This is what came up with the code you told me to type in your previous post.
I'll try the steps in the post above mine, and let you know what's up.

---

### Post by kristeng on 2008-01-11
It keeps telling me that those directories don't exist. ):

---

### Post by balaknair on 2008-01-11
Don't worry about the first command, just copy and paste the entire line(including the little '` at the end. that's part of the command.
you have to make a couple of directories, that's what the mkdir commands do.
which directories does it say does not exist? at which step did you come up against that?
The 'downloads' folder in your home folder you have to make on your own(open home folder(places menu>home, right click and create new folder, name it downloads, copy the alsa archive files into it).
Then open a terminal and type in those commands, and follow the steps sequentially.
I'm not sure which directory you have trouble with, so could you post step by step what you did and where you have trouble?
It's past 3:50 AM here now, and I'm just going to grab some shuteye now(was up studying, just thought I'd check up on this thread before I went to bed). I'll be back in a couple of hours and see how it's going.
bye

---

### Post by kristeng on 2008-01-11
```
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```

These were the ones that I was having problems with, they were saying that the directories didn't exist.
I really appreciate all of your help, thank you. (:

---

### Post by balaknair on 2008-01-11
it's case sensitive
In your home folder is the folder named Downloads or downloads? :D I'd made the same mistake first. I'll just lay it out 

the command _cd /usr/src/alsa_ opens the new directory /usr/src/alsa and_sudo cp ~/downloads/alsa* ._ copies all the alsa files (the 3 archives you downloaded)from the folder named  downloads into the current folder( /usr/src/alsa)
then _sudo tar xjf alsa-driver*.bz2_ is the command to extract the archive alsa-driver-1.0.15(you can try replacing the * with -1.0.15) and so on. Could you check the file names are correct?
If you're unsure whether the files have been copied, try this graphically

hit alt+F2-----> this will open a run dialog----> type in "gksudo nautilus" without the quotes----> it'll ask for your password- enter password---->this will open an instance of nautilus(the file browser) with root privileges----> now navigate to the /usr/src/alsa folder and check if the three alsa tar.bz2 archives are present----> right click each one and extract
now return to the terminal and type

cd usr/src/alsa/alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

and proceed with the rest of the steps(exactly as I've posted  earlier)

this I think should solve the missing directory issue.

---


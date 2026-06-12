---
title: "[SOLVED] ibook clamshell"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by ReaRea on 2008-10-22
Hi, I've recently aquired a 2000 ibook M6411 (clamshell). I was wondering if there is a certain version of Ubuntu to put on it or would the current one work?

PowerPC G3
Mac OS 9.0.4
Mac OS ROM 5.3.1
9.36GB HD
466MHz
64MB memory

Never really used a mac before and the system is outdated anyway (it has IE5 & Netscape 4.7 on it). Looking to see if there's a OS that'll run on it. Any advice is appreciated.

---

### Post by cyberdork33 on 2008-10-22
You have to use the PowerPC version of Ubuntu...

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by tgalati4 on 2008-10-22
Tiger runs OK, but max out the memory.  PPC Ubuntu is fiddly.

---

### Post by cyberdork33 on 2008-10-23
> **ReaRea said:**
> Never really used a mac before and the system is outdated anyway (it has IE5 & Netscape 4.7 on it). Looking to see if there's a OS that'll run on it. Any advice is appreciated.

PS, IE5 was the last version of IE that was released for Mac.

---

### Post by Frak on 2008-10-23
I'd also try Fedora PPC. It runs somewhat nicely (in comparison to Ubuntu, no offence)

---

### Post by ReaRea on 2008-10-23
I attempted to install 7.10 alt ppc version. It went through the install and rebooted. When it rebooted it flashes what looks like the GUI then in a split second goes to a white screen with text then goes to this
> 
[  26.521623] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[  36.414604] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[http://i252.photobucket.com/albums/hh7/Rea_Rea11/DSCF0524.jpg](http://i252.photobucket.com/albums/hh7/Rea_Rea11/DSCF0524.jpg)
first three lines load, then after a few minutes the rest pops up
any ideas

---

### Post by brain2008 on 2008-10-24
Three distinct designs of the iBook were introduced during its lifetime. The first design, known as the "Clamshell", was a significant departure from portable computer designs at the time, due to its shape, bright colors, inclusion of a handle, and support for wireless networking.
=====================================================
Brian
Our mission is to provide high quality end to end solutions to the BPO segment in a manner that will improve the operational efficiency while reducing the cost of the services to the client.
[email]4thdimension1@gmail.com[/email]

---

### Post by oswaldkelso on 2008-10-24
The minimum system requirements are 256 MB of RAM for the default desktop. You could run a lighter desktop or a distro more suited to less ram. Debian, Slackintosh, and Gentoo would be my recommends for ppc. In order of ease of installation. 

The real answer is get more Ram. Then install the distro you want, not the distro you have to.

---

### Post by ReaRea on 2008-10-25
Tried installing Xubuntu 6.06 (I figured I'd upgrade later if needed). It installed. Booted up. Then went to a black screen. I'm thinking either the drivers arent there or the video card isnt right? I can actually log in and hear it processing and all, just cant see it.
How would I go about checking to see what the problem is and putting the drivers on if that's the problem?

PS: This is really my first experiences working with Linux and a Mac

---

### Post by tiresia on 2008-10-25
You can get a shell pressing ctrl+opt+F1 (or F2-F6) and set up your system. 
Most probably you need to edit your xorg.conf file (/etc/X11/xorg.conf)
```
sudo nano /etc/X11/xorg.conf
```

I don't know your model, but it can be, that it support only a resolution 800x600
If MacOS9 is still installed, you can get more information from there.

Before editing the xorg.conf file make a backup
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by ReaRea on 2008-10-25
> **ReaRea said:**
> 2000 ibook M6411 (clamshell)
PowerPC G3
Mac OS 9.0.4
Mac OS ROM 5.3.1
9.36GB HD
466MHz
64MB memory


Tried steps listed [https://wiki.ubuntu.com/PowerPCKnownIssues#Blank](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank) screen on iMac G3 but GUI still doesnt work. Anything else I can try?

---

### Post by tiresia on 2008-10-25
Start please again your computer and at the yaboot prompt type video=ofonly.
Can you please post your xorg.conf file (at least the section "Screen")?

---

### Post by ReaRea on 2008-10-25
```

Section "Screen"
    Identifier   "Default Screen"
    Device       "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
    Monitor      "Generic Monitor"
    DefaultDepth 24
    SubSection "Display"
           Depth       1
           Modes       "1024x768" "800x600" "640x480"
           EndSubSection
   
```
It also lists depth 4, 8, 15, 16, and 24 but all are the same as 1

---

### Post by tiresia on 2008-10-25
As I said, I don't know your model, but you can try following:
1. Make a Backup of the file!!!
2. Change the Default Depth to 16
3. If it does not work, remove from the line Modes "1024x768"
4. Try the other combination: Default Depth 24 and Modes "800x600"

---

### Post by tiresia on 2008-10-25
I think I found the right links for your model

It looks like your Mac is this one:
[http://www.everymac.com/systems/apple/ibook/stats/ibook_se_466.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_se_466.html)

Your grafic card is a "ATI Rage Mobility M3 AGP 2x"
Edit the xorg.conf file following this link
[http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x](http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x)

I think it's very important for you to find more RAM (have a look on eBay)

---

### Post by stir-crazy on 2008-10-25
> **Frak said:**
> I'd also try Fedora PPC. It runs somewhat nicely (in comparison to Ubuntu, no offence)

From my experience, gotta disagree.  Just yesterday switched back from Fedora to Ubuntu 8.04 on my wife's Tangerine iBook.  Fedora just bogged down the poor thing, and I'm maxed out on RAM @ 542 (though it reads 565...go figure).

I originally had Xubuntu on this, but tried out Fedora because I read that it could get the Airport card to work with WPA encryption...it can't btw.

---

### Post by ReaRea on 2008-10-25
Thanks to everyone who helped. Fixed it. Was ready to throw in the towel on it but kept at it. Played with the Hor/Vert

Original Code (Xubuntu 6.06)
```

Section "Module"
     Load    "dri"
EndSection
Section "Monitor"
     HorizSync   28-51
     VertRefresh 43-60
EndSection
Section "Screen"
     DefaultDept    24
<all (1, 4, 8, 15, 16, and 24) SubSection "Display" the same>
     Modes      "1024x768" "800x600" "640x480"
EndSection
```
Changed Code
```

Section "Module"
     #Load   "dri"
EndSection
Section "Monitor"
     HorizSync    30-80
     VertRefresh  50-120
EndSection
Section "Screen"
     DefaultDepth    16
<changed all (1, 4, 8, 15, 16, and 24) SubSection "Display" to>
     Modes       "800x600" "640x480"
EndSection
```

---

### Post by tiresia on 2008-10-26
In some links I have seen that it should be possible also a resolution of '1024x768'
Maybe you can try it (with default Depth 16)
You can search also in this forum for more information

---

### Post by stir-crazy on 2008-11-06
> **tiresia said:**
> In some links I have seen that it should be possible also a resolution of '1024x768'
Maybe you can try it (with default Depth 16)
You can search also in this forum for more information

Possible, yes, after insane modifications to the hardware and firmware.  It's out there on the forums, but can't be achieved on a standard iBook screen.

---

### Post by stream303 on 2008-11-09
If you are indeed running 7.10, you may want to look into getting a small performance boost and possibly a longer hard-drive life by adding **noatime** to your /etc/fstab file:

[http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime](http://ubuntuforums.org/showthread.php?t=692318&highlight=noatime)

IIRC, Hardy+ uses a relative of noatime, "relatime" to achieve much the same, but noatime should work well on earlier releases.

---


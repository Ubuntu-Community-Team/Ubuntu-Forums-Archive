---
title: "Professor Fate --- I killed it!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by professor fate on 2007-10-24
My God, I think I've killed it! I'm not kidding. This is what I did. I got into the Compiz Settings Manager (CSM) and selected the "screen shot" option. I closed the manager and in turn it rendered everything unusable. For instance, I cannot use the CSM, the Synaptic Package Manager, the Internet (on my work computer now), etc. I mean, nothing works. I've restarted several times. I get the desktop, but I can't control the computer.  Any ideas?

---

### Post by professor fate on 2007-10-24
i was told on another thread to restart > options > failsafe terminal.  now what?

---

### Post by p_quarles on 2007-10-24
```
cd /var/log
ls
```
Those two commands will take you to your logs directory and then display the files. I would start by looking at faillog by typing:
```
less faillog
```
That might give a clue to what's wrong. If it's empty (as it normally should be), next check dmesg and syslog using the same command (less). Press the "q" key to leave "less."

I'm guessing it's an X server problem, but it would be wise to make sure first. :)

---

### Post by professor fate on 2007-10-24
OK...I have a Syslog and a Syslog.o.  I have four dmesg files.  (I like the red color.  Must be important).  And I have a faillog.  

I keyed in less faillog and said that the may be binary.  Well, it was.  lol. 
The other stuff had info, but I don't know what I'm looking for and I can't really cut and paste it here.

---

### Post by p_quarles on 2007-10-24
In syslog and dmesg (the ones without numbers on the end -- those are  the most recent), did you see anything indicating an error and/or anything related to the X server? Anything related to the network?

---

### Post by professor fate on 2007-10-24
> **p_quarles said:**
> In syslog and dmesg (the ones without numbers on the end -- those are  the most recent), did you see anything indicating an error and/or anything related to the X server? Anything related to the network?

The syslog shows a lot of disconnected network manager

---

### Post by Dr Small on 2007-10-24
Have you tried killing compiz-fusions ?

---

### Post by professor fate on 2007-10-24
> **Dr Small said:**
> Have you tried killing compiz-fusions ?


I tried that.  I opened up the Systems Manager but that's all it will let me do: open it.  I can't access anything.  I click on it and I get no activity.  It's this way for everything.  It's odd in that none of the "close" buttons work.  I have to use the upper right x to close everything.

---

### Post by Dr Small on 2007-10-24
I do not have compiz, so i can not test anything, but here is what I would try, if I were in your shoes.

Find the pidnumber of compiz-fusion
```
ps aux | grep compiz
```
(You may have to try alternate methods, meaning where "compiz" is, to find the actual application).

Then I would issue:
```
kill *pidnumber*
```

I would then remove it from my Sessions, so it does not automatically start up, and then you can try to fool with it from there.

Dr Small

---

### Post by p_quarles on 2007-10-24
> **professor fate said:**
> The syslog shows a lot of disconnected network manager
Ethernet or wireless? 

Also, check /var/log/messages -- does it indicate anything of interest happening right around the time that the GUI stopped responding?

---

### Post by rorestuff on 2007-10-24
A couple quick and dirty solutions:

remove compiz
```
sudo aptitude remove compiz-fusion
```

Or

install another Window Manager to at least gain access to your system.
You can try KDE
```
sudo aptitude install kubuntu-desktop
```
or something lighter like IceWM
```
sudo aptitude install icewm
```

---

### Post by Crashmaxx on 2007-10-24
Okay, it took me a minute to find the keys I wanted to edit and the proper syntax to do it in the command line. To disable compiz, type in these two commands:
```

gconftool-2 --type string --set /desktop/applications/window_manager/default "/usr/bin/metacity"
gconftool-2 --type string --set /desktop/gnome/applications/window_manager/default "/usr/bin/metacity"

```
Then do a <Ctrl><Alt>Backspace and log in again. If that doesn't work, type in:
```

sudo gdm

```
and then log in normally.

And a nice tip, if you want a command line like you have now when you are logged in and have trouble, just do <Ctrl><Alt>F2 and to get back do <Ctrl><Alt>F9. Linux runs what are called terminals, 1 is for start up, 2-6 are just extra, 7 usually is the X-server(GUI), but I just tried it and it was on 9 now. Doing the combo I just said just switches them. So if F9 is wrong, then try F7 and then the other F#'s.

Hopefully, that will get you back up and running for the moment. If you want to turn compiz back on, at least go into CSM and turn off screenshot since that is what seems to have caused the issue.

---

### Post by professor fate on 2007-10-24
All wireless.  

This is what I'm going to do.  It's no hair off my nuts for me to reinstall this. Compiz is not the end all be all for me, so I'll just keep it standard and move on to bigger fish.  I'm much more concerned about sound and getting one radio station I listen to on the net.  I'm going get this thing installed again then go home.  I'll be on a bit later tonight provided I can get the wireless internet working again. :)

---

### Post by Crashmaxx on 2007-10-24
> **Dr Small said:**
> I do not have compiz, so i can not test anything, but here is what I would try, if I were in your shoes.

Find the pidnumber of compiz-fusion
```
ps aux | grep compiz
```
(You may have to try alternate methods, meaning where "compiz" is, to find the actual application).

Then I would issue:
```
kill *pidnumber*
```

I would then remove it from my Sessions, so it does not automatically start up, and then you can try to fool with it from there.

Dr Small

Compiz is setup differently, so it is not in sessions anymore. And if he wanted to try this, ```
metacity --replace
``` would be better. But I don't believe he has an X-server running at the moment so I doubt either of these would work.

> 
A couple quick and dirty solutions:


Those may work, but let's not have him try other window managers, nor remove compiz completely at the moment.

I recommend you try what I said in my last post first, then removing compiz may be worth trying, although, if mine doesn't work, compiz may not be the problem.

---

### Post by Crashmaxx on 2007-10-24
> **professor fate said:**
> All wireless.  

This is what I'm going to do.  It's no hair off my nuts for me to reinstall this. Compiz is not the end all be all for me, so I'll just keep it standard and move on to bigger fish.  I'm much more concerned about sound and getting one radio station I listen to on the net.  I'm going get this thing installed again then go home.  I'll be on a bit later tonight provided I can get the wireless internet working again. :)

That will work, but please just try my idea first. I spent a little bit of time here hunting done the proper commands to fix it for you, please don't give up yet.

---

### Post by p_quarles on 2007-10-24
> **professor fate said:**
> All wireless.  

This is what I'm going to do.  It's no hair off my nuts for me to reinstall this. Compiz is not the end all be all for me, so I'll just keep it standard and move on to bigger fish.  I'm much more concerned about sound and getting one radio station I listen to on the net.  I'm going get this thing installed again then go home.  I'll be on a bit later tonight provided I can get the wireless internet working again. :)
That's what I would do, but I'm always reluctant to suggest it to others (kind of a copout as "advice," you know). 

Anyway, you should give Crashmaxx's suggestions a try first. That very well may fix things.

---

### Post by professor fate on 2007-10-24
> **Crashmaxx said:**
> That will work, but please just try my idea first. I spent a little bit of time here hunting done the proper commands to fix it for you, please don't give up yet.

Sorry, but I just checked in and saw your post.  Ubuntu is reinstalling at this moment.  Thanks for the effort though.

---

### Post by Matakoo on 2007-10-24
> **professor fate said:**
> All wireless.  

This is what I'm going to do.  It's no hair off my nuts for me to reinstall this. Compiz is not the end all be all for me, so I'll just keep it standard and move on to bigger fish.  I'm much more concerned about sound and getting one radio station I listen to on the net.  I'm going get this thing installed again then go home.  I'll be on a bit later tonight provided I can get the wireless internet working again. :)

Welcome to the club ;) I can't remember how many times I caused a problem I couldn't fix when I was a Linux-newbie...good thing is that once you're an intermediary user or higher, things can usually be fixed without the drastic reinstall option.

As far as your sound goes, you can try the following:
1.Create a backup-directory.
2.Hit Control-H to show all files.
3. Look for the files two files with names starting with .asound. (files starting with a  full-stop are hidden files).
4. Move those into your backup-directory.
5. Hit control-h again to hide the hidden files.
6. Log out of Gnome and in again

Now sound should hopefully work. That little quick-and-dirty trick fixed the sound on all three Gutsy-machines I have installed. 

If it doesn't, open up a terminal and issue the following command:

sudo lspci

That gives you a list of your installed hardware. Find the line that indicates what audio-hardware you have, and post it. Makes it a lot easier to see if it is possible to get it to work.

---

### Post by Crashmaxx on 2007-10-24
> **professor fate said:**
> Sorry, but I just checked in and saw your post.  Ubuntu is reinstalling at this moment.  Thanks for the effort though.

Too bad. Anyway, if you see this before its not too late. I recommend repartitioning it so that you have a separate /home. This way if you need to (or prefer to) reinstall again, you can keep all you user settings and data in tact.

if it is too late, but you'd still like to try this, see here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't think you need to install GParted on the live CD anymore. I'm pretty sure its there by default. But if you run the command and its installed, it will just tell you its installed, so no biggie.

---

### Post by professor fate on 2007-10-24
> **Crashmaxx said:**
> Too bad. Anyway, if you see this before its not too late. I recommend repartitioning it so that you have a separate /home. This way if you need to (or prefer to) reinstall again, you can keep all you user settings and data in tact.

if it is too late, but you'd still like to try this, see here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't think you need to install GParted on the live CD anymore. I'm pretty sure its there by default. But if you run the command and its installed, it will just tell you its installed, so no biggie.

Are the user settings you're talking about like backing up the registry in Windows?

---

### Post by professor fate on 2007-10-24
> **Matakoo said:**
> 

If it doesn't, open up a terminal and issue the following command:

sudo lspci

That gives you a list of your installed hardware. Find the line that indicates what audio-hardware you have, and post it. Makes it a lot easier to see if it is possible to get it to work.

Here is what I got with the lspci comand:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by Matakoo on 2007-10-24
> **professor fate said:**
> Here is what I got with the lspci comand:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Should work. Have you managed to get any sound whatsoever out of the computer?

---

### Post by FuturePilot on 2007-10-24
> **Matakoo said:**
> Should work. 

Not yet. Took me a lot of work to get that working. It was easier in Gutsy though.
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559")

---

### Post by Matakoo on 2007-10-24
> **professor fate said:**
> Are the user settings you're talking about like backing up the registry in Windows?

Sort of, yeah. Except that if you have /home on a separate partition and take care not to reformat it while reinstalling, the user settings do not have to be backed up explicitly as the windows registry.

Say you've set up your desktop just like you want it. Your preferred wallpaper, that font goes there, this font goes there, a nice color-scheme and what not (and maybe even installed some extra fonts or icon packs). And you've added a lot of bookmarks to Firefox as well as making Firefox remember your identity on a couple of sites.

Now, if the worst happens and you need to reinstall your system...well, let's just say that your previous settings are "magically" restored when you login the first time on your fresh installation.

---

### Post by Matakoo on 2007-10-24
> **FuturePilot said:**
> Not yet. Took me a lot of work to get that working. It was easier in Gutsy though.
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/130559)

Damn. Was it enough with the backports modules?

---

### Post by FuturePilot on 2007-10-24
> **Matakoo said:**
> Damn. Was it enough with the backports modules?

Yep. That did it for me. It was a nightmare on Feisty though. I already suggested this to PF but he said it didn't work:confused:

---


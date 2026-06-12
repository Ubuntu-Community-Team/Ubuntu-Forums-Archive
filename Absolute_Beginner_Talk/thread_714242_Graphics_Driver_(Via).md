---
title: "Graphics Driver (Via)"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by James Haigh on 2008-03-03
Hi, I only have 1 main problem left: Graphics.

The resolution is 800x600 when it should be 1280x800 and 'Desktop effects could not be enabled'. Which driver do I need? This page has too many; I don't know which 1 is the right 1.

[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)

Thanks.

James.

---

### Post by forestpixie on 2008-03-03
if you do this in a terminal it might give some clue as to what card you've got 

```
lspci |grep VGA
``` or
```
lspci
```

---

### Post by James Haigh on 2008-03-03
Sorry, I forgot.

```
james@james-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

---

### Post by forestpixie on 2008-03-03
it appears that all the buntu 7.10 drivers are the same - coulkd check by physically looking at the card - but I'd try that if it was me

[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=159](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=159)

hope that helps some

---

### Post by ryanhaigh on 2008-03-03
You will not be able to run desktop effects on your system with the via graphics card no matter what driver you use. Attatch a copy of /etc/X11/xorg.conf so that we can see what driver is currently being used and also your graphics configuration. Ubuntu provides the via drivers without needing to download from the web.

---

### Post by RussellGee on 2008-03-03
Here is the download link from the website:

[http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip](http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip)

Theres instructions with it on how to use it and this will automaticly set up your xorg.conf.

Russell

---

### Post by James Haigh on 2008-03-04
Thanks RussellGee!

My max res is now 1024x768 which is a lot less cramped and looks better. My screen is 1280x800 so it is not a complete solution but I'm half way there!

ryanhaigh,

I attached xorg.conf (After installing what RussellGee suggested). I don't really mind about desktop effects, it's just a bonus, I can't miss what I didn't have.

Are we somehow related? Lol!

Thanks.

James.

---

### Post by ryanhaigh on 2008-03-04
I know that you will need this

```

	SubSection "Display"
		Modes  "1280x800"
		Depth		24
	EndSubSection

```

but I also think you will need a corresponding modeline (Monitor section) and I do not know what that would be. Howerver [this page can work one out for you]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl"). I have created one and attached the screenshot.

On my laptop I had to remove all other resolutions...you may not have to just keep it in mind. As always backup the config first.


Haha I hadn't noticed, same last names, same os, same forum/thread we MUST be related. (ok bit of a stretch there)

---

### Post by James Haigh on 2008-03-04
Hey Ryan, something else in common, you joined this forum only 2 days after me! So how come I'm a newb and your not? How do you know that via cannot run desktop effects? I didn't try your solution sorry because I'm not sure of the risks. The method appears to force the res. Even if I backed up xorg.conf and the graphics failed how would I be able to restore it if I cannot see what I am doing?

I noticed some strange things about RussellGee's solution: My touchpad started tap clicking and the tab with this option in mouse preferences had disappeared. Also my user name in the top panel has moved (Which doesn't bother me.) How odd!

Ps. Ryan, I live in Shropshire (UK), and my ancestors are from Huddersfield. I think that's where a lot of Haighs come from. You live in Australia, wow! Haighs far and wide! Lol! I think we have too much in common not to be buddies.

James.

---

### Post by forestpixie on 2008-03-04
> Even if I backed up xorg.conf and the graphics failed how would I be able to restore it if I cannot see what I am doing?

if the graphics failed - start in recovery mode - then use this command, replacing with real file names - assuming you kept the backup in the same place ie - /etc/X11

don't think you need sudo in recovery mode - so without sudo

```
mv /etc/X11/*nameofbackup* /etc/X11/xorg.conf
```

that copys the file 'nameofbackup' to xorg.conf

---

### Post by James Haigh on 2008-03-04
Thanks forestpixie,

I now feel brave enough to give Ryan's solution a go. Lol! I will see what happens.

---

### Post by Tatty on 2008-03-04
[https://help.ubuntu.com/community/ViaEpiaDriHowto?highlight=%28via%29]("https://help.ubuntu.com/community/ViaEpiaDriHowto?highlight=%28via%29")

This page is rather out of date now and looks a bit heavy, but might be worth reading if you are struggling.

---

### Post by ryanhaigh on 2008-03-04
Ive been using Linux (suse/debian/ubuntu) for a few years now which has given me a LITTLE bit of knowledge, enough that I can try and help some people. I have actually been a member of this forum for a while but I decided I wanted to contribute more actively and made a new user account here, on launchpad and brainstorm.

I actually have a via based laptop (which I am lending my brother at the moment) which is how I know you cannot run desktop effects, although you can use an alternate compositor call xcompmgr but it was buggy and slow for me. Basically the reason you can't have compiz enabled is that the driver isn't good enough, when I was doing my research to solve my own problem I read that the way it works makes it slow and not to hold my breath for aiglx support.

As forestpixie indicated it is quite easy to restore your graphics configuration. Hopefully if the graphics failed you would get the bulletproof x environment where you could fix it from the gui, either way I find it easier to do from the command line...so using applications>terminal
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup #to create the backup
sudo nano /etc/X11/xorg.conf #to edit the file (change nano to gedit if u want to use the gui editor)

```
Make the changes discussed earlier.

Test your configuration by pressing control+alt+backspace to restart X (the whole GUI environment) closing anything you are working on first. If all goes well you will get a login screen with the right resolution for your monitor.

If the configuration fails you will either get bulletproof x (kinda like safe mode) you can change to a terminal by pressing control+alt+F1 or just the terminal. From there you can do the following to restore your working config and restart X.

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf #restores the backup
sudo /etc/init.d/gdm restart #this restarts the login manager and X

```

As far as the other ubuntu issues go: panel applets will sometimes move when you logout/in if they are not locked and rarely even if they are. For the mouse, the driver probably changed your config which has resulted in these changes, you can see if it created a backup of your old xorg.conf in the /etc/X11 directory and either restore it completely or just the sections related to the mouse.

I know that my ancestors are from the UK, my grandmother has a pretty extensive family tree which goes back a long way, I should ask if we are from Huddersfield.

---

### Post by James Haigh on 2008-03-08
After messing with xorg.conf for a while, I got 1280x800! I should have replied earlier (On Wednesday) but I've been quite busy and I haven't always had internet access. I have had 1280x800 for 3 days.

I tried to work out what worked and I'm not really sure. I worked out that there are 3 sections of xorg.conf that are relevant not 2. I attached the sections that worked. I noticed that my driver was set to 'vesa' not 'via' in my original backup. The config even worked after uninstalling the driver from RussellGee.

However, I reinstalled Ubuntu for another reason and changing those sections failed and I got that bullet proof 'X' thing you were talking about. I don't really know what worked anymore. I've spent a lot of time messing and trying to find the solution myself, it is a good learning experience and allows other newbs more attention. But I'm stuck again with 800x600.

The link at the start of this thread is probably the simplest solution but how do I find my chipset ID?

[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)

Ryan, even so, your last reply was useful, thanks.

James.

---

### Post by ryanhaigh on 2008-03-08
The ouput of ```
lspci -v
``` will display the info you need just look for the graphics/vga controller in the list.

Can you post your new xorg.conf, you shouldn't need to install third party drivers I believe those are the same ones already packaged with ubuntu. Actually if you go to the next page (click on any driver) you will see that the one they supply works for all of them which makes me even more sure it is the same via driver as used in ubuntu.

---

### Post by James Haigh on 2008-03-09
I am now very confused with the Via website; It is not very good.

I Googled 'VGA'. it means 'Video Graphics Array'. I didn't know why there was so much Via stuff yet only 'VGA' is relevant. I think my laptop is based on Via. It is Fujitsu Siemens. Maybe -vvv will help.

```

james@james-laptop:~$ lspci -vvv > ~/Desktop/lspci-vvv.txt

Relevant section:
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
	Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10ae
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min)
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Region 1: Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>

```

I haven't changed xorg.conf since I reinstalled Ubuntu but I attached it anyway. What is 'vesa'?

Thanks.

---

### Post by ryanhaigh on 2008-03-09
vesa is a generic driver that will work with most graphics cards but doesn't provide any 3d features or anything like that.
The first thing that I would do is to make a backup of your xorg.conf file as discussed above.
You can then try using ubuntus built in graphics config tool in system>admininstration>screens and graphics. Under the graphics card tab change the driver to via and under the screen tab change the model to generic lcd at 1280x800. I haven't used this in a while so Im not sure what the buttons are but I assume there is a ok button to save your config, you may even be able to test it first. 

Alternately you can open the xorg.conf file, as above, in whichever editor you want to use (gedit/nano) and change vesa to via, also change "800x600" to "1280x800" and then restart the x server by pressing ctrl+alt+backspace.

Of course if things go bad you can always revert to the previous config, in fact if via doesn't work you could try using 1280x800 with the vesa driver although I am not sure how well it will work.

---


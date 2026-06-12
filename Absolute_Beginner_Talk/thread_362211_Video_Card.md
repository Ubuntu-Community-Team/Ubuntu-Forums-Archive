---
title: "Video Card"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-02-15
Ok , I guess i start at the beginning with a problem everyone will likely have. 

My video card is stuck at 800x600 in ubuntu
The screen resolution preferences give no other choices

I know my video card on the old clunker can do better , its 128megs.

How do I find out the brand name ?

Where do I get drivers for it ?

How does one install video drivers in Ubuntu ?

---

### Post by taurus on 2007-02-15
Applications -> Accessories -> Terminal
```
lspci
```
And post the output here.  You just need to install a driver for it before you can get higher resolutions.

---

### Post by koconnor100 on 2007-02-15
wow, what a lot of gobbily gook... but I see it's an nvidea
-------------------------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by mysticrider92 on 2007-02-15
First, try opening a terminal and type 'lspci'. Look for a line that says video card, display adapter, or something similar. That should tell you the make of the card. 

After that, type 'sudo gedit /etc/X11/xorg.conf' in a terminal. Scroll down and look for a line that says device. It should have at least the card name there. Open Synaptic (System>Administration>Synaptic Package Manager) and search for the drivers for your video card (probably nVidia or nvidia-glx). Install them, then put the driver name in the xorg.conf under 'device' where it says 'driver'. For my card it is just nvidia, it could be different for your card. Go down to 'default screen' and put in your screen resolution under the color depth you want. Save the file and close anything that is open. Press <Ctrl><Alt><backspace> and log back in. It should now be in the correct mode.

[edit] Looks like you got there before me.

---

### Post by taurus on 2007-02-15
```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

It is an nVidia.  Here's a guide to install nVidia driver for your graphic card.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by aktiwers on 2007-02-15
I Installed my nVidia card successfully with this automated script
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Great script!

---

### Post by koconnor100 on 2007-02-15
> **aktiwers said:**
> I Installed my nVidia card successfully with this automated script
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Great script!

I ran it , rebooted Ubuntu (ugh ... I was testing how long before it would crash ...I was up to four days ...now I have to start over). 

I swear the menu icon's are "prettier" , but my screen resolution is still stuck at 60hz 800x600 max, and I was kind of hoping to go up from that.

---

### Post by aktiwers on 2007-02-15
Did it crash your machine?
And did you follow the guide on the page?

---

### Post by aktiwers on 2007-02-15
This is from the site:

[COLOR=#3366FF]Instructions[/COLOR][FONT=FreeSans][B]
						 						[/B][/FONT][FONT=FreeSans][/FONT]
 						 						
 						 						[COLOR=#FF0000][FONT=FreeSans]**NOTE: 						Make sure you have all the repositories enabled (also universe and 						multiverse) in your */etc/apt/sources.list***[/FONT][/COLOR][FONT=FreeSans] 						[/FONT]
 						 						[FONT=FreeSans] 						If you do not know how to enable those repositories, please take a look 						at this page:[/FONT]
 						 						[enabling_extra_repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
 						 						[FONT=FreeSans][B]
						 						How to Install the 						package
						 						
						 						1) Download and install the deb package
						 						
						 						2) Log out and press CTRL+ALT+F1 [/B][/FONT][FONT=FreeSans](so as to get out of the 						Desktop Environment, i.e.[/FONT][FONT=FreeSans]** 						[COLOR=#FF0000]you'll see ONLY the 						command line[/COLOR]**[/FONT][FONT=FreeSans])[/FONT][FONT=FreeSans][B]
						 						
						 						3) Log in [/B][/FONT][FONT=FreeSans](if 						required)[/FONT][FONT=FreeSans][B]
						 						
						 						4) Run "envy" by opening Terminal or Konsole and typing (quite 						obviously):
						 						
						 						[/B][/FONT] 						 						 						 						 						 						 						**envy** 						 						 						 						 						 						 						[FONT=FreeSans]****[/FONT]
 						 						[FONT=FreeSans]**5) 						Choose to install or 						uninstall the driver (from the textual interface)**[/FONT]

---

### Post by headphase on 2007-02-15
How do I install mine? It's a Intel Corporation Mobile Integrated Graphics Controller (rev 03).  I saw the FAQ thread for Intel 945, but I don't know how to do the alien.

---

### Post by koconnor100 on 2007-02-15
Yes , i was just re-reading the site. Forgot to Cntl-Alt-F1 to the dos prompt (linux promt ?) and run envy.  Took me on a ride that reminded me of my old dos days. Also impressed me as to how my high speed lite connection managed 112kb/s even though my winxp machine is streaming tunes in the background to listen to while this is going on. (router, both computers online). 

This is much better. 1000 x 700 ( more or less) resolution. Now maybe the bottom of half the applications and install programs won't be clipped so as to make them unusable. :)
:lolflag: 


> **aktiwers said:**
> This is from the site:

[COLOR=#3366FF]Instructions[/COLOR][FONT=FreeSans][B]
						 						[/B][/FONT][FONT=FreeSans][/FONT]
 						 						
 						 						[COLOR=#FF0000][FONT=FreeSans]**NOTE: 						Make sure you have all the repositories enabled (also universe and 						multiverse) in your */etc/apt/sources.list***[/FONT][/COLOR][FONT=FreeSans] 						[/FONT]
 						 						[FONT=FreeSans] 						If you do not know how to enable those repositories, please take a look 						at this page:[/FONT]
 						 						[enabling_extra_repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
 						 						[FONT=FreeSans][B]
						 						How to Install the 						package
						 						
						 						1) Download and install the deb package
						 						
						 						2) Log out and press CTRL+ALT+F1 [/B][/FONT][FONT=FreeSans](so as to get out of the 						Desktop Environment, i.e.[/FONT][FONT=FreeSans]** 						[COLOR=#FF0000]you'll see ONLY the 						command line[/COLOR]**[/FONT][FONT=FreeSans])[/FONT][FONT=FreeSans][B]
						 						
						 						3) Log in [/B][/FONT][FONT=FreeSans](if 						required)[/FONT][FONT=FreeSans][B]
						 						
						 						4) Run "envy" by opening Terminal or Konsole and typing (quite 						obviously):
						 						
						 						[/B][/FONT] 						 						 						 						 						 						 						**envy** 						 						 						 						 						 						 						[FONT=FreeSans]****[/FONT]
 						 						[FONT=FreeSans]**5) 						Choose to install or 						uninstall the driver (from the textual interface)**[/FONT]

---

### Post by aktiwers on 2007-02-15
> How do I install mine? It's a Intel Corporation Mobile Integrated Graphics Controller (rev 03). I saw the FAQ thread for Intel 945, but I don't know how to do the alien.

did you ```
sudo apt-get install alien
```  ?

---

### Post by Maestro23 on 2007-02-15
> **aktiwers said:**
> did you ```
sudo apt-get install alien
```  ?

And just to piggyback, more helpful threads:

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                                     [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


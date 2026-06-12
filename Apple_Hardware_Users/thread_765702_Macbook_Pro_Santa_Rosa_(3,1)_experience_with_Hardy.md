---
title: "Macbook Pro Santa Rosa (3,1) experience with Hardy"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by CodeSamurai on 2008-04-24
Hey all.  I installed the RC a couple days ago.  Is there any reason I should reinstall with the final version?  Either way, here is my experience so far:

Wireless works great! I configured madwifi using subversion and have had no problems thus far.  

Battery Life is awesome! I'm actually getting better battery life in Hardy than I did in OS X.  I'm close to 3.5 hours with wireless on, light internet, open office and brightness set to about 3/4.  Not bad at all.  I did have an issue today where powertop reported acpi wakeups at about 500 (twice as much as I pulled without it) so the battery life dropped significantly.  I restarted and it was gone.

Compizfusion works fine.  It gets a little jumpy sometimes, but nothing bad. 

Backlit keyboard does not work (yet)  I'm still looking for a fix for this.  Any ideas?  

iSight works fine.  

Keymapping is fine.

Volume is a little weird.  Is there a way to change the increments in which volume is adjusted? I'm getting really large jumps when adjusting PCM, and when I use Master Volume the bottom half of the volume bar is non-audible.  Any ideas?

Let me know if you guys want to know anything else.  It's been awhile since I used Ubuntu last (finally got rid of OS X for the last time) so I'm a little rusty, but I'll catch back up again.  

Once again, is there any reason I should update to the final or am I ok with the newest RC?  Thanks!

Trent out

---

### Post by slacka-vt on 2008-04-24
This is very interesting as I am on a PowerMac G5 (ppc architecture) and those are my exact tiny qualms with how Hardy works. I have been using through the developmental cycle for about 2 months now.

The volume seems to almost mute between "usable" volume increments. :confused:

As far as compiz, animated windows is a little jumpy but still fun 8) and workspaces cube
won't let me change the top and bottom pics. :confused:

This are extremely miniscule nuances in comparison to the over all great performance of this wonderful OS

Awesome, Awesome OS Ubuntu Team !!!!!!   :guitar:

~s

---

### Post by Tamiyadd on 2008-04-25
i have problem with sound :( it doesn't work!

when i try to reload the module with 
```
rmmod snd_hda_intel
```

he say:
ERROR: Module snd_hda_intel is in use

someone can help me?

---

### Post by guj4_n3b3sk4 on 2008-04-25
> **Tamiyadd said:**
> i have problem with sound :( it doesn't work!

when i try to reload the module with 
```
rmmod snd_hda_intel
```

he say:
ERROR: Module snd_hda_intel is in use

someone can help me?

Problem solved on the other thread with:
```

alsamixer
```

---

### Post by cyberdork33 on 2008-04-25
> **CodeSamurai said:**
> Hey all.  I installed the RC a couple days ago.  Is there any reason I should reinstall with the final version?
no, they are almost identical from what I can tell. If you have been upgrading the dev versions all along then I might do a clean install, but if you just installed RC, then I would stick with it.

> **CodeSamurai said:**
> Backlit keyboard does not work (yet)  I'm still looking for a fix for this.  Any ideas?Did you install pommed yet?

> **CodeSamurai said:**
> Volume is a little weird. Is there a way to change the increments in which volume is adjusted? I'm getting really large jumps when adjusting PCM, and when I use Master Volume the bottom half of the volume bar is non-audible. Any ideas?
I know that my audio is usually not controllable at all with the Master control. I have to adjust PCM. I would start alsamixer in the terminal and see the effects of adjusting the different channels. It might be that pulling up one of the channels makes the master control work more as expected.

---

### Post by 9192 on 2008-04-25
Codesamurai,
Which version did you install on your MBP, x86 or 64?
I have Santa Rosa MBP too and really want to get it work full time on mine.  However, how did you get the wireless work with madwifi (I am a newbie) or it just wrks out of the box?  

Thanks,

9192

---

### Post by CodeSamurai on 2008-04-25
@cyberdork33> Did you install pommed yet?
Yes I have actually.  The graphical interface pops up when I press the "brighten" button for the keyboard, but nothing happens.  Any other ideas?

Update on Volume:  Got it working nicely.  For some reason, PCM and Master were adjusting together so I could never get good volume increments (PCM has a lower range than master) so now I have it fixed so only master adjusts and PCM stays at about 75%.  Works nicely.  

@Tamiyadd  
I would try reinstalling the alsa driver.  Instructions can be found on the forum I believe.

@9192 > Which version did you install on your MBP, x86 or 64?
I have Santa Rosa MBP too and really want to get it work full time on mine. However, how did you get the wireless work with madwifi (I am a newbie) or it just wrks out of the box?

I'm currently using x86 as I have had not-so-good experiences with 64bit in the past.  I'm not saying to not use it, but it's just my preference for now.  As for wireless, I had to get it working using subversion.  Here are the instructions: (Just do this in a terminal, nothing too difficult)
> [QUOTE]sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi -r3403
cd madwifi
make
sudo make install
sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local
sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local

(note that madwifi newer than [WWW] r3403 has been reported not to work as of March 28, 2008 [WWW] here. )

At this point the driver is installed and should work and the internal wifi will be enabled after reboot. Alternatively, you can skip the reboot and use these commands to insert the driver into the running kernel:

> sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo iwpriv ath0 bgscan 0

Finally, the MadWifi driver will prevent you from resuming after suspend-to-ram. To fix this, edit /etc/default/acpi-support and add the ath_pci driver to the MODULES variable using "sudo gedit /etc/default/acpi-support" in the terminal.  When it opens add this:

> # ...
MODULES="ath_pci"

# ...
[/QUOTE]

---

### Post by JMC_Rimmer on 2008-04-26
I can confirm that madwifi 3403 works fine on my Macbook Pro Santa Rosa.  Haven't tested much else yet.

---

### Post by ritz on 2008-04-26
i cant get wifi to work i have a macbook pro 3,1 with 2.2ghz etc. and when i install using the macbook pro wiki for ubuntu i install the madwifi drivers and then when i click my network icon in the top bar it can see my WEP network and i put in the WEP password and then it just does that spiny thing and then asks for my wep again!!! help please

---

### Post by abhisheknk on 2008-04-26
I have been unable to install the madwifi from the pre-r3403 tars. I was unable to find the 3403 snapshot from the madwifi, and used 3402. Also, I get many errors after execution of make and sudo make install.

I'm using the x64 version of Ubuntu on my MacBook Pro 2.2 Santa Rosa C2D. In the Hardware Test, Ubuntu shows me the Atheros 5418 Wireless(b/g/n) chipset on the network card list but it doesn't appear on the Network Configuration. I only see one Wired Connection and Point to Point connection.

I've chosen to virtualize Linux in the past, but would like to use it with full functionality for which I can't use VMware. The wireless isn't currently working for me and until it does, Ubuntu is just another Linux distro that's failed to work.

Also, I'm on a shared wireless connection without access to the ethernet interface, which is why I have to download all the tarballs on OS X and put it in my pen drive to use it on Ubuntu. I assume the apt-get requires network access, and I wonder how people have got it to work if they aren't even connected to the internet.

---

### Post by ritz on 2008-04-26
i have connected my laptop to my router through etherent cable so that is what i am using for the moment

---

### Post by abhisheknk on 2008-04-26
I've confirmed from the System Profiler that the I have the Airpot Atheros 5424 Wireless Chipset. I wonder if anyone has been able to get this installed. Ubuntu calls it 5418 in the hardware test.

---

### Post by cyberdork33 on 2008-04-26
> **abhisheknk said:**
> I have been unable ...Please don't double post.
[http://ubuntuforums.org/showthread.php?t=768056](http://ubuntuforums.org/showthread.php?t=768056)

---


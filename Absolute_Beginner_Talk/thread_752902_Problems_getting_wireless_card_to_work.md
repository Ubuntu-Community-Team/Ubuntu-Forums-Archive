---
title: "Problems getting wireless card to work"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Triox on 2008-04-12
Hello,

I got a laptop last week, and decided to put Gusty Gibbon on it. After the install, I went to connect to my wireless router, and it was showing no routers.

After a little research, I kept finding I needed to get ndiswrapper to install the driver.  After I installed it and loaded my .inf it was showing no card found on the system, even other areas seem to recognize my card was physically connected.

Anyway, I tried running though trouble shooting ([from here]("https://help.ubuntu.com/7.10/internet/C/troubleshooting.html")) but ran into a few problems (I don't see a System &#8594; Administration &#8594; Device Manager) or some things I didn't understand what I was looking for ("Check to see if the device is turned on" Well, I did the command, but what am I looking at?) or how to correct it.

Anyway, I have a fresh install of Gusty Gibbon and a few hours to mess with it, it someone wouldn't mind helping me, but more importantly, kinda explaning what I am looking at and doing instead of me just following a guide.  I would appreciate it.

Thanks

---

### Post by Triox on 2008-04-12
Sorry for the bump, but I 45 minutes left at work, where I am literally just sitting here doing nothing. Being new to Ubuntu, i'm sure it's something simple that can be fixed fairly quickly.

If anyone can help me, I would greatly appreciate it

---

### Post by Triox on 2008-04-12
Still looking for some help if anyone has any to offer.  I'll even start:

According to [this]("https://help.ubuntu.com/7.10/internet/C/troubleshooting.html"), The first step is "Open Device Manager (System &#8594; Administration &#8594; Device Manager)."

I do not have System -> Administration -> Device Manager.

---

### Post by Tom--d on 2008-04-12
What is your wireless card? 

Type this in a termainal 
```
lspci
```
or 
```
lsusb
```

Paste the out come in here

Edit: Thanks otrojake 
I'm going to fast these days... need to check it before I post xD

---

### Post by otrojake on 2008-04-12
Tom meant to put

```
lspci
```

not lspic.

---

### Post by famous3warriors on 2008-04-12
I apologize for the interruption but I am having the same problem.  Here is what I got.

---

### Post by famous3warriors on 2008-04-12
forgot to post the attachment.

---

### Post by Triox on 2008-04-12
I apologize for the late reply.

Had to reboot laptop and I am copying the results to a text file to this computer with net connection to post it.

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by Tom--d on 2008-04-12
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

That is your wireless. 

Do you have the Windows drivers for it?

---

### Post by Tom--d on 2008-04-12
> **famous3warriors said:**
> I apologize for the interruption but I am having the same problem.  Here is what I got.

Do you have the windows drivers for your card?

---

### Post by Triox on 2008-04-12
> **Tom--d said:**
> 01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

That is your wireless. 

Do you have the Windows drivers for it?

Yes, when I install them with "Windows Driver Manager" it would say something along the lines of "No card found".

I don't have "Windows Driver Manager" installed as this is a fresh install.  In fact, let me backtrack a little also.  When I would install Windows Driver Manager it would say there is an update (from 1.8 to 1.9).  If I tried installing with 1.9 it wouldn't do anything.  1.8 would show the driver installed but no card.

---

### Post by Tom--d on 2008-04-12
Ok.. 

You have ndiswrapper installed? 
If so, search ndisgtk in Synapic Package Manger

It is the GUI of ndiwrapper

---

### Post by Triox on 2008-04-12
The only things I see on Synaptic Package Manager is

*ndiswrapper-common
*ndiswrapper-utlis-1.9

---

### Post by twist2b on 2008-04-12
It is actually called "Restricted Driver Manager" but w.e
run it by doing this:
gksu -D /usr/share/applications/restricted-manager.desktop /usr/bin/restricted-manager

if you dont see just add it to the "seeing" list by right clicking applications and selecting edit menus.
go to administration and check the missing application :P
there are other methods to getting your wireless card to work though.

What are your specs by the way?

---

### Post by Tom--d on 2008-04-12
[http://packages.ubuntu.com/gutsy/net/ndisgtk]("http://packages.ubuntu.com/gutsy/net/ndisgtk")

Install it through there. 
Its a .deb package (like .exe in windows)

---

### Post by famous3warriors on 2008-04-12
Hello Tom --d thanks for your help it worked great.  I really do appreciate it.

---

### Post by Tom--d on 2008-04-12
> **famous3warriors said:**
> Hello Tom --d thanks for your help it worked great.  I really do appreciate it.

Thanks :D

(Just click the Star next to quote on my post please ;))

---

### Post by Triox on 2008-04-12
> **twist2b said:**
> It is actually called "Restricted Driver Manager" but w.e
run it by doing this:
gksu -D /usr/share/applications/restricted-manager.desktop /usr/bin/restricted-manager

if you dont see just add it to the "seeing" list by right clicking applications and selecting edit menus.
go to administration and check the missing application :P
there are other methods to getting your wireless card to work though.

What are your specs by the way?

If this is refering to me, I have "Restricted Driver Manager".  When I open it up, I see what is included in my attachment

> [http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk)

Install it through there.
Its a .deb package (like .exe in windows)

OK, I have the .deb on the computer and will install it now.

---

### Post by Tom--d on 2008-04-12
Software Modem Driver is for a modem. 

Are you going to use a modem? If not, dont use it.

After install of ndisgtk..

Go System > Admin > Windows Wireless Drivers 

then locate the .inf file of the driver and it will install. the hardware present should be yes. If its no. YOu have the wrong driver.

(Must have the .sys and .inf file of the windows driver in a folder)

---

### Post by Triox on 2008-04-12
> **Tom--d said:**
> Software Modem Driver is for a modem. 

Are you going to use a modem? If not, dont use it.

That's what I figured, so I never installed it.  :)

OK, I installed ndiswrapper.  I now have the System -> Administration -> Windows Wireless Drivers

---

### Post by Triox on 2008-04-12
OK, this is as far as I have gotten before.

Ok, I opened "Windows Wireless Drivers" then I navigated to the folder where my files are. I would select the .inf and click install.  It would then show me the screen I see in attachment 1.

Attachment 2 is the folder where I get the .inf from.

 In case you are going to ask, I got my drivers from [Intel's website]("http://downloadcenter.intel.com/detail_desc.aspx?agr=N&ProductID=944&DwnldID=11918&strOSs=44&OSFullName=Windows"), which I found through [this page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

---

### Post by Tom--d on 2008-04-12
I would put the w70n501.inf and w70n51.sys in one folder and then put w70n501.inf and w70n5.sys in another. 

Install one and then see what happenes. If it doesnt work, try the next one.. 

your wireless works as it is listed in [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

---

### Post by Triox on 2008-04-12
OK, I created 2 folders, put the 2 files in each folder, and tried installing each one.

I still receive the screen from the previous post where is shows nothing installed on each attempt.

---

### Post by Tom--d on 2008-04-12
I think I know why. With the screen shot you have given me, it shows that the w70n501.inf is only a read only file. That will stop you installing (I think)

Sorry, NOT owned by root. It is only a read only file!

---

### Post by Triox on 2008-04-12
OK, first, how were you able to tell that from the screen shot? (wanting to actually learn Ubuntu, not just told what to do :) )

Second, what do I need to do now then?

---

### Post by Tom--d on 2008-04-12
Right, I think I know how to change this. 

Right click the .inf file. Go to permissions. In there. Change it from read to read and write. 

Now try it..

(There is a lock symbol in the corner of the file)

---

### Post by Triox on 2008-04-12
OK, I changed the permissions on all 3 files (The original one, and the 2 in each of the folders I created).

Owner, Group and Other all have Read and Write permissions.

I still do not showed a driver installed still.

Also, thank you for being not only patient, but explaining some of the simple stuff I don't quite understand yet.

---

### Post by Tom--d on 2008-04-12
Thats ok :) 
I like doing it. 
I'm still learning.

I'm going to look on the internet for some help with what to do here (when having multiple files) as this is where I learn :)

---

### Post by Triox on 2008-04-12
Thank you very much.

When I reached this point in trying it myself, I thought "OK, something should be happening".   I decided to try looking it up on the internet, hence why I am here.

Plus, I can always use more reference sites if I run into other problems with other things I am trying to do. :)

---

### Post by Tom--d on 2008-04-12
There is always a way. Just don't give up :)

Now.. for me, bed :)

---

### Post by Tom--d on 2008-04-13
This might work.. 

put the .cat (and change its permission to read and write) in both of the folders and see if it works then

---

### Post by Triox on 2008-04-13
> **Tom--d said:**
> This might work.. 

put the .cat (and change its permission to read and write) in both of the folders and see if it works then

Sorry for the late reply.  Just woke up. :)

I did as you said and still don't show an installed driver.

---

### Post by Triox on 2008-04-14
OK, back at work with about 6 hours to kill.

So, if Tom-d or anyone has any suggestions, or maybe somewhere I can try and find the answers myself, I would appreciate it. :)

---

### Post by Triox on 2008-04-14
Going to bed, but I'll check back later to see if anyone has anything for me to try.

---

### Post by NullHead on 2008-04-14
Ok so whats the problem now? I went through it all and I got lost. You're having troubles changing permissions? or you just plain can't get the card to work?

---

### Post by Triox on 2008-04-14
Card not working.

Installed ndiswrapper and  tried installing the driver through that, but nothing happened.

---

### Post by NullHead on 2008-04-14
Could you put this in your terminal and post the output please? ```
lsmod
```

---

### Post by Triox on 2008-04-14
This is what I got
> Module    Size  Used by
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_centrino      8256  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
battery                11012  0 
ac                      6148  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
sbs                    19592  0 
video                  18060  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
pcmcia                 41388  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
ipw2100                72240  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211              35656  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
joydev                 11328  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
psmouse                39952  0 
serio_raw               8068  0 
pcspkr                  4224  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
8139too                27776  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


---

### Post by NullHead on 2008-04-15
ok try this:
This will load ndiswrapper, the driver into the running modules found by "lsmod". ```
sudo modprobe ndiswrapper
```
This will add ndiswrapper, the driver, to /etc/modules witch gets scanned at boot to load the drivers listed in that file. ```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

---

### Post by Triox on 2008-04-15
OK, the first command did nothing

The second command returned "ndiswrapper".

Attachment is my terminal window when I did it (tried the first command twice since it returned nothing)

---

### Post by NullHead on 2008-04-15
Well either of those will return nothing to imply they worked or not, but you should now have the result of working wifi. Try using the network manager applet to connect to your wireless network.

---

### Post by Triox on 2008-04-15
I still do not see any wireless networks still.

The problem Tom-d and I ran into so far was when I went to install my wireless card driver with ndiswrapper, it appeared to not install the driver. (First post on page 3 of this thread)

---

### Post by Triox on 2008-04-15
Bump!

Here is the run down of what has happened so far in this thread

**Problem:**  When I look at the network manager, it now showing my wireless router 5 feet away

**What we have done**

1.) Started off with a fresh 7.10 install
2.) My wireless card is an "Intel Pro/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)"
3.) I installed ndiswrapper
4.) I downloaded the correct windows driver
5.) When using "Windows Wireless Driver" to install the driver for my card, it would not show any driver installed when I clicked the install button.
6.) Realized the driver download has 2 separate .sys files
7.) Created 2 new folders, put .inf, .cat and one of the .sys in each folder and tried installing each separately.  Did not work
8.) Did a modprobe on ndiswrapper.  Still not showing wireless networks


So if anyone has suggestions, I am up to try things.  Playing Tali is fun, but I would love to get on the internet with this. :)

---

### Post by NullHead on 2008-04-16
Ok here is what I would try. Yes I know this is common ground, but stick with me here. 

Download the intel drivers and unzip them to find the .inf, .sys and .cat. This install them using the terminal. ```
sudo ndiswrapper -i "drivername.inf"
``` Then setup tthe driver ```
sudo ndiswrapper -m
``` Then load ndiswrapper ```
sudo modprobe ndiswrapper
``` Then restart network manager: ```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Make sure all of your other attempts of installing the drivers are removed. Check by doing "ndiswrapper -l" (no quotes) and using "ndiswrapper -r" to remove them before re-installing them. 

If even this fails then you should just try another driver. Also I'd search on the ndiswrapper website to see if anyone has a working solution for your card.

---

### Post by beltoni on 2008-04-17
I need the windows driver for my card too! I can use ndiswrapper in the comand line but cant get it to recognize the driver I downloaded for mi wifi card. Does anyone know a link for 
wifi card driver for the Asus F5R Laptop and a driver for the ATI 1100 graphics Card. Cheers!:guitar:

---

### Post by Triox on 2008-04-18
Hello again

OK, so I had the last few days off work, and I didn't see any replies here, so I decided to try something on my own, just to satisfy my curiosity.

I grabbed my XP disk and did a full install on the laptop.  Once installed, I installed the cards driver.  Well, the card wouldn't work on XP either.

So, my guess is a problem is with the card itself, and nothing to do with Ubuntu.  Anyway, I remembered that I had bought a PCMCIA card for an incrediable old laptop I got a while ago,, slapped in the card, and I   put in the Live CD for 7.10, slapped in the card, and it worked.

I'm now posting this from my laptop with 7.10 freshly installed again. I apologize for the trouble I put everyone, and am very thankful for all the help. You guys were more than patient.

(I may still try what you posted NullHead, just to see what happens, or if you are curious)

Thanks again.

---


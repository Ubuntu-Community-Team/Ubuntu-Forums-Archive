---
title: "Netzero on Ubuntu?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by bighomer on 2008-01-16
Hi again. 

After some effort I finally managed to install my modem (winmodem), and afterwards installed gnome-ppp, knowing full well that it wasn't going to work with netzero. And I was right. 

I did an extensive search, read a few articles (some on this site), and many said there was a netzero.deb file available for linspire. I had already downloaded this particular file and found it to be an exe file. Anyway, long story short, I found the netzero.deb file somewhere else (version 6) and installed it. When I run it from the programs menu (I'm not so very good with the terminal...where can I get info on this?) and nothing happens. 

I currently have Wine installed, the only app I've successfully ran so far is Foobar. If I run my windows netzero install file, I get some error about not having dial-up networking installed. Can I make Wine emulate this? When I open my windows partition and try running exec.exe (the netzero file in c:\program files\netzero), it tells me that the netzero installation is corrupted and I should reinstall it. I've had this same error message in windows, but currently in windows it works fine. 

Tired of dual booting. Can anyone offer some insight into this problem, short of switching ISP's? I know, netzero really sucks:mad:. I definitely wouldn't recommend them to anyone. But my options are limited. 

Or maybe you could point me to a good ISP with plenty of access numbers, under $10 a month, and waits at least six hours before they kick you off automatically? "Unlimited" access, of course. I go way over 20 hours a month. 

Thanks in advance.

---

### Post by eolson on 2008-01-16
It's been awhile,  and I was with ATT,  but with them, the big problem was getting the username and password that they wanted.  It wasn't the same as the one they wanted for my email and other stuff.  Once I had that I was good to go.   I can't remember exactly the steps I used,  but I used my Windows connection and very early on there was a screen when with a little fiddling around I found them.

That probably isn't much help.

You might check your installation cd and see if there's something on there.

---

### Post by wolfen69 on 2008-01-16
can you afford another $4.95 a month? DSL-hi speed is only $14.95

---

### Post by Hospadar on 2008-01-16
You won't really be able to do anything with wine in the case, their installer no doubt has a windows kernel module (or something like it) and since Wine Is Not an Emulator, the module file will get put somewhere in your false windows drive (the one in ~.wine/drive_c) but won't do anything.

After I type that, I realize it may be inane techno-babble, but bottom line, wine ain't gonna cut it for stuff like this.

If you *do* have a .deb file, that you installed as it sounds, you can try opening the dialer from a terminal to see if there is some helpful error messages or output.  Go to Applications->Accessories->Terminal. now we need to figure out what the name of the program you installed is.  What I would do, is go to wherever the launcher for their software is (probably in Applications somewhere? or on the desktop) and drag it to the desktop (if it's not already there) then right-click->properties->launcher and copy the "command" line into your terminal (you'll need to right-click in the terminal and say paste, ctrl-V doesn't work in the terminal) and hit enter.

Post any sort of terminal output or errors you might get and maybe we can help you further.

Also, you may want to do a little googling around for linux command line tutorials, being more comfortable with the terminal can go a long way in the linux world, it's definitely a worthwhile skill to pick up

---

### Post by Hospadar on 2008-01-16
double post, my bad

---

### Post by dstew on 2008-01-16
I think it helps to have a real hardware modem. [Here]("http://www.techsupportforum.com/736571-post6.html") is one person's story, at least with Juno. DSL is pretty cheap in most big cities. I have Verizon for $15/mo, and Juno dial-up was $10/mo.

---

### Post by bighomer on 2008-01-16
Yeah, I just recently found out about Netzero's DSL service. Unfortunately, it's not available in this area. I live in the boonies. 

OK now here's a real noob question for you. How do I run a program from the terminal? I change to the directory, type in the name of the program and it says command not found. Yes, I'm in the right directory. 

Also, it's an sh file. Never heard of them, until I did a little research on the netzero.deb.

---

### Post by Iowan on 2008-01-16
> OK now here's a real noob question for you. How do I run a program from the terminal? I change to the directory, type in the name of the program and it says command not found. Yes, I'm in the right directory. 
 Might need a ./commandname.

---

### Post by disturbed1 on 2008-01-16
Does your modem even work? In other words, when you use Gnome-PPP does it get a dial tone?

If you at least get a dial tone, the modem is fine, and Net Zero will work.

```
lspci
```This will list the pci devices on your system.
Then, also in the terminal
```
lsmod
```This will list the modules (drivers) that are loaded, to see if one is loaded for your modem. HSF, Linmodem, Winmodem, are types of modem that are not optimal to have. Using one of the above for dial up is like drag racing with a Geo Metro. Yes it will cross the finish line........................ ....................hopefully.............................some time :D

read this thread also
[http://ubuntuforums.org/showthread.php?t=143472](http://ubuntuforums.org/showthread.php?t=143472)

---

### Post by SanjoEel on 2008-01-16
This is a good Linux friendly dial-up service. I have used them as a back-up isp for a long time and never had any connection issues, and there is no software or anything to download, just straight dial-up. 
[http://www.copper.net]("http://www.copper.net") AND Did I mention it's cheap as well?

---

### Post by eolson on 2008-01-16
If your hardward is functional,  this works.

[https://help.ubuntu.com/7.10/internet/C/modem-connect.html](https://help.ubuntu.com/7.10/internet/C/modem-connect.html)

---

### Post by bighomer on 2008-01-16
```

./runclient.sh
DM set to off

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

lsmod
Module                  Size  Used by
ipv6                  273892  8 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
button                  8976  0 
sbs                    19592  0 
battery                11012  0 
container               5504  0 
dock                   10656  0 
ac                      6148  0 
video                  18060  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  2 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  25 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
joydev                 11328  0 
evdev                  11136  7 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sd_mod                 30336  4 
ata_generic             8452  0 
b44                    28300  0 
mii                     6528  1 b44
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
steven@gunslinger:~/Desktop/nzclient$ 

```

I honestly don't know what most of this means, but I really think my modem's working. gnome ppp is actually dialing the number, unlike before I installed the modem driver. 

I'm gonna take a break from this for a while.

---

### Post by disturbed1 on 2008-01-16
Here's your modem -
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
And the drivers are loaded, plus you stated you can here Gnome PPP dial the numbers. All good news.

According to the thread I linked above, you need to have java installed (which needs internet access :( )

sun-java6-jre_6-03-0ubuntu2_all.deb
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmultiverse%2Fs%2Fsun-java6%2Fsun-java6-jre_6-03-0ubuntu2_all.deb&md5sum=0b3152ea17f38ed49c47caced0620bf6&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmultiverse%2Fs%2Fsun-java6%2Fsun-java6-jre_6-03-0ubuntu2_all.deb&md5sum=0b3152ea17f38ed49c47caced0620bf6&arch=all&type=main)
java-common_0.26ubuntu1_all.deb
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fj%2Fjava-common%2Fjava-common_0.26ubuntu1_all.deb&md5sum=737dceb86abaf31458885efb44a44793&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fj%2Fjava-common%2Fjava-common_0.26ubuntu1_all.deb&md5sum=737dceb86abaf31458885efb44a44793&arch=all&type=main)
sun-java6-bin_6-03-0ubuntu2_i386.deb
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsun-java6%2Fsun-java6-bin_6-03-0ubuntu2_i386.deb&md5sum=1f7cb15e08e74b57d2f9ef59c770bd05&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fs%2Fsun-java6%2Fsun-java6-bin_6-03-0ubuntu2_i386.deb&md5sum=1f7cb15e08e74b57d2f9ef59c770bd05&arch=i386&type=main)

Those are the links to install Java Run Time from the Ubuntu Package Database for Gusty. You could boot into Windows, go there download the files to USB stick or burn to cd, then install once rebooted into Gusty.

Or cancel netzero and go with [www.copper.net](www.copper.net)

---

### Post by Shazaam on 2008-01-16
bighomer....
I use Juno which is the same as NetZero (UnitedOnline). I have NEVER had to use their software to surf the net or access email (using linux OR Windows). If you have the local phone numbers, username and password you enter them in gnome-ppp.
BTW, Juno is $9.95US/month.

---

### Post by Bartender on 2008-01-16
shazam -
Are you using Juno 6?  
I still don't understand the difference between Juno 5 and Juno 6, but I'm on the old Juno 5.  Still.  Don't ask me why.  It doesn't work worth a damn in Linux.  I've tried numerous distros, it makes no difference.  Using US Robotics serial modems I can dial in to Juno and actually connect, but speeds are abysmal until they kick me off.
And I tried dialing in by building a dialer in Windows, but got an immediate error signal, something about not proper authorization.  Had to go back to their software.   

One of these days I'm gonna dump Juno and go with US Netizen or Copper.net or BasicISP or any number of basic dial-up services that don't require proprietary software to dial. 

But you know what, trying to maintain a Linux PC on dial-up is just pathetic.  The downloads are too big.  I recently bought a laptop and dual-booted it to Linux.  Now I can at least go down to the library or coffee shop and get a decent download.

---

### Post by Shazaam on 2008-01-16
Lol I have gotten used to long downloads so I feel your pain. Especially with my new Gutsy install. :)
I have ZERO Juno software running in Linux. I use it in Windows ONLY to manage my webmail otherwise I don't use it.
In Windows just go to Internet Options and make a new connection. Add in your user info and off you go.
In Ubuntu (or any other version of linux) use whatever dialer you like (wvdial from the cli, gnome-ppp, kppp etc), add your info and your done. The only problem I have is they like to kick you off after a few hours which is easy to fix (I haven't done it yet) with some kind of keep-allive setup.

---

### Post by bighomer on 2008-01-23
bump :)

took your advice, eolson. Got everything but the DNS name. 
DNS? Whose DNS? Would it be netzero.com or something? Or my IP? How would I find out?

disturbed1:
those deb files didn't work for me. 
after installing the common:
tried installing sun-java6-jre_6-03-0ubuntu2_all.deb
Error: Dependency is not satisfiable: sun-java6-bin|ia32-sun-java6-bin
tried installing sun-java6-bin_6-03-0ubuntu2_i386.deb
Error: Dependency is not satisfiable: sun-java6-jre
It's like these two files have a dependency for each other...
Looked up ia32-sun-java6-bin, it's only available for amd64?
This is not an issue. I visited their website and installed from the src file. This was all after I reinstalled Ubuntu (let's just say I get very familiar with the reinstall process).

Then I install netzero (it's not a deb, actually, but a tarball).
Then, in the terminal:
$./runclient.sh
DM set to off

WHAT is DM??? Why is it set to off and what can I do about this? If you know anything about this, please tell me.

---

### Post by disturbed1 on 2008-01-23
The client requires java. You need the java runtime installed. I'd read (or re-read the thread I linked to) which details the installation of the Netzero client on Ubuntu. It details that you need the java runtime, and the client needs to be ran in root mode. It should be pretty self explanatory why running a program that gives your computer access to the outside world as root would be a bad idea ;)

Try this for a DNS
4.2.2.1
4.2.2.6

---

### Post by neobuddha on 2008-03-25
I got the netzero deb to work like this.Open a terminal and type "sudo /opt/nzclient/runclient.sh".This works for me.The software isn't great ,but it functions.If this works then right click on the applications bar on the taskbar.Choose edit menus.In the left panel click on internet.In the right panel ,right click on netzero.Choose properties.In the new box precede the command with gksu.Then it  will work from the menu.If it is not already on the menu then in the edit menu box choose internet then click "new item".In the new box for name put "netzero" or whatever you want.For the command type gksu /opt/nzclient/runclient.sh.
I hope this helps you.

---


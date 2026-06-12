---
title: "No sound after installing Ubuntu 7-10 :("
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2008-02-02
Hi there!

I've just installed Ubuntu 7.10 from the live-cd and I've noticed that I have no sound!!! my system is a Pentium IV and I have 512MB of RAM, Some ideas why the sound not working? :( I'm kinda newbie I hope that wouldn't be a drivers or hardware problem (the windows partition have not this problem).

Thank you very much!

---

### Post by nickpaton on 2008-02-02
What is the make and model of your PC?

Also what version of 7.10 have you installed and were there any problems during the install process?

Also please could you post the output of

```
lspci
```
 (first letter lower case L)

This gives a list of your detected hardware.

Nick

---

### Post by jan quark on 2008-02-02
go to system > preferences > sound

select auto detect 

see my working :) confguration tell us what is yours

---

### Post by fredscripts on 2008-02-02
Thanks for your help :)

The output of the command:

fredgl@fredglab:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645 Host & Memory & AGP Controller (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
fredgl@fredglab:~$ 


and I'm attaching an screen shot of my sound on preferences:

---

### Post by nickpaton on 2008-02-02
Thanks for that.

I don't see your sound card listed in lspci list.

What is the make and model of your PC?

---

### Post by fredscripts on 2008-02-02
Humm well its a Pentium IV with 512MB of RAM, I'm quite newbie on hardware stuff, If you wish some screen shot or the output of some command to know what you need I'll do it immediately :)

---

### Post by nickpaton on 2008-02-02
Can you send me the output of this:

```
sudo lshw
```

It's a much longer and more detailed list.  Post it all!!

---

### Post by fredscripts on 2008-02-02
Sure, here it goes!


```
fredgl@fredglab:~$ sudo lshw
[sudo] password for fredgl:
fredglab                  
    description: Desktop Computer
    product: MS-6547
    vendor: MSI
    version: 2.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: MS-6547
       vendor: MSI
       physical id: 0
       version: 2.00
       serial: 00000000
       slot: PCI2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (12/20/01)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: PGA478
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KB
             capacity: 1MB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KB
             capacity: 1MB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 511MB
     *-pci
          description: Host bridge
          product: SiS645 Host & Memory & AGP Controller
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-isa
             description: ISA bridge
             product: SiS961 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: SCSI Disk
                product: ST380011A
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 5JVKPHLK
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 19GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 49GB
                   capacity: 49GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10236MB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 972MB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 19GB
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 19GB
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-M1612
                vendor: TOSHIBA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1004
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 10
             serial: 00:a0:c5:b3:5e:48
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.36 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 2
          bus info: usb@2:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Disk
             vendor: Ext Hard
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 186GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4
           *-volume
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                capacity: 186GB
                capabilities: primary
fredgl@fredglab:~$
```

---

### Post by nickpaton on 2008-02-02
From the information you've sent me,[ this]("http://www.msicomputer.com/product/detail_spec/645ultra.htm") is your motherboard.

From this page, you have on-board audio with the following spec:

>     * Audio  AC'97 link controller integrated in SiS® 961.
    * 2 channels S/W audio codec ALI 201A
    * - Compliance w/ AC'97 v2.2 Spec.
    * - Meet PC2001 audio performance requirement. 

I'm now going to check the SiS 961 chipset to see if there's anything strange about it on the audio side.

It's not listed in your last post.

Anyone else any ideas?

---

### Post by fredscripts on 2008-02-02
What an extrange thing, I haven't any extrange hardware :S I have a quite-standard pc and the sound works on the windows partition. Maybe the model of the soundcard isn't recognized by ubuntu? 

Thank you very much to all !! I need sound again to enjoy 100% ubuntu :D

---

### Post by nickpaton on 2008-02-02
Can you have a look at this post and tell my how you get on:

[http://ubuntuforums.org/showthread.php?t=248461]("http://ubuntuforums.org/showthread.php?t=248461")

---

### Post by fredscripts on 2008-02-02
Hi, Thanks for the link. I've had a problem on the first step , I don't see any "Master surround" :S

---

### Post by nickpaton on 2008-02-02
Don't worry about the Master Surround.

The main thing is that it appears to detect your sound chip as a soundblaster.

You'll notice that Line In has a red X against it.  Can you click on that to enable it (X should disappear).

Also within Alsa can you go to Edit > Preferences and post back a picture of what you've got there.

---

### Post by nickpaton on 2008-02-02
It's weird that your soundcard chip isn't listed.

Can you also post the output of:

```
cat /proc/asound/cards
```

---

### Post by fredscripts on 2008-02-02
Thanks. Sure, here it goes!

The command:

```
fredgl@fredglab:~$ cat /proc/asound/cards
 1 [MP3            ]: USB-Audio - Sound Blaster MP3+
                      Creative Labs Sound Blaster MP3+ at usb-0000:00:02.3-2, full speed
fredgl@fredglab:~$
```

---

### Post by fredscripts on 2008-02-02
SOS please...:( I don't want to boot the windows partition but I need listening to music :'(

---

### Post by Mze on 2008-02-02
Ubuntu detects your soundcard so that's a good thing.

Open Volume control>>EDIT>Preferences>>>select headphones. Close window.

Right click on your speaker icon on the top panel. Select>>Preferences>
HOLD down the CTRL and click on headphones and PCM (while holding down the CTRL key).

Close window.

Try to play any sound track.

Let's see how it goes.

---

### Post by nickpaton on 2008-02-02
Sorry had to take a phone call - and I'm about to have a meal so will be away for a small while!

Mmmm everything's there but no sound (have you tried it again BTW?).

One thing I've noticed from your screen print is that it says you have some restricted drivers to still install (the icon to the left of the network twin screen icon) - looks like a plug in board.

Can you click on that to open it and send a screen dump of its contents - maybe there's something for the sound chip.

---

### Post by fredscripts on 2008-02-02
Thanks for answering :)

Ok, let's see, first of all, I don't have the "headphones" option on edit-preferences of Volume Control :S

Yep, I've tried playing an mp3 song (I've installed the codecs) and the song is running on the player but I can't listen nothing on the headphones :(

Finally, do you mean this?

---

### Post by xc3RnbFO8P on 2008-02-02
> **fredscripts said:**
> Hi, Thanks for the link. I've had a problem on the first step , I don't see any "Master surround" :S

on your screen shot is sound blaster line in muted

---

### Post by fredscripts on 2008-02-02
> **Ringi said:**
> on your screen shot is sound blaster line in muted
 Yep, Thanks. I've solved it, I turned it on but still can't listen nothing.

---

### Post by nickpaton on 2008-02-02
Yes I did mean that, and no it of course doesn't help!  Oh well - a shot in the dark!

I'm getting to the point of wondering whether to reinstall alsa with the latest drivers etc.

Give me a while to look further into this (also about to eat)

Speak in a while

Nick

---

### Post by fredscripts on 2008-02-02
Thank you very much for your help :D. Also, If someone wants to enter to my computer with the Remote Desktop utilitity to take a look I add him/her to MSN and we can try it out :)

---

### Post by azimuth on 2008-02-02
You have more than one sound card. From the comand line type "alsamixer" and tell us which of your sound cards is in use.
If it is not the  Sound Blaster MP3+ that is plugged into your usb port then we will know better how to help you.

---

### Post by xc3RnbFO8P on 2008-02-02
got 2 soundcards, did you tried to plug to onboard soundcard?

---

### Post by fredscripts on 2008-02-02
> **azimuth said:**
> You have more than one sound card. From the comand line type "alsamixer" and tell us which of your sound cards is in use.
If it is not the  Sound Blaster MP3+ that is plugged into your usb port then we will know better how to help you.


Hi, Thanks for answering. Take a look at the output of the command, seems that something is wrong :S
```

fredgl@fredglab:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
fredgl@fredglab:~$ 


```

---

### Post by fredscripts on 2008-02-02
> **Ringi said:**
> got 2 soundcards, did you tried to plug to onboard soundcard?

Lol, I Thought I just had one soundcard. The fact is that I bought some years ago an external sound card because the internal get crashed (but seems that is still inside the computer). I have the headphones plugged to the external soundcard and always listen all the sound from that.

Should I try to open the computer and take the internal soundcard out of the box?

Thanks.

---

### Post by xc3RnbFO8P on 2008-02-02
You cant, it is onboard.

---

### Post by Fechter on 2008-02-02
I have some experience with hardware and I must say yours isn't pretty new. I have had many problems with Sis and, not to disappoint you, but I don't believe there will be any support- Sis were not famous with good quality even those days. Anyway, I rad sth interesting- 
# Audio  AC'97 link controller integrated in SiS® 961. 
- Compliance w/ AC'97 v2.2 Spec.

So, there aren't drivers for Linux neither on Silicon Integrated Systems nor on MSI's site, but your Realtek codecs are available. In my opinion, go to Realtek's site and download the soft listed under Unix/Linux
or
[http://www.opendrivers.com/company/2358/realtek-free-driver-download.html](http://www.opendrivers.com/company/2358/realtek-free-driver-download.html)
Install the tarball any you ought to have sucess. I know it is hard, but this is my advice. I hope that I have been helpful.

---

### Post by Mze on 2008-02-02
I didn't see that he had 2 soundcards. Thanks to the poster for seeing that.

Plugging into the onboard soundcard, should give you sound. From the look of things.

Deactivating onboard sound may have to be done in the BIOS.

---

### Post by fredscripts on 2008-02-02
> **Fechter said:**
> I have some experience with hardware and I must say yours isn't pretty new. I have had many problems with Sis and, not to disappoint you, but I don't believe there will be any support- Sis were not famous with good quality even those days. Anyway, I rad sth interesting- 
# Audio  AC'97 link controller integrated in SiS® 961. 
- Compliance w/ AC'97 v2.2 Spec.

So, there aren't drivers for Linux neither on Silicon Integrated Systems nor on MSI's site, but your Realtek codecs are available. In my opinion, go to Realtek's site and download the soft listed under Unix/Linux
or
[http://www.opendrivers.com/company/2358/realtek-free-driver-download.html](http://www.opendrivers.com/company/2358/realtek-free-driver-download.html)
Install the tarball any you ought to have sucess. I know it is hard, but this is my advice. I hope that I have been helpful.

Thanks for answering. I didn't undertand most of what you said, Sis is the model of my soundcard?
Or the problem is on the motherboard or some other hardware?

---

### Post by azimuth on 2008-02-02
Don't worry about the SiS card. You said it was broken anyway. Your USB card is supported [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs) so lets work on it.

---

### Post by azimuth on 2008-02-02
I suspect blacklisting the onboard card will let the system route the usb card through Alsa. Am I on the right track here guys?

---

### Post by nickpaton on 2008-02-02
Sorry, I too missed the two soundcards, obvious when you look at it.

@Azimuth - You're right that it's supported, but not sure about blacklisting it.

I have found this post which seemed to work for the OP:

[http://ubuntuforums.org/showthread.php?t=601760]("http://ubuntuforums.org/showthread.php?t=601760")

Worth a go?

To be honest this is getting beyond my knowledge, so can others take over!

Nick

---

### Post by fredscripts on 2008-02-02
> **nickpaton said:**
> Sorry, I too missed the two soundcards, obvious when you look at it.

@Azimuth - You're right that it's supported, but not sure about blacklisting it.

I have found this post which seemed to work for the OP:

[http://ubuntuforums.org/showthread.php?t=601760]("http://ubuntuforums.org/showthread.php?t=601760")

Worth a go?

To be honest this is getting beyond my knowledge, so can others take over!

Nick

Thanks for the link, I've read it but I can't find out where on the whole ubuntu system is the "select sound card from USB" option. 

Do you think that re-installing the whole system would fix the problem? Should I try to get some software to "wake up" the usb soundcard?

Thanks.

---

### Post by azimuth on 2008-02-02
> **nickpaton said:**
> 

To be honest this is getting beyond my knowledge, so can others take over!

Nick

Don't feel bad, I'm working above my pay grade here too [-o< I think you did find a good option to try in that link. Just check that the sound is set to the USB in the sound control panel.

---

### Post by Mze on 2008-02-02
Try deactivating the onboard sound card in your BIOS and then boot into UBuntu

Hopefully, UBuntu finds the USB as your default, if not it ALSA may have to be reconfigured/reinstalled to find the USB soundcard.

---

### Post by fredscripts on 2008-02-02
> **azimuth said:**
> . Just check that the sound is set to the USB in the sound control panel.

Sorry for the newbie question but, where I can check that? I'm surfing on all the sound stuff but I don't find that option :S

Thanks

---

### Post by fredscripts on 2008-02-02
> **Mze said:**
> Try deactivating the onboard sound card in your BIOS and then boot into UBuntu

Hopefully, UBuntu finds the USB as your default, if not it ALSA may have to be reconfigured/reinstalled to find the USB soundcard.


Sorry, I'm quite newbie on that kind of configurations. What do you mean deactivating the onboard soundcard in the BIOS? Should I enter to the BIOS and touch some things?

Thanks

---

### Post by azimuth on 2008-02-02
> **fredscripts said:**
> Thanks for the link, I've read it but I can't find out where on the whole ubuntu system is the "select sound card from USB" option. 

Do you think that re-installing the whole system would fix the problem? Should I try to get some software to "wake up" the usb soundcard?

Thanks.
 
What is the default Device in your System>Preferences>Sound ? If it is not the USB card then use the arrow on the box to find that device.

---

### Post by fredscripts on 2008-02-02
YES!!! I just changed Autodetect to USB Audio and the sound worked!!!!! :D:D:D

Thank you very much you all for the help!!! A pleasure being member of this forum!

EDIT: I can listen to music on the player but I can't listen the sound of the youtube videos, anyone knows why? :S

---

### Post by azimuth on 2008-02-02
I am glad that worked =D>  We are definatly out of my know how on the flash players for youtube. Can someone help?

---

### Post by fredscripts on 2008-02-02
Maybe I should touch something on Firefox, I can't listen any sound from webpages.

---

### Post by azimuth on 2008-02-02
I think we can assume that the problem is the same as what was just fixed, the Foxfire plugins are pointed to the wrong device. I don't know where to change that one, though.

---

### Post by azimuth on 2008-02-02
I found this [http://planet-geek.com/archives/003048.html](http://planet-geek.com/archives/003048.html) . It describes your exact problem and has a fix.

---

### Post by xc3RnbFO8P on 2008-02-02
You need flash player,
in Add/remove  (all available application) Macromedia Flash plugin

---

### Post by fredscripts on 2008-02-02
Thanks for answering. I've been looking on the preferences of Firefox but didn't see nothing about sound configuration.I have already Flash player. I'll take a look on that link.

---

### Post by nickpaton on 2008-02-02
I guess you may have not installed a number of multimedia plugins, so here's the lot!

If you have not installed JRE java give me a shout & me or someone else willl post for you. 

_**Flash Plugin**_

In a Terminal one line at a time and hit enter key:

```
sudo apt-get remove flashplugin-nonfree
```

And hit Enter key

```
rm ~/.mozilla/plugins/*flash*
```

(This is done just to be on the safe side!  It may give no file found message.)

Download the Flash Plugin.  This will automatically be downloaded into your home/your_name/ folder

```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Left Click to uncompress.  In the new window select Extract and extract into Home/your_name/ folder

Install and move the flash plugin to the correct folders:

```
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
```

Hit Enter key, then:

```
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/
```

and to tidy up:

```
rm install_flash_player_9_linux.tar.gz
```

Hit Enter key, then:

```
rm -r install_flash_player_9_linux
```



_**Install Streaming Video Plugin**_

[http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)


_**Install Helix Realplayer plugin**_

Uninstall Realplayer first if necessary from within Synaptic &#8211; throws up error when installing Helix RP.

sudo apt-get install helix-player mozilla-helix-player


_**Install Mplayer Plugins (for BBC Radio typically)**_

Install mozilla-mplayer from Synaptic.

<EDIT> if streaming video plugin above installed, you don't need to do this step.


_**Installing Mulitmedia Plugins**_

For mp3, etc. 
Open up Add/Remove programs from your Application bar. 

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)
"GStreamer ffmpeg video plugin" 
"GStreamer extra plugins" 
"GStreamer plugins for aac, xvid, mpeg2, faad" 
"GStreamer plugins for mms, wavpack, quicktime, musepack" 

Then go to Other subsection of Add/Remove and find
"Ubuntu restricted extras" 

_**DVD Codecs and Win 32 Codecs:**_

Ensure medibuntu repos are added:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.listt
```

Add GPR key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then

```
sudo apt-get update
```

And finally install the codecs:

```
sudo apt-get install libdvdcss2 w32codecs
```

Great news about the sound - well done M8!

Nick

---

### Post by nickpaton on 2008-02-02
Oh well, OK I'll include java jre plugin too!!!

Open Synaptic.

Search:  jre

From the resultant list Mark for installation:

```
sun-java6-jre
```

Apply, and close when fully installed etc.

---

### Post by fredscripts on 2008-02-02
Thank you very much for all the multimedia plugins. I had most of them but not all :), now I have all. Sadly, I can see youtube videos but without the sound, they are mute. I followed the steps of the link [http://planet-geek.com/archives/003048.html](http://planet-geek.com/archives/003048.html) , then I restarted the computer and checked again but there isn't no sound on webpages yet :(. Any ideas?

Thanks again.

---

### Post by nickpaton on 2008-02-02
Have you installed alsa-oss as per the Planet Geek HOWTO?

If not give that a go.

Then check the plugins in the Firefox directory:

Places > Computer > Filesystem.

In new window listing the directory and file tree, at the top  View  and click on Show Hidden Files.

In the directory tree navigate to:

usr > lib > Firefox > Plugins

You should have following .so and .xpt files from mplayerplug-in
.so  /  .xpt
-dvx.
-qt.
-rm.
-wmp.

Let me know if any are missing, and if any are missing list everything that is there.

Close the directory tree.

Also make sure that in alsamixer there are no disabled channels and that they are turned up to at least 70.  Exlude the microphone channel.

---

### Post by fredscripts on 2008-02-02
Well I guess at this point of the problem isn't easy to solve. So thank you all very much for the very useful help and if someone had some free time to spend on trying to help me with the "get internet sound" matter I wish we put in contact.

EDIT: Didnt read the last post. Thanks, gonna try that :)

---

### Post by fredscripts on 2008-02-02
Yes, I followed both steps of the planet geek link and web sound didn't appear.

Here I attach an screen shot of the folder you said:

I don't know what you mean about checking some channels. You mean on Open Volume Control -> Edit->Preferences all the boxes ticked?

Thansk.

---

### Post by xc3RnbFO8P on 2008-02-02
you are missing **flashplugin-alternative.so**

---

### Post by fredscripts on 2008-02-02
Thanks!. How could I get it?

---

### Post by xc3RnbFO8P on 2008-02-02
> **Ringi said:**
> You need flash player,
in Add/remove  (all available application) Macromedia Flash plugin

:)

---

### Post by nickpaton on 2008-02-02
Also the mplayer plugins.

Can I suggest you install flash and Mplayer plugins as per my post #48:

It would appear you do not have the following installed:

Install Flash

Install Streaming Video Plugin

Install Helix Realplayer Plugin

Install Mplayer Plugins

And from #49 java jre plugin

Then check the Firfox plugins folder to make sure they are all there as per my last post.

You should have:

flashplugin-alternative.so
libjavaplugin.so

The following.so and .xpt files:

mplayerplug-in
mplayerplug-in-dvx
mplayerplug-in-qt
mplayerplug-in-rm
mplayerplug-in.wmp

---

### Post by fredscripts on 2008-02-03
Hi! Thanks! I've been trying to get all those files.

I'm missing the flashplugin-alternative.so even thought I've installed Macromedia Flash Plugin ;S where can I get that .so file?

---

### Post by xc3RnbFO8P on 2008-02-03
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

### Post by fredscripts on 2008-02-03
Thanks for the link. I've installed the Adobe Flash Player following the instruccions. But the file flashplugin-alternative.so still doesn't appears on the plugin directory. Any ideas?

---

### Post by xc3RnbFO8P on 2008-02-03
and still no sound?

---

### Post by fredscripts on 2008-02-03
Nope :(, I just can listen to the mp3 files of my HD, can't listen to youtube videos (I can see the video but without sound) and the rest of webpages with any kind of sound.

---

### Post by xc3RnbFO8P on 2008-02-03
I found this:


Sound
If you have tried all the other fixes for sound in flash. Close all browsers and open programs. Open a terminal and type in
Code:

killall esd

Then start Firefox and see if flash has sound. If it dose you may have to do this to make sure that other applications are not using the sound card.

---

### Post by nickpaton on 2008-02-03
Have you actually tried to install Flash Alternative using my instructions?

I've just rechecked the instructionsand done a reinstall to check and they work OK.  You do not need to install the official Adobe Flash plugin (apologies to Ringi :) ).

See also[ this post]("http://www.psychocats.net/ubuntu/flash") which gives similar instructions.

Good luck!

Nick

---

### Post by fredscripts on 2008-02-03
> **Ringi said:**
> I found this:


Sound
If you have tried all the other fixes for sound in flash. Close all browsers and open programs. Open a terminal and type in
Code:

killall esd

Then start Firefox and see if flash has sound. If it dose you may have to do this to make sure that other applications are not using the sound card.

Thanks, seems that won't kill the process :S

```
fredgl@fredglab:~$ killall esd
esd: no process killed
fredgl@fredglab:~$ sudo killall esd
[sudo] password for fredgl:
esd: no process killed
fredgl@fredglab:~$ 

```

Working on you link nickpaton, thanks!

---

### Post by nickpaton on 2008-02-03
Fred

Here is the procedure I've used for months for installing Flash nonfree:

In a Terminal one line at a time and hit enter key:

```
sudo apt-get remove flashplugin-nonfree
```

And hit Enter key

```
rm ~/.mozilla/plugins/*flash*
```

(This is done just to be on the safe side!  It may give no file found message.)

Download the Flash Plugin.  This will automatically be downloaded into your home/your_name/ folder:

```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Left click and uncompress the file.  In the new window hit the Extract button.  Make sure your home/your_name/ folder is selected.

Move to the Flashplayer directory:

```
cd install_flash_player_9_linux
``` 

Then install the program:

```
 ./flashplayer-installer
```

Create a symlink between the installed libflashplayer.so program and the firefox/plugins folder:

```
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
```

and to tidy up - close the Terminal and in a new one::

```
rm install_flash_player_9_linux.tar.gz
```

Hit Enter key, then:

```
rm -r install_flash_player_9_linux
```

I hope this is simpler and helps you.

Good luck!

Nick

---

### Post by fredscripts on 2008-02-03
> **nickpaton said:**
> Have you actually tried to install Flash Alternative using my instructions?

I've just rechecked the instructionsand done a reinstall to check and they work OK.  You do not need to install the official Adobe Flash plugin (apologies to Ringi :) ).

See also[ this post]("http://www.psychocats.net/ubuntu/flash") which gives similar instructions.

Good luck!

Nick

Well actually I did the instructions of that link right after the installation when I entered youtube for the first time. Now, I can see youtube videos and family guy episodes without any problem (well, the problem is the sound, all videos are mute!) so I guess I have that "missing plugins" stuff fixed but seems that firefox "don't know" where to send the signal of the sound of the videos.  I've been touching edit-preferences on firefox and googling arround on this but seems difficult to solve.

EDIT: working on your last post :)

---

### Post by fredscripts on 2008-02-03
I remember following the installation instruccions you've shown me on your last post, but I had the same problem I've just had now trying it again:

```
fredgl@fredglab:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97252 files and directories currently installed.)
Removing flashplugin-nonfree ...
fredgl@fredglab:~$ rm ~/.mozilla/plugins/*flash*
fredgl@fredglab:~$ wget -c http://fpdownload.macromedia.com/get...9_linux.tar.gz
--18:03:01--  http://fpdownload.macromedia.com/get...9_linux.tar.gz
           => `get...9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.154.70
Connecting to fpdownload.macromedia.com|84.53.154.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:03:02 ERROR 404: Not Found.

fredgl@fredglab:~$ 
```

---

### Post by nickpaton on 2008-02-03
Typical!  I too get the same error.

Give me a couple of seconds.....:(

---

### Post by nickpaton on 2008-02-03
Right....

Try again, I've updated the plugin hyperlink to the one Ringi recommended (apologies M8 - you were right and my bad!!)

Just tested it and it should now all work.

<EDIT> Instructions now corrected.

---

### Post by fredscripts on 2008-02-03
Thanks you very much for your help. Now seems the wget command worked, but some file missing error on the lasts steps:
```

fredgl@fredglab:~$ sudo apt-get remove flashplugin-nonfree
[sudo] password for fredgl:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fredgl@fredglab:~$ rm ~/.mozilla/plugins/*flash*
rm: cannot remove `/home/fredgl/.mozilla/plugins/*flash*': No such file or directory
fredgl@fredglab:~$ wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
--18:24:01--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.154.70
Connecting to fpdownload.macromedia.com|84.53.154.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

100%[====================================>] 3,036,127    311.00K/s    ETA 00:00

18:24:10 (306.88 KB/s) - `install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

fredgl@fredglab:~$ ls
amsn_received  install_flash_player_9_linux.tar.gz  Public
Desktop        Music                                Templates
Documents      nautilus-debug-log.txt               Videos
Examples       Pictures
fredgl@fredglab:~$ cd Desktop/
fredgl@fredglab:~/Desktop$ sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
fredgl@fredglab:~/Desktop$ sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/
mv: cannot stat `install_flash_player_9_linux/flashplayer.xpt': No such file or directory
fredgl@fredglab:~/Desktop$ 
```

---

### Post by nickpaton on 2008-02-03
Aaaah Fred - MY BAD .... AGAIN!!!

I think I'll shoot myself!!  Sorry stay in the Home directory.

So close the Terminal down and restart it, and just run the sudo mv install instructions from your normal Termainal location.

Sorry about that.  I'm going too fast here!

N

---

### Post by Fechter on 2008-02-03
Well to enter your BIOS, when you start ypur pc from the button you should receive a message on the black screen, saying
To enter Bios, press /and which keyboard button to press/.
I am not sure for your motherboard, but Asrock enter bios by pressing F2, Gigabyte- ctrl+F1, but most /and the older ones/ enter BIOS through pressing the DEL button:)
After you enter Bios, you should find your way. If not, post.
/Sry, when I  typed this there were already 30 responses./

---

### Post by fredscripts on 2008-02-03
Don't worry , I'm very grateful to you for your help.

Let's see, what do you exactly mean? 

I've extracted the tar.gz file on the home folder, so a directory appears. Inside it, there are only 2 files: flashplayer-installer and libflashplayer.so

where do you want I move those files?

Thanks.

---

### Post by fredscripts on 2008-02-03
> **Fechter said:**
> Well to enter your BIOS, when you start ypur pc from the button you should receive a message on the black screen, saying
To enter Bios, press /and which keyboard button to press/.
I am not sure for your motherboard, but Asrock enter bios by pressing F2, Gigabyte- ctrl+F1, but most /and the older ones/ enter BIOS through pressing the DEL button:)
After you enter Bios, you should find your way. If not, post.
/Sry, when I  typed this there were already 30 responses./

Thanks for answeringWhat I should do after entering to the BIOS to solve my internet sound problem? , I mean, the hardware works because I can listen the mp3 files of my HD, the only problem is that I can't listen to the sound of firefox (youtube and the rest of websites).

---

### Post by Fechter on 2008-02-03
Can you listen only to mp3s? Can you listen to other formats? mka, ogg?

---

### Post by Fechter on 2008-02-03
Flash is broken in syanptic. Download the tarball form macromedia's site, unrar it to the desktop, run the script in terminal./you should download it to the desktop/

---

### Post by nickpaton on 2008-02-03
Ok Fred 

Install and move the flash plugin to the correct folders:

From the normal palce in Terminal (don't move to Desktop or anywhere else)

```
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
```

Hit Enter key, then:

```
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/
```

and to tidy up:

```
rm install_flash_player_9_linux.tar.gz
```

Hit Enter key, then:

```
rm -r install_flash_player_9_linux
```

Give these a go, just copy and paste the instructions into the Terminal

Nick

---

### Post by fredscripts on 2008-02-03
Omg I have a big mess here.

Let's see:

 - I download the tar.gz file on the Desktop
- I extract it. It appears a folder with two files: flashplayer-installer and libflashplayer.so
- I navigate to that folder with the terminal and run ./flashplayer-installer till it tells "Installation complete"

On the folder, there are still two files: flashplayer-installer and libflashplayer.so

So you are telling me to move the  libflashplayer.so, which is ok, but I don't have the flashplayer.xpt file on the folder, so an error when trying to move it appears.

---

### Post by nickpaton on 2008-02-03
> **fredscripts said:**
> Omg I have a big mess here.

Let's see:

 - I download the tar.gz file on the Desktop
- I extract it. It appears a folder with two files: flashplayer-installer and libflashplayer.so
- I navigate to that folder with the terminal and run ./flashplayer-installer till it tells "Installation complete"

On the folder, there are still two files: flashplayer-installer and libflashplayer.so

So you are telling me to move the  libflashplayer.so, which is ok, but I don't have the flashplayer.xpt file on the folder, so an error when trying to move it appears.

OK you've downloaded it to the Desktop and presumably extracted it to the Desktop too.

Yes you're right, the files within there are fp-installer and .so.

Ok, do this from the Teminal from the Desktop (assuming flash_player_9_linux is on the Desktop):

```
cd install_flash_player_9_linux
``` 

Then

```
 ./flashplayer-installer
```

Then press the ENTER key when instructed and this should install flash for you.

Good luck again

Nick

---

### Post by fredscripts on 2008-02-03
Thanks. As you can read on my previous message, I did it :)

But unfortunatelly, still can't listen internet sound :(

---

### Post by xc3RnbFO8P on 2008-02-03
libflashplayer.so is in /usr/lib/flashplugin-nonfree

---

### Post by nickpaton on 2008-02-03
Can you have a look in /usr/lib/firefox/plugins/ to see if it's there.
If it's not there can you check /usr/lib/flashplugin-nonfree.
If it's there we'll show you how to make a symlink to the firefox plugin folder.

If libflashplayer.so is not in firefox/plugins but is in flashplugin-nonfree you need to create a symlink between the two files as follows::

```
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
```

I'm also thinking that it would be a good idea if you install the mplayer plugins, which are much easier to do and you'll need them.

Open Synaptic package manager - System > Administration > Synaptic Package Manager

Click Search and enter:

```
mozilla-mplayer
```

Click Search again within the new window. 

Find it on the list and right click and select Mark for Installation.

If there are any other programs, they will be automatically selected as well.

Then click on Apply

That's it.

Nick

---

### Post by nickpaton on 2008-02-03
Couple of easy sites to test Flash is working:

[http://www.adobe.com/products/flash/about/]("http://www.adobe.com/products/flash/about/")

Will say Adobe Flash Player Version 9,0,48,0 Installed Successfully.

Also the following indicates Flash player is installed and makes a little whooshing noise too:

[http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/")

Ignore the missing Shockwave plugin which doesn't exist in Linux.

---


---
title: "How to play mp3's"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by calderbankw on 2006-03-09
Hi everyone
please could someone help me ive just installed ubuntu, but can not get mp3s to play or xmms to install. I have tryed everything i could. What makes it worst i have not internet connection on that machine. Please could some tell me how it can be done.
Thanks 
Calderbankw

---

### Post by Pragmatist on 2006-03-09
Well, you can't do it without an internet connection as you need to download a decoder.  Try and troubleshoot your Internet connection by making a new post.  After that use this to get MP3 and other restricted formats to work:
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3)

---

### Post by calderbankw on 2006-03-09
I have an internet connection on a different machine and ive downloaded the codecs but (as i understand) i nead to install the universe and multiverse repositories how do i do this with out the net on the pc that i have installed ubuntu onto

---

### Post by Brunellus on 2006-03-09
[QUOTE=calderbankw]I have an internet connection on a different machine and ive downloaded the codecs but (as i understand) i nead to install the universe and multiverse repositories how do i do this with out the net on the pc that i have installed ubuntu onto[/QUOTE]
[http://packages.ubuntu.org](http://packages.ubuntu.org)

web-browsable repositories.  Download the packages you need one by one, then install the debs on the other computer using dpkg.

---

### Post by Pragmatist on 2006-03-09
Here is the gstreamer .deb file mentioned in the link I gave you before:
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.8/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.8/)
Download it and to install, in a terminal, type:
```
sudo dpkg -i NameOfDebPackage
``` and put the name of the .deb package in place of NameOfDebPackage

---

### Post by calderbankw on 2006-03-09
Thanks ill give it a go now

---

### Post by calderbankw on 2006-03-09
ive done that and it worked. Could someone please post a link to a download a media player and show me how to install it

---

### Post by kaamos on 2006-03-09
Ubuntu comes with [rhythmbox](http://gnome.org/projects/rhythmbox/) (for audio) and [totem](http://gnome.org/projects/totem) (for video).

If you want others than those, some popular ones are beep-media-player, mplayer and vlc. Packages.ubuntu.com should have these as well.

---

### Post by calderbankw on 2006-03-09
when  i attempt to open an mp3, rythembox opens but nothing else happens. What am i doing wrong?

---

### Post by kaamos on 2006-03-09
Try again after this command
```
gst-register-0.8
```
That registers the new decoders. If it still does not work, try to drag-and-drop and mp3 to rhythmbox and see if you get an error message.

---

### Post by Pragmatist on 2006-03-09
Are you using KDE or GNOME?

---

### Post by Mustard on 2006-03-09
[QUOTE=calderbankw]when  i attempt to open an mp3, rythembox opens but nothing else happens. What am i doing wrong?[/QUOTE]

Does the mp3 you are wanting to play appear as a selection in the rhythmbox interface?

If it is visible and selected, when you press play does it appear to be playing but no sound is coming out?

---

### Post by calderbankw on 2006-03-09
No. absolutly nothing happens it just opens. It didnt work the register thing. I tryed drag-and-drop but nothing happen ive also tryed to add it to the liberary the error that it shows say that its not an audio stream.:-?

---

### Post by calderbankw on 2006-03-09
I beleive its gnome im not to sure, im new to ubuntu and linux.

---

### Post by Mustard on 2006-03-09
[QUOTE=calderbankw]No. absolutly nothing happens it just opens. It didnt work the register thing. I tryed drag-and-drop but nothing happen ive also tryed to add it to the liberary the error that it shows say that its not an audio stream.:-?[/QUOTE]

Ok, I would think that you haven't finished installing all the necessary packages to get mp3's playing.  Rather than replying with something like, "I've done that", what we really need to see is exact details of what you have done, so that we can get a picture in our minds of what point you are at in the installation process.  At this stage I have no idea of what has been installed already.  Can you make a list of what packages you have installed  so far with regards to getting mp3 playback working please?

---

### Post by usererror on 2006-03-09
Hello!  I just also reinstalled Ubuntu.  I got a new bigger hard drive for my pc.

anyway, I'm also re-setting everything up.  I just tried a bunch of packages but the two packages that made the mp3s play for me in rythmbox are these two:

> apt-get install  gstreamer0.8-plugins   gstreamer0.8-ffmpeg

and then run this command:

> gst-register-0.8

make sure that rythymbox is not running when you do that...at least it worked that way for me.

good luck! :)

---

### Post by derekd on 2006-03-09
I really like amaroK as a media player, and you don't need any extra codecs or anything for mp3s.

---

### Post by AtinLango on 2006-03-09
[QUOTE=usererror]Hello!  I just also reinstalled Ubuntu.  I got a new bigger hard drive for my pc.

anyway, I'm also re-setting everything up.  I just tried a bunch of packages but the two packages that made the mp3s play for me in rythmbox are these two:



and then run this command:



make sure that rythymbox is not running when you do that...at least it worked that way for me.

good luck! :)[/QUOTE]



The above quote pre-supposes internet connection in Ubuntu. But remember calderbankw does not have internet connection on the Ubuntu box. So apt-get, etc won't work.

I am in the same situation with calderbankw. I have internet connection in Windows but no internet in the Ubuntu box. So, I d/l from windows and install manually in Ubuntu. Even after installing the decoders, nothing happened.

What I finally did was to install Beep-media-player (for audio) and gxine (for video) and they are working fine. But up to now, totem and rythembox are not playing.

---

### Post by calderbankw on 2006-03-10
[QUOTE=AtinLango]The above quote pre-supposes internet connection in Ubuntu. But remember calderbankw does not have internet connection on the Ubuntu box. So apt-get, etc won't work.

I am in the same situation with calderbankw. I have internet connection in Windows but no internet in the Ubuntu box. So, I d/l from windows and install manually in Ubuntu. Even after installing the decoders, nothing happened.

What I finally did was to install Beep-media-player (for audio) and gxine (for video) and they are working fine. But up to now, totem and rythembox are not playing.[/QUOTE]

Could please tell me were to find Beep-media-player (for audio) and gxine (for video) and i will try them thanks.

---

### Post by kaamos on 2006-03-10
[http://packages.ubuntu.com/breezy/sound/beep-media-player](http://packages.ubuntu.com/breezy/sound/beep-media-player)

[http://packages.ubuntu.com/breezy/graphics/gxine](http://packages.ubuntu.com/breezy/graphics/gxine)

---

### Post by AtinLango on 2006-03-10
[QUOTE=calderbankw]Could please tell me were to find Beep-media-player (for audio) and gxine (for video) and i will try them thanks.[/QUOTE]


[Here]("http://packages.ubuntu.com/") and you serach beep-media-player and gxine (both case sensitive).

PS: And dont get scared by too many dependencies. Some of them are already installed by default.

For beep-media-player, I actually downloaded only beep-media-player_0.9.7.1+cvs20050803-1ubuntu1_i386.deb without any dependencies and it worked.

For gxine, I downloaded only gxine_0.4.4-0ubuntu5_i386.deb and the following 3 dependencies:

libsmjs1_1.5rc6a-1_i386.deb
libxine1c2_1.0.1-1ubuntu10.2_i386.deb depends on libmodplug0c2_0.7-4.1_i386.deb

Good luck.

---

### Post by calderbankw on 2006-03-10
Thanks. I have installed beep-media-player. Unfortunatly when i go to play an mp3 the following message is displayed:

> Can not open audio

Please check the following:
1. That you have the correct output plugin selected
2. No other software is blocking the soundcard.
3  Your soundcard is configured properly.


I then, because of this error, opened sound preferences (system => Preferences => sound preferences.) In the default sound card box is empty and there is no choices. Therefore I believe that the sound card must not be configured. The sound card is relalivly old its a "sound blaster awe64 CT400". Do I have to install drivers? Where can i get these from? and how can i install them?

---

### Post by Pragmatist on 2006-03-10
They have the AWE32 here and I would try that driver out:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

---

### Post by Pragmatist on 2006-03-10
These are somewhat old, but may help:
thttp://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Soundblaster-AWE.html
[http://mitglied.lycos.de/iwai/awedrv.html](http://mitglied.lycos.de/iwai/awedrv.html)
I got those links via this one: [http://linux-sound.org/drivers.html](http://linux-sound.org/drivers.html)

---

### Post by calderbankw on 2006-03-10
Ive read the above links and to be honist they are way to compliacated to me. Although im confident with windows i no very little about linux. I hate to be a pain but please could some one explain it to me. (thanks for all your help so far).

---

### Post by Pragmatist on 2006-03-10
no problem.  Ok, first give us the output of: 
```
lsmod |grep snd
```
and
```
uname -r
```
Ignore those links I gave you, I think this will be much easier.  Just a matter of inserting the right module.  These initial questions are just to see what is currently loaded on your system.

---

### Post by calderbankw on 2006-03-11
Thanks so much. 

lsmod | grep snd didnt return anthing although lsmod return the following:

> Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
sd_mod                 17424  2
analog                 10528  0
ns558                   5508  0
gameport               14472  3 analog,ns558
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
i2c_piix4               8336  0
i2c_core               19728  1 i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
processor              23100  0
usb_storage            64704  1
scsi_mod              124872  2 sd_mod,usb_storage
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104188  3 usb_storage,uhci_hcd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 usb_storage,ide_disk,ide_generic,piix
unix                   24624  503
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


and uname -r returned:

> 2.6.12-9-386

Unfortunatly grep snd did nothing ?

---

### Post by calderbankw on 2006-03-13
*bump* soz but i need to get this machine running

---

### Post by Pragmatist on 2006-03-13
Is your soundcard an ISA or PCI card?

Give output of these commands:
```
modinfo soundcore
```
```
locate sbawe
```

---

### Post by Jose Catre-Vandis on 2006-03-13
I've installed the gstreamer stuff and tried registering, still no mp3 playing in totem or mplayer??

---

### Post by Pragmatist on 2006-03-13
****Are you using GNOME or KDE?

---

### Post by hezral on 2006-03-13
since we're talking about downloading packages, may i ask if anyone has downloaded packages for banshee manually? because i dont have an internet connection on my ubuntu box. thanx in advance

---

### Post by Pragmatist on 2006-03-13
> since we're talking about downloading packages, may i ask if anyone has downloaded packages for banshee manually? because i dont have an internet connection on my ubuntu box. thanx in advanceThis is the fourth post in **THIS** thread.
> 
Originally Posted by** Brunellus**
     Quote:
                                                Originally Posted by **calderbankw**
                 *I have an internet connection on a different machine and ive downloaded the codecs but (as i understand) i nead to install the universe and multiverse repositories how do i do this with out the net on the pc that i have installed ubuntu onto*
                                
  [http://packages.ubuntu.org]("http://packages.ubuntu.org/")
 
web-browsable repositories. Download the packages you need one by one, then install the debs on the other computer using dpkg.

---

### Post by hezral on 2006-03-14
[QUOTE=Pragmatist]This is the fourth post in **THIS** thread.[/QUOTE]

sorry for that. but the dependencies issues is really tough to get thru.

Thanks for that anyway.

I guess what i wanted to know was,

has anyone tried downloading banshee manually from the packages.ubuntu.com

and what files did they get to make it working, like the post a few pages before 

the guy stated what files he downloaded to make the gxine working. 

Sorry again.

---

### Post by Pragmatist on 2006-03-14
>  guess what i wanted to know was, has anyone tried downloading banshee manually from the packages.ubuntu.com

Sometimes it happens that people start to post different, though somewhat related, questions in the same thread.  In fact, I shouldn't have answered your previous post in this thread.
[B]
Please make a _*new thread*_ when you have a statement or question not directly related to helping the OP (Original Poster).[/B]

---

### Post by hezral on 2006-03-15
sorry then ;)

---

### Post by calderbankw on 2006-03-16
It is a ISA

Modinfo soundcore returned:

> Filename: /lib/modules/2.6.12-9-386/kernal/sound/sound core.ko
Description: Core sound module
Author Alan Cox
Licence: GPL
Alias: Char-major-14-*
Vermagic: 2.6.12-9-386 386 gcc3.4
Depends:
Srcversion E11490DC3F523551C4C2A6D

Locate Sound Core Returned: 
> /lib/modules/2.6.12-9-386/kernal/sound/soisa/sb/snd-bawe.ko

---

### Post by Pragmatist on 2006-03-16
Ok, great news!  All you should have to do is install this package:
**isapnptools**

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=isapnp&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=isapnp&searchon=names&subword=1&version=breezy&release=all)

---

### Post by calderbankw on 2006-03-16
ive installed that but nuthing seem to happen these stilll no soundcard displayed

---

### Post by Pragmatist on 2006-03-16
1.) How did you install the package?
2.) Did you reboot after installing the package?
3.) After rebooting, type this and give us the output:
```
dmesg | grep isa
```

---

### Post by calderbankw on 2006-03-22
1) sudo dpkg -i NameOfDebPackage
2) Yes
3) > [4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   28.109177] SELinux:  Disabled at boot.
[   30.637916] ACPI: Interpreter disabled.
[   30.637976] pnp: PnP ACPI: disabled
[   30.657292] audit: initializing netlink socket (disabled)
[   30.658942] isapnp: Scanning for PnP cards...
[   30.781409] isapnp: Card 'Creative AWE64 PnP'
[   30.781430] isapnp: 1 Plug & Play card detected total
[   30.952769] EISA: Probing bus 0 at eisa.0
[   31.043434] input: AT Translated Set 2 keyboard on isa0060/serio0
[  100.254548] input: PS/2 Generic Mouse on isa0060/serio1
[  278.570796] Disabled Privacy Extensions on device c02eb280(lo)


Soz ive taken so long to reply ive had a lot of coursework to do

---

### Post by Pragmatist on 2006-03-22
> 

[QUOTE][4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 28.109177] SELinux: Disabled at boot.
[ 30.637916] ACPI: Interpreter disabled.
[ 30.637976] pnp: PnP ACPI: disabled
[ 30.657292] audit: initializing netlink socket (disabled)
[ 30.658942] isapnp: Scanning for PnP cards...
[ 30.781409] **isapnp: Card 'Creative AWE64 PnP'**
[ 30.781430] isapnp: 1 Plug & Play card detected total
[ 30.952769] EISA: Probing bus 0 at eisa.0
[ 31.043434] input: AT Translated Set 2 keyboard on isa0060/serio0
[ 100.254548] input: PS/2 Generic Mouse on isa0060/serio1
[ 278.570796] Disabled Privacy Extensions on device c02eb280(lo)
[/QUOTE]

Well, this seems like it sees your card!  However, before we get too excited, lets try some things out.  Try to work through some of the suggestions in the following Howto and post your results to here:

[https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29](https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29)

---

### Post by calderbankw on 2006-03-22
Yer i no. Thanks youve helped great deal i will run through those as you suggested thanks again.

---


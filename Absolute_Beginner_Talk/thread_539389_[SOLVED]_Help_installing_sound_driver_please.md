---
title: "[SOLVED] Help installing sound driver please"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by TaoBoogie on 2007-08-31
I have posted this question before but have not received a reply that helps yet, so I thought I'd try here. I hope that is OK.

My system is AMD 64 bit although I am only running it as 32bit. I have an ABIT KN9 Ultra MoBo with an on-board sound card (RealTek HD).
I am dual booting on separate drives with XP Pro. The sound card work while in XP but I can't get any sound/music to work in ubuntu.
When I go to System>Sound and test the "Sound Events" "Music and Movies" and "Audio Conferencing" I can hear a faint tone sound on test.

I cannot hear any of my music or video files.
I have visited the RealTek website and downloaded the "RealTek-Linux-Audiopack -3.5-6 but I'm not sure if:
A) It is the right driver.
B) How to install it.
I am very new to ubuntu so these instructions that came in a text file with the audio pack don't really help me, as I do not understand the directions. There is an installer file in the pack but I've been warned against installing software this way.
Any help to get me back on the Boogie Woogie would be joyfully received.
Thanks
Tao

---

### Post by ddrichardson on 2007-09-01
This is a very problematic card, can you post the output of```
lspci
``` from the terminal?

The best place to start is the [Intel HDA Howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28intel%29").

---

### Post by jonmichi on 2007-09-01
I am in the same boat.  I can't get my sound to work.  I have only been doing linux for a few days now so I am a baby at this awesome new operating system.  Can someone please stear me in the right direction?  If this helps I have an ASUS M2N E SLI motherboard with onboard sound.  Any help would be greatly appreciated.

---

### Post by ddrichardson on 2007-09-01
jonmichi - output of lspci?

---

### Post by jonmichi on 2007-09-01
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 RAID bus controller: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)

---

### Post by ddrichardson on 2007-09-01
OK jonmichi - either you have a USB soundcard or the system isn't even detecting an attached PCI soundcard. Is there any mention of a soundcard under System/Administration/Devices?

---

### Post by jonmichi on 2007-09-01
I really appreciate your help there is one problem.  Under system/administration there is no place for devices.  Thank you for taking your time with me though

---

### Post by ddrichardson on 2007-09-01
In the terminal, type```
aplay -l
``` post theoutput here.

---

### Post by jonmichi on 2007-09-01
jonmichi@jonmichi-desktop:~$ 
jonmichi@jonmichi-desktop:~$   #7   Report Post  
jonmichi@jonmichi-desktop:~$ Old 4 Minutes Ago
bash: Old: command not found
jonmichi@jonmichi-desktop:~$ jonmichi jonmichi is online now
bash: jonmichi: command not found
jonmichi@jonmichi-desktop:~$ First Cup of Ubuntu
bash: First: command not found
jonmichi@jonmichi-desktop:~$   
jonmichi@jonmichi-desktop:~$ Join Date: Sep 2007
bash: Join: command not found
jonmichi@jonmichi-desktop:~$ Location: JAPAN
bash: Location:: command not found
jonmichi@jonmichi-desktop:~$ Beans: 3
bash: Beans:: command not found
jonmichi@jonmichi-desktop:~$ Ubuntu 7.04 Feisty Fawn User
bash: Ubuntu: command not found
jonmichi@jonmichi-desktop:~$ Re: Help installing sound driver please
bash: Re:: command not found
jonmichi@jonmichi-desktop:~$ I really appreciate your help there is one problem. Under system/administration there is no place for devices. Thank you for taking your time with me though
bash: I: command not found
jonmichi@jonmichi-desktop:~$ __________________
bash: __________________: command not found
jonmichi@jonmichi-desktop:~$ Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
bash: Edit/Delete: No such file or directory
jonmichi@jonmichi-desktop:~$ jonmichi
bash: jonmichi: command not found
jonmichi@jonmichi-desktop:~$ View Public Profile
bash: View: command not found
jonmichi@jonmichi-desktop:~$ Send a private message to jonmichi
bash: Send: command not found
jonmichi@jonmichi-desktop:~$ Send email to jonmichi
bash: Send: command not found
jonmichi@jonmichi-desktop:~$ Find all posts by jonmichi
bash: Find: command not found
jonmichi@jonmichi-desktop:~$ Add jonmichi to Your Buddy List
bash: Add: command not found
jonmichi@jonmichi-desktop:~$   #8   Report Post  
jonmichi@jonmichi-desktop:~$ Unread 1 Minute Ago
bash: Unread: command not found
jonmichi@jonmichi-desktop:~$ ddrichardson's Avatar 
> ddrichardson ddrichardson is online now
> Has an Ubuntu Drip
>   
> Join Date: Jul 2007
> Location: Wattisham, UK
> Beans: 751
> Ubuntu 7.04 Feisty Fawn User
> Windows User
> Send a message via AIM to ddrichardson Send a message via MSN to ddrichardson Send a message via Yahoo to ddrichardson
> Re: Help installing sound driver please
> In the terminal, type
> Code:
> 
> aplay -l

---

### Post by ddrichardson on 2007-09-01
Sorry - its in System/Preferences/Hardware Information, thinking of Windows again.

---

### Post by jonmichi on 2007-09-01
what was all of that?

---

### Post by jonmichi on 2007-09-01
ok I went to the device manager and it seems that it's not reading any audio.  For PnP Audio device it says Unknown vendor...ect. USB audio interface is also unknown.  Any ideas?

---

### Post by ddrichardson on 2007-09-01
It would appear you have a USB soundcard - something I have no experience with at all. Hopefully someone with more knowledge on them will be able to pick up the thread. Sorry.

---

### Post by jonmichi on 2007-09-01
I will check back in a little bit I have to go for now thank you for your help.  If you are coming up with a solution I really appreciate your time and effort.  The Ubuntu world seems really friendly just by reading other posts.  Have a good evening...well it's evening for me :)

---

### Post by jonmichi on 2007-09-01
Yea it's weird I have on board sound with my mother board.

---

### Post by TaoBoogie on 2007-09-07
Gosh! I completely forgot about this thread, I'm so sorry I made such a stupid error, my apologies to all involved. I was offline for a while and forgetting that I had already asked this question posted it up again here.
The good news is the problem is now solved. You can see the thread with the solution **[here]("http://ubuntuforums.org/showthread.php?t=518695&page=4")** I'll just slink away and give myself a good talking too.
Apologies once again.
Tao

---

### Post by steveo862004 on 2008-07-07
Hi, i just installed ubuntu today, and im having sound issures, i am trying to run ventrilo and WoW but i cant talk or hear in vent... and iam still patching WoW. I amrunning them both through Wine. here is my output from the terminal. 

steven@steven-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

any help is much appreciated.

---


---
title: "Need help getting sound"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by Edico on 2005-08-28
A friend of mine got Ubuntu a while ago and said he automatically had sound, but I recently installed it and there's no sound at all. What do I need to do to get sound?

---

### Post by Kapre on 2005-08-28
[QUOTE=Edico]A friend of mine got Ubuntu a while ago and said he automatically had sound, but I recently installed it and there's no sound at all. What do I need to do to get sound?[/QUOTE]

Did you try installing all the codecs? Maybe your sound in "Mute" in your settings or maybe the volume is set to low. Please check and if this is not the case, is there sound coming out of your speakers when you start ubuntu? 

K

---

### Post by fartbarker on 2005-08-28
I'm not getting sound either. I get this error message when accessing volume control.

*No volume control elements and/or devices found.*

---

### Post by varunus on 2005-08-28
Can everyone without sound post the following (when typed into a terminal):

lsmod | grep snd
lspci

---

### Post by fartbarker on 2005-08-28
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:06:05.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 03)

---

### Post by fartbarker on 2005-08-28
I found this [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

will give it a try




[I]
didnt work[/I]

---

### Post by varunus on 2005-09-04
Was lsmod | grep snd empty?

---

### Post by rafakl on 2005-09-04
It didnt work because you dont have any sound modules installed.

Try varnus idea

---

### Post by varunus on 2005-09-06
I just noticed something, you have an intel hda sound card.

Here's instructions on getting that to work (I suggest you follow the second method, make sure you have build-essential installed from synaptic).

[https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28intel%29%7C%28hda%29](https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28intel%29%7C%28hda%29)

---

### Post by scaza on 2005-09-07
when I do this step
# dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

I get the following:

dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

is there any reason why it might have a different name on my machine?
everything else seemed to work

---

### Post by varunus on 2005-09-08
Does that file exist in the directory?  Use an ls to find it...

---

### Post by GrootBrak on 2005-09-09
To add my two cents worth. The file as above does not exist. You won't find it, and I found it impossible to set up. To much codes and stuff that I don't understand. My simpathy with your soundless system. I took me the better of two months to actually have sound, and it still is faint. 

I know, I have the same board and sound drivers. Look under my username for threats regarding your system. Next time you will complain about pathetic video graphics esp. with 3d games. Search under [www.linuxquestions.com](www.linuxquestions.com) for drivers regarding sound. Search under username "GreatBrak" in linuxquestions. If you are lucky you will have sound soon. I still have lots of games that won't work with sound.

Unfortunately, few users will actually jump at it to try and help. They will have the VERY best of intentions, but their replies is generic. Even users that sucessfully got their sound going on Intel 915G boards gives flaky advice, and after a couple of tries they give up. I think the sucessfull "set uppers" is the worse. They will tell you what worked for them, if it does not work for them, they stop replying. Worse still, I'm in the same league!!! So I will follow this thread until it dies naturally, but don't give up!!!

So far nothing seems to work properly with our and similair system boards. BTW. Forget about downloading from Intel and configuring your board in Linux, it won't work. You will waste hours, and get nowhere.

---

### Post by sbooth on 2005-09-09
I can't get sound at all either - I'm sure I had it two days ago, don't know what I've done that's broken it (I know, I know, I'm stupid... I have searched the forums and tried various things... tried the add-on cd instructions and still have no sound).  I'd really appreciate some help!  Here are my results of "lsmod | grep snd" and "lspci" as mentioned earlier in this thread.

snd_cs46xx             80328  1
snd_rawmidi            22944  1 snd_cs46xx
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_cs46xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_cs46xx,snd_pcm
gameport                4608  1 snd_cs46xx

0000:00:00.0 Host bridge: Intel Corp. Workstation Memory Controller Hub (rev 09)
0000:00:00.1 ff00: Intel Corp. Memory Controller Hub Error Reporting Register (rev 09)
0000:00:02.0 PCI bridge: Intel Corp. Memory Controller Hub PCI Express Port A0 (rev 09)
0000:00:03.0 PCI bridge: Intel Corp. Memory Controller Hub PCI Express Port A1 (rev 09)
0000:00:04.0 PCI bridge: Intel Corp. Memory Controller Hub PCI Express Port B0 (rev 09)
0000:00:1c.0 PCI bridge: Intel Corp. 6300ESB 64-bit PCI-X Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 6300ESB USB Universal Host Controller (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 6300ESB USB Universal Host Controller (rev 02)
0000:00:1d.4 System peripheral: Intel Corp. 6300ESB Watchdog Timer (rev 02)
0000:00:1d.5 PIC: Intel Corp. 6300ESB I/O Advanced Programmable Interrupt Controller (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 6300ESB USB2 Enhanced Host Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 0a)
0000:00:1f.0 ISA bridge: Intel Corp. 6300ESB LPC Interface Controller (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 6300ESB PATA Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 6300ESB SATA Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 6300ESB SMBus Controller (rev 02)
0000:05:02.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
0000:05:03.0 Ethernet controller: Intel Corp. 82541GI/PI Gigabit Ethernet Controller (rev 05)
0000:05:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

I'm jolly confused... if you need any more info that I can provide, I will do so asap!

Thank you

Sarah

---

### Post by Kyral on 2005-09-09
[QUOTE=GrootBrak]To add my two cents worth. The file as above does not exist. You won't find it, and I found it impossible to set up. To much codes and stuff that I don't understand. My simpathy with your soundless system. I took me the better of two months to actually have sound, and it still is faint. 

I know, I have the same board and sound drivers. Look under my username for threats regarding your system. Next time you will complain about pathetic video graphics esp. with 3d games. Search under [www.linuxquestions.com](www.linuxquestions.com) for drivers regarding sound. Search under username "GreatBrak" in linuxquestions. If you are lucky you will have sound soon. I still have lots of games that won't work with sound.

Unfortunately, few users will actually jump at it to try and help. They will have the VERY best of intentions, but their replies is generic. Even users that sucessfully got their sound going on Intel 915G boards gives flaky advice, and after a couple of tries they give up. I think the sucessfull "set uppers" is the worse. They will tell you what worked for them, if it does not work for them, they stop replying. Worse still, I'm in the same league!!! So I will follow this thread until it dies naturally, but don't give up!!!

So far nothing seems to work properly with our and similair system boards. BTW. Forget about downloading from Intel and configuring your board in Linux, it won't work. You will waste hours, and get nowhere.[/QUOTE]
 Just because it doesn't work for you doesn't mean it won't for everyone else. My friends advocate Gentoo, but I used Gentoo and it didn't work for me. Doesn't mean it won't work for everyone else.

To scaza: Try an ls, the try to do a tab-complete. That is, type out "sudo dpkg -i alsa" then hit tab a couple times, BEFORE you hit return. This will make the shell try to autocomplete. If its not in the directory, then do this.

sudo slocate -u /

That updates the locate database. Once its done type

sudo slocate alsa

That will search the entire filesystem for "alsa", which could be a lot of stuff. So do this

sudo slocate alsa | less

Which pipes it to less so you can scroll up and down with the arrow keys. Once you find out where its hiding, well, I think you know what to do

---


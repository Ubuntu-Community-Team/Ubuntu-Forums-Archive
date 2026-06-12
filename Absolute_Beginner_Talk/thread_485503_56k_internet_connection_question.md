---
title: "56k internet connection question"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-06-27
hey everyone,

I am home for summer break from school and I don't have anything but a 56k internet connection here.  I was wondering if there was a script to install my modem and setup up the modem so I can connect.  I have looked into setting it up and it looks rather complicated (for me at least lol) and was hoping that somewhere out there was a script that would hook me up.

---

### Post by swoll1980 on 2007-06-27
go here this will explain it [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup) if you have any questiions let us know

---

### Post by familyjules74123 on 2007-06-28
so i did scanmodem... and I got the results, but what I don't know is what is the important info in the file.

this is the section that I am thinking had what I'm looking for, if someone can help me by telling me what that is I would really appreciate it.  And, if what I need isn't in this section I will post the rest.
> Next deducing cogent software ===

 For candidate modem in PCI bus:  00:1f.6
   Class 0703: 8086:24c6 Modem: Intel Corporation 82801DB/DBL/DBM
      Primary PCI_id  8086:24c6
    Subsystem PCI_id  14e4:4d64 , 14e4 is an ALSA compatible identification
    Softmodem codec or Vendor from diagnostics: BCM64, a Broadcom type.
                              from    Archives: BCM64, a Broadcom type.
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-intel8x0m and audio drivers it depends on,
 displayed by:	lsmod | grep snd_intel8x0m
Module                  Size  Used by
-------------------------------------
snd_intel8x0m          18700  0 
snd_ac97_codec         98336  2 snd_intel8x0m,snd_intel8x0
snd_pcm                79876  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  13 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  3 snd_intel8x0m,snd_intel8x0,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
01-00: Intel ICH - Modem : Intel 82801DB-ICH4 Modem - Modem : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
 0 snd_intel8x0
 1 snd_intel8x0m
	/proc/asound/card1/codec97#0/mc97#1-1+regs
-------------------------------
0:7c = 4243  and  0:7e = 4d64
which were translated from hexadecimal code into:  BCM64

	/proc/asound/card1/codec97#0/mc97#1-1
-------------------------------
Extended modem ID: codec=1 LIN1

and from the command:
	aplay -l | grep -i modem
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================




Thanks in advance for the help I get.

---

### Post by darkrose on 2007-06-28
> 
Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
$ tar zxf SLMODEMD-1.0.13.tar.gz
and read instructions therein. But briefly, the modem is setup with command:
sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
reporting dynamic creation of ports:
/dev/ttySL0 --> /dev/pts/N , with N some number
Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

Just follow that and you should be all set.

---

### Post by familyjules74123 on 2007-06-28
> reporting dynamic creation of ports:
/dev/ttySL0 --> /dev/pts/N , with N some number
Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

How do I do this part? Also, once I have done all this, how do I connect to the internet using the modem?

---


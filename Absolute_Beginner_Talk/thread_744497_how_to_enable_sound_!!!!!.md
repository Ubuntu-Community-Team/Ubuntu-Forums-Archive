---
title: "how to enable sound !!!!!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by rookie4evr on 2008-04-03
I don't know, but i can't get any sound on my laptop ....
help please ... i am new to ubuntu .....

---

### Post by StOoZ on 2008-04-03
can you post your specs? in terminal type:
> lspci

and then:
> asoundconf list

and post the output here

---

### Post by rookie4evr on 2008-04-03
ok....

---

### Post by zvacet on 2008-04-04
&#346;ystem>preferences>multimedia system editor (or something similar) and check your audio and video.Go to the system<preferences>volum control>edit>choose **master and PCM **and  yo ucan add other if you like.Go to the file tab and choose between ALSA and OSS.

---

### Post by superprash2003 on 2008-04-04
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by rookie4evr on 2008-04-04
I tried the way, that the person who gave me the link above did ...
but when I chose some of them ...
I am getting this message,

"Failed to construct test pipeline for 'gconfaudiosrc !
audioconvert ! audiosample ! gconfaudiosink profile=chat"

"audiotestsrc wave=sine freq=512! audioconvert ! audiosample ! gconfaudiosink profile= chat: Resource busy or not available."

is there way a I can download a driver, for my sound card ????

---

### Post by nnamdi on 2008-04-04
pls type lspci 
on terminal and post back the output ok

---

### Post by s3a on 2008-04-04
I am not sure but wouldn't typing alsamixer in terminal and then doing stuff in there fix the problem?

---

### Post by nnamdi on 2008-04-04
if u really want to work on this we need your sharp response ok
type: lspci
first post the output from your terminal back

---

### Post by rookie4evr on 2008-04-05
rookie@rookie-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)




HOPE THIS HELP !!!!! :)

---

### Post by Michael.Godawski on 2008-04-05
Please post also the result of this terminal command:
```
sudo lshw -C multimedia
```

What happens if you run
```
alsamixer 
```in terminal 
and increase the volume of master and pcm?

---

### Post by rookie4evr on 2008-04-05
when i typed "alsamixer" ..
this is what I got from the terminal ..see the attached file ...

---

### Post by Michael.Godawski on 2008-04-05
Increase the volume of the Master.

---

### Post by rookie4evr on 2008-04-05
when i type this command code in terminal this what i get ....
[PHP]sudo lshw -C multimedia[/PHP]

rookie@rookie-laptop:~$ sudo lshw -C multimedia
[sudo] password for rookie:
  *-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
rookie@rookie-laptop:~$

---

### Post by rookie4evr on 2008-04-05
I don't know how to increase the volume of the master ????

---

### Post by Michael.Godawski on 2008-04-05
You can switch to the different devices with the left and right arrow. And you can then increase and decrease with up and down arrows.

---

### Post by rookie4evr on 2008-04-05
"You can switch to the different devices with the left and right arrow. And you can then increase and decrease with up and down arrows."

hmmm working for the "PCM" and "MIC" ...but when i try to do the same thing for the 
"MASTER" I can't increase .... When I press Arrow key up ..... to increase the volume ..
tryied it on the other two ..I can lower and higher them ... not for the master ....

---

### Post by Michael.Godawski on 2008-04-05
Click with the right mouse button on the speaker in the upper right corner of the display.
Select "Open Volume Control". I s there a Master Switch? Can you increase the sound there?

---

### Post by rookie4evr on 2008-04-05
@above ...
yeah ... 
its at FULL ...what can i do now ????? :(

---

### Post by rookie4evr on 2008-04-05
anyone please .... help me ..
I cannot keep .. Ubuntu ..without having sound for it .....:confused::(

---

### Post by gandaran on 2008-04-05
> **rookie4evr said:**
> anyone please .... help me ..
I cannot keep .. Ubuntu ..without having sound for it .....:confused::(

what application or file you trying to get sound out of, mp3 file? have you installed the necessary codecs?

---

### Post by rookie4evr on 2008-04-05
hmmmm overall ... I am just trying to get the sound ...
if their is codecs are driver .... I have listed my specification of my laptop ..can someone please tell me, what program I got to download ... to make it work .... PLEASE >....:(

---

### Post by gandaran on 2008-04-06
> **rookie4evr said:**
> hmmmm overall ... I am just trying to get the sound ...
if their is codecs are driver .... I have listed my specification of my laptop ..can someone please tell me, what program I got to download ... to make it work .... PLEASE >....:(

look to get sound, make sure you have the speakers enabled (right click on the panel speaker icon, open volume crontrol, see if all items are enabled, check also volume level) 
drivers: you already have two installed by default, right click on the panel speaker icon, select preferences, you can choose there either one 'alsa' or 'oss', if neither of these two support your hardware (which I don't think is the case here, it should work) there is still another one you could try, you'll have to install it, use synaptic to install, look for pulseaudio and install.
codecs: you must have the gstreamer codecs to get sound out of any file, I recommend you to install all the gstreamer plugins, the good, bad, ugly and fffmepg, install also the ubuntu-restricted-extras package.

---

### Post by rookie4evr on 2008-04-06
[PHP]look to get sound, make sure you have the speakers enabled (right click on the panel speaker icon, open volume crontrol, see if all items are enabled, check also volume level) 
drivers: you already have two installed by default, right click on the panel speaker icon, select preferences, you can choose there either one 'alsa' or 'oss', if neither of these two support your hardware (which I don't think is the case here, it should work) there is still another one you could try, you'll have to install it, use synaptic to install, look for pulseaudio and install.
codecs: you must have the gstreamer codecs to get sound out of any file, I recommend you to install all the gstreamer plugins, the good, bad, ugly and fffmepg, install also the ubuntu-restricted-extras package.
__________________

[/PHP]


hmmmm 
so, I have to download to things from, synaptic:
#1: gstreamer codecs 
#2: ubuntu-restricted-extras package
all i do is, type these two in the search button right in Synpatic .......
will try it ....

---

### Post by rookie4evr on 2008-04-06
"look to get sound, make sure you have the speakers enabled (right click on the panel speaker icon, open volume crontrol, see if all items are enabled, check also volume level) 
drivers: you already have two installed by default, right click on the panel speaker icon, select preferences, you can choose there either one 'alsa' or 'oss', if neither of these two support your hardware (which I don't think is the case here, it should work) there is still another one you could try, you'll have to install it, use synaptic to install, look for pulseaudio and install.
codecs: you must have the gstreamer codecs to get sound out of any file, I recommend you to install all the gstreamer plugins, the good, bad, ugly and fffmepg, install also the ubuntu-restricted-extras package.
"

I did everything u told me :( ..nothing is working .....

---

### Post by danbuter on 2008-04-06
double click the volume button. Go to preferences. Turn on surround sound. Unmute it and raise volume.

---

### Post by Cubby on 2008-04-06
This how-to helped me bunches

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by rookie4evr on 2008-04-07
[PHP](3) Check to see if the ALSA driver for your sound card exists. Go to http://www.alsa-project.org/alsa-doc/ and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).[/PHP]

can some one tell me ... which alsa driver goes with my sound card please....

---

### Post by rookie4evr on 2008-04-08
"requisted operation requires superuser pivilege" ????

---

### Post by redbob on 2008-04-08
Of course, my friend. Everything you need to do such configuration and installing must be did with "sudo" before the command. For example, execute in your terminal:
> sudo alsamixer
then slide up ALL items you have. Did sound appeared??
Other thing you could try is to make a test in Sound. Go to System>Preferences>Sound. At 'devices' tab, choose "auto-detect" to Sound Events and click in Test button. Then try with other, choosing one after another.

---


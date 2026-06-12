---
title: "help with audio drivers"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by maybevampires on 2005-07-26
i have two audio devices one is the on board device the second is an m-audio delta-44 card i use for digital recording. i found the drivers i need and downloaded them but when i go to install it says i have a conflicting driver, i was curious about the ablity to run multipule sound cards here is my command lines

root@maxx:/home/dan # cd /tmp
root@maxx:/tmp # ls
audacity1.2-dan  keyring-R0hKrJ                      oss-install
EULA             libgksu1.2-Vi5jsw                   oss.pkg
filex5Xn8J       mapping-dan                         ssh-mSxSUI6832
gconfd-dan       mozilla-thunderbird-pkg.aeWceX      ui_curses.so
gconfd-root      orbit-dan                           ui_X.so
hsperfdata_dan   orbit-root
INSTALL          oss3993b-linux-x86-v26-regparm.tar
root@maxx:/tmp # tar xvf oss3993b-linux-x86-v26-regparm.tar
INSTALL
EULA
oss-install
oss.pkg
ui_X.so
ui_curses.so
root@maxx:/tmp # ./oss-install
Checking for any previously installed sound drivers...
*** Sound driver is already running - trying to unload it ***


You appear to have the the kernel level sound driver installed as a loadable
module. Unload it by executing rmmod sound and try installing OSS/Linux again.

If this error repeats again you probably have the sound driver being loaded
automagically by the kerneld daemon. In this case you should log out from the
X Windows session, then press <ctl><alt><F1> and log in on the Linux console
as root and then install OSS again.

Am I allowed to do these changes automatically for you (Y/N) ?



am i missing somthing here or what any input would be appreciated

---

### Post by varunus on 2005-07-26
The drivers look very old and out of date; it looks like you're trying to install OSS (open sound system) drivers instead of ALSA (advanced linux sound architecture) drivers.  OSS is deprecated and not used anymore, so I would not recommend installing drivers for it.

Can you post the output of "lspci" and "lsmod | grep snd" in a terminal?

The way to set up multiple sound cards (including using one just for recording) is to use the ".asoundrc" file.  This is a file you have to create in your home directory containing sound settings.  I can help you make one if you post the output of the above.

---

### Post by maybevampires on 2005-07-26
root@maxx:/home # lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
root@maxx:/home # lsmod | grepsnd
bash: grepsnd: command not found
root@maxx:/home # lsmod | grep snd
snd_ice1712            57412  0
snd_ice17xx_ak4xxx      4096  1 snd_ice1712
snd_ak4xxx_adda         5760  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9984  1 snd_ice1712
snd_i2c                 5376  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         7168  1 snd_ice1712
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd_intel8x0           29984  0
snd_ac97_codec         64608  2 snd_ice1712,snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_ice1712,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  13 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

thnak you for the support, what next?

---

### Post by varunus on 2005-07-27
It seems that both of your sound cards are being detected.

Try the following howto:
[http://www.ubuntuforums.org/showthread.php?t=27186](http://www.ubuntuforums.org/showthread.php?t=27186)

After this, can you at least hear sound? If you can, we can do a little modification to the /etc/asound.conf file you create in the howto to enable recording too.  :)

Good luck.

---


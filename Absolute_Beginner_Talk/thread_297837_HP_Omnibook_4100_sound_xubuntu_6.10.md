---
title: "HP Omnibook 4100 sound xubuntu 6.10"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Windsurfer99 on 2006-11-11
Despite my best efforts and a lot of time searching the forums I am unable to get sound working on my HP Omnibook 4100 ](*,) I have added pnpbios=off to the /boot/grub/menu.lst but do not have the option within the PC BIOS to disable pnp.  I have created an /etc/modprobe.d/sound file containing the options for cs4236 sound and added snd-cs4236 to /etc/modules.

output from aplay -l
aplay: device_list:222: no soundcards found...

output from lspci
00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:04.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:04.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

output from dmesg
[17621.295457] lp0: using parport0 (interrupt-driven).
[17621.613538] CS4236+ soundcard not found or device busy
[17621.994398] NET: Registered protocol family 17
[17622.033884] Adding 200772k swap on /dev/disk/by-uuid/52006a8c-14e2-49a4-99fa-ab6444dacac9.  Priority:-1 extents:1 across:200772k
[17622.289448] EXT3 FS on hda1, internal journal
[17635.856612] NET: Registered protocol family 10
[17635.857485] lo: Disabled Privacy Extensions
[17635.859021] IPv6 over IPv4 tunneling driver
[17646.462387] ath0: no IPv6 routers present
[17676.504050] apm: BIOS version 1.2 Flags 0x03 (Driver version

/etc/modprobe.d/sound
options snd-cs4236 isapnp=0 port=0x530 cport=0x538 irq=5 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0

Any help or guidance is appreciated...I would hate to have to reload Windows to get sound:cry: 

Thanks

---

### Post by linuxmama on 2007-04-24
I know this post is old, but I thought this might help someone else in the same situation.

I got the sound to work using these options:
options snd-cs4236 isapnp=0 port=0x530 **cport=0xf00** irq=5 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0

Also [http://alsa.opensrc.org/Cs4236](http://alsa.opensrc.org/Cs4236) says that the sound card should be set to "Enabled" rather than "Auto" in the BIOS setup.  Mine was already set that way, so I'm not sure if that's really necessary.

---

### Post by fabschf on 2008-03-05
I don't know if anyone's still using one of these old machines.
I installed Xubuntu 7.10 after replacing the RAM  with an 160MB version and it worked reasonably well, except for the sound.


This is how I got it working (there are plenty of explanations on the net but none of them did the trick for me):

Looking at the startup messages instead of the splash screen (use ctrl-Alt-F1 when the splash screen comes up) told me that the system tries to load snd-cs4232 and fails with a PnP-error.

People on forums talk about using snd-cs4236 with this laptop, so I tried to manually remove snd-cs4232 using modprobe -r. This did not lead to success, apparently it cannot be removed properly once the x-server is up.

So I added the following line to /etc/modprobe.d/blacklist

> # stop snd-cs4236 from loading
blacklist snd-cs4232

After a reboot I was then able to successfully load snd-cs4236:
> sudo modprobe snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0


Therefore I added the following line to /etc/modules

> # manually load the correct sound module
snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0

Without the options it doesn't seem to load correctly.
It now gives a little noise each time at startup when the module loads but I can listen to my music again :-).

It does not work when ACPI is switched on, so do make sure NOT to have a Kernel option "acpi=force" in your /boot/grub/menu.lst
I know that this means that the computer is no longer able to switch itself properly off after shutdown. 

Workaround: add the kernel option "apm=force" to /boot/grub/menu.lst
and add the line

> apm power_off=1

to /etc/modules


Good Luck!

---


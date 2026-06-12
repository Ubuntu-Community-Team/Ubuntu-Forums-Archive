---
title: "how do io set up a sound card with linux?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by ecto on 2005-10-06
How do i get about installing a sound card in linux. Do i do this is root or sudo? Then what next?

---

### Post by swerner on 2005-10-06
[QUOTE=ecto]How do i get about installing a sound card in linux. Do i do this is root or sudo? Then what next?[/QUOTE]

If you are using Ubuntu it should detect your sound card automagically.  However if you are still have problems, try [http://www.ubuntuguide.org/#configuresoundproperly]("http://www.ubuntuguide.org/#configuresoundproperly") to configure your sound properly in Gnome.

If you still have troubles, type 'lsmod | grep snd' in the terminal and copy the output and paste it here.  If you have lots of "snd_*" entries in the output, that's a good start.  Also tell us what sound card you have too.

Cheers

---

### Post by dskloet on 2005-10-08
I've got the same problem.
I tried the instructions from the guide but it didn't help.
"lsmod|grep snd" gives zero output.
My sound card is a Sound Blaster 16.

I really hope you can help me,
David

The entire output of lsmod is:
```

Module                  Size  Used by
ipv6                  217408  6
af_packet              20232  2
ide_floppy             17664  0
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
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
mousedev               10912  1
psmouse                26116  0
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ne2k_pci               10464  0
8390                    9088  1 ne2k_pci
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
piix                    9476  1
ide_core              125268  5 ide_floppy,ide_cd,ide_disk,ide_generic,piix
unix                   24624  456
fbcon                  34176  0
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0
commoncap               6784  1 capability

```

---


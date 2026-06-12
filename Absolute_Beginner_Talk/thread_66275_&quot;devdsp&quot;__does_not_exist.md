---
title: "&quot;/dev/dsp&quot;  does not exist"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by rainbow_fire on 2005-09-16
hi ok my totem movie player no stop brings this up it is also a problem i am having with my sound drive although all of my alsa packages have been installed i need to know how to create the directories i think???? can someone help me.

---

### Post by mlomker on 2005-09-16
There are commands to manually create that device but it should be automatically done if your driver is loaded.  Do you know what your sound card is?

**lspci** should list the devices in your machine and one of them will be the sound card.

**lsmod | more** will give you a list of drivers that are loaded.

---

### Post by rainbow_fire on 2005-09-16
ok so i  took outt he onesthat i already knew what they were the graphics and the ethernet cards i dont know what a sound card looks like i had sound when i had windows and i messed up really bad one time and i got an extra tool bar from no where that made a beep when i pushed it but it went away and so did my sound haha i have to go to work so watch my thread ok please
Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  03)
0000:00:02.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:02.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:02.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:02.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)

---

### Post by mlomker on 2005-09-16
I don't recognize those.  I assume that the sound is built into the motherboard?

Post the output of **lsmod**.

[Here is](http://linux.iuplog.com/default.asp?item=94639) a check-list that you can try out.

---

### Post by rainbow_fire on 2005-09-17
here is the results from lsmod it is all sooo greek to me lol i have already tried the solutions in the link you posted some time ago i know i must be missing something simple. :o)
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
e100                   32384  0
mii                     4736  1 e100
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
usblp                  12032  0
uhci_hcd               30224  0
usbcore               107384  3 usblp,uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
pcspkr                  3816  0
rtc                    12216  0
floppy                 54864  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  592
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by mlomker on 2005-09-17
I don't see anything loaded that looks like a sound driver.  It's almost like your system isn't recognizing it at all!  Have you checked your BIOS to make sure the sound subsystem isn't disabled?

Have you booted another operating system were sound works?  Maybe a Knoppix CD?

---

### Post by rainbow_fire on 2005-09-17
i did get it to beep three timesonce over some strange tool bar that has never been seen since. so the potental for sound exists can i just over write the system with the comand lines that will create the /dev/dsp thing

---

### Post by mlomker on 2005-09-17
I assume that when you walked through the sound troubleshooting that you've made sure that the volume controls and all that jazz are turned up?

There are similar threads on here if you searc.  [Here's one](http://ubuntuforums.org/showthread.php?t=62053&highlight=%2Fdev%2Fdsp) that I tried to help out in.

---


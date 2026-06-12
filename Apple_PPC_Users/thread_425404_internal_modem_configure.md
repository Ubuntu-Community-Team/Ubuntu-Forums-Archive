---
title: "internal modem configure"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by oaklad on 2007-04-27
Like almost everyone else I am having trouble configuring my internal dial-up modem on my iBook G3 Dual. The Airport card works great. I am quite the newbee and have tried to follow past postings. Here is what I have found so far:

gerald@iBookG3:~$ dmesg | grep modem
[   65.875025] pmac_zilog: i2c-modem detected, id: 1
[   65.875117] ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem

gerald@iBookG3:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?


gerald@iBookG3:~$ lsmod
Module                  Size  Used by
ppdev                  11268  0 
lp                     13612  0 
parport                44624  2 ppdev,lp
cpufreq_userspace       5588  1 
cpufreq_stats           6532  0 
cpufreq_powersave       2176  0 
cpufreq_ondemand        8128  0 
cpufreq_conservative     8448  0 
ppp_generic            33972  0 
slhc                    7488  1 ppp_generic
sbp2                   26440  0 
scsi_mod              175824  1 sbp2
apm_emu                 8140  1 
af_packet              25192  2 
snd_powermac           49916  1 
snd_aoa_i2sbus         24516  0 
airport                 7232  0 
orinoco                45556  1 airport
hermes                  8736  2 airport,orinoco
sungem                 35492  0 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
evdev                  12736  8 
tsdev                   9120  0 
sungem_phy             10720  1 sungem
snd_pcm                95556  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
uninorth_agp           11144  1 
agpgart                38204  1 uninorth_agp
snd                    69940  8 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
pmac_zilog             21060  0 
serial_core            24896  1 pmac_zilog
ext3                  161576  1 
jbd                    69556  1 ext3
usbhid                 52132  0 
ohci1394               41840  0 
ieee1394              431440  2 sbp2,ohci1394
ide_cd                 36420  0 
ohci_hcd               24228  0 
usbcore               151676  3 usbhid,ohci_hcd
cdrom                  47932  1 ide_cd
ide_disk               19296  3 
capability              5320  0 
commoncap               8064  1 capability

gerald@iBookG3:~$ sudo setserial /dev/ttyS0 spd_vhi
sudo: setserial: command not found

When I try to add the line "pmac_zilog" to the /etc/modules file I get:
gerald@iBookG3:~$ sudo /etc/modules
sudo: /etc/modules: command not found

Any help would be appreciated.

By the way XUBUNTU 6.10 was a breeze to install. Thanks to all. I downloaded UBUNTU 7.04 but was unable to update directly from the cd. Will this need to be done from the terminal?:(

---

### Post by oaklad on 2007-04-27
Duh!

Quite the newbee. While awaiting a comment I ran Synaptic Package Manager only to find that setserial package was not installed.

I will keep on trucking.

---

### Post by oaklad on 2007-04-28
I continue to struggle trying to connect the internal 56k modem on my iBook G3 Dual . I installed setserial but am having trouble establishing an argument. I have tried:

gerald@iBookG3:~$ sudo dmesg | grep modem
[   61.627401] pmac_zilog: i2c-modem detected, id: 1
[   61.627498] ttyS0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem

gerald@iBookG3:~$  sudo setserial /dev/ttyS0 port 0x80013020  skip_test auto_irq autoconfig
Cannot set serial info: Invalid argument

gerald@iBookG3:~$ sudo setserial /dev/ttyS0 UART: 16650, Port:0x80013020, IRQ: 22
Invalid flag: UART:

Can someone help me set the correct argument?

---

### Post by TCE on 2007-07-05
I was just able to get my internal modem working with no problems with ubuntu feisty on my ibook g3 333mhz.  I just used gnome ppp and it detected it right away.  I heard something that xubuntu uses an older kernel than ubuntu.  i hope this can help you.

---

### Post by oaklad on 2007-08-05
I went to a WI-FI cafe and did a complete install of Ubuntu 5.04. When I got home I was able to connect via my internal modem. 

Question:

At what point did the kernel break for support of internal modems? Can my version of Ubuntu be upgraded without losing modem accessibility?

I have been unsuccesful with Ubuntu 6 and Ubuntu 7.

---


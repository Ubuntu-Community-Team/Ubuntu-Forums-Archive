---
title: "serial internal modem on new-world iBook G3"
date: 2004-12-16
forum: Apple PPC Users
---

### Post by burningbed on 2004-12-16
Hi!
I've installed Ubuntu 4.10 on a new-world Apple G3 iBook. According to
dmesg the internal modem is detected and it seems to be a serial modem.

# dmesg | grep modem
pmac_zilog: i2c-modem detected, id: 1
ttyS0 at MMIO 0x80013020 (irq=22) is a Z85c30 ESCC - Internal Modem

I can't make a connection with the gnome network-admin, so I tried
wvdial. That connects, but it I see lots of garbage on the screen which
I suspect to be information sent to the OS to make the modem sounds
(that's only a guess though, based on what I've read on various
webpages). Then I get an error message saying that the modem hung up
(ppp exit code 16) and it tries to reconnect with the same result.
[...]
pppd: +FCLASS=0L3
Disconnecting at [date & time]
The PPP daemon has died: A modem hung up the phone (exit code = 16)
[...]

/var/log/messages does not contain any usefull info.

I really need to use the modem. It seems like it shouldn't be too hard
to get it to work as it is already detected and connects briefly, but I
cannot find out how. I read on a webpage that sending the ATZL0L0
command to the modem would help. I tried that with echo ATZL0L0 >
/dev/ttyS0 and I tried saving it with echo AT\&W > /dev/ttyS0 and echo
AT\&W > /dev/ttyS0 but nothing changes.

Do you have any suggestions? Any help would be appreciated. There must be some of you with the same hardware who got it to work ... please let me know.

By the way during install, I chose "do not configure network at this
time", as I was not connected to the internet. However, wireless
connections work.

Thanks!

---

### Post by trash on 2004-12-16
dunno if this'll help but this is my wvdial.conf... internal G4,
dmesg | grep modem is the same as yours
pmac_zilog: i2c-modem detected, id: 1
ttyS0 at MMIO 0x80013020 (irq=22) is a Z85c30 ESCC - Internal Modem

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>

Dial Command = ATDT
Phone = xxxxxxxxxxxxxxxx
Username = xxxxxxxxxxxx
Password = xxxxxxxxxxx
Stupid mode = 1
[Dialer ppp0]
Init2 = ATL1
Password = xxxxxxxxx
Stupid mode = 1
Init1 = ATZ
Phone = xxxxxxxxxxxxx
Username = xxxxxxxxxxxx
Dial Command = ATDT
~

---

### Post by Ptero-4 on 2004-12-18
[QUOTE=burningbed]Hi!
I've installed Ubuntu 4.10 on a new-world Apple G3 iBook. According to
dmesg the internal modem is detected and it seems to be a serial modem.

# dmesg | grep modem
pmac_zilog: i2c-modem detected, id: 1
ttyS0 at MMIO 0x80013020 (irq=22) is a Z85c30 ESCC - Internal Modem

I can't make a connection with the gnome network-admin, so I tried
wvdial. That connects, but it I see lots of garbage on the screen which
I suspect to be information sent to the OS to make the modem sounds
(that's only a guess though, based on what I've read on various
webpages). Then I get an error message saying that the modem hung up
(ppp exit code 16) and it tries to reconnect with the same result.
[...]
pppd: +FCLASS=0L3
Disconnecting at [date & time]
The PPP daemon has died: A modem hung up the phone (exit code = 16)
[...]

/var/log/messages does not contain any usefull info.

I really need to use the modem. It seems like it shouldn't be too hard
to get it to work as it is already detected and connects briefly, but I
cannot find out how. I read on a webpage that sending the ATZL0L0
command to the modem would help. I tried that with echo ATZL0L0 >
/dev/ttyS0 and I tried saving it with echo AT\&W > /dev/ttyS0 and echo
AT\&W > /dev/ttyS0 but nothing changes.

Do you have any suggestions? Any help would be appreciated. There must be some of you with the same hardware who got it to work ... please let me know.

By the way during install, I chose "do not configure network at this
time", as I was not connected to the internet. However, wireless
connections work.

Thanks![/QUOTE]
 Connecting is simple. Just run sudo pppconfig enter your password and follow the on-screen instructions (Tip: leave the ISP name as "provider"). After completing the ppp configuration through pppconfig go to the users and groups utility which is in the "system" menu in the top panel, add the group dip to your list of groups, log out and log in again and finally enable the modemlights applet. If you left the ISP name as "provider" the applet will be ready to run. But if you changed the ISP name in pppconfig you will need to put an space and your ISP name after the pon and the poff commands in the applet configuration dialog.

---


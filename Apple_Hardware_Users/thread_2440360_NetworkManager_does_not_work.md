---
title: "NetworkManager does not work"
date: 2020-04-09
forum: Apple Hardware Users
---

### Post by fil3000 on 2020-04-09
Dear ubuntu community,


I have a problem with my ubuntu installation that prevents me from going online. I am not the proest of Linux users and after researching, trying out different thing and failing, I decided to ask you. Maybe you can help.

_1. Setup:_ I have a MacBook Pro (2016) with dual boot. And I am using the ubuntu 20.04 Focal Fossa Beta version. Since I had the exact same problem with Mint 19.3 (except my phone hotspot worked), I dare say that I do not think the problem arises from the Beta status of the OS. I am also not able (in both) to use my touchpad, but that's for another day.

_2. The problem:_ I can install ubuntu without any major problems, while using an external mouse. I can, however, not access the internet. When I enter my password, I will be prompted again and again to authenticate.

_3. Self diagnosis:_ After researching and trying out, I found out, that the network manager is not working.

```
**fub@fub:~/Desktop$** *systemctl status NetworkManager.service*
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: **failed** (Result: exit-code) since Thu 2020-04-09 06:14:40 EDT; 36s ago
       Docs: man:NetworkManager(8)
    Process: 6468 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, status=1/FAILURE)
   Main PID: 6468 (code=exited, status=1/**FAILURE**)
Apr 09 06:14:40 fub systemd[1]: NetworkManager.service: Scheduled restart job, restart counter is >
Apr 09 06:14:40 fub systemd[1]: Stopped Network Manager.
Apr 09 06:14:40 fub systemd[1]: NetworkManager.service: Start request repeated too quickly.
Apr 09 06:14:40 fub systemd[1]: NetworkManager.service: **Failed** with result 'exit-code'.
Apr 09 06:14:40 fub systemd[1]: **Failed** to start Network Manager.
```

_4. Tried solutions:_ I tried to activate the Network Manager, but it failed.

```
**fub@fub:~/Desktop$** [I]sudo service network-manager start
[/I]Job for NetworkManager.service **failed** because the control process exited with error code.
See "systemctl status NetworkManager.service" and "journalctl -xe" for details.
```

And I tried to reinstall it. I downloaded it, while in macOS and put it on a USB stick. Also didn't work.

```
**fub@fub:~/Desktop$** [I]sudo dpkg -i das_hier_network-manager_1.22.10-1ubuntu1_amd64.deb 
[/I](Reading database ... 149231 files and directories currently installed.)
Preparing to unpack das_hier_network-manager_1.22.10-1ubuntu1_amd64.deb ...
Unpacking network-manager (1.22.10-1ubuntu1) over (1.22.10-1ubuntu1) ...
Setting up network-manager (1.22.10-1ubuntu1) ...
Job for NetworkManager.service failed because the control process exited with error code.
See "systemctl status NetworkManager.service" and "journalctl -xe" for details.
Processing triggers for systemd (245.2-1ubuntu2) ...
Processing triggers for dbus (1.12.16-2ubuntu2) ...
Processing triggers for man-db (2.9.1-1) ...
```

Furthermore, I tried to reinstall ubuntu, but during the installation I already had the error.

_5. Despair:_ I don't know, where to go from here. Can you help? I'd really appreciate it since I want to try to use Linux in my every-day life, due to it's awesomeness.

Thank you, best and stay healthy
fil

---

### Post by Cheese Sandwich on 2020-05-10
Type this command:

```
sudo nano /lib/firmware/brcm/brcmfmac43602-pcie.txt

```

And paste this into it:

```
boardrev=0x1101

sromrev=11
boardtype=0x073e
vendid=0x14e4
devid=0x43ba

macaddr=00:90:4c:0d:f4:3e

#ccode=X3
#regrev=15
ccode=0
regrev=1

# Board flags:
# X BFL_BTCOEXIST          = 0x00000001   This board implements Bluetooth coexistence
#   BFL_EXTLNA             = 0x00001000   This board has an external LNA (2G)
#   BFL_FEM_BT             = 0x00400000   This board has shared antenna w/ BT
# X BFL_PALDO              = 0x02000000   Power topology uses PALDO ? - CHECK
#   BFL_EXTLNA_5GHz        = 0x10000000   Board has an external LNA in 5GHz band
boardflags=0x02000001

# Board flags 2:
#   BFL2_BT_SHARE_ANT0     = 0x00800000   share core0 antenna with BT
# X BFL2_LNA1BYPFORTR2G    = 0x40000000   acphy, enable lna1 bypass for 2G clip lo
# X BFL2_LNA1BYPFORTR5G    = 0x80000000   acphy, enable lna1 bypass for 5G clip lo
# X BFL2_SPUR_WAR          = 0x00000200   Board has a WAR for clock-harmonic spurs
#   BFL2_2G_SPUR_WAR       = 0x00002000   Board has a WAR to reduce and avoid clock-harmonic spurs in 2G band
boardflags2=0xC0000000

# Board flags 3:
# X BFL3_RCAL_WAR          = 0x00000008   acphy rcal war active on this board (mainly for 4335a0)
# X BFL3_FEMTBL_FROM_NVRAM = 0x00000100   acphy, femctrl table is read from nvram
boardflags3=0x40000108

#btc_mode=0

#### added rx de-sense

btcdyn_flags=0x7
# Media profile
btcdyn_profile_type=0x2  
btcdyn_dflt_dsns_level=0
btcdyn_low_dsns_level=0
btcdyn_mid_dsns_level=21
btcdyn_high_dsns_level=22
btcdyn_default_btc_mode=4
# --- number of rows in the array vars below ---
btcdyn_msw_rows=1
btcdyn_dsns_rows=1
# --- mode switch data rows (max is 4) ---
btcdyn_msw_row0=1,-16,-95,-100
# --- desense switching data rows (max is 4) ---
btcdyn_dsns_row0=4,-16,-63,-95

#### end of rx de-sense


xtalfreq=40000
otpimagesize=484
nocrc=1
muxenab=0x1
btc_params82=0x60



########################################################
# RF Control Definitions

antswitch=0
rxchain=3
txchain=3
aa2g=3
aa5g=3
femctrl=10

# antenna gain per core g-band
agbg0=2
agbg1=2

# antenna gain per core a-band
aga0=2
aga1=2

# RFSWCTRL 2G and 5G iLNA
#            WL_TX,     WL_RX,     WL_RX_ATTN, BT_TX_RX, WL_MASK
swctrlmap_2g=0x04010401,0x08080808,0x04010401,0x00000000,0x000000ff
swctrlmap_5g=0x08080808,0x04010401,0x08080808,0x00000000,0x000000ff

swctrlmapext_2g=0x00000000,0x00000000,0x00000000,0x000000,0x003
swctrlmapext_5g=0x00000000,0x00000000,0x00000000,0x000000,0x003
########################################################

# Bypass offsetting PAPD_EPS_TABLE_PER_TX_INDEX feature
epsdelta2g0=0,-1,0,0,0,0,0,0
epsdelta2g1=0,-1,0,0,0,0,0,0

########################################################
# Rx gain and RSSI parameters
#
# Default so do not set:
# rxgaincal_rssical=0
# rssi_cal_rev=0
# rxgains[25]gtrisoa[01]
# rxgains[25]g[mh]trelnabypa[01]=0

# BW20,BW40
rssicorrnorm_c0=4,4
rssicorrnorm_c1=4,4

# subband5gver=4 =>
# BW20,BW40,BW80  <5250|<5500|<5745|>=5745
#                  <70m| <100| <149|>=149
rssicorrnorm5g_c0=1,2,3,1,2,3,1,2,3,1,2,3
rssicorrnorm5g_c1=1,2,3,1,2,3,1,2,3,1,2,3

########################################################


########################################################
# 20 MHz in 40 MHz Power Offsets and Duplicate Modes
# 2G and 5G bands

sb20in40hrpo=0x0
sb20in40lrpo=0x0

dot11agduphrpo=0x0
dot11agduplrpo=0x0
########################################################


########################################################
# PAPD parameters
fastpapdgainctrl=0

########################################################
# 2G TSSI / PA Parameters

tworangetssi2g=1
tssipos2g=1
extpagain2g=2
pdgain2g=2

# 2G Max Power
maxp2ga0=74
maxp2ga1=74

# 2G PA Parameters
# Order is A1,B0,B1
#pa2ga0=-125,6514,-739  used for p113 and p115
#pa2ga1=-141,6391,-738  used for p113 and p115
#pa2ga0=-169,6473,-759
#pa2ga1=-174,6462,-759
pa2ga0=-162,6368,-735
pa2ga1=-170,6349,-742



# 2G Power Offsets
cckbw202gpo=0x0000
cckbw20ul2gpo=0x0000
mcsbw202gpo=0x99644422
mcsbw402gpo=0x99644422
dot11agofdmhrbw202gpo=0x6666
ofdmlrbw202gpo=0x0022

########################################################

#AvVmid_c0=2,140,2,145,2,145,2,145,2,145
#AvVmid_c1=2,140,2,145,2,145,2,145,2,145
#AvVmid_c2=0,0,0,0,0,0,0,0,0,0

# AvVmid 2GHz and 5GHz LabNotebook 43569A2_012 data from pcieir
AvVmid_c0=2,140,2,125,2,125,2,135,2,135
AvVmid_c1=2,140,3,100,3,100,3,100,3,100
AvVmid_c2=0,0,0,0,0,0,0,0,0,0

########################################################
# 5G TSSI / PA Parameters

tworangetssi5g=0
tssipos5g=1
extpagain5g=2
subband5gver=0x4
pdgain5g=2

# 5G Max Powers
maxp5ga0=74,74,74,74
maxp5ga1=74,74,74,74

# 5G PA Parameters initial
#pa5ga0=152,5462,658,150,5547,663,150,5950,697,170,5782,688
#pa5ga1=177,5661,685,178,5712,691,166,6161,725,195,5811,706

# 5G PA Parameters *** from LabNotebook 43569A0_099 TSSI opt for 8::18:
#pa5ga0=-181,5835,-709,-183,5842,-712,-186,5832,-710,-187,5744,-703
#pa5ga1=-198,5767,-710,-190,5915,-721,-185,6067,-732,-186,6024,-731

# Updated with LabNotebook 43569A2_012
pa5ga0=-194,5833,-713,-186,6042,-730,-181,5927,-714,-197,5562,-687
pa5ga1=-186,6139,-737,-196,5988,-726,-203,5852,-713,-204,5836,-713



# 5G Power Offsets
mcsbw205glpo=0x88766663
mcsbw405glpo=0x88666663
mcsbw805glpo=0xbb666665
mcsbw205gmpo=0xd8666663
mcsbw405gmpo=0x88666663
mcsbw805gmpo=0xcc666665
mcsbw205ghpo=0xdc666663
mcsbw405ghpo=0xaa666663
mcsbw805ghpo=0xdd666665
mcslr5glpo=0x0000
mcslr5gmpo=0x0000
mcslr5ghpo=0x0000
sb20in40hrpo=0x0
sb20in80and160hr5glpo=0x0
sb40and80hr5glpo=0x0
sb20in80and160hr5gmpo=0x0
sb40and80hr5gmpo=0x0
sb20in80and160hr5ghpo=0x0
sb40and80hr5ghpo=0x0
sb20in40lrpo=0x0
sb20in80and160lr5glpo=0x0
sb40and80lr5glpo=0x0
sb20in80and160lr5gmpo=0x0
sb40and80lr5gmpo=0x0
sb20in80and160lr5ghpo=0x0
sb40and80lr5ghpo=0x0

pdoffset40ma0=0x0000
pdoffset80ma0=0x0000
pdoffset40ma1=0x0000
pdoffset80ma1=0x0000

########################################################


########################################################
# Temperature Values

tempthresh=120
tempoffset=255
rawtempsense=0x1ff

phycal_tempdelta=255
temps_period=15
temps_hysteresis=15

########################################################


```

And reboot. If wifi still doesn't work, try replacing this line

```
macaddr=00:90:4c:0d:f4:3e

```

with your own wifi device MAC.

---

### Post by wildmanne39 on 2020-05-10
Hello Cheese Sandwich.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thread moved to Apple Hardware Users.

Will you please explain what your instructions do and why you think it will help the OP, I do not think it is clear that he is using the brcmfmac firmware and the OP states and posts information that suggests network manger is not working.

---


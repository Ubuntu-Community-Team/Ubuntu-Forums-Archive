---
title: "Suspend to Disk Powerbook G4 12'' (nvidia graphics card)"
date: 2006-12-13
forum: Apple PPC Users
---

### Post by dbuzi123 on 2006-12-13
Hi,

I'm trying to get suspend to disk to work.  I've heard this is easier to get working than suspend to ram.  Currently when I close the lid, or push the power button, or access the ubuntu shutdown dialog and select suspend it locks the screen and gives the option to re login by typing my password.  Any suggestions to get this working properly?

This is my pbbuttonsd.conf:

# Configuration file for PBButtonsd >= Version 0.5
# for complete list of options please see pbbuttonsd.conf man-page

# [SYSTEM]
#userallowed           = "paranoid"	; user who is allowed to use IPC
autorescan            = yes		; automatic rescan of event devices
CmdTimeout            = 8

# [MODULE POWERSAVE]
onAC_policy           = performance	; nochange, performance, custom or powersave
onAC_TimerAction      = none		; none, suspend-to-ram, suspend-to-disk, blankscreen
onAC_CoverAction      = suspend-to-disk
onAC_KeyAction        = none		; SleepKey
onAC_SuspendTime      = 0		; time in 1/10 seconds
onAC_DimTime          = 0		; time in 1/10 seconds

onBattery_policy      = powersave
onBattery_TimerAction = none		; none, suspend-to-ram, suspend-to-disk, blankscreen
onBattery_CoverAction = suspend-to-disk
onBattery_KeyAction   = none		; SleepKey
onBattery_SuspendTime = 0		; time in 1/10 seconds
onBattery_DimTime     = 0		; time in 1/10 seconds

SleepKey              = 116
SleepKeyDelay         = 0		; values > 0 may be dangerous, if the power key is used to trigger sleep
BWL_first             = 22		; first battery warnlevel, time in minutes
BWL_second            = 10		; second battery warnlevel, time in minutes
BWL_last              = 3		; last battery warnlevel, time in minutes
Script_PMCS           = "/etc/power/pmcs-pbbuttonsd %s %s %s"
EmergencyAction       = sleep		; action, if battery is critically low
HeartbeatBeep         = no		; beep, if nothing else showed that the computer lives
CPULoad_sleeplock     = yes
CPULoad_min           = 20		; value in percent
CPULoad_period        = 20		; time in seconds
NETLoad_sleeplock     = yes
NETLoad_min           = 4096		; traffic in Bytes/s
NETLoad_period        = 20		; time in seconds
NETLoad_device        = "eth0"

# [MODULE DISPLAY]
#LCD_Brightness        = 8		; initial LCD brightness level
LCD_FadingSpeed       = 4		; 0 = no smooth fading
LCD_AutoAdjust        = yes		; only on Aluminum PowerBooks
LCD_IllumUpKey        = 225
LCD_IllumDownKey      = 224
LCD_Threshold         = 94
LCD_AutoAdjMin_Bat    = 2		; autoadjust parameter
LCD_AutoAdjMax_Bat    = 7
LCD_AutoAdjMin_AC     = 1
LCD_AutoAdjMax_AC     = 15
#KBD_Brightness        = 0		; initial keyboard illumination level
KBD_OnBrightness      = 5		; initial level if KBD on/off key is pressed
KBD_FadingSpeed       = 5		; 0 = no smooth fading
KBD_AutoAdjust        = yes		; only on Aluminum PowerBooks
KBD_IllumUpKey        = 230
KBD_IllumDownKey      = 229
KBD_IllumOnKey        = 228
KBD_Threshold         = 28		; only on Aluminum PowerBooks
dev_FrameBuffer       = "/dev/fb0"
UseFBBlank            = yes
DimFullyDark          = no
CRT_MirrorKey         = 65 + ctrl

# [MODULE MIXER]
SoundSystem           = none		; none, auto, OSS or ALSA
#Volume                = 50		; initial volume level
Speakers_muted        = no		; mute after startup?
VolumeUpKey           = 115
VolumeDownKey         = 114
MuteKey               = 113
OSS_Mixer             = "/dev/mixer"	; settings for OSS
OSS_Channels          = "volume, speaker"
ALSA_Card             = "default"	; settings for ALSA
ALSA_Elements         = "Master, 'PC Speaker'"
MixerInitDelay        = no

# [MODULE CDROM]
dev_CDROM             = "/dev/cdrom"
EjectCDKey            = 161
EjectCDKeyDelay       = 0

# [MODULE PMAC]
dev_PMU               = "/dev/pmu"
dev_ADB               = "/dev/adb"
TPModeUpKey           = 225 + alt
TPModeDownKey         = 224 + alt
TPMode                = notap
KBDMode               = fkeysfirst
Batlog                = none
NoTapTyping           = no

---

### Post by stmiller on 2006-12-13
Yes you are right. Sleep (suspend to ram) doesn't work on nvidia based ppc hardware. Only ATI. But hibernate (suspend to disk) SHOULD work.

See if the info here helps:

[http://www.ncc.up.pt/~rvr/kh/kh.html](http://www.ncc.up.pt/~rvr/kh/kh.html)

---

### Post by dbuzi123 on 2006-12-14
Thanks for the info.  I'm not sure I really have the experience to rebuild my kernel.  I was hoping there might be some slightly easier way to get this working. I'm also concerned about the compatibility of pmud and pbbuttonsd.  In that article he used pmud, but I have pbbuttonsd.conf

Also, what does the system->preferences->power management dialog actually change.  When I change options in there it doesn't seem to have any effect on my pbbuttonsd.conf, but does effect my system.  So if i specify that it should suspend to disk when I click the powerbutton in my pbbuttonsd.conf file it doesn't change anything....

---

### Post by stmiller on 2006-12-14
You need pmud it looks like. apt-get install pmud. Pmud does not conflict with pbbuttonsd. It sounds like pmud will do what you want. Search for pmud and powerbook.

---

### Post by agds on 2006-12-21
@dbuzi123:

Have you made any headway with this problem?  I'd love to know whether pmud fixed it, since I've also been trying to get power management working properly on my 12" PowerBook G4.  (It's the one with the NVIDIA GeForce FX Go5200.)

---


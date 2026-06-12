---
title: "Pbbuttonsd: Blankscreen and iMac"
date: 2006-07-11
forum: Apple PPC Users
---

### Post by keifer on 2006-07-11
Has anyone else had a problem with getting pbbuttonsd to work when set to 'blankscreen'? Suspend to ram works fine, but I only wish to turn off the screen. I had it working when the machine was running gentoo, so I'm thinking that it may just be the kernel.


My /etc/pbbuttonsd.conf file:
```
# Configuration file for PBButtonsd >= Version 0.5
# for complete list of options please see pbbuttonsd.conf man-page

# [SYSTEM]
#userallowed           = "paranoid"	; user who is allowed to use IPC
autorescan            = no		; automatic rescan of event devices
CmdTimeout            = 8

# [MODULE POWERSAVE]
onAC_policy           = performance	; nochange, performance, custom or powersave
onAC_TimerAction      = blankscreen		; none, suspend-to-ram, suspend-to-disk, blankscreen
onAC_CoverAction      = suspend-to-ram
onAC_KeyAction        = blankscreen		; SleepKey
onAC_SuspendTime      = 3000		; time in 1/10 seconds
onAC_DimTime          = 0		; time in 1/10 seconds

onBattery_policy      = powersave
onBattery_TimerAction = blankscreen		; none, suspend-to-ram, suspend-to-disk, blankscreen
onBattery_CoverAction = suspend-to-ram
onBattery_KeyAction   = blankscreen		; SleepKey
onBattery_SuspendTime = 3000		; time in 1/10 seconds
onBattery_DimTime     = 0		; time in 1/10 seconds

SleepKey              = 116
SleepKeyDelay         = 0		; values > 0 may be dangerous, if the power key is used to trigger sleep
BWL_first             = 22		; first battery warnlevel, time in minutes
BWL_second            = 10		; second battery warnlevel, time in minutes
BWL_last              = 3		; last battery warnlevel, time in minutes
Script_PMCS           = "/etc/power/pmcs-pbbuttonsd %s %s %s"
EmergencyAction       = sleep		; action, if battery is critically low
HeartbeatBeep         = no		; beep, if nothing else showed that the computer lives
CPULoad_sleeplock     = no
CPULoad_min           = 20		; value in percent
CPULoad_period        = 20		; time in seconds
NETLoad_sleeplock     = no
NETLoad_min           = 4096		; traffic in Bytes/s
NETLoad_period        = 20		; time in seconds
NETLoad_device        = "eth1"

# [MODULE DISPLAY]
#LCD_Brightness        = 8		; initial LCD brightness level
LCD_FadingSpeed       = 0		; 0 = no smooth fading
LCD_AutoAdjust        = no		; only on Aluminum PowerBooks
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
SoundSystem           = ALSA		; none, auto, OSS or ALSA
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

```

---


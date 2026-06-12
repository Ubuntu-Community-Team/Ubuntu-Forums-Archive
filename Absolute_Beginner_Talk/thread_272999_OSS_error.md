---
title: "OSS error"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Haydar on 2006-10-07
[img]http://i12.tinypic.com/3zc1xed.png[/img]


TeamSpeak + Games = no sound i even tryed this because i play Enemy-territory

echo "et.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
/proc/asound/card0/pcm1p/oss: Onbekend bestand of map


Unknown map or file error 

something wrong with oss ? i'm out of idea's [-( \

=(

---

### Post by zappa on 2006-10-07
Do you get anything when you type
ls /dev | grep dsp
lshal | grep sound
Reason is probably that you need drivers for your soundcard to be recognised. 

veel success ;-)

---

### Post by Haydar on 2006-10-07
haydar@haydar-desktop:~$ ls /dev | grep dsp
adsp1
dsp
dsp1
haydar@haydar-desktop:~$ shal | grep sound
bash: shal: command not found
haydar@haydar-desktop:~$ lshal | grep sound
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/timer'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/seq'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/sequencer2'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC0D0c'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/dsp'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/audio'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/controlC0'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/mixer'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/midiC1D1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/amidi1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/midiC1D0'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/midi1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D3p'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D2p'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D2c'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D1c'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/adsp1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D0p'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/pcmC1D0c'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/dsp1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/audio1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/controlC1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/mixer1'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/midiC1D2'  (string)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/class/sound/midiC1D3'  (string)
  info.product = 'AT-style speaker sound'  (string)
  pnp.description = 'AT-style speaker sound'  (string)



this is what i get good sign?

still no sound :(

---


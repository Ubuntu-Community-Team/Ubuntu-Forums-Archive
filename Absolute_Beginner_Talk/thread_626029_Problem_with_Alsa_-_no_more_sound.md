---
title: "Problem with Alsa - no more sound"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-11-28
Hi, it looks like I can no longer get any sound using Alsa. I'm not sure what has happened because I've been using Alsa for a while now.

When I start xmms I get the following errors:
> 
** WARNING **: alsa_setup_mixer(): Failed to find mixer element: PCM
total-tracks: 1
testing-track: 0
total-tracks: 1
testing-track: 0

Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.



Starting Guitar Pro with Wine I get this message:

> 
~$ winelauncher ~/.wine/drive_c/Program\ Files/Guitar\ Pro\ 5/GP5.exe
Invoking /usr/bin/wine /home/andrew/.wine/drive_c/Program Files/Guitar Pro 5/GP5.exe ...
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 0
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 1
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 2
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:2
fixme:mixer:ALSA_MixerInit No master control found on UA-25, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Camera         , disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x34f820,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x30060,0x00000000,200,2): stub!



Then with Gtick it popups an error message:

> 
Couldn't start metronome. Please check if specified sound device and sample file are accessible.


Does anyone know what has got messed up and how I can fix it?

---

### Post by master_kernel on 2007-11-28
You might have to recompile ALSA...

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---


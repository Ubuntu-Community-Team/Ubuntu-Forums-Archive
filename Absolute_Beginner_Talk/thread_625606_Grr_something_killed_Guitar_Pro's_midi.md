---
title: "Grr something killed Guitar Pro's midi"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-11-28
I was trying to install my webcam without much success, so I gave up. Now one of my programs, Guitar Pro running under wine, has stopped playing back sound.
I've had this program working for a couple of months now so I'm guessing I must have done something to kill its midi.
Also now Guitar Pro crashes now when I try to adjust its audio settings.

Does anyone know what it could be?

Sound and midi works fine in my other applications.

When I was trying to install my webcam I was mostly installing/uninstalling packages and running easycam2. The only other notable command that I ran was:

 export CC=/usr/bin/gcc-3.4

and then later

export CC=/usr/bin/gcc-4.1

I'm not sure what that actually did? Given that it didn't help me, do I need to reverse whatever it did?

---

### Post by acl123 on 2007-11-28
Following up with some more info - if I start Guitar Pro from the terminal I get the following output before it runs:

> 
$ winelauncher ~/.wine/drive_c/Program\ Files/Guitar\ Pro\ 5/GP5.exe

Invoking /usr/bin/wine /home/andrew/.wine/drive_c/Program Files/Guitar Pro 5/GP5.exe ...
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 0
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 1
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:1
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 2
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:2
fixme:mixer:ALSA_MixerInit No master control found on UA-25, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Camera         , disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x34f820,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x30060,0x00000000,200,2): stub!



---

### Post by iamaqbot on 2007-12-02
I'm having a similar problem. What version are you running? I haven't had sound at all the whole time I've been running Guitar Pro so i'm still trying to figure that out. Do you know of the program Tuxguitar? It's not as good as guitar pro but i've been using that for most of my tabbing, then using guitar pro with out if there's something i can't do on Tuxguitar.

I get this when I run it GP5 in terminal
Invoking /usr/bin/wine /home/timmy/.wine/drive_c/Program Files/Guitar Pro 5/GP5.exe ...
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:EnumDisplayDevicesW ((null),0,0x33f820,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x3005c,0x00000000,200,2): stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8210 (SPI_GETFONTSMOOTHINGORIENTATION)

---

### Post by acl123 on 2007-12-04
Yeah, I still haven't fixed this problem. A real pity, because I was very happy to have Guitar Pro working.
It was definately something I did when I was trying to install my webcam.

I tried reinstalling Guitar Pro. Funnily enough, before the reinstall I couldn't see text properly above the score... now I can. Still no sound though.

I have Gutsy upgraded to Ubuntu Studio and using GP5 with the patch.

I'm not confident enough to reinstall Alsa. I don't want anything else to break.

TuxGuitar is OK, but still has some way to go to rival Guitar Pro. Also it can't play a lot of my Guitar Pro tracks.

Plz let me know if you have any luck with fixing it.

---


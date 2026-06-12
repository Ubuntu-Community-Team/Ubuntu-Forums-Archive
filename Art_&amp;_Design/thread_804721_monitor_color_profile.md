---
title: "monitor color profile"
date: 2008-05-23
forum: Art &amp; Design
---

### Post by breek on 2008-05-23
recently i'm trying to use monitor color profiles in graphic applications but it seems that only gimp (2.4.5) and rawtherapee (2.4m1) apply them.
inkscape 0.46, gqview 2.1.5, and digikam 0.9.3 simply ignore them if suggest to use the system one (loaded via xicc or xcalib) or even if i specify the single color profile in the app.
eog should use the system one but it doesn't.
lcms is installed and the icm file is not broken since i've tried to use other ones without succes.
some people says that xnview and faststone (via wine) can use monitor color profile but they only load the ones attached in the images.

ideas? suggestions?
thanx in advance ;)

ps: xubuntu 8.04 and nvidia driver

---

### Post by breek on 2008-06-13
i forgot to say that i solved this problem :P

gqview
edit */home/user/.gqview/gqviewrc* and set
*color_profile_use_image: true*
and
*color_profile_screen_type: 1*

inkscape
edit */home/user/.inkscape/preferences.xml* and set
[i]<group
id="displayprofile"
enable="1"[/i]


so i have rawtherapee, gimp, gqview and inkscape... all using the same profile... good enough for me! ;)

---

### Post by sstalpers on 2009-06-28
I am having the same problem in Digikam 0.9.4 running in Intrepid. When changing the monitor profile, there is no change in the way that photos are displayed. Gimp works correctly with my monitor profile.

I tried editing ~/.kde/share/config/digikamrc to make sure that Digikam is using my monitor profile. Here are my settings:
```
[Color Management]
BPCAlgorithm=false
BehaviourICC=false
CMInRawLoading=true
DefaultPath[$e]=/usr/share/apps/digikam/profiles/
EnableCM=true
InProfile=0
InProfileFile[$e]=
ManagedView=true
MonitorProfile=1
MonitorProfileFile[$e]=/usr/share/apps/digikam/profiles/Scott_Contr85Bri0r181g203b185.icc
ProofProfile=0
ProofProfileFile[$e]=./Fuji_Frontier-sRGB_CA-Type-II_V2.icc
RenderingIntent=0
WorkProfileFile[$e]=/usr/share/apps/digikam/profiles/sRGB.icm
WorkSpaceProfile=2
```
Can anyone confirm that monitor profiling works in Digikam? Any help is much appreciated! 

p.s. The problem might be related to [this bug]("http://bugs.kde.org/show_bug.cgi?id=163161"). I can't be sure which profile digikam is using. I eventually managed to make sure that both the preferences dialogue box and the configuration file point to my monitor's profile. But the 'info' button in the dialogue box displays the sRGB profile and not my monitor's profile.

---


---
title: "Issues with installing Medal of Honor: Allied Assult (Linux Native) on Linux Lite"
date: 2014-08-22
forum: Any Other OS
---

### Post by cobradabest on 2014-08-22
I'm trying to install the Linux version of Medal of Honor Allied Assault on Linux lite x64 (Xubuntu Derivative), because the Windows version doesn't work on my wine and it runs pretty slowly on Wibndows 7 on the same machine.

I'm having issues with it, however.

I found [this tutorial]("http://www.nufclan.net/index.php?topic=1298.0") on how to install MOHAA on Ubuntu 10.4LTS, which seems fairly modern to me and I figured since Linux Lite is based on Ubuntu, I'd give it a show, and I followed through it without issues except for testing it in the end. When I tried to run it in the terminal, I got this error:
```
./mohaa_lnx: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```
I installed libstdc++5, as I was told that would fix it, but I still got the same error.

Then I remembered that the UK and US versions of the game differ a little, at least when it comes to installation, so I figured maybe the archive linked in the tutorial was for the US version. Though I'm not 100% sure it would really matter.

I downloaded a UK installer from [here]("http://www.liflg.org/?catid=6&gameid=8"), but when I try to run it, I get this error:
```
*Program Directory*/.setup2847: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
I look this error up and it usually occurs when trying to run an old 32-bit program on a 64-bit OS, and that ubuntu dropped support for this library some time ago, but before I had to reinstall Linux Lite due to an error that stopped it from booting, I had a program that uses the exact same library (ePSXe), and I got that working, albiet with sound issues, so I know it's possible to get this issue fixed on modern Linux OSes.

So what can I do/try to get either method working?

---

### Post by Dreamer Fithp Apprentice on 2014-08-22
> **cobradabest said:**
> I'm trying to install the Linux version of Medal of Honor Allied Assault on Linux lite x64 (Xubuntu Derivative), because the Windows version doesn't work on my wine and it runs pretty slowly on Wibndows 7 on the same machine.If it runs poorly on W7, unless there is something wrong on the Windows set up, it probably won't do much better in linux. And under Wine it will probably be awful.

> **cobradabest said:**
> I'm trying to install the Linux version of  Medal of Honor Allied Assault on Linux lite x64 (Xubuntu Derivative),  because the Windows version doesn't work on my wine . . . I found [this tutorial]("http://www.nufclan.net/index.php?topic=1298.0")  on how to install MOHAA on Ubuntu . . . That link doesn't seem  to be discussing installing a "linux version" but rather installing the  Windows version under Wine. Which you say doesn't work. Am I missing  something here?

> **cobradabest said:**
>  . . . how to install MOHAA on Ubuntu  10.4LTS, which seems fairly modern to me and I figured since Linux Lite  is based on Ubuntu . . . based on Ubuntu 14.04, which is 4 years  newer than 10.04. I wouldn't say 10.04 isn't "modern" but there is  still a heap of difference. For one thing, if you install with apt-get  (and I presume Synaptic), 32 bit compatibility is SUPPOSED to be  automatic now. I may be wrong but I don't think that's true if you  install from a .deb file. 
==================================
          - the 32 vs. 64 bit issue -
So  it probably won't do any good to address 32 bit compatibility, but if  you want to try, I can't see that it would hurt. In that light, I looked  at the distro's home page and it says it's based on 14.04. I  assume that means it uses the Ubuntu repositories. If that's accurate, I  think this would be worth a try:```
sudo apt-get install lib32z1  lib32ncurses5 lib32bz2-1.0
```Then try installing again.

I got  that by first putting "32 bit compatibility ubuntu" (with no " marks)  in the startpage.com search engine. From the result I got this page:
[http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system](http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system).  I confirmed that```
sudo apt-get install ia32-libs
```still gets  the same error message it did when the post beginning "According to the  error message that I got . . ." was made.

There are more links on  that page if you want to pursue that angle, but my understanding is  that all that stuff is SUPPOSED to be automatic now if you use apt-get  or a GUI front end for apt-get to install a program. I'm not sure that's  true if you use other installation methods.
=========================
    - on Wine -
Wine is hellaciously complicated. Just because it doesn't work the first go round doesn't mean it can't be made to work. It's got a bunch of settings that can be tailored differently for each application you want to run under it. If you spend enough time at it, especially if you use a search engine like startpage.com to read about what other people have done to get a program to run under Wine, and fiddle with a lot, trying different things, a lot of programs that don't run off the bat can be made to work. But I doubt it will work as well as it did under Windows, let alone work better.
========================
                      - VMs -
Running a Windows program in a VM running Windows will almost allways work, unless the machine just doesn't have sufficient resources. Much more dependable than Wine, but if you get Wine to work, Wine is likely to be faster. But just as with Wine, I doubt the program will work as well as it did under Windows on bare metal, let alone work better.
=====================
      - another, somewhat exotic,  VM approach -
There is one more way: Use a VM, but instead of useing a virtual hard drive, set it up to use the bare metal Windows partition.  This is likely to work almost as well as running the program under Windows, unless resources are real tight, but no better, so the only advantage would be not having to reboot. And this is quite complicated to set up because the Windows code that tries to stop OS-piracy doesn't distinguish properly between a VM accessing the windows partition (which does NOT violate the liscense unless they've changed it since I read about it.  ) and a second installation made with the same installation CD (which does). Don't expect MS tech support people to understand this. The people at MS  with brains are busy writing code, not manning phone lines. 
=====================
All things considered, you're probably better off running this under Windows since you're dual booting anyway apparently, and try to figure out ways to make it run better in that environment. Heresy, I know, but that's the way I see it.

---

### Post by cobradabest on 2014-08-22
> **Dreamer Fithp Apprentice said:**
> If it runs poorly on W7, unless there is something wrong on the Windows set up, it probably won't do much better in linux. And under Wine it will probably be awful.
Alright, I maybe over exaggerated, it runs okay, but I immagine it would run smoother under Linux, since Linux itself is more lightweight, and there's a massive difference in operformace compared to windows on the same machine.

> **Dreamer Fithp Apprentice said:**
> That link doesn't seem  to be discussing installing a "linux version" but rather installing the  Windows version under Wine. Which you say doesn't work. Am I missing  something here?
You are, it later mentions downloading a linux client, and placing the  contents of it in the game's directory after installing the windows version under wine...

> **Dreamer Fithp Apprentice said:**
> based on Ubuntu 14.04, which is 4 years  newer than 10.04. I wouldn't say 10.04 isn't "modern" but there is  still a heap of difference. For one thing, if you install with apt-get  (and I presume Synaptic), 32 bit compatibility is SUPPOSED to be  automatic now. I may be wrong but I don't think that's true if you  install from a .deb file. 
==================================
          - the 32 vs. 64 bit issue -
So  it probably won't do any good to address 32 bit compatibility, but if  you want to try, I can't see that it would hurt. In that light, I looked  at the distro's home page and it says it's based on 14.04. I  assume that means it uses the Ubuntu repositories. If that's accurate, I  think this would be worth a try:```
sudo apt-get install lib32z1  lib32ncurses5 lib32bz2-1.0
```Then try installing again.
Okay, I tried that, but got the same results. Another forum suggested I make a blank libgtk-1.2.so.0 in a libs directory, and it came up with the error saying it's "too short", so the libraries I've been trying to install haven't been installing the one file it's looking for...
```
*setup directory*/.setup30558: error while loading shared libraries: /usr/lib/libgtk-1.2.so.0: file too short
```
Is there anyway I can download that file and replace it and see if that works?

> **Dreamer Fithp Apprentice said:**
> I got  that by first putting "32 bit compatibility ubuntu" (with no " marks)  in the startpage.com search engine. From the result I got this page:
[http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system](http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system).  I confirmed that```
sudo apt-get install ia32-libs
```still gets  the same error message it did when the post beginning "According to the  error message that I got . . ." was made.

There are more links on  that page if you want to pursue that angle, but my understanding is  that all that stuff is SUPPOSED to be automatic now if you use apt-get  or a GUI front end for apt-get to install a program. I'm not sure that's  true if you use other installation methods.
I'll have a look around, thanks.

EDIT: I figured out how to install libraries in 32-bit mode, it seems you simple type ":i386" at the end, I tried it with "libstdc++5", and it installed, and it got me a step further with the archived mohaa binaries, I'm getting some other errors, though, here's what came out of the terminal:
```
--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/cobradabest/.mohaa/main
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/pak7.pk3 (89 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak6EnUk.pk3 (395 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/pak6.pk3 (104 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak5.pk3 (259 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak4.pk3 (593 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak3.pk3 (669 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak2.pk3 (4722 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak1.pk3 (396 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak0.pk3 (11174 files)

----------------------
18401 files in pk3 files
execing default.cfg
execing menu.cfg
execing newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem
```

How do I fix it?

I also tried doing the same thing for the installer, but I got the same errors as before, it seems the libgtk libraries were taken off of the ubuntu servers or something... How would I get the installer working now?

---

### Post by cobradabest on 2014-08-23
Nevermind, I fixed the problem, I typed in:
```
./mohaa_lnx +set r_gldriver libGL.so.1
```
and it works perfectly! The only problem is that there's no sound, but I heard sound issues were common with the game, but is there anything I can do to help fix it?

EDIT: It seems that OpenAL is the issue, it can't load it up, it might be missing or not working.

```
OpenAL: Opening device {default}...
open /dev/[sound/]dsp: No such file or directory
OpenAL: Could not open device
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: initialization failed. No audio will play.
```

I installed OpenAL on my system, but it didn'thelp, is there a code I can use similar to the one above but with OpenAL?

---

### Post by Dreamer Fithp Apprentice on 2014-08-28
> **cobradabest said:**
> You are, it later mentions downloading a linux client, and placing the  contents of it in the game's directory after installing the windows version under wine...I see. I read it some more. Interesting. A sort of hybrid installation. I've never seen that done before. Cool. Rube Goldbery would be proud. ;)> **cobradabest said:**
> Another forum suggested I make a blank  libgtk-1.2.so.0 in a libs directory, and it came up with the error  saying it's "too short", so the libraries I've been trying to install  haven't been installing the one file it's looking for...
```
*setup directory*/.setup30558: error while loading shared libraries: /usr/lib/libgtk-1.2.so.0: file too short
```
Is there anyway I can download that file and replace it and see if that  works?Maybe. I doubt it would hurt to try. The trick may be in  finding it. Looks like it hasn't been in Ubuntu since Jaunty. I thought  it'd be easy to find but I just tried for 10 minutes or so and it isn't.  If you don't fix the sound problem and want to come back and try this  approach, I'm sure it CAN be had. If nothing else, I'm sure there are  people out there who still have working Jaunty installations. Maybe  someone could just make you a copy of the binary. Somebody probably has  it in an archive somewhere, which a more determined search might find.  Totally in over my head here, as I've only compiled aps a couple of  times and I'm not even sure if libraries ARE compiled, but I'd assume  the ideal thing would be to get the source code and compile it, since  the environment has changed a bit since this library became extinct.
> **cobradabest said:**
> The only problem is that there's no sound,  but I heard sound issues were common with the game, but is there  anything I can do to help fix it?

EDIT: It seems that OpenAL is the issue, it can't load it up, it might be missing or not working.

```
OpenAL: Opening device {default}...
open /dev/[sound/]dsp: No such file or directory
OpenAL: Could not open device
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: initialization failed. No audio will play.
```

I installed OpenAL on my system, but it didn'thelp, is there a code I  can use similar to the one above but with OpenAL?Sounds like you  almost have it licked.

I put part of that error message in startpage search and came up with a  bunch of links. You might want to try that. I didn't study any of them  really, but this one looks like it might be relevant:
[http://www.ogre3d.org/addonforums/viewtopic.php?f=10&t=11540](http://www.ogre3d.org/addonforums/viewtopic.php?f=10&t=11540)

If you don't find something pretty quickly that way, I'd suggest starting a new thread with a title like:
"OpenAL: Could not open device" - no sound
That might be more likely to catch the eye of someone who might know what to do about it.

---

### Post by cobradabest on 2014-08-29
I managed to fix the problem, sort of, I installed osspd, and I'm now getting sound, although some sound effects are missing, but I hear that was a fault with the Linux port, so I suppose there's not much I can do. Here's the terminal output anyway:
```
--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/cobradabest/.mohaa/main
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/pak7.pk3 (89 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak6EnUk.pk3 (395 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/pak6.pk3 (104 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak5.pk3 (259 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak4.pk3 (593 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak3.pk3 (669 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak2.pk3 (4722 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak1.pk3 (396 files)
/home/cobradabest/.wine/drive_c/Program Files (x86)/EA GAMES/MOHAA/main/Pak0.pk3 (11174 files)

----------------------
18401 files in pk3 files
execing default.cfg
execing menu.cfg
execing newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
execing configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so.1: Initializing SDL OpenGL display
...setting mode 6: 1024 768
Attempting 4/4/4 Color bits, 24 depth, 0 stencil display...
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
STUB: missing hardware detection in unix/linux_glimp_sdl.c line 985.
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array

GL_VENDOR: X.Org
GL_RENDERER: Gallium 0.4 on AMD PALM
GL_VERSION: 3.0 Mesa 10.1.3
GL_EXTENSIONS: [...omitted...]
GL_MAX_TEXTURE_SIZE: 16384
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: gl_linear_mipmap_linear
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
Initializing Shaders
Setting up Shaders
----- finished R_Init -----
------- profiling DrawBackground methods -------
glDrawPixels w/ BGR: 0 clocks
glDrawPixels w/ RGB: 0 clocks
glTexSubImage2D w/ BGR: 0 clocks
glTexSubImage2D w/ RGB: 0 clocks
DrawBackground: using glDrawPixels with BGR data
-------------------------------
Opening IP socket: localhost:12203
Hostname: cobradabest-Satellite-C660D
IP: 127.0.1.1
------- Sound Initialization (full) -------
OpenAL: Opening device {default}...
OpenAL: Device opened successfully.
OpenAL: Creating AL context...
OpenAL: Context created successfully.
AL_VENDOR: J. Valenzuela
AL_VERSION: 0.0.7
AL_RENDERER: Software
AL_EXTENSIONS:  AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format  AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback  ALC_LOKI_audio_channel 
AL extension: Looking up required symbol "alutLoadMP3_LOKI"......found.
AL extension: Looking up symbol "alReverbScale_LOKI"......found.
AL extension: Looking up symbol "alReverbDelay_LOKI"......found.
Loading global/sound0.txt
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 22050
----------------------
------- Sound Initialization Complete ------- 233 ms
Setting up Shaders
Loading inventory...
----- Client Initialization Complete ----- 3058 ms
--- Common Initialization Complete --- 3990 ms
--- Localization: I see 0 localization files
--- Localization: reading file global/localization.txt
Loading Localization File global/localization.txt
Loaded 1242 localization entries
------- Sound Initialization (full) -------
Cmd_AddCommand: play already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
Cmd_AddCommand: sounddump already defined
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 22050
----------------------
------- Sound Initialization Complete ------- 1 ms
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
FIXME: Allow reverb toggle at runtime in OpenAL code.
You are now setup for hard mode.
------ Server Initialization ------
Server: briefing/briefing1
Called FadeSound with: 0.000000
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
Setting up Shaders
UI_DrawConnect called
------ Unloading fgame.so ------
------- Attempting to load ./fgame.so -------
^~^~^ Add the following line to the *_precache.scr map script:
cache models/player/american_army.tik
------ Server Initialization Complete ------  1.67 seconds
Called FadeSound with: 0.000000
------- Sound Begin Registration -------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Begin Registration Complete -------
------- Attempting to load ./cgame.so -------


-----------PARSING UBERSOUND------------
Any  SetCurrentTiki errors means that tiki wasn't prefetched and  tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore  if you don't use that tiki on this level.
Parse/Load time: 0.087000 seconds.
-------------UBERSOUND DONE---------------



-----------PARSING UBERDIALOG------------
Any  SetCurrentTiki errors means that tiki wasn't prefetched and  tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore  if you don't use that tiki on this level.
Parse/Load time: 0.164000 seconds.
-------------UBERDIALOG DONE---------------

stitched 0 LoD cracks
...loaded 6 faces, 0 meshes, 0 trisurfs, 0 flares
R_LevelMarksLoad: maps/briefing/briefing1.dcl not found
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_paper_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_paper_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_wood_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_wood_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_metal_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_metal_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_stone_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_stone_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_dirt_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_dirt_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_grass_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_grass_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_mud_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_mud_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_water_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_water_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_glass_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_glass_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_sand_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_sand_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_foliage_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_foliage_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_snow_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_snow_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_carpet_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_carpet_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_human_uniform_lite.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bh_human_uniform_hard.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_trail_bubble.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_base.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/bazookaexp_base.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_paper.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_wood.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_metal.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_stone.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_dirt.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_grass.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_mud.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_water.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_gravel.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_sand.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_foliage.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_snow.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/grenexp_carpet.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_ripple_still.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/water_ripple_moving.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_big.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_medium.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_small.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_oil_leak_splat.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_big.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_medium.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_small.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/barrel_water_leak_splat.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_light_dust.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_heavy_dust.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_dirt.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_grass.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_mud.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_puddle.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_sand.tik
^~^~^ Add the following line to the *_precache.scr map script:
cache models/fx/fs_snow.tik
------- Sound End Registration -------
------- Sound End Registration Complete -------
CL_EndRegistration:  0.01 seconds
CL_InitCGame:  1.05 seconds
Saving to briefing_briefing10014 (autosave)...
Game Saved
Done.
Called FadeSound with: 0.000000

ERROR PlaySound: snd_step_metal needs an alias in ubersound.scr or uberdialog.scr - Please fix.

ERROR PlaySound: snd_step_equipment needs an alias in ubersound.scr or uberdialog.scr - Please fix.
^~^~^ Add the following line to the *_precache.scr map script:
cache models/player/american_army_fps.tik

ERROR PlaySound: snd_landing_metal needs an alias in ubersound.scr or uberdialog.scr - Please fix.
------ Server Initialization ------
Server: m1l1
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
Setting up Shaders
UI_DrawConnect called
------ Unloading fgame.so ------
------- Attempting to load ./fgame.so -------
------ Server Initialization Complete ------  6.41 seconds
Called FadeSound with: 0.000000
------- Sound Begin Registration -------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Begin Registration Complete -------
------- Attempting to load ./cgame.so -------


-----------PARSING UBERSOUND------------
Any  SetCurrentTiki errors means that tiki wasn't prefetched and  tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore  if you don't use that tiki on this level.
Parse/Load time: 2.240000 seconds.
-------------UBERSOUND DONE---------------



-----------PARSING UBERDIALOG------------
Any  SetCurrentTiki errors means that tiki wasn't prefetched and  tiki-specific sounds for it won't work. To fix prefetch the tiki. Ignore  if you don't use that tiki on this level.
Parse/Load time: 1.112000 seconds.
-------------UBERDIALOG DONE---------------

stitched 446 LoD cracks
...loaded 3655 faces, 615 meshes, 0 trisurfs, 0 flares
Cmd_AddCommand: ter_restart already defined
R_LevelMarksLoad: maps/m1l1.dcl not found
------- Sound End Registration -------
------- Sound End Registration Complete -------
CL_EndRegistration:  0.05 seconds
CL_InitCGame:  9.33 seconds
Saving to m1l10018 (autosave)...
Game Saved
Done.
Called FadeSound with: 0.000000
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_loop_block in client/snd_openal_new.cpp line 3930.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
Loading game...m1l10017
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------ Server Initialization ------
Server: m1l1
Called FadeSound with: 0.000000
Game Loaded
------ Server Initialization Complete ------  0.10 seconds
------- S_StopAllSounds (don't stop music) -------
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
------- S_StopAllSounds (don't stop music) -------
------- S_StopAllSounds Complete-------
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
Called FadeSound with: 0.000000
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_loop_block in client/snd_openal_new.cpp line 3930.
Press the OBJECTIVE key  ( Tab ) to see your objectives.
FIXME: Allow different speaker types in OpenAL code.
s_khz will be changed upon restarting.
STUB: sound stuff in client/cl_main.c line 1554.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
STUB: sample_offset in client/snd_openal_new.cpp line 3803.
------- Sound Shutdown (partial) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: Destroying context...
OpenAL: Context destroyed successfully.
OpenAL: Closing device...
OpenAL: Device closed successfully.
------- Sound Shutdown Complete -------
------- Sound Initialization (partial) -------
Cmd_AddCommand: sounddump already defined
OpenAL: Opening device {default}...
OpenAL: Device opened successfully.
OpenAL: Creating AL context...
OpenAL: Context created successfully.
AL_VENDOR: J. Valenzuela
AL_VERSION: 0.0.7
AL_RENDERER: Software
AL_EXTENSIONS:  AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format  AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback  ALC_LOKI_audio_channel 
AL extension: Looking up required symbol "alutLoadMP3_LOKI"......found.
AL extension: Looking up symbol "alReverbScale_LOKI"......found.
AL extension: Looking up symbol "alReverbDelay_LOKI"......found.
Loading global/sound0.txt
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 44100
----------------------
------- Sound Initialization Complete ------- 463 ms
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
STUB: sample_loop_block in client/snd_openal_new.cpp line 3930.
Use your compass to guide you to your next objective.
Recovered 100 Health
Got 5 Grenade Rounds
Press the USE key  ( e ) to grab items off tables.
Got 16 Pistol Rounds
Picked Up MP40
Got 32 Smg Rounds
An objective has been completed!
An objective has been completed!
Use your compass to guide you to your next objective.
----- Server Shutdown -----
------ Unloading fgame.so ------
---------------------------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- CL_Shutdown -----
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Shutdown (full) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: Destroying context...
mutex 0xa128998 busy
mohaa_lnx: mutex/posixmutex.c:38: Assertion `0' failed.
----- CL_Shutdown -----
recursive shutdown
```

There anythijng I can do to get the installer working? It works great the way it is, minus the sound, but If I used the installer, I can create a desktop shortcut, and maybe because the versions would match, the sound issue may be fixed.

---

### Post by Dreamer Fithp Apprentice on 2014-09-24
> **cobradabest said:**
> There anythijng I can do to get the installer working?Damfino. Your persistence is impressive. All I can suggest is running the installer in a terminal and searching the net for every error message you get. Or run it in a Windows VM. That should work (assuming the Windows version works) but might take some hardware upgrades to work with acceptable speed.

---


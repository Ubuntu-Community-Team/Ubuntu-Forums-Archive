---
title: "Feisty and TiBook G4"
date: 2007-04-17
forum: Apple PPC Users
---

### Post by stmiller on 2007-04-17
Okay I've just installed Feisty beta on my 15" TiBook. It's a G4 867Mhz model. Overall everything is great right out of the box. 
Here are a few comments for any other TiBook owners out there:

- Had to install with the alternate CD; gnome would not load after the live cd booted for some reason. 
**EDIT**: You have to open a terminal and type 
```
killall esd
```
to get gnome to load. Then uncheck 'ESD' under Gnome's sound prefs. (Thanks ssam)

- Feisty failed to load the sound modules at boot after install. The fix is to add these two things to your /etc/modules:
snd-powermac
snd-seq

And now sound will work (for Aluminum Powerbook models). For Tibook owners- there is a horrible [BUG]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/"). 
 
- Connecting WPA is not an option under the network manager. Only WEP or open access points. WPA should be possible with this card (original Airport). I'm going to try to investigate more.

- Xorg is setup automagically and works! Did not have to edit the xorg.conf file to specify a resolution, or anything.

- General hardware support such as CPU throttling works out of the box. (My model throttles from 667 to 867Mhz)

- Suspend to ram works.

more to come...

Install the program hwinfo (apt-get install hwinfo) to give lots of info about your machine.

---

### Post by ssam on 2007-04-18
i am on a ti powerbook 1Ghz 15", which i think is almost identical to yours.

to get gnome to start i had drop to a terminal and do
```
killall esd
```

i seems that any sound i play freezes that process (eg the startup sound freezes the start up).

i had not made and progress with getting sound to work so have had to disable it. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

could you post the output of these commands

```

uname -a
lsmod
cat /proc/cpuinfo

```

thanks

---

### Post by anders_gud on 2007-04-18
> **stmiller said:**
> 
- Feisty failed to load the sound modules at boot after install. The fix is to add these two things to you /etc/modules:
snd-powermac
snd-seq

And now sound will work.


Interesting...
I'm on a Tibook 1 Ghz and cannot get sound to work with kernel 2.6.20 on Feisty, even tried the latest alsa-drivers and libasound (1.0.14rc3) from alsa-project.org. No luck...
Please post your specs

---

### Post by stmiller on 2007-04-18
Grrr. After doing some Feisty updates, Gnome does not load. I've installed Xfce for the moment.

I had to open alsamixer in the terminal and hit 'M' to unmute the master to get sound. Sound works in audacity but having problems with VLC. I'll have to try a few things.

```

stmiller@mahler:~$ uname -a
Linux mahler 2.6.20-15-powerpc #3 Sun Apr 15 06:45:49 UTC 2007 ppc GNU/Linux

```


```
stmiller@mahler:~$ cat /proc/cpuinfo 
processor       : 0
cpu             : 7455, altivec supported
clock           : 667.000000MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 66.56
timebase        : 33330863
platform        : PowerMac
machine         : PowerBook3,5
motherboard     : PowerBook3,5 MacRISC2 MacRISC Power Macintosh
detected as     : 80 (PowerBook Titanium IV)
pmac flags      : 0000001b
L2 cache        : 256K unified
pmac-generation : NewWorld
stmiller@mahler:~$ 
```

```
stmiller@mahler:~$ lsmod
Module                  Size  Used by
af_packet              24936  2 
binfmt_misc            13672  1 
rfcomm                 46076  0 
l2cap                  25988  5 rfcomm
bluetooth              65388  4 rfcomm,l2cap
uinput                 11264  2 
ppdev                  11268  0 
lp                     13580  0 
parport                44304  2 ppdev,lp
radeon                144776  2 
drm                    96920  3 radeon
cpufreq_ondemand        9160  0 
cpufreq_stats           6436  0 
cpufreq_userspace       5332  1 
cpufreq_conservative     8096  0 
cpufreq_powersave       2048  0 
snd_powermac           49984  0 
sbp2                   25188  0 
scsi_mod              181324  1 sbp2
apm_emu                 8012  1 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  2 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  11 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus
pmac_zilog             21140  0 
serial_core            24384  1 pmac_zilog
airport                 7104  0 
orinoco                44948  1 airport
hermes                  8352  2 airport,orinoco
pcmcia                 46544  0 
yenta_socket           31660  1 
rsrc_nonstatic         13920  1 yenta_socket
pcmcia_core            49240  3 pcmcia,yenta_socket,rsrc_nonstatic
uninorth_agp           12012  1 
agpgart                41308  2 drm,uninorth_agp
tsdev                   9056  0 
evdev                  12800  16 
ext3                  159048  1 
jbd                    68488  1 ext3
mbcache                 9572  1 ext3
ide_cd                 36900  0 
cdrom                  47580  1 ide_cd
ide_disk               18880  3 
sungem                 35460  0 
sungem_phy             12128  1 sungem
ohci1394               43152  0 
ieee1394              430800  2 sbp2,ohci1394
ohci_hcd               36100  0 
usbcore               158260  2 ohci_hcd
capability              5256  0 
commoncap               7968  1 capability
stmiller@mahler:~$ 
```


```
stmiller@mahler:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
stmiller@mahler:~$ 


```

```
stmiller@mahler:~$ glxgears 
18611 frames in 5.0 seconds = 3722.097 FPS
18528 frames in 5.0 seconds = 3705.438 FPS
18528 frames in 5.0 seconds = 3705.493 FPS

```

---

### Post by anders_gud on 2007-04-19
> **stmiller said:**
> 
```
stmiller@mahler:~$ glxgears 
18611 frames in 5.0 seconds = 3722.097 FPS
18528 frames in 5.0 seconds = 3705.438 FPS
18528 frames in 5.0 seconds = 3705.493 FPS

```

Wow!
I get 6676 frames in 5.0 seconds = 1335.179 FPS 
Can i see your xorg.conf please...

This audio issue is driving me nuts... Can it be a module conflict? (I had problems with sound when plugging in a usb-bluetooth device in dapper and edgy.) 
ssam, did you do a clean install or a dist-upgrade?

my lsmod:
```

Module                  Size  Used by
af_packet              24936  4 
binfmt_misc            13672  1 
rfcomm                 46076  3 
l2cap                  25988  5 rfcomm
bluetooth              65388  4 rfcomm,l2cap
ipv6                  307500  14 
autofs4                24548  0 
radeon                144776  2 
drm                    96920  3 radeon
ppdev                  11268  0 
lp                     13580  0 
parport                44304  2 ppdev,lp
cpufreq_userspace       5332  1 
cpufreq_stats           6436  0 
cpufreq_powersave       2048  0 
cpufreq_ondemand        9160  0 
cpufreq_conservative     8096  0 
sr_mod                 18916  0 
snd_powermac           49984  3 
sbp2                   25188  0 
scsi_mod              181324  2 sr_mod,sbp2
apm_emu                 8012  1 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  4 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  3 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
airport                 7104  0 
pcmcia                 46544  0 
orinoco                44948  1 airport
snd                    69812  14 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus
hermes                  8352  2 airport,orinoco
pmac_zilog             21140  0 
serial_core            24384  1 pmac_zilog
yenta_socket           31660  1 
rsrc_nonstatic         13920  1 yenta_socket
pcmcia_core            49240  3 pcmcia,yenta_socket,rsrc_nonstatic
uninorth_agp           12012  1 
agpgart                41308  2 drm,uninorth_agp
tsdev                   9056  0 
evdev                  12800  10 
ext3                  159048  2 
jbd                    68488  1 ext3
mbcache                 9572  1 ext3
usbhid                 28996  0 
hid                    43968  1 usbhid
ide_cd                 36900  0 
cdrom                  47580  2 sr_mod,ide_cd
ide_disk               18880  3 
ohci1394               43152  0 
ieee1394              430800  2 sbp2,ohci1394
sungem                 35460  0 
sungem_phy             12128  1 sungem
ohci_hcd               36100  0 
usbcore               158260  3 usbhid,ohci_hcd
raid10                 26624  0 
raid456               126992  0 
xor                     9736  1 raid456
raid1                  27168  0 
raid0                   8832  0 
multipath              10368  0 
linear                  6624  0 
md_mod                 95732  7 raid10,raid456,raid1,raid0,multipath,linear
dm_mod                 67468  15 
capability              5256  0 
commoncap               7968  1 capability

```

---

### Post by stmiller on 2007-04-19
I put my xorg.conf here:
[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

I have compiz working great, just from starting the beryl manager thing.

I always run glxgears then put the terminal window completely on top of the gears. So yes- sort of cheating I suppose. :) But that's the way I've read others run that for a benchmark.

And the gnome-network-monitor applet does not let you choose WPA as an option, though it should work with this chip. I've installed the knetworkmanager which allows the choice of WPA. I'm trying a few things with this and my access point to get WPA going.

Investigating sound. My sound is spotty at best when it plays back. Only oss programs like Audacity seem to get a 'peep' but then they lock up. I get errors in vlc like

```
stmiller@mahler:~$ vlc
VLC media player 0.8.6 Janus
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
[00000351] alsa audio output error: write failed (Input/output error)
```

---

### Post by anders_gud on 2007-04-19
> **stmiller said:**
> I put my xorg.conf here:
[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

Thanks!

> **stmiller said:**
> 
I always run glxgears then put the terminal window completely on top of the gears. So yes- sort of cheating I suppose. :) But that's the way I've read others run that for a benchmark.

Cheating did the trick:lolflag: 
21697 frames in 5.0 seconds = 4339.283 FPS

> **stmiller said:**
> 
And the gnome-network-monitor applet does not let you choose WPA as an option, though it should work with this chip. I've installed the knetworkmanager which allows the choice of WPA. I'm trying a few things with this and my access point to get WPA going.


Try [wicd]("http://compwiz18.blackhole.cx/wicd/wb/"). (Rather than network-manager)

> **stmiller said:**
> 
Investigating sound. My sound is spotty at best when it plays back. Only oss programs like Audacity seem to get a 'peep' but then they lock up. 

But you do get coherent sound with ALSA apps?
Try aplay /path/to/somefile...

---

### Post by ssam on 2007-04-20
i have tried clean installs and upgrades. i have tried putting those bits into /etc/modules. i have tired blacklisting all the aoa (apple on board audio) stuff.

i dont mind being with out sound to much (my music is on another computer, network jukebox type thing). i'll try building a 2.6.21 kernel when that comes out.

---

### Post by stmiller on 2007-04-21
Okay. Installed a the program hwinfo (apt-get install hwinfo). This gave lots of info.

Seems that the current tibook airport driver shipping with ubuntu only supports WEP, and not wpa. I will see what it takes to build the driver from source, perhaps and see if I can get WPA to work.

And for sound: I cannot figure out what is going on. There is another module, snd-aoa, but that is for newer powerbooks and powermacs. Not this old TiBook. So snd-powermac IS the correct driver for this. I tried snd-aoa for the heck of it, and that didn't work.

Then,
I fetched the latest alsa sources and compiled a new snd-powermac driver. I tried that driver, but still same issues. Plays back choppy for 1 second, then sound drops out/fails.

This is so odd, as there are no error messages in any logs, and the snd-powermac driver loads fully without problems. It is recognized in every app. Very strange.

---

### Post by stmiller on 2007-04-22
[http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml](http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml)

This gentoo pages explains that the powermac dmasound support should be disabled in the kernel, or it will conflict with the alsa driver (snd-powermac). I noticed in the stock ubuntu kernel 2.6.20-15 the pmac dmasound modules IS installed/enabled, as a module. 

So I don't know if that is making the conflict, or what. I think I will just configure my own kernel from kernel.org with the gentoo guide for ppc and see how that goes.

---

### Post by Gredo on 2007-04-22
> **stmiller said:**
> I put my xorg.conf here:
[http://ubuntuforums.org/showthread.php?p=2483422#post2483422](http://ubuntuforums.org/showthread.php?p=2483422#post2483422)

I have compiz working great, just from starting the beryl manager thing.

[/CODE]I have the exact same PowerBook and I can't get any desktop effects to work.  I have beryl-manager installed and setup to run at login.  It runs but I'm not getting the desktop effects.  I'm using your xorg.conf file and still nothing.  Any ideas on what I've done wrong?

---

### Post by stmiller on 2007-04-22
Right click on the Beryl Manager, and pick Advanced Beryl Options>Rendering Path>Copy

And for Select Window Manager> I have to pick Compiz. Selecting Beryl makes it crash and resort to the fall back window manager (Xfce in my case).

The desktop background does not take up the entire screen when using Compiz. I think it's defaulting to a narrower resolution in some setting. I haven't messed with it yet to figure out what's going on. 

--------
And update RE: sound. I fetched and compiled a kernel from kernel.org configuring sound as it says on the gentoo ppc faq page. And: the problem remains. Sound will play for maybe 1 second, then drops out. The program playing the audio then becomes unstable.

---

### Post by anders_gud on 2007-04-22
> **stmiller said:**
> 
And update RE: sound. I fetched and compiled a kernel from kernel.org configuring sound as it says on the gentoo ppc faq page. And: the problem remains. Sound will play for maybe 1 second, then drops out. The program playing the audio then becomes unstable.

2.6.21 has supposedly solved this bug. Hunting through 2.6.21[**commit logs**]("http://kernel.org/pub/linux/kernel/v2.6/testing/"), there must be a patch somewhere... They merged a lot of alsa 1.0.14rc3 stuff

---

### Post by stmiller on 2007-04-22
Excellent! Thank you for the tip. I'll try a .21 kernel snapshot later.

Btw I finally got gnome to start. I had to end an 'esd' process or command that was freezing up while gnome was loading. I then disabled ESD in the gnome sound prefs. Now gnome starts fine. (Anyone else have this problem?) 
I think it's related to the sound issue.

---

### Post by ssam on 2007-04-22
> **anders_gud said:**
> 2.6.21 has supposedly solved this bug. Hunting through 2.6.21[**commit logs**]("http://kernel.org/pub/linux/kernel/v2.6/testing/"), there must be a patch somewhere... They merged a lot of alsa 1.0.14rc3 stuff

once 2.6.21 is out i'll have a go packaging it (if it doesn't happen in the middle of my exams)

---

### Post by anders_gud on 2007-04-23
Sorry - 2.6.21-rc7 does not fix it, I was mislead by [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/comments/25"). 

Anyway - I am now running:
2.6.21-rc7
libasound2 1.0.14rc3

Identical symptoms as in stock Feisty kernel...

---

### Post by stmiller on 2007-04-24
I've subscribed to this report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/)

I spent a good hour and a half searching all the kernel.org mailing lists, and all of the alsa mailing lists. There are no mentions of this problem. Hopefully the .21 kernel will fix this, as the latest alsa will be included in that kernel. I can't imagine what is happening to make this fail.

On the gentoo ppc forums JoseJX recommends using the snd-aoa driver for this machine. He is perhaps one of the biggest ppc linux guys out there- he writes a lot of these drivers. There are big changes in the .21 kernel for alsa and macs, it seems like. Gone are the dma-sound (?) oss drivers, and seems like all focus is on the snd-aoa driver as a main driver.

Anyways, hopefully this will pan out soon.

---

### Post by anders_gud on 2007-04-25
> **stmiller said:**
> I've subscribed to this report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/)
 

Maybe we should file a [kernel bug]("http://bugzilla.kernel.org/") instead, I'm beginning to believe that the ubuntu teams are told not to work on ppc issues...   

> **stmiller said:**
> 
I spent a good hour and a half searching all the kernel.org mailing lists, and all of the alsa mailing lists. 
 

Ah - so have I...


> **stmiller said:**
> 
On the gentoo ppc forums JoseJX recommends using the snd-aoa driver for this machine. He is perhaps one of the biggest ppc linux guys out there- he writes a lot of these drivers. 

Hope you are right - but I can't get snd-aoa to recognize the built in Pmac Snapper card...
Here is a diff on the sound/ppc drivers between 2.6.17 and 2.6.20:

```
 diff -x '*.cmd' -x '*.o' -ur ppc/awacs.c ../../linux-source-2.6.20/sound/ppc/awacs.c
--- ppc/awacs.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/awacs.c	2007-04-12 19:16:28.000000000 +0200
@@ -801,11 +801,10 @@
 	chip->revision = (in_le32(&chip->awacs->codec_stat) >> 12) & 0xf;
 #ifdef PMAC_AMP_AVAIL
 	if (chip->revision == 3 && chip->has_iic && CHECK_CUDA_AMP()) {
-		struct awacs_amp *amp = kmalloc(sizeof(*amp), GFP_KERNEL);
+		struct awacs_amp *amp = kzalloc(sizeof(*amp), GFP_KERNEL);
 		if (! amp)
 			return -ENOMEM;
 		chip->mixer_data = amp;
-		memset(amp, 0, sizeof(*amp));
 		chip->mixer_free = awacs_amp_free;
 		awacs_amp_set_vol(amp, 0, 63, 63, 0); /* mute and zero vol */
 		awacs_amp_set_vol(amp, 1, 63, 63, 0);
diff -x '*.cmd' -x '*.o' -ur ppc/beep.c ../../linux-source-2.6.20/sound/ppc/beep.c
--- ppc/beep.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/beep.c	2007-04-12 19:16:28.000000000 +0200
@@ -215,15 +215,18 @@
 {
 	struct pmac_beep *beep;
 	struct input_dev *input_dev;
+	struct snd_kcontrol *beep_ctl;
 	void *dmabuf;
 	int err = -ENOMEM;
 
 	beep = kzalloc(sizeof(*beep), GFP_KERNEL);
+	if (! beep)
+		return -ENOMEM;
 	dmabuf = dma_alloc_coherent(&chip->pdev->dev, BEEP_BUFLEN * 4,
 				    &beep->addr, GFP_KERNEL);
 	input_dev = input_allocate_device();
-	if (!beep || !dmabuf || !input_dev)
-		goto fail;
+	if (! dmabuf || ! input_dev)
+		goto fail1;
 
 	/* FIXME: set more better values */
 	input_dev->name = "PowerMac Beep";
@@ -244,17 +247,24 @@
 	beep->volume = BEEP_VOLUME;
 	beep->running = 0;
 
-	err = snd_ctl_add(chip->card, snd_ctl_new1(&snd_pmac_beep_mixer, chip));
+	beep_ctl = snd_ctl_new1(&snd_pmac_beep_mixer, chip);
+	err = snd_ctl_add(chip->card, beep_ctl);
 	if (err < 0)
-		goto fail;
-
-	chip->beep = beep;
-	input_register_device(beep->dev);
-
-	return 0;
-
- fail:	input_free_device(input_dev);
-	kfree(dmabuf);
+		goto fail1;
+ 
+ 	chip->beep = beep;
+
+	err = input_register_device(beep->dev);
+	if (err)
+		goto fail2;
+ 
+ 	return 0;
+ 
+ fail2:	snd_ctl_remove(chip->card, beep_ctl);
+ fail1:	input_free_device(input_dev);
+	if (dmabuf)
+		dma_free_coherent(&chip->pdev->dev, BEEP_BUFLEN * 4,
+				  dmabuf, beep->addr);
 	kfree(beep);
 	return err;
 }
diff -x '*.cmd' -x '*.o' -ur ppc/daca.c ../../linux-source-2.6.20/sound/ppc/daca.c
--- ppc/daca.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/daca.c	2007-04-12 19:16:28.000000000 +0200
@@ -258,10 +258,9 @@
 		request_module("i2c-powermac");
 #endif /* CONFIG_KMOD */	
 
-	mix = kmalloc(sizeof(*mix), GFP_KERNEL);
+	mix = kzalloc(sizeof(*mix), GFP_KERNEL);
 	if (! mix)
 		return -ENOMEM;
-	memset(mix, 0, sizeof(*mix));
 	chip->mixer_data = mix;
 	chip->mixer_free = daca_cleanup;
 	mix->amp_on = 1; /* default on */
diff -x '*.cmd' -x '*.o' -ur ppc/Kconfig ../../linux-source-2.6.20/sound/ppc/Kconfig
--- ppc/Kconfig	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/Kconfig	2007-04-12 19:16:28.000000000 +0200
@@ -33,3 +33,25 @@
 	  option.
 
 endmenu
+
+menu "ALSA PowerPC devices"
+        depends on SND!=n && ( PPC64 || PPC32 )
+
+config SND_PS3
+	tristate "PS3 Audio support"
+	depends on SND && PS3_PS3AV
+	select SND_PCM
+	default m
+	help
+	  Say Y here to include support for audio on the PS3
+
+	  To compile this driver as a module, choose M here: the module
+	  will be called snd_ps3.
+
+config SND_PS3_DEFAULT_START_DELAY
+	int "Startup delay time in ms"
+	depends on SND_PS3
+	default "2000"
+
+endmenu
+
diff -x '*.cmd' -x '*.o' -ur ppc/keywest.c ../../linux-source-2.6.20/sound/ppc/keywest.c
--- ppc/keywest.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/keywest.c	2007-04-12 19:16:28.000000000 +0200
@@ -64,11 +64,10 @@
 	if (strncmp(i2c_device_name(adapter), "mac-io", 6))
 		return 0; /* ignored */
 
-	new_client = kmalloc(sizeof(struct i2c_client), GFP_KERNEL);
+	new_client = kzalloc(sizeof(struct i2c_client), GFP_KERNEL);
 	if (! new_client)
 		return -ENOMEM;
 
-	memset(new_client, 0, sizeof(*new_client));
 	new_client->addr = keywest_ctx->addr;
 	i2c_set_clientdata(new_client, keywest_ctx);
 	new_client->adapter = adapter;
@@ -118,6 +117,9 @@
 {
 	int err;
 	
+	if (!keywest_ctx || !keywest_ctx->client)
+		return -ENXIO;
+
 	if ((err = keywest_ctx->init_client(keywest_ctx)) < 0) {
 		snd_printk(KERN_ERR "tumbler: %i :cannot initialize the MCS\n", err);
 		return err;
diff -x '*.cmd' -x '*.o' -ur ppc/Makefile ../../linux-source-2.6.20/sound/ppc/Makefile
--- ppc/Makefile	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/Makefile	2007-04-12 19:16:28.000000000 +0200
@@ -6,4 +6,5 @@
 snd-powermac-objs := powermac.o pmac.o awacs.o burgundy.o daca.o tumbler.o keywest.o beep.o
 
 # Toplevel Module Dependency
-obj-$(CONFIG_SND_POWERMAC) += snd-powermac.o
+obj-$(CONFIG_SND_POWERMAC)	+= snd-powermac.o
+obj-$(CONFIG_SND_PS3)		+= snd_ps3.o
diff -x '*.cmd' -x '*.o' -ur ppc/pmac.c ../../linux-source-2.6.20/sound/ppc/pmac.c
--- ppc/pmac.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/pmac.c	2007-04-12 19:16:28.000000000 +0200
@@ -713,7 +713,7 @@
  * interrupt handlers
  */
 static irqreturn_t
-snd_pmac_tx_intr(int irq, void *devid, struct pt_regs *regs)
+snd_pmac_tx_intr(int irq, void *devid)
 {
 	struct snd_pmac *chip = devid;
 	snd_pmac_pcm_update(chip, &chip->playback);
@@ -722,7 +722,7 @@
 
 
 static irqreturn_t
-snd_pmac_rx_intr(int irq, void *devid, struct pt_regs *regs)
+snd_pmac_rx_intr(int irq, void *devid)
 {
 	struct snd_pmac *chip = devid;
 	snd_pmac_pcm_update(chip, &chip->capture);
@@ -731,7 +731,7 @@
 
 
 static irqreturn_t
-snd_pmac_ctrl_intr(int irq, void *devid, struct pt_regs *regs)
+snd_pmac_ctrl_intr(int irq, void *devid)
 {
 	struct snd_pmac *chip = devid;
 	int ctrl = in_le32(&chip->awacs->control);
@@ -1120,6 +1120,7 @@
 	struct snd_pmac *chip;
 	struct device_node *np;
 	int i, err;
+	unsigned int irq;
 	unsigned long ctrl_addr, txdma_addr, rxdma_addr;
 	static struct snd_device_ops ops = {
 		.dev_free =	snd_pmac_dev_free,
@@ -1153,10 +1154,6 @@
 	if (chip->is_k2) {
 		static char *rnames[] = {
 			"Sound Control", "Sound DMA" };
-		if (np->n_intrs < 3) {
-			err = -ENODEV;
-			goto __error;
-		}
 		for (i = 0; i < 2; i ++) {
 			if (of_address_to_resource(np->parent, i,
 						   &chip->rsrc[i])) {
@@ -1170,9 +1167,10 @@
 					       chip->rsrc[i].start + 1,
 					       rnames[i]) == NULL) {
 				printk(KERN_ERR "snd: can't request rsrc "
-				       " %d (%s: 0x%08lx:%08lx)\n",
-				       i, rnames[i], chip->rsrc[i].start,
-				       chip->rsrc[i].end);
+				       " %d (%s: 0x%016llx:%016llx)\n",
+				       i, rnames[i],
+				       (unsigned long long)chip->rsrc[i].start,
+				       (unsigned long long)chip->rsrc[i].end);
 				err = -ENODEV;
 				goto __error;
 			}
@@ -1184,10 +1182,6 @@
 	} else {
 		static char *rnames[] = {
 			"Sound Control", "Sound Tx DMA", "Sound Rx DMA" };
-		if (np->n_intrs < 3) {
-			err = -ENODEV;
-			goto __error;
-		}
 		for (i = 0; i < 3; i ++) {
 			if (of_address_to_resource(np, i,
 						   &chip->rsrc[i])) {
@@ -1201,9 +1195,10 @@
 					       chip->rsrc[i].start + 1,
 					       rnames[i]) == NULL) {
 				printk(KERN_ERR "snd: can't request rsrc "
-				       " %d (%s: 0x%08lx:%08lx)\n",
-				       i, rnames[i], chip->rsrc[i].start,
-				       chip->rsrc[i].end);
+				       " %d (%s: 0x%016llx:%016llx)\n",
+				       i, rnames[i],
+				       (unsigned long long)chip->rsrc[i].start,
+				       (unsigned long long)chip->rsrc[i].end);
 				err = -ENODEV;
 				goto __error;
 			}
@@ -1218,28 +1213,30 @@
 	chip->playback.dma = ioremap(txdma_addr, 0x100);
 	chip->capture.dma = ioremap(rxdma_addr, 0x100);
 	if (chip->model <= PMAC_BURGUNDY) {
-		if (request_irq(np->intrs[0].line, snd_pmac_ctrl_intr, 0,
+		irq = irq_of_parse_and_map(np, 0);
+		if (request_irq(irq, snd_pmac_ctrl_intr, 0,
 				"PMac", (void*)chip)) {
-			snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n", np->intrs[0].line);
+			snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n",
+				   irq);
 			err = -EBUSY;
 			goto __error;
 		}
-		chip->irq = np->intrs[0].line;
+		chip->irq = irq;
 	}
-	if (request_irq(np->intrs[1].line, snd_pmac_tx_intr, 0,
-			"PMac Output", (void*)chip)) {
-		snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n", np->intrs[1].line);
+	irq = irq_of_parse_and_map(np, 1);
+	if (request_irq(irq, snd_pmac_tx_intr, 0, "PMac Output", (void*)chip)){
+		snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n", irq);
 		err = -EBUSY;
 		goto __error;
 	}
-	chip->tx_irq = np->intrs[1].line;
-	if (request_irq(np->intrs[2].line, snd_pmac_rx_intr, 0,
-			"PMac Input", (void*)chip)) {
-		snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n", np->intrs[2].line);
+	chip->tx_irq = irq;
+	irq = irq_of_parse_and_map(np, 2);
+	if (request_irq(irq, snd_pmac_rx_intr, 0, "PMac Input", (void*)chip)) {
+		snd_printk(KERN_ERR "pmac: unable to grab IRQ %d\n", irq);
 		err = -EBUSY;
 		goto __error;
 	}
-	chip->rx_irq = np->intrs[2].line;
+	chip->rx_irq = irq;
 
 	snd_pmac_sound_feature(chip, 1);
 
diff -x '*.cmd' -x '*.o' -ur ppc/powermac.c ../../linux-source-2.6.20/sound/ppc/powermac.c
--- ppc/powermac.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/powermac.c	2007-04-12 19:16:28.000000000 +0200
@@ -181,21 +181,14 @@
 	if ((err = platform_driver_register(&snd_pmac_driver)) < 0)
 		return err;
 	device = platform_device_register_simple(SND_PMAC_DRIVER, -1, NULL, 0);
-	if (!IS_ERR(device)) {
-		if (platform_get_drvdata(device))
-			return 0;
-		platform_device_unregister(device);
-		err = -ENODEV;
-	} else
-		err = PTR_ERR(device);
-	platform_driver_unregister(&snd_pmac_driver);
-	return err;
+	return 0;
 
 }
 
 static void __exit alsa_card_pmac_exit(void)
 {
-	platform_device_unregister(device);
+	if (!IS_ERR(device))
+		platform_device_unregister(device);
 	platform_driver_unregister(&snd_pmac_driver);
 }
 
Binärfilerna ppc/snd-powermac.ko och ../../linux-source-2.6.20/sound/ppc/snd-powermac.ko skiljer
diff -x '*.cmd' -x '*.o' -ur ppc/snd-powermac.mod.c ../../linux-source-2.6.20/sound/ppc/snd-powermac.mod.c
--- ppc/snd-powermac.mod.c	2006-10-24 11:01:04.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/snd-powermac.mod.c	2007-04-19 16:50:11.000000000 +0200
@@ -16,89 +16,90 @@
 static const struct modversion_info ____versions[]
 __attribute_used__
 __attribute__((section("__versions"))) = {
-	{ 0x938ec8c6, "struct_module" },
+	{ 0xfb52f745, "struct_module" },
 	{ 0x3ce4ca6f, "disable_irq" },
-	{ 0x1a1a4f09, "__request_region" },
-	{ 0xadddffeb, "i2c_attach_client" },
+	{ 0x4c3af445, "__request_region" },
+	{ 0x10a7ebe2, "i2c_attach_client" },
 	{ 0xf9a482f9, "msleep" },
 	{ 0x89b301d4, "param_get_int" },
-	{ 0x9efed5af, "iomem_resource" },
-	{ 0x360f04ce, "i2c_detach_client" },
-	{ 0x9793a323, "i2c_del_driver" },
-	{ 0xb893ab41, "snd_pcm_period_elapsed" },
-	{ 0xb8cbe4b6, "ppc_md" },
-	{ 0x2a69ddd8, "platform_device_register_simple" },
-	{ 0xb13d73c9, "malloc_sizes" },
-	{ 0xf0762bfe, "i2c_smbus_write_byte_data" },
-	{ 0x7ad5eec9, "schedule_work" },
+	{ 0xdc3eaf70, "iomem_resource" },
+	{ 0x1bfc936, "irq_of_parse_and_map" },
+	{ 0x2eb412d2, "i2c_detach_client" },
+	{ 0x63b8b133, "i2c_del_driver" },
+	{ 0xb08ba7a1, "snd_pcm_period_elapsed" },
+	{ 0xc611086b, "ppc_md" },
+	{ 0x5e29d1af, "platform_device_register_simple" },
+	{ 0x3a262df3, "malloc_sizes" },
+	{ 0xe3e4781c, "i2c_smbus_write_byte_data" },
+	{ 0xc633495b, "schedule_work" },
 	{ 0x9309de94, "cuda_request" },
-	{ 0xd477cb23, "pci_device_to_OF_node" },
+	{ 0x7b0fdc3f, "pci_device_to_OF_node" },
 	{ 0x98bd6f46, "param_set_int" },
 	{ 0x1d26aa98, "sprintf" },
-	{ 0xd3e08d81, "snd_pcm_hw_constraint_integer" },
+	{ 0x2b32bccb, "snd_pcm_hw_constraint_integer" },
 	{ 0xe2d5255a, "strcmp" },
-	{ 0xd8188fbb, "snd_pcm_suspend_all" },
-	{ 0xa796ba4c, "class_device_put" },
+	{ 0x68a40f90, "snd_pcm_suspend_all" },
 	{ 0xaa136450, "param_get_charp" },
 	{ 0x5f754e5a, "memset" },
-	{ 0x537f749c, "snd_device_new" },
+	{ 0x2bc3a70, "snd_device_new" },
 	{ 0xdd132261, "printk" },
 	{ 0x80cc7af9, "ioremap" },
-	{ 0x9ef544b0, "snd_pcm_set_ops" },
-	{ 0xaea7cb30, "snd_ctl_notify" },
+	{ 0x6403aab2, "snd_pcm_set_ops" },
+	{ 0xcbc6678e, "snd_ctl_notify" },
 	{ 0xdc76cbcb, "param_set_bool" },
 	{ 0xa39b4cf2, "udelay" },
 	{ 0x84b183ae, "strncmp" },
-	{ 0x2edc6649, "snd_pcm_lib_free_pages" },
-	{ 0xd94d96ea, "platform_device_unregister" },
-	{ 0xe6faae78, "platform_driver_register" },
-	{ 0x3d723658, "snd_pcm_lib_ioctl" },
-	{ 0xc854cf59, "macio_find" },
-	{ 0x62bad416, "snd_pcm_lib_malloc_pages" },
+	{ 0x22c8a719, "snd_pcm_lib_free_pages" },
+	{ 0x887b3080, "platform_device_unregister" },
+	{ 0x1d53b3d5, "platform_driver_register" },
+	{ 0x394dd300, "snd_pcm_lib_ioctl" },
+	{ 0x43b0c9c3, "preempt_schedule" },
+	{ 0xd28d7d20, "macio_find" },
+	{ 0xb299a9f, "snd_pcm_lib_malloc_pages" },
 	{ 0x7be4827c, "pci_dram_offset" },
-	{ 0x112a1c29, "i2c_register_driver" },
-	{ 0xafbf0a7b, "snd_card_new" },
-	{ 0x4cfc1b77, "find_devices" },
+	{ 0xbf13e95d, "i2c_register_driver" },
+	{ 0xa93d8337, "snd_card_new" },
+	{ 0x1e427a16, "find_devices" },
 	{ 0xc0d84ced, "cuda_poll" },
-	{ 0x8523fd53, "kmem_cache_alloc" },
-	{ 0x59e76f0d, "i2c_smbus_write_block_data" },
+	{ 0x5073f9f2, "i2c_smbus_write_block_data" },
 	{ 0x74fe8730, "sys_ctrler" },
 	{ 0x93fca811, "__get_free_pages" },
-	{ 0x9d85afa9, "input_register_device" },
-	{ 0x8acf5d0d, "request_irq" },
-	{ 0x2e450ec3, "get_property" },
-	{ 0x344326e6, "snd_ctl_new1" },
-	{ 0x329a418c, "mach_powermac" },
-	{ 0xd49501d4, "__release_region" },
-	{ 0x383fbfff, "snd_pcm_set_sync" },
-	{ 0x35fe47a1, "init_timer" },
+	{ 0x19a74a0c, "input_register_device" },
+	{ 0x2cf190e3, "request_irq" },
+	{ 0xc5ab9c45, "get_property" },
+	{ 0xe444ab2f, "snd_ctl_new1" },
+	{ 0x8d9acf3f, "input_free_device" },
+	{ 0x96381e3e, "mach_powermac" },
+	{ 0x8bb33e7d, "__release_region" },
+	{ 0x5f378932, "snd_pcm_set_sync" },
+	{ 0x72576def, "snd_ctl_remove" },
 	{ 0x2cd7da6c, "param_set_charp" },
 	{ 0x4302d0eb, "free_pages" },
 	{ 0xb6c70a7d, "__wake_up" },
-	{ 0xc818ff24, "kmem_cache_zalloc" },
+	{ 0x15f873be, "kmem_cache_zalloc" },
 	{ 0x952e843b, "machine_is_compatible" },
 	{ 0xfcec0987, "enable_irq" },
 	{ 0x37a0cba, "kfree" },
 	{ 0x9d669763, "memcpy" },
-	{ 0xeb27a54a, "input_unregister_device" },
+	{ 0xebb03e32, "input_unregister_device" },
 	{ 0x98adfde2, "request_module" },
 	{ 0xedc03953, "iounmap" },
-	{ 0x8174ce01, "pci_get_device" },
-	{ 0xdd902bd6, "snd_pcm_lib_preallocate_pages_for_all" },
-	{ 0xe95dbbbc, "snd_card_free" },
-	{ 0x7ffb067e, "snd_card_register" },
+	{ 0xee99138d, "pci_get_device" },
+	{ 0x59576a22, "snd_pcm_lib_preallocate_pages_for_all" },
+	{ 0xb05666df, "snd_card_free" },
+	{ 0xaea24900, "snd_card_register" },
 	{ 0x5611e4ec, "param_get_bool" },
-	{ 0xf2eda8a6, "pci_dev_put" },
-	{ 0x398b49a5, "i2c_smbus_write_i2c_block_data" },
-	{ 0x7e043ace, "of_address_to_resource" },
-	{ 0xed5b6b7b, "snd_pcm_new" },
-	{ 0x91ef0981, "snd_ctl_add" },
-	{ 0x11de8e16, "platform_driver_unregister" },
-	{ 0x22a36dfd, "machine_id" },
-	{ 0x9f1c4c8a, "device_is_compatible" },
+	{ 0xe7177f95, "pci_dev_put" },
+	{ 0xf2aa1d53, "i2c_smbus_write_i2c_block_data" },
+	{ 0xc8d70044, "of_address_to_resource" },
+	{ 0xa157f1e5, "snd_pcm_new" },
+	{ 0x4ca7f502, "snd_ctl_add" },
+	{ 0xedf50934, "platform_driver_unregister" },
+	{ 0x76a15475, "machine_id" },
+	{ 0x3a37a793, "device_is_compatible" },
 	{ 0xf20dabd8, "free_irq" },
 	{ 0xe914e41e, "strcpy" },
-	{ 0x41a75a1d, "input_allocate_device" },
+	{ 0xa765dffe, "input_allocate_device" },
 };
 
 static const char __module_depends[]
@@ -107,4 +108,4 @@
 "depends=snd-pcm,snd";
 
 
-MODULE_INFO(srcversion, "FD773CD6EC893B1609167B7");
+MODULE_INFO(srcversion, "F78A3AD46FE070AB797CAB2");
Endast i ../../linux-source-2.6.20/sound/ppc: snd_ps3.c
Endast i ../../linux-source-2.6.20/sound/ppc: snd_ps3.h
Endast i ../../linux-source-2.6.20/sound/ppc: snd_ps3_reg.h
diff -x '*.cmd' -x '*.o' -ur ppc/tumbler.c ../../linux-source-2.6.20/sound/ppc/tumbler.c
--- ppc/tumbler.c	2006-09-23 05:19:21.000000000 +0200
+++ ../../linux-source-2.6.20/sound/ppc/tumbler.c	2007-04-12 19:16:28.000000000 +0200
@@ -942,10 +942,11 @@
 }
 
 static struct work_struct device_change;
+static struct snd_pmac *device_change_chip;
 
-static void device_change_handler(void *self)
+static void device_change_handler(struct work_struct *work)
 {
-	struct snd_pmac *chip = self;
+	struct snd_pmac *chip = device_change_chip;
 	struct pmac_tumbler *mix;
 	int headphone, lineout;
 
@@ -1017,7 +1018,7 @@
 
 
 /* interrupt - headphone plug changed */
-static irqreturn_t headphone_intr(int irq, void *devid, struct pt_regs *regs)
+static irqreturn_t headphone_intr(int irq, void *devid)
 {
 	struct snd_pmac *chip = devid;
 	if (chip->update_automute && chip->initialized) {
@@ -1036,7 +1037,7 @@
 		return NULL;
   
 	for (np = np->child; np; np = np->sibling) {
-		char *property = get_property(np, "audio-gpio", NULL);
+		const char *property = get_property(np, "audio-gpio", NULL);
 		if (property && strcmp(property, name) == 0)
 			return np;
 	}  
@@ -1063,7 +1064,8 @@
 				struct pmac_gpio *gp, int is_compatible)
 {
 	struct device_node *node;
-	u32 *base, addr;
+	const u32 *base;
+	u32 addr;
 
 	if (is_compatible)
 		node = find_compatible_audio_device(device);
@@ -1075,9 +1077,9 @@
 		return -ENODEV;
 	}
 
-	base = (u32 *)get_property(node, "AAPL,address", NULL);
+	base = get_property(node, "AAPL,address", NULL);
 	if (! base) {
-		base = (u32 *)get_property(node, "reg", NULL);
+		base = get_property(node, "reg", NULL);
 		if (!base) {
 			DBG("(E) cannot find address for device %s !\n", device);
 			snd_printd("cannot find address for device %s\n", device);
@@ -1091,13 +1093,13 @@
 
 	gp->addr = addr & 0x0000ffff;
 	/* Try to find the active state, default to 0 ! */
-	base = (u32 *)get_property(node, "audio-gpio-active-state", NULL);
+	base = get_property(node, "audio-gpio-active-state", NULL);
 	if (base) {
 		gp->active_state = *base;
 		gp->active_val = (*base) ? 0x5 : 0x4;
 		gp->inactive_val = (*base) ? 0x4 : 0x5;
 	} else {
-		u32 *prop = NULL;
+		const u32 *prop = NULL;
 		gp->active_state = 0;
 		gp->active_val = 0x4;
 		gp->inactive_val = 0x5;
@@ -1106,7 +1108,7 @@
 		 * as we don't yet have an interpreter for these things
 		 */
 		if (platform)
-			prop = (u32 *)get_property(node, platform, NULL);
+			prop = get_property(node, platform, NULL);
 		if (prop) {
 			if (prop[3] == 0x9 && prop[4] == 0x9) {
 				gp->active_val = 0xd;
@@ -1122,7 +1124,7 @@
 	DBG("(I) GPIO device %s found, offset: %x, active state: %d !\n",
 	    device, gp->addr, gp->active_state);
 
-	return (node->n_intrs > 0) ? node->intrs[0].line : 0;
+	return irq_of_parse_and_map(node, 0);
 }
 
 /* reset audio */
@@ -1265,16 +1267,16 @@
 				    &mix->line_mute, 1);
 	irq = tumbler_find_device("headphone-detect",
 				  NULL, &mix->hp_detect, 0);
-	if (irq < 0)
+	if (irq <= NO_IRQ)
 		irq = tumbler_find_device("headphone-detect",
 					  NULL, &mix->hp_detect, 1);
-	if (irq < 0)
+	if (irq <= NO_IRQ)
 		irq = tumbler_find_device("keywest-gpio15",
 					  NULL, &mix->hp_detect, 1);
 	mix->headphone_irq = irq;
  	irq = tumbler_find_device("line-output-detect",
 				  NULL, &mix->line_detect, 0);
- 	if (irq < 0)
+ 	if (irq <= NO_IRQ)
 		irq = tumbler_find_device("line-output-detect",
 					  NULL, &mix->line_detect, 1);
 	mix->lineout_irq = irq;
@@ -1317,10 +1319,9 @@
 		request_module("i2c-powermac");
 #endif /* CONFIG_KMOD */	
 
-	mix = kmalloc(sizeof(*mix), GFP_KERNEL);
+	mix = kzalloc(sizeof(*mix), GFP_KERNEL);
 	if (! mix)
 		return -ENOMEM;
-	memset(mix, 0, sizeof(*mix));
 	mix->headphone_irq = -1;
 
 	chip->mixer_data = mix;
@@ -1417,7 +1418,8 @@
 	chip->resume = tumbler_resume;
 #endif
 
-	INIT_WORK(&device_change, device_change_handler, (void *)chip);
+	INIT_WORK(&device_change, device_change_handler);
+	device_change_chip = chip;
 
 #ifdef PMAC_SUPPORT_AUTOMUTE
 	if ((mix->headphone_irq >=0 || mix->lineout_irq >= 0) 
```

---

### Post by stmiller on 2007-04-26
Hm, yeah you are right I tried the latest alsa rc and snd-aoa loads, but rejects the hardware. I'll try to get in touch with JoseJX on irc.

Read this:

[http://forums.gentoo.org/viewtopic-t-548091.html](http://forums.gentoo.org/viewtopic-t-548091.html)

There is hope... :)

---

### Post by anders_gud on 2007-04-26
> **stmiller said:**
> 
[http://forums.gentoo.org/viewtopic-t-548091.html](http://forums.gentoo.org/viewtopic-t-548091.html)
There is hope... :)

I think that thread is about a albook G4 :( 

edit: You were right! there is hope after all.... 

There must be others with the same issue (tibook+recent kernels...)

---

### Post by boucaron on 2007-04-26
> **anders_gud said:**
> Sorry - 2.6.21-rc7 does not fix it, I was mislead by [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/comments/25"). 

Anyway - I am now running:
2.6.21-rc7
libasound2 1.0.14rc3

Identical symptoms as in stock Feisty kernel...

I also have a TiBook with a 550 Mhz and also the sound issue with Feisty.
I **"almost"** fixed it, see files (config, kernel package) on my personal homepage: [http://julien.boucaron.free.fr/apple_titanium/]("http://julien.boucaron.free.fr/apple_titanium/")
However the powermac_dma stuff seems to be a little bit buggy sending kind of spurious irq from time to time (tiny glitch on the sound) :guitar: 

See the config of my kernel (previous homepage): now powermac_dma and powermac_sound the whole ALSA also is linked in the kernel instead to be a module.

Hope that helps

Cheers
Julien

---

### Post by anders_gud on 2007-04-27
> **boucaron said:**
> I also have a TiBook with a 550 Mhz and also the sound issue with Feisty.
I **"almost"** fixed it, see files (config, kernel package) on my personal homepage: [http://julien.boucaron.free.fr/apple_titanium/]("http://julien.boucaron.free.fr/apple_titanium/")
However the powermac_dma stuff seems to be a little bit buggy sending kind of spurious irq from time to time (tiny glitch on the sound) :guitar: 


Yes, I can also get sound using the obsolete OSS (dmasound_pmac) drivers... But ALSA remains broken...

---

### Post by anders_gud on 2007-04-27
Update:
No improvement with kernel 2.6.21 - released today...

---

### Post by stmiller on 2007-04-27
Hm. Well I might try compiling an older version of alsa. I've got the new 2.6.21 kernel installed also. Thought it would work- oh well. :(

---

### Post by anders_gud on 2007-04-27
> **stmiller said:**
> Hm. Well I might try compiling an older version of alsa. I've got the new 2.6.21 kernel installed also. Thought it would work- oh well. :(

Posted on [**Gentoo Forums**]("http://forums.gentoo.org/viewtopic-t-551762.html"), asking for help...

---

### Post by math_penguin on 2007-04-27
I am having the same proble and am just now starting to investigate it. I noticed that dmesg does not reference ALSA (except for anders_gud's kernel with ALSA built in debug mode.) However, in the post-Feisty kernel we seem to be getting the following lines:

[   28.303895] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[   30.884751] i2c_adapter i2c-2: unable to read EDID block.
[   31.040742] i2c_adapter i2c-2: unable to read EDID block.
[   31.196741] i2c_adapter i2c-2: unable to read EDID block.
[   31.352739] i2c_adapter i2c-3: unable to read EDID block.
[   31.508738] i2c_adapter i2c-3: unable to read EDID block.
[   31.664737] i2c_adapter i2c-3: unable to read EDID block.


These did not appear during the earlier kernel boot processes, and seem to be indicating something abad is happening. I don't know much about the hardware or drivers, but I did read that this is the bus that is trying to talk to the sound card. Does this spark any ideas?

---

### Post by anders_gud on 2007-04-28
> **math_penguin said:**
> 

[   28.303895] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[   30.884751] i2c_adapter i2c-2: unable to read EDID block.
[   31.040742] i2c_adapter i2c-2: unable to read EDID block.
[   31.196741] i2c_adapter i2c-2: unable to read EDID block.
[   31.352739] i2c_adapter i2c-3: unable to read EDID block.
[   31.508738] i2c_adapter i2c-3: unable to read EDID block.
[   31.664737] i2c_adapter i2c-3: unable to read EDID block.


These did not appear during the earlier kernel boot processes, and seem to be indicating something abad is happening. I don't know much about the hardware or drivers, but I did read that this is the bus that is trying to talk to the sound card. Does this spark any ideas?

Yes I've seen his too - I think it's related to monitor sleep in the radeon card and the PMU...

---

### Post by stmiller on 2007-04-30
Okay no luck so far, but here's what I've tried to get sound going. Using a 2.6.21 kernel.

Downloaded the most recent alsa (.14rc3) from the alsa sourceforge page, and install all components, as outlined here:

[https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)

I use these configure options for the driver:

$ ./configure --with-sequencer=yes --with-oss=yes --with-cards=powermac,aoa,usb-audio,aoa-fabric-layout,aoa-soundbus

Still same problem. No fix. Then I tried a past version of alsa from source, installing as above. (Ver. .12) Same problem. I then tried the following older Edgy alsa packages:

alsa-base_1.0.11-5ubuntu1_all
alsa-firmware-loaders_1.0.11-1_powerpc
alsa-oss_1.0.11-1_powerpc
alsa-tools_1.0.11-1_powerpc
alsa-utils_1.0.11-6ubuntu2_powerpc

And confirmed that they all installed fine, downgrading my alsa version. Rebooted, and tried the snd-powermac driver and no luck. SAME problem. 1-2 seconds of audio, then total dropout/program freeze.

I might try another previous ubuntu ppc alsa release, one before edgy and see if that works, perhaps.

EDIT: Just tried the Dapper versions of the above pacakges (1.0.10). No fix, same issue exists. This is quite a bug. Something is very broken. :-(

---

### Post by anders_gud on 2007-05-01
> **stmiller said:**
> 
No fix, same issue exists. This is quite a bug. Something is very broken. :-(
This must be a kernel bug, tried booting off a [non-ubuntu]("http://ppckernel.org/download/pb-stable/linux-pb-stable-2.6.21.1.tar.bz2") kernel for titanium powerbooks. No improvement...
There has been so many changes in 2.6.20... And I dont have time to do a git bisect.

---

### Post by stmiller on 2007-05-01
Ah you are right. I just compiled a 2.6.19.7 kernel, and I have sound working perfectly with the snd-powermac driver! Looks like a problem with the .20 kernels.

I did a 
$ make pmac32_defconfig
and have my sound options configured as below in the images:

---

### Post by anders_gud on 2007-05-01
> **stmiller said:**
> Looks like a problem with the .20 kernels.

Have you tried any of the earlier kernels (ie. 2.6.20.1 ->)?
Our only hope now is to know where it broke. According to Johannes Berg (the author of snd-aoa) on [**linuxppc-dev**]("http://ozlabs.org/pipermail/linuxppc-dev/2007-May/035091.html") there is no plans for supporting older chips in the Apple On-board Audio drivers.

---

### Post by stmiller on 2007-05-01
I tried a 2.6.20.7 kernel, which didn't work. I see that 2.6.20 had many powerpc changes. I could try that one and see if it is indeed where the problem started? Perhaps we should make a kernel bug report?

I searched here for alsa and did not see anything related.
[http://bugme.osdl.org/](http://bugme.osdl.org/)

Scott

---

### Post by ssam on 2007-05-01
in the ben collins git branch of the kernel the bug
6706860d711b83f628dc89eed70b2fac641af683 Ubuntu-2.6.20-0.0 is good
[http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commit;h=6706860d711b83f628dc89eed70b2fac641af683](http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commit;h=6706860d711b83f628dc89eed70b2fac641af683)

the herd2 kernel was bad
probably [http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commit;h=77e42f1ee6f8b60c441f705f71e1a8f189f383d9](http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commit;h=77e42f1ee6f8b60c441f705f71e1a8f189f383d9)  guessing by dates

this is as far as i got with git bisecting. most of the time the bisect would give me something that would not build. maybe someone is better at building kernels or using git than me.

---

### Post by stmiller on 2007-05-01
Thought I would add this into our mega TiBook G4 thread. I got the DVI-out to work, with the following added to my /etc/X11/xorg.conf:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	#Option		"UseFBDev"		"true"
	Option		"AGPMode"	"4"
	Option		"AGPFastWrite"	"true"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel"	"true"
	Option		"AccelMethod"	"exa"
	Option		"backingstore"
	Option		"UseFWPLL"	"true"
	Option		"MergedFB"	"true"
	Option		"CRT2Position"	"Clone"
	Option		"MetaModes"	"1280x854 1024x768 800x600"
	Option		"CloneMode"	"1280x854"
EndSection
```

After connecting the monitor, press ctrl+alt+backspace [delete] to restart X. The second display will now turn on. To revert back, unplug the second display, and hit ctrl+alt+backspace to restart X and you will be back to normal.

Note: the above configuration is for mirroring, only. And you could perhaps put more metamodes, but 1024x768 is probably safest for most overheads and such.

I think this will work with all ati chips. (Note: older agp 2x chips will have to specify agpmode 2)

---

### Post by stmiller on 2007-05-07
Okay here is my xorg.conf for this 15" 867 Mhz Tibook. This works for me to have dri loaded, and 3D working, though X becomes somewhat unstable when dri is enabled. This includes the mirroring DVI-out settings.

I'm trying different settings to get Beryl or Compiz going. You can see the different options I've tried, most commented out here. (Compiz worked without altering the stock xorg.conf for me previously!- But I've compiled a 2.6.19.7 kernel now and for some reason Compiz does not work.)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"mac"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"BusType"	"PCI"
	#Option		"ForcePCIMode"	"true"
	#Option 	"VideoRam"	"32MB"
	#Option		"UseFBDev"	"true"
	Option		"AGPMode"	"2"
	Option		"AGPFastWrite"	"true"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel"	"true"
	Option		"AccelMethod"	"exa"
	Option		"backingstore"  "true"
	Option		"UseFWPLL"	"true"
	Option		"MergedFB"	"true"
	Option		"CRT2Position"	"Clone"
	Option		"MetaModes"	"1280x854 1024x768 800x600"
	Option		"CloneMode"	"1280x854"
	#Option		"DRI"		"true"
	Option		"GARTSize"	"64"
	#Option		"AddARGBGLXVisuals"	"true"
	#Option		"DisableGLXRootClipping"	"true"
	#Option		"AllowGLXWithComposite"		"true"
	#Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Color LCD"
	DefaultDepth	24
	#Option		"AllowGLXWithCompisite"	"true"
	#Option		"AddARGBVisuals"	"true"
	#Option		"NoLogo"		"true"
	SubSection "Display"
		Depth		1
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x854"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"		"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "Extensions"
#	Option	"Composite"	"enable"
#	Option	"RENDER"	"enable"
#EndSection

Section "DRI"
	Mode	0666
EndSection
```


You can comment out

Load	"dri"

to turn off dri if it's too unstable.

---

### Post by rph on 2007-05-08
Thanks for documenting all of this.

I have the same model TiBook, but I can't get my external monitor to work with your xorg.conf.  The monitor--a Dell 24 inch LCD--seems to be getting a signal since it's not going into power save mode.  But the screen stays blank.  Which settings in xorg.conf do you think I should try to play with to get things working?

---

### Post by stmiller on 2007-05-08
Hey that sounds like the Dell LCD is not getting a resolution it can display, so it's just staying blank. Some of those larger LCDs are picky with which resolutions they can use, and may only want a wide screen resolution. You'll have to play with the metamodes and clone mode settings to try a few different resolutions.

Try this, perhaps:

Option		"MetaModes"	"1280x800 1024x768 800x600"
Option		"CloneMode"	"1280x800"



If you do

$ cat /var/log/Xorg.0.log when trying to use the second display it will probe and tell you the possible resolutions of "CRT2" That may give you better resolution options.

---

### Post by rph on 2007-05-10
Hmm.  I've tried a number of different MetaModes and CloneModes settings, but still can't get any picture from the Dell LCD.  No problems with the powerbook's internal LCD though.

Here's the section of /var/log/Xorg.0.log that details the possible resolutions for the Dell.  It seems to prefer 1920x1200.

If you have any ideas, I'd love to hear them.


(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a017  Serial#: 825242195
(II) RADEON(0): Year: 2007  Week: 4
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 52  vert.: 33
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
(II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) RADEON(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) RADEON(0): Serial No: CC30271Q102S
(II) RADEON(0): Monitor name: DELL 2407WFP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 170 MHz

---

### Post by stmiller on 2007-05-29
I've made a bug report on the alsa bug reporter. I'll try there first, and see if it's a snd-powermac issue this team can fix. The alsa folks might recommend to send it to the kernel bug list. We'll see.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3126](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3126)

---

### Post by lixus on 2007-06-19
I am also a TiBook G4 user.
I wasted several hours while  trying to get feisty to work and finally gave up.

Sleep/wakeup did not work (frozen X display), external usb HDs made the
whole system rebooting, usb devices were not set to sleep when lid was closed,
external usb keyboard did not work after wakeup, fans were running all the time, sound did not work, etc ...

I now restored my latest dapper 6.06 LTS backup were everything works perfect out of the box
and I am happy again.  My suggestion: use 6.06 LTS and be happy.

---

### Post by ag0g0girl on 2007-07-08
I am not going back to Dapper, my screen resolution was too low.  Edgy and Feisty both have the sound problem for me. 

Can someone explain the kernel switch.  Does this change anything else besides the sound?

ag0g0girl

---

### Post by stmiller on 2007-07-09
Hi, to install an earlier kernel, just do this:

Step one: Install Feisty as usual, do all updates

Step two: download a kernel from Edgy, this one:

[http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-11-powerpc](http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-11-powerpc)

(Click on powerpc in the box at the bottom)

And then after it downloads double click to install the deb.

You may have to edit your /etc/yaboot.conf so you default to booting into this earlier kernel.

There is no difference in Feisty with an older kernel; a kernel makes no difference in software versions, or anything else. It's Feisty.

---

### Post by jaskah on 2007-07-13
i can get sound working on feisty on my 1 ghz titanium powerbook, but *only* with my rme hammerfall sound card--and the sound quality is crap, with lots of dropouts and clicks. i even tried compiling my own low-latency kernel and re-installing the most current alsa drivers and but this still made no difference.
everything else that i checked is working fine;pnly sound--any sound--is not.
any help on this would be greatly appreciated!

---

### Post by stmiller on 2007-07-13
jaskah:

Check out this bug report for the current status: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/)

Basically no one knows what is going on. But running a kernel pre-2.6.20 works with sound just fine. Other PowerPC distros don't seem to be having this problem, or at least from what I've searched no one is having issues. :(

The driver snd-powermac is being replaced by a newer, better driver snd-aoa. But the person who makes the snd-aoa driver doesn't have one of these older Macs to build/test this driver on our older Macs. Nor does he have time, it looks like from his response on debian ppc.

So we are stuck at the moment unfortunately.

---

### Post by jaskah on 2007-07-14
stmiller:
thanks for your reply.
i am new to ubuntu; is there a link somewhere, showing how i can replace my current kernel with a pre-2.6.20 kernel?
or should i just wait until this bug gets fixed in the next kernel?
not sure what to do, at this point...

---

### Post by stmiller on 2007-07-14
Just look four posts UP on this very thread. :)

[http://ubuntuforums.org/showpost.php?p=2990910&postcount=42](http://ubuntuforums.org/showpost.php?p=2990910&postcount=42)

---

### Post by stmiller on 2007-07-20
Update: vanilla 2.6.22.1 kernel and sound is still broken. Also tried the latest alsa 1.0.14 and same problem.

:(

---

### Post by jaskah on 2007-07-22
before i go ahead and install an older kernel, i was just wondering if anyone had any news about a fix for this bug...maybe in the latest kernel?
thanks!

---

### Post by ChillMonkey on 2007-08-13
i've got a TiBook Mercury i'm about to do an install on. no word on the sound issue i take it? not that it's a big enough issue to stop me, more of a nuisance i guess.

just as a side point, I'm currently running Tiger and clicking on Audio(Built in) in System Profiler just gives me "There was an error while gathering this information" 

unrelated?, i don't know.

---

### Post by jaskah on 2007-08-16
hello 

> **ChillMonkey said:**
> i've got a TiBook Mercury i'm about to do an install on. no word on the sound issue i take it? not that it's a big enough issue to stop me, more of a nuisance i guess..

i installed an earlier kernel (2.6.17-12-powerpc) and now sound works, though there are still some problems being able to use the alsa drivers in jack.
hope this helps.

---

### Post by ChillMonkey on 2007-08-17
> **jaskah said:**
> hello 

i installed an earlier kernel (2.6.17-12-powerpc) and now sound works, though there are still some problems being able to use the alsa drivers in jack.
hope this helps.

thanks i'll install with the 7.04 alternate cd and downgrade to that kernel, hope it works.

---

### Post by smackswell on 2007-11-05
> **stmiller said:**
> Hi, to install an earlier kernel, just do this:

Step one: Install Feisty as usual, do all updates

Step two: download a kernel from Edgy, this one:

[http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-11-powerpc](http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-11-powerpc)

(Click on powerpc in the box at the bottom)

And then after it downloads double click to install the deb.

You may have to edit your /etc/yaboot.conf so you default to booting into this earlier kernel.

There is no difference in Feisty with an older kernel; a kernel makes no difference in software versions, or anything else. It's Feisty.


Okay, so I downloaded the kernel and installed it. But i'm uber-new to linux. Doing very minor command line editing on my old ROKR E2 is as far as i've gotten. So how do i edit yaboot to make it load this kernel? And do i just do it in terminal, or in the startup command lines? 

Originally I installed feisty, immediately upgraded to gutsy, and fubr'd my system. I'm trying to go about this carefully now. My TiBook deserves better <3

Thanks in advance!

---

### Post by driven1 on 2007-11-26
I am having sound problems as well with my tibook running kubuntu. The sound works if I switch the source from line to mic, but that's all. Anyone know if this kernel swap will work for me? Thanks.

---

### Post by jaskah on 2007-11-27
my solution was to install kernel 2.6.17-12-powerpc.
after this, i had no problems with sound quality; though i can´t say if your problem will be solved, as i work with an external (rme hammerfall) soundcard and run all my inputs/outputs through this.

---

### Post by anders_gud on 2008-01-13
There is a patch at:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/87652)

Working sound on a 2.6.22.9  kernel.

---

### Post by ssam on 2008-01-14
w00t

the patch works on the 2.6.20 feisty kernel. here are the steps to make yourself a fixed kernel (the instructions should be roughly the same for 2.6.22). you will need about 3GB of free disk space.

```

#get all the dependancies
sudo apt-get install build-essential
sudo apt-get build-dep linux-sourc
sudo apt-get install linux-kernel-devel fakeroot m4 device-tree-compiler

#get the kernel source
apt-get source linux-source-2.6.20 

#get the patch
wget http://launchpadlibrarian.net/11311439/pmac.c.diff

cd linux-source-2.6.20-2.6.20/

# apply the patch
patch sound/ppc/pmac.c < ../pmac.c.diff

#start the build
AUTOBUILD=1 fakeroot debian/rules binary-debs

```
the building will take several hours. the resulting deb files will be put in debian/build

use
```
sudo dpkg -i foo.deb
```
to install the one you want.

I can post a compiled deb if there is demand.

bonus points for anyone who knows how to stop the build script building powerpc64 and smp versions (might make the build much faster)

---

### Post by driven1 on 2008-01-15
Thanks for the update with this issue. I got sound working by installing kernel 2.6.17-12. Is there a benefit to applying this new fix? I really won't have time to even try for a couple of weeks (if it takes hours to build). Thanks again to all who helped resolve this issue.

---

### Post by ssam on 2008-01-17
please can everyone effected by the sound bug post what hardware they have

just to make sure we don't get multiple bugs muddled:
sound cuts out after a fraction of a second, or a few seconds.
adding 'snd-powermac' to /etc/modules does not fix the issue.
running a pre 2.6.20 kernel does fix the issue.

please can you post a description of your mac, eg TiBook 1GHz 15inch.
and the model number, eg PowerBook3,5
this is found by running
```

cat /proc/cpuinfo

```

I will add these to the bug report

---

### Post by szim90 on 2008-01-26
Hi. Here is my system info: (Powermac G4 Quicksilver)

machine: PowerMac3,5
motherboard: PowerMac3,5 MacRISC2 MacRISC Power Macintosh
detected as: 69 (PowerMac G4 Silver)

Thanks for resolving this.

Sean

---

### Post by ssam on 2008-01-27
thanks

so far we only have
PowerMac3,5 and PowerBook3,5

are there any iBooks effected?

---

### Post by stream303 on 2008-01-27
> **ssam said:**
> are there any iBooks effected?

My late 2004 G4 iBook had to have snd-powermac and snd-seq added to /etc/modules.

In my enthusiasm to install, I also forced the use of ALSA in the sound prefs, rather than leave them at "autodetect" or OSS.  Not sure if this was necessary to get it to work initially.

It was this very thread that got my iBook working with sound on Gutsy!  Thanks everyone!

---

### Post by ubuntubrian on 2008-02-21
> **ssam said:**
> w00t

I can post a compiled deb if there is demand.

bonus points for anyone who knows how to stop the build script building powerpc64 and smp versions (might make the build much faster)

Please do post the compiled deb! that would be great. 
I have burned a Hardy live cd and it boots right up on my TiBook but the sound issue is present, ie, a short burst of sound and then nothing. Hardy looks to be great with many pluses and if the sound issue is resolved then I am onboard that train! (no nasty boot problems at all)

BTW:
~$ cat /proc/cpuinfo
processor       : 0
cpu             : 7455, altivec supported
clock           : 667.000000MHz
revision        : 0.2 (pvr 8001 0302)
bogomips        : 66.56
timebase        : 33331553
machine         : PowerBook3,5
motherboard     : PowerBook3,5 MacRISC2 MacRISC Power Macintosh
detected as     : 80 (PowerBook Titanium IV)
pmac flags      : 0000001b
L2 cache        : 256K unified
pmac-generation : NewWorld

---

### Post by MikeTheC on 2008-03-17
Hello All...

I've had an issue with audio playback on both my iMac G4, as well as a PowerBook G4 I used to own, and it's been present in Ubuntu, Fedora, and a couple others as well, so this is not something specific to Ubuntu (presently at 7.10).

The issue is basically this: sound below a certain level is simply clipped, resulting in total silence (of whatever duration). I can force this to not happen by manually cranking my volume levels all the way up (though, depending on how much audio is actually present in that instant, I may still get nothing).

I'm really at a loss over this and was hoping someone else has experienced this (ergo: it's not simply that I'm crazy) and has a notion of how to fix it, or at least where to look.

FWIW, this issue occurs under BOTH the Alsa and OSS mixers.

Thanks very much in advance!


Mike

---

### Post by stream303 on 2008-03-17
How's your PCM level?  I had this issue once and had to run

alsamixer

from a terminal to get fine adjustments of my sound levels.  PCM was waaaay down.  Usually it's is too hot!  After that, I just check the default sound level outputs in the applications themselves.

---

### Post by slacka-vt on 2008-03-18
just installed Hardy from the netinstall mini.iso
on a powerbook G4.
made sure to burn the iso image at 8X
everything went flawless.
detected the wifi b card and configure dhcp
full installation took 2 hrs over a 400kbps cable ilne
i did have to modify the /etc/apt/sources.list
to get rid of the ports.ubuntu.com/ubuntu-ports deb-src entries
and point them to the archive.ubuntu.com/ubuntu
why does this keep happening ?
other then that
all i had to do was add the snd_powermac entry in the /etc/modules file
took me a good 2 hours to read the forum and fix that using
modprobe snd_powermac
and adding it to the /etc/modules config file.

many thanks to all ubuntu devs
you are doing us all a great favor
keep up the good work !
~s:guitar:

---

### Post by ubuntubrian on 2008-04-14
> just installed Hardy from the netinstall mini.iso
on a powerbook G4.
an awfully late post on my part but is this a TiBook G4? Which one? I'm on a 1Ghz and no sound with Hardy. I'm using the LiveCD althought the latest aren't working at all- see:
[http://ubuntuforums.org/showthread.php?t=705267](http://ubuntuforums.org/showthread.php?t=705267)

---


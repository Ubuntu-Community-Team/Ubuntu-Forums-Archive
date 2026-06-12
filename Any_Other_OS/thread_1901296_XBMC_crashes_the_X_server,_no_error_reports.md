---
title: "XBMC crashes the X server, no error reports"
date: 2011-12-28
forum: Any Other OS
---

### Post by jampe on 2011-12-28
Hi there,

I've had some trouble with XBMC.
No matter which version I install, it goes to the splash image and then crashes the X server and exits me to the login screen. I've checked the log file, and there doesn't seem to be any errors to report.

This happens with the game Crayon Physics Deluxe as well. The problem started in Oneiric and persists in Lisa (Mint). Both 32-bit and 64-bit versions. Does anyone here have a similar problem?

I'll post the logfile from XBMC, just in case.
**UPDATE:** After turning on debugging, I got some more info:
```
&#65279;13:55:50 T:140289205454720  NOTICE: -----------------------------------------------------------------------
13:55:50 T:140289205454720  NOTICE: Starting XBMC, Platform: Linux (Linux Mint 12 Lisa, 3.0.0-13-generic x86_64). Built on Dec 28 2011 (Git:Unknown)
13:55:50 T:140289205454720  NOTICE: special://xbmc/ is mapped to: /usr/share/xbmc
13:55:50 T:140289205454720  NOTICE: special://xbmcbin/ is mapped to: /usr/lib/xbmc
13:55:50 T:140289205454720  NOTICE: special://masterprofile/ is mapped to: /home/jampe/.xbmc/userdata
13:55:50 T:140289205454720  NOTICE: special://home/ is mapped to: /home/jampe/.xbmc
13:55:50 T:140289205454720  NOTICE: special://temp/ is mapped to: /home/jampe/.xbmc/temp
13:55:50 T:140289205454720  NOTICE: The executable running is: /usr/lib/xbmc/xbmc.bin
13:55:50 T:140289205454720  NOTICE: Log File is located: /home/jampe/.xbmc/temp/xbmc.log
13:55:50 T:140289205454720  NOTICE: -----------------------------------------------------------------------
13:55:50 T:140289205454720  NOTICE: Setup SDL
13:55:50 T:140289205454720    INFO: Available videomodes (xrandr):
13:55:50 T:140289205454720    INFO: Number of connected outputs: 1
13:55:50 T:140289205454720    INFO: Output 'LVDS1' has 5 modes
13:55:50 T:140289205454720    INFO: ID:0x43 Name:1024x600 Refresh:60.053699 Width:1024 Height:600
13:55:50 T:140289205454720    INFO: Pixel Ratio: 1.045313
13:55:50 T:140289205454720    INFO: ID:0x44 Name:1024x600 Refresh:50.044750 Width:1024 Height:600
13:55:50 T:140289205454720    INFO: Pixel Ratio: 1.045313
13:55:50 T:140289205454720    INFO: ID:0x45 Name:800x600 Refresh:60.316540 Width:800 Height:600
13:55:50 T:140289205454720    INFO: Pixel Ratio: 1.338000
13:55:50 T:140289205454720    INFO: ID:0x46 Name:800x600 Refresh:56.250000 Width:800 Height:600
13:55:50 T:140289205454720    INFO: Pixel Ratio: 1.338000
13:55:50 T:140289205454720    INFO: ID:0x47 Name:640x480 Refresh:59.940479 Width:640 Height:480
13:55:50 T:140289205454720    INFO: Pixel Ratio: 1.338000
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.ConsoleKit on /org/freedesktop/ConsoleKit/Manager with interface org.freedesktop.ConsoleKit.Manager and method CanStop
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UPower on /org/freedesktop/UPower with interface org.freedesktop.UPower and method EnumerateDevices
13:55:50 T:140289205454720    INFO: Selected UPower and ConsoleKit as PowerSyscall
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.ConsoleKit on /org/freedesktop/ConsoleKit/Manager with interface org.freedesktop.ConsoleKit.Manager and method CanStop
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.ConsoleKit on /org/freedesktop/ConsoleKit/Manager with interface org.freedesktop.ConsoleKit.Manager and method CanRestart
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UPower on /org/freedesktop/UPower with interface org.freedesktop.DBus.Properties and method Get
13:55:50 T:140289205454720   DEBUG: Previous line repeats 1 times.
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UPower on /org/freedesktop/UPower with interface org.freedesktop.UPower and method EnumerateDevices
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UPower on /org/freedesktop/UPower/devices/line_power_ACAD with interface org.freedesktop.DBus.Properties and method GetAll
13:55:50 T:140289205454720   DEBUG: Previous line repeats 1 times.
13:55:50 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UPower on /org/freedesktop/UPower/devices/battery_BAT1 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:50 T:140289205454720   DEBUG: Previous line repeats 1 times.
13:55:50 T:140289205454720  NOTICE: load settings...
13:55:50 T:140289205454720   DEBUG: SECTION:LoadDLL(libcrystalhd.so.3)
13:55:50 T:140289205454720   DEBUG: Loading: libcrystalhd.so.3
13:55:50 T:140289205454720   ERROR: Unable to load libcrystalhd.so.3, reason: libcrystalhd.so.3: cannot open shared object file: No such file or directory
13:55:50 T:140289205454720   DEBUG: Dll libcrystalhd.so.3 was not found in path
13:55:50 T:140289205454720   DEBUG: CrystalHD: broadcom crystal hd not found
13:55:50 T:140289205454720  NOTICE: special://profile/ is mapped to: special://masterprofile/
13:55:50 T:140289205454720  NOTICE: loading special://masterprofile/guisettings.xml
13:55:50 T:140289205454720  NOTICE: Getting hardware information now...
13:55:50 T:140289205454720    INFO: Using analog output
13:55:50 T:140289205454720    INFO: AC3 pass through is enabled
13:55:50 T:140289205454720    INFO: DTS pass through is enabled
13:55:50 T:140289205454720    INFO: AAC pass through is disabled
13:55:50 T:140289205454720    INFO: MP1 pass through is disabled
13:55:50 T:140289205454720    INFO: MP2 pass through is disabled
13:55:50 T:140289205454720    INFO: MP3 pass through is disabled
13:55:50 T:140289205454720  NOTICE: Checking resolution 12
13:55:50 T:140289205454720  NOTICE: Loading player core factory settings from special://xbmc/system/playercorefactory.xml.
13:55:50 T:140289205454720   DEBUG: CPlayerCoreConfig::<ctor>: created player DVDPlayer for core 1
13:55:50 T:140289205454720   DEBUG: CPlayerCoreConfig::<ctor>: created player oldmplayercore for core 1
13:55:50 T:140289205454720   DEBUG: CPlayerCoreConfig::<ctor>: created player PAPlayer for core 3
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: system rules
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: rtv
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: hdhomerun/myth/rtmp/mms/udp
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: lastfm/shout
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: rtsp
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: streams
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: flv/aacp/sdp
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: mp2
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: dvd
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: dvdfile
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: dvdimage
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: sdp/asf
13:55:50 T:140289205454720   DEBUG: CPlayerSelectionRule::Initialize: creating rule: nsv
13:55:50 T:140289205454720  NOTICE: Loaded playercorefactory configuration
13:55:50 T:140289205454720  NOTICE: Loading player core factory settings from special://masterprofile/playercorefactory.xml.
13:55:50 T:140289205454720  NOTICE: special://masterprofile/playercorefactory.xml does not exist. Skipping.
13:55:50 T:140289205454720  NOTICE: No settings file to load to load (special://xbmc/system/advancedsettings.xml)
13:55:50 T:140289205454720  NOTICE: No settings file to load to load (special://masterprofile/advancedsettings.xml)
13:55:50 T:140289205454720  NOTICE: Default DVD Player: dvdplayer
13:55:50 T:140289205454720  NOTICE: Default Video Player: dvdplayer
13:55:50 T:140289205454720  NOTICE: Default Audio Player: paplayer
13:55:50 T:140289205454720  NOTICE: Disabled debug logging due to GUI setting. Level 1.
13:55:50 T:140289205454720  NOTICE: Log level changed to 1
13:55:50 T:140289205454720  NOTICE: Loading media sources from special://masterprofile/sources.xml
13:55:50 T:140289205454720    INFO: creating subdirectories
13:55:50 T:140289205454720    INFO: userdata folder: special://masterprofile/
13:55:50 T:140289205454720    INFO: recording folder:
13:55:50 T:140289205454720    INFO: screenshots folder:
13:55:50 T:140289205454720    INFO: thumbnails folder: special://masterprofile/Thumbnails
13:55:50 T:140289205454720    INFO: load language info file: special://xbmc/language/English/langinfo.xml
13:55:50 T:140289205454720   DEBUG: trying to set locale to en_AU.UTF-8
13:55:50 T:140289205454720    INFO: global locale set to en_AU.UTF-8
13:55:50 T:140289205454720    INFO: load language file:special://xbmc/language/English/strings.xml
13:55:50 T:140289205454720   DEBUG: SECTION:LoadDLL(special://xbmcbin/system/libcpluff-x86_64-linux.so)
13:55:50 T:140289205454720   DEBUG: Loading: /usr/lib/xbmc/system/libcpluff-x86_64-linux.so
13:55:50 T:140289205454720    INFO: ADDON: cpluff: 'Could not read plug-in directory /usr/lib/xbmc/addons: No such file or directory'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.json has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.albums.allmusic.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in webinterface.default has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in repository.xbmc.org has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.black has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.euphoria has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.projectm has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in weather.wunderground has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.simplejson has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.dim has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.themoviedb.org has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.artists.allmusic.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.metadata has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in skin.confluence has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.glspectrum has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.pil has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.gui has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.milkdrop has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.dxspectrum has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.core has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.solarwinds has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.slideshow has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.htbackdrops.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.allmusic.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.yahoomusic.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.tvdb.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.last.fm has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.themoviedb.org has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.python has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.imdb.com has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.waveform has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.plasma has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.addon has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.pysqlite has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.hdtrailers.net has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.itunes has been installed.'
13:55:50 T:140289205454720   DEBUG: ADDON: cpluff: 'Not all directories were successfully scanned.'
13:55:50 T:140289205454720   DEBUG: LoadMappings - loaded node "Motorola Nyxboard Hybrid"
13:55:50 T:140289205454720   DEBUG: LoadMappings - loaded node "Pulse-Eight CEC Adaptor"
13:55:50 T:140289205454720   DEBUG: CPeripheralBusUSB - initialised udev monitor: 14
13:55:50 T:140288906225408   DEBUG: Thread XBMC Peripherals start, auto delete: 0
13:55:50 T:140289205454720    INFO: LIRC Initialize: using: /dev/lircd
13:55:50 T:140289205454720    INFO: LIRC Initialize: connect failed: No such file or directory
13:55:50 T:140289205454720   DEBUG: Failed to connect to LIRC. Retry in 10s.
13:55:50 T:140289205454720   DEBUG: OnLostDevice - notify display change event
13:55:50 T:140289205454720    INFO: XRANDR: /usr/lib/xbmc/xbmc-xrandr --output LVDS1 --mode 0x43
13:55:50 T:140289205454720  NOTICE: Using visual 0x22
13:55:50 T:140289205454720    INFO: GL: Maximum texture width: 2048
13:55:50 T:140289205454720   DEBUG: SECTION:LoadDLL(special://xbmcbin/system/ImageLib-x86_64-linux.so)
13:55:50 T:140289205454720   DEBUG: Loading: /usr/lib/xbmc/system/ImageLib-x86_64-linux.so
13:55:50 T:140289205454720   DEBUG: GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_multithread_makecurrent GLX_MESA_swap_control GLX_OML_swap_method GLX_OML_sync_control GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap GLX_INTEL_swap_event
13:55:50 T:140289205454720  NOTICE: CRenderSystemGL::CheckOpenGLQuirks - unable to parse mesa version string
13:55:50 T:140289205454720  NOTICE: GL_VENDOR = Tungsten Graphics, Inc
13:55:50 T:140289205454720  NOTICE: GL_RENDERER = Mesa DRI Intel(R) IGD
13:55:50 T:140289205454720  NOTICE: GL_VERSION = 1.4 Mesa 7.11
13:55:50 T:140289205454720  NOTICE: GL_SHADING_LANGUAGE_VERSION = 1.20
13:55:50 T:140289205454720  NOTICE: GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_vertex_program1_1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_rectangle GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_EXT_texture_env_combine GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_EXT_separate_shader_objects GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_robustness
13:55:50 T:140289205454720   DEBUG: OnLostDevice - notify display change event
13:55:50 T:140289205454720   ERROR: GLX: Same window as before, refreshing context
13:55:50 T:140289205454720    INFO: GL: Maximum texture width: 2048
13:55:50 T:140289205454720    INFO: load default splash image: /usr/share/xbmc/media/Splash.png
13:55:51 T:140289205454720    INFO: load keymapping
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/appcommand.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/gamepad.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Alienware.Dual.Compatible.Controller.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.AppleRemote.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Harmony.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Interact.AxisPad.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Logitech.RumblePad.2.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Microsoft.Xbox.360.Controller.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Microsoft.Xbox.Controller.S.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.PS3.Remote.Keyboard.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.Sony.PLAYSTATION(R)3.Controller.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/joystick.WiiRemote.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/keyboard.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/mouse.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/keymaps/remote.xml
13:55:51 T:140289205454720    INFO: Loading special://xbmc/system/Lircmap.xml
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'mceusb'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'XboxDVDDongle'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'Microsoft_Xbox'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'PinnacleSysPCTVRemote'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'anysee'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'iMON-PAD'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'Antec_Veris_RM200'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'MCE_via_iMON'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'TwinHanRemote'
13:55:51 T:140289205454720    INFO: * Adding remote mapping for device 'linux-input-layer'
13:55:51 T:140289205454720    INFO: * Linking remote mapping for 'linux-input-layer' to 'cx23885_remote'
13:55:51 T:140289205454720    INFO: * Linking remote mapping for 'linux-input-layer' to 'devinput'
13:55:51 T:140289205454720   DEBUG: CButtonTranslator::Load - no userdata Lircmap.xml found, skipping
13:55:51 T:140289205454720    INFO: GUI format 1024x600 1024x600 @ 60.05 - Full Screen
13:55:51 T:140289205454720   DEBUG: guilib: Fill viewport always for solving rendering passes
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks with interface org.freedesktop.UDisks and method EnumerateDevices
13:55:51 T:140289205454720   DEBUG: Selected UDisks as storage provider
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DaemonVersion 1
13:55:51 T:140289205454720   DEBUG: UDisks: Querying available devices
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks with interface org.freedesktop.UDisks and method EnumerateDevices
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda5)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda5 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda5: IsFileSystem true HasFileSystem ext4 IsSystemInternal true IsMounted true IsRemovable false IsPartition true IsOptical false
13:55:51 T:140289205454720  NOTICE: UDisks: Added /home
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda6)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda6 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda6: IsFileSystem true HasFileSystem ext4 IsSystemInternal true IsMounted true IsRemovable false IsPartition true IsOptical false
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda7)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda7 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda7: IsFileSystem true HasFileSystem ext3 IsSystemInternal true IsMounted false IsRemovable false IsPartition true IsOptical false
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda: IsFileSystem false HasFileSystem  IsSystemInternal true IsMounted false IsRemovable false IsPartition false IsOptical false
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda1)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda1 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda1: IsFileSystem false HasFileSystem  IsSystemInternal true IsMounted false IsRemovable false IsPartition true IsOptical false
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded (/org/freedesktop/UDisks/devices/sda2)
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda2 with interface org.freedesktop.DBus.Properties and method GetAll
13:55:51 T:140289205454720   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sda with interface org.freedesktop.DBus.Properties and method Get
13:55:51 T:140289205454720   DEBUG: UDisks: DeviceAdded - DeviceUDI /org/freedesktop/UDisks/devices/sda2: IsFileSystem false HasFileSystem  IsSystemInternal true IsMounted false IsRemovable false IsPartition true IsOptical false
13:55:51 T:140289205454720  NOTICE: start dvd mediatype detection
13:55:51 T:140289205454720  NOTICE: initializing playlistplayer
13:55:51 T:140289205454720  NOTICE: DONE initializing playlistplayer
13:55:51 T:140289205184256   DEBUG: Thread CDetectDVDMedia start, auto delete: 0
13:55:51 T:140289205184256   DEBUG: Compiled with libcdio Version 0.81
13:55:51 T:140289205454720   DEBUG: DPMS: supported power-saving modes: SUSPEND OFF STANDBY
13:55:51 T:140289205184256   DEBUG: Thread CDetectDVDMedia 140289205184256 terminating
13:55:51 T:140289205454720    INFO: Unloading old skin ...
13:55:51 T:140289205454720    INFO:   load skin from:/usr/share/xbmc/addons/skin.confluence
13:55:51 T:140289205454720    INFO:   load fonts for skin...
13:55:51 T:140289205454720    INFO: Loading fonts from /usr/share/xbmc/addons/skin.confluence/720p/Font.xml
13:55:51 T:140289205454720    INFO: Loading skin includes from /usr/share/xbmc/addons/skin.confluence/720p/includes.xml
13:55:51 T:140289205454720    INFO:   load new skin...
13:55:51 T:140289205454720    INFO: Loading skin file: Home.xml
13:55:51 T:140289205454720    INFO: Loading user windows, path /usr/share/xbmc/addons/skin.confluence/720p
13:55:51 T:140289205454720   DEBUG: Load Skin XML: 104.99ms
13:55:51 T:140289205454720    INFO:   initialize new skin...
13:55:51 T:140289205454720   DEBUG: guilib: Fill viewport always for solving rendering passes
13:55:51 T:140289205454720    INFO: Loading skin file: Pointer.xml
13:55:51 T:140289205454720    INFO: Loading skin file: DialogVolumeBar.xml
13:55:51 T:140289205454720    INFO: Loading skin file: DialogKaiToast.xml
13:55:51 T:140289205454720    INFO: Loading skin file: DialogMuteBug.xml
13:55:51 T:140289205454720    INFO: Loading skin file: DialogSeekBar.xml
13:55:51 T:140289205454720    INFO: Loading skin file: DialogBusy.xml
13:55:51 T:140289205454720   DEBUG: CGUIAudioManager::Initialize
13:55:51 T:140289205454720    INFO: Loading /usr/share/xbmc/addons/skin.confluence/sounds/sounds.xml
13:55:51 T:140289205454720    INFO:   skin loaded...
13:55:51 T:140289205454720   DEBUG: Activating window ID: 12999
13:55:51 T:140289205454720   DEBUG: ------ Window Init (Startup.xml) ------
13:55:51 T:140289205454720    INFO: Loading skin file: Startup.xml
13:55:51 T:140289205454720    INFO: removing tempfiles
13:55:51 T:140289205454720   DEBUG: ADDON: Starting service addons.
13:55:51 T:140289205454720  NOTICE: initialize done
13:55:51 T:140289205454720  NOTICE: Running the application...
13:55:51 T:140289205454720   DEBUG: ExecuteXBMCAction : Translating ReplaceWindow(Home)
13:55:51 T:140289205454720   DEBUG: ExecuteXBMCAction : To ReplaceWindow(Home)
13:55:51 T:140289205454720   DEBUG: Activating window ID: 10000
13:55:51 T:140289205454720   DEBUG: OpenBundle - Opened bundle /usr/share/xbmc/addons/skin.confluence/media/Textures.xbt
13:55:51 T:140288884709120   DEBUG: Thread Jobworker start, auto delete: 1
13:55:51 T:140289205454720   DEBUG: ------ Window Init (Pointer.xml) ------
13:55:51 T:140289205454720   DEBUG: ------ Window Deinit (Startup.xml) ------
13:55:51 T:140289205454720   DEBUG: CheckDisplayEvents: Received RandR event 101
13:55:51 T:140289205454720   DEBUG: CheckDisplayEvents - notify display reset event
13:55:51 T:140288884709120   DEBUG: DoWork - took 179 ms to load special://skin/backgrounds/videos.jpg
13:55:52 T:140288906225408   DEBUG: Thread XBMC Peripherals 140288906225408 terminating
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.json has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.albums.allmusic.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in repository.xbmc.org has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in webinterface.default has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.euphoria has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.black has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.projectm has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.simplejson has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in weather.wunderground has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.dim has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.artists.allmusic.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.themoviedb.org has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.metadata has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in skin.confluence has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.glspectrum has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.milkdrop has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.gui has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.pil has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.dxspectrum has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.core has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.solarwinds has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.xbmc.builtin.slideshow has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.htbackdrops.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.tvdb.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.yahoomusic.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.allmusic.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.last.fm has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.themoviedb.org has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.imdb.com has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.python has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in xbmc.addon has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in screensaver.rsxs.plasma has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.waveform has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in script.module.pysqlite has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in visualization.itunes has been uninstalled.'
13:55:52 T:140289205454720   DEBUG: ADDON: cpluff: 'Plug-in metadata.common.hdtrailers.net has been uninstalled.'

```

---

### Post by Perfect Storm on 2011-12-29
Moved to Other OS/Distro Talk.

---

### Post by jampe on 2011-12-29
Fair enough :)

**Another update:**
This only happens on one of my machines, the Lenovo s10-3t. Could it be something with the touch screen?

---

### Post by anthropo on 2012-01-02
hello,

same problem here after an update of xbmc-live 

did you find a solution ?

thanks

---

### Post by jampe on 2012-01-02
Not really, although I did get it to run on Meego with the same machine. It's an elusive issue, because the error reports don't seem to even know about this major bug. It must be a segmentation fault, but there is just no immediate information on it :/

---

### Post by jose1711 on 2012-02-04
i am wondering if this [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/925747](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/925747) is a related bug. jose

---

### Post by legionovo on 2012-03-16
Hello,


I found a method that works for me. First, at the login screen, I chose xbmc session instead of gnome.
After that xbmc ran correctly. I changed the settings, full screen view to windowed mode. I logged back into gnome session, ran xbmc normally and changed again the display mode.

regards,
--
Gio

---

### Post by jampe on 2012-03-16
Yeah, I guess I should have mentioned that :P I stumbled upon that solution as well, completely by accident. It does make a lot more sense than starting it from within Gnome

---

### Post by surajit697 on 2012-04-20
Hello.
  I have no idea about XBMC, installed it for just giving it a try. My  desktop has **Natty 64-bit** with a **Raedon HD 6770** gpu. Now, after  installing it I rebooted the machine once and it was fine (dont know how  it happens).
  But after a 2nd reboot, I got the Xserver crash. Whenever I hit login  after givinig password to the graphical login screen it goes blank and  again returned me the same screen.
  My preferred session is Ubuntu Classic, I found there a XBMC session,  selected that and goes for login, but this also give me the same result.
  I need to get rid of that, I can uninstall the XBMC, but firstly will it  be totally removed and secondly, will it fix the problem, I mean will it  set the Xserver to the gdm environment and work fine?
 
 NB: The XBMC was running fine when my system was running. My graphics card does not have full length support with the  proprietary driver provided by ubuntu. Some games like superTux dont  give the full support with this card and that recommended driver.

---


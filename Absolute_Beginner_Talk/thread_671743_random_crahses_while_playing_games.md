---
title: "random crahses while playing games"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by smartalecks on 2008-01-18
Games such as Warsow will randomly crash while I am playing them. When I run it from the terminal when it crashes this is the error it outputs:

```

fish@jellyfish:~$ sh /home/me/.games/warsow/warsow

// Loads Maps

Using /home/me/.games/warsow for writing
Executing: default.cfg
Executing: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.
Hostname: me
IP: 127.0.1.1
Game running at 62 fps. Server transmit at 20 pps
Console initialized.
------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

----- R_Init -----
ref_gl version: GL 0.01
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
..Got colorbits 24, depthbits 24, stencilbits 0
800x600 -> 1680x1050: 450
800x600 -> 1280x1024: 424
800x600 -> 1280x960: 360
800x600 -> 1280x800: 200
800x600 -> 1152x864: 264
800x600 -> 1024x768: 168
800x600 -> 832x624: 24
800x600 -> 800x600: 0
800x600 -> 1680x1050: 450
800x600 -> 1600x1024: 424
800x600 -> 1440x900: 300
800x600 -> 1400x1050: 450
800x600 -> 1400x1050: 450
800x600 -> 1400x1050: 450
800x600 -> 1280x1024: 424
800x600 -> 1280x768: 168
800x600 -> 1280x720: 120
800x600 -> 1280x720: 120
800x600 -> 1152x768: 168
800x600 -> 1024x768: 168
800x600 -> 1024x768: 168
800x600 -> 960x600: 0
800x600 -> 800x600: 0
800x600 -> 800x600: 0
800x600 -> 800x600: 0
800x600 -> 800x600: 0
800x600 -> 800x600: 0
800x600 selected
...setting fullscreen mode 4:

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5500/AGP/SSE/3DNOW!
GL_VERSION: 2.1.1 NVIDIA 100.14.19
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_TEXTURE_UNITS: 4
GL_MAX_CUBE_MAP_TEXTURE_SIZE: 4096
GL_MAX_3D_TEXTURE_SIZE: 512

mode: 4, fullscreen
CDS: enabled
picmip: 0
texturemode: GL_LINEAR_MIPMAP_NEAREST
swap interval: disabled
compiled vertex array: enabled
multitexture: enabled
texture cube map: enabled
texture3D enabled
texenv add: enabled
texenv combine: enabled
texenv dot3: enabled
NVtexenv combine4: enabled
texture edge clamp: enabled
anisotropic filtering: disabled
compressed textures: disabled
draw range elements: enabled
BGRA byte order: enabled
----- finished R_Init -----
Unknown command "menu_main"
Opening UDP/IP socket: *:0

Initializing Shaders:

// Loads shaders

--------------------------------------

Closing SDL audio device...
SDL audio device shut down.
------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------
Checking for Warsow update.
Downloading warsow_last_version.txt from http://update.warsow.net/warsow_last_version.txt
Your Warsow version is up-to-date.
====== Warsow Initialized ======
pinging broadcast...

// Server List

Connecting to 208.100.47.70:44400...
208.100.47.70:44400: challenge 26997
208.100.47.70:44400: client_connect
Closing SDL audio device...
SDL audio device shut down.

------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

^1
^7wca1

Asking to download: sounds/announcer/score/team3_leads01.wav
Server refused download request: File not found
Asking to download: sounds/announcer/score/team3_leads02.wav
Server refused download request: File not found
Asking to download: sounds/announcer/score/team4_leads01.wav
Server refused download request: File not found
Asking to download: sounds/announcer/score/team4_leads02.wav
Server refused download request: File not found
Pure server. Restarting media...
Closing SDL audio device...
SDL audio device shut down.

------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------
me (no sound)^7 entered the game

// Gameplay

********************
ERROR: Received signal 6

********************
Closing SDL audio device...
SDL audio device shut down.
Received signal 6, exiting...

```

(at the bottom)
It seems to be some audio driver; recently the ALSA mixer was updated and it seemed to have fixed it, but now it is crashing again! I have updated a few times since then, though I don't remember updating anything that may have messed up something...

Any ideas?

---

### Post by Hospadar on 2008-01-18
it looks like it might be a server problem, with those messages about file not founds.  when exactly does it crash? only when joining servers? try turning the game sound off and see if that changes the issues.  do other games or audio apps have different effects?

---

### Post by smartalecks on 2008-01-18
It doesnt crash when it tries to load those sound files... I manage to play for, say, 10 minutes until it crashes. I've tried disabling the sound, but that does not work. 

Is there an update log, or something like that, in ubuntu?

---


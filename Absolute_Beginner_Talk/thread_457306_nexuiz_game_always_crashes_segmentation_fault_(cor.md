---
title: "nexuiz game always crashes: segmentation fault (core dumped"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-05-28
[FONT=Arial][COLOR=#000000]Hello,
I added nexuiz game into my 1 week new ubuntu system and it always crashes. Here is the terminal printout. Please help a newbie. Thank you.





-------------------Start of Printout--------------------------

~$ [/COLOR][COLOR=#000000]nexuiz
Console initialized.
Nexuiz Linux 23:49:57 Feb  7 2007
Trying to load library... "libz.so.1" - loaded. 
Compressed files support enabled
Added packfile /usr/share/games/nexuiz/data/data20070123.pk3 (2875 files)
Trying to load library... "libcurl.so.3" - loaded.
cURL support enabled
Initializing client 
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Starting video system
Video: fullscreen 800x600x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
checking for OpenGL 1.1.0...  enabled
GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
GL_VERSION: 1.3 Mesa 6.5.2
GL_EXTENSIONS: GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_MESAX_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotrop ic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod 
SDL_EXTENSIONS: 
Checking OpenGL extensions...
checking for glDrawRangeElements...  enabled
checking for GL_ARB_multitexture...  enabled
checking for GL_ARB_texture_env_combine...  enabled
checking for GL_ARB_texture_env_dot3...  enabled 
checking for GL_EXT_texture3D...  enabled
checking for GL_ARB_texture_cube_map...  enabled
checking for GL_ARB_texture_non_power_of_two...  not detected
checking for GL_EXT_compiled_vertex_array...  enabled
checking for GL_EXT_texture_edge_clamp...  enabled
checking for GL_EXT_texture_filter_anisotropic...  enabled
checking for GL_EXT_blend_minmax...  enabled
checking for GL_EXT_blend_subtract...  enabled
checking for GL_EXT_stencil_two_side...  not detected 
checking for GL_ARB_shader_objects...  not detected
0 SDL joystick(s) found:
OpenGL Backend starting...
glDrawRangeElements detected (max vertices 3000, max indices 3000)
multitexture detected: texture units = 8 
OpenGL backend started.
Trying to load library... "libjpeg.so.62" - loaded.
JPEG support enabled
Trying to load library... "libpng12.so.0" - loaded.
PNG support enabled
Draw_CachePic: failed to load gfx/complete 
Draw_CachePic: failed to load gfx/inter
Draw_CachePic: failed to load gfx/finale
SndSys_Init: using the SDL module
Sound format: 48000Hz, 2 channels, 16 bits per sample 
Found 1 cdrom drives.
No CD in drive 0. 
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Draw_CachePic: failed to load gfx/m_white
No CD in player.
Client using port 0
Client opened a socket on address local:2 
Client opened a socket on address [/COLOR][_[COLOR=#0000ff]0.0.0.0:32891[/COLOR]_]("http://0.0.0.0:32891/")
[COLOR=#000000]maps/aneurysm.bsp: could not load texture for missing shader "noshader"
maps/aneurysm.bsp: could not load texture for missing shader "textures/NULL" 
Server using port 26000
Server listening on address local:1
Server listening on address [/COLOR][_[COLOR=#0000ff]0.0.0.0:26000[/COLOR]_]("http://0.0.0.0:26000/")
[COLOR=#000000]Loaded maps/aneurysm.ent

Trying to connect...
"challenge ]Lc_2)+!d,#" received, sending connect request back to local:1 
Got challenge response
"challenge ]Lc_2)+!d,#" received, sending connect request back to local:1
Got challenge response
Accepted

Connection accepted to local:1
<-- server to client keepalive 

Server: Nexuiz build 23:49:57 Feb  7 2007 (progs 36690 crc)

<===================================>

Aneurysm
CDAudio: Bad track number 0.
Player entered the game
No CD in player.
autoswitch turned on 
Player is playing now
[BOT]Flatline drew first blood
[BOT]Paranoia was gunned by [BOT]Flatline
[BOT]Flatline was gunned by [BOT]Resurrection
Segmentation fault (core dumped)[/COLOR][/FONT]

---

### Post by Bachstelze on 2007-05-28
A segfault is the equivalent of a BSOD in Windows. It is most often caused by a bug in the software so try to contact the developpers of the game and/or file a bug report about it on [http://bugs.ubuntu.com](http://bugs.ubuntu.com)

---


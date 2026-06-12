---
title: "ATI-restricted, open, composite, direct rendering, compiz-fuzion, &amp; quake 3 confusion"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by jakelee on 2007-12-19
Been fighting with endless ATI / Ubuntu confusion since getting Ubuntu installed about 1.5 weeks ago now.  Lots of frustration comes from so much (seemingly) contradictory info being posted over long periods of time on misc. forums.  It's hard to know what is correct (or most correct) currently.

"you should use the opensource ATI drivers, they're better supported"
"no, you should use the restricted ATI drivers, they're faster"
"You need to have direct rendering=yes for compiz/fuzion effects to work properly"
"you DONT need to have direct rendering=yes for compiz/fuzion effects to work properly"

"The very recent new proprietary ATI drivers are really good now, with xxx support"
"The very recent new proprietary ATI drivers are still not very good, with xxx support"

etc...

What I have: ATI 9800pro, (I think) currently with the restricted drivers that were available via Ubuntu about 1.5 weeks ago.

As far as I can, after tweaking some things here and there (unfortunately didn't log/track what was done exactly), almost everything seems to work great.  All the desktop effects are running very well and extremely fast, movies play great, etc...  BUT:

I recently followed some simple instructions for installing quake3 on Ubuntu, and I got it to install seemingly fine, and it only 'sorta' works.  BY that I mean that it starts off fine with the intro and menu, but it goes kinda haywire when the '3D' game kicks in.  I can play, hear sounds, and make out some stuff, and it seems to run fast (framerate), but it's like all the textures are very badly distorted, as well as the in-game menus from that point on.  After I exit the game properly, if I try to relaunch it, I get a sort of crash, and then I have to relogin.

If I had to guess, this may all be likely due to this part(?):

glxinfo | grep direct
direct rendering=No

FWIW, Grid wars also doesn't work at all.

Here's the rest of the glxinfo:

name of display: :3.0
Xlib:  extension "XFree86-DRI" missing on display ":3.0".
display: :3  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

FWIW, the 'driver' info listed from within Quake3 is the same as "OpenGL version string" shown above: ATI 1.2 (2.0.6473 (8.37.6))

How to best go from here to (hopefully) retain the current desktop effect goodness while  also enabling direct rendering=yes,...if that is in fact likely causing the problems w/ quake3 and grid wars,...and possibly/likely many other 3D games that I'd want to install in the future.?

thanks much in advance!

---

### Post by approaching on 2007-12-19
i have a sapphire x1950, and have been privvy to those issues no doubt. it has really made me just not play games that much, but as a general case, that isn't an acceptable solution. i do know a few things that you should know that i have picked up.

the composite what-not doesn't play nice with full screen things. or pretty much games in general. i haven't gotten much working, but things get better when i do a metacity --replace to get rid of compiz. when you are done do a compiz --replace to get yer eye candy back. not a fantastic solution, but you can sure put that in a script i would imagine to do all that for you.

as far as the drivers go, i have no idea, but the new one (fglrx) is a hell of a lot better than the old fglrx. i kinda got over screwing myself by messing with all of these different things, that once i got something to work, i didn't touch anything. but then again, i don't game much, so that is just fine for me, the 3d is handled for screen savers by gl, and the compiz is handled just fine, and video works. So even though i hate that fglrx with a passion (it still is by no means fantastic), things do in fact work. besides the maximizing to both monitors instead of one like a sane person, which for some reason on some x system restart decides to do what it is supposed to and maximize to one... Totally can't vouch for the open source driver though, haven't tried it out. if it works out for you let me know.

i have also even heard of something besides the glx, i may be mistaken, but it's worth looking into.

BTW i have totally been waiting for one of my friends to want to trade my card for their not so good nvidia.

---

### Post by jakelee on 2007-12-19
Hey, thanks for the nice reply.  Unless somebody cimes in with a better suggestion, I'm going to experiment with backing up my existing Ubuntu install now that it's (seemingly) so close to being how I want everything, and then probably dive in and see if I can't figure out how to manage everything all over again using the open-source ATI drivers, and see how the games work with the 'direct' = yes hopefully properly enabled.

Just my luck,...I'll go through all that only to find out that Quake 3 is running, yet with very odd graphics for some completely unrelated reason :(

Speaking of your last comment,...I actually meant to include the final question:,...are all of my above concerns and confusion pretty much a moot point when using an nvidia card/driver?

Maybe it's worth trying to, at least temporarily, disable all the compiz-fuzion stuff, and then see if Quake3 runs more normally?  Too many variables to juggle :(

I just have no idea what actual tangible side-effect(s) to expect by that disturbing line: "Direct Rendering = No"  Does that even have the slightest thing to do with the Quake3 engine displaying textures properly? :::shrug::::  Seems likely, judging by the wording, but who knows for sure?

---

### Post by approaching on 2007-12-19
i don't know about backing up the entire install. i mean, it's not a bad idea, but for what you are doing it's overkill. just do this:

cp /etc/X11/xorg.conf{,.bak}

that copies what you have now as your xorg.conf (everything graphics related and more, very important, make sure you are confident in moving that file to replacing your messed up one if you screw something up. then you should just be able to restart x. and better yet, well not better, just more brute force is doing a dpkg -reconfigure, but make sure you look up that command and write it down. (if you need it, you won't have a browser to get it...).

replacing compiz with metacity isn't going to break anything. but back up your xorg.conf first.

pretty sure that the nvidia is pretty much a non-issue when it comes to linux, but make sure you look up your specific make and model of that card before you get to spending money thinking it will solve all of your problems.

there should be some kind of default button to set all of the graphics options to default in quake 3. if that is messed up, then i doubt that quake is the problem.

---


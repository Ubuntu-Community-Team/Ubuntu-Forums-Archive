---
title: "[SOLVED] Compiz wont anable."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-17
I was having problems with my video card but i seem to have it fixed. Here is the thread if you want to see what i was dealing with...

[http://ubuntuforums.org/showthread.php?t=697959]("http://ubuntuforums.org/showthread.php?t=697959")

the restricted driver manager says its enabled and in use.



Now when i go to enable my desktop effects i get this...

"The Composite extension is not available"

Im not sure if my card still isnt working or if there is a compiz problem so i just started a new thread.


I have tried a few simple things, but again I have reached the extent to my knowledge.

---

### Post by jan quark on 2008-02-17
install this package

```
sudo apt-get install xserver-xgl
```

log out and select xclient session 
and try to enable compiz one more time

---

### Post by Joeb454 on 2008-02-17
Well what have you tried? And what make/model is your video card?

---

### Post by sb12 on 2008-02-17
> **LostMagix said:**
> I was having problems with my video card but i seem to have it fixed. Here is the thread if you want to see what i was dealing with...

[http://ubuntuforums.org/showthread.php?t=697959]("http://ubuntuforums.org/showthread.php?t=697959")

the restricted driver manager says its enabled and in use.



Now when i go to enable my desktop effects i get this...

"The Composite extension is not available"

Im not sure if my card still isnt working or if there is a compiz problem so i just started a new thread.


I have tried a few simple things, but again I have reached the extent to my knowledge.

you need a section that looks like this in xorg.conf:

Section "Extensions"
        Option  "Composite"     "Enable"
 EndSection

you should have the section already just add the Option line

---

### Post by LostMagix on 2008-02-17
For the card i have been focising on these two...

[http://combatwombat.7doves.com/index.php/2007/10/31/gutsy_effort_in_new_ati_driver]("http://combatwombat.7doves.com/index.php/2007/10/31/gutsy_effort_in_new_ati_driver")

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

AIT randoen 9550

There are a few other things i tryed that are in the thread I posted.

I useing sudo apt-get install xserver-xgl right now

---

### Post by LostMagix on 2008-02-17
Now im getting..

"Desktop effects could not be enabled"

so that helped to a point.

---

### Post by jan quark on 2008-02-17
do you have changed the session to xclient during login?

---

### Post by LostMagix on 2008-02-17
Nope

---

### Post by jan quark on 2008-02-17
do so and try again

---

### Post by LostMagix on 2008-02-17
???

I think we had a breakdown in communication somewhere, are you talking about the screen you get at login when you video driver isnt right and it says something like

"xsession needs configured"

---

### Post by jan quark on 2008-02-17
hmm I meant here

[http://farm3.static.flickr.com/2129/1657633031_7ac0a7ae04.jpg](http://farm3.static.flickr.com/2129/1657633031_7ac0a7ae04.jpg)

left bottom corner

---

### Post by LostMagix on 2008-02-17
oooo

my bad, i have it set to skip the login screen so i didnt think about that.

ill give it a try.

---

### Post by LostMagix on 2008-02-17
No good.

---

### Post by LostMagix on 2008-02-17
Why does it always seem i get these overly complicated problems.

---

### Post by LostMagix on 2008-02-17
So where do you think the problem is, compiz, the config files or the video card.

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by Mjölner on 2008-02-17
did you Go into your xorg.conf file and change the "Section "Extensions" Options"?

If you didn't go to etc/X11/xorg.conf

And right at the end you get something like this...

[PHP]EndSection
Section "Extensions"
	Option		"Composite"	"on"
EndSection[/PHP]

You see mine has got the option "on" there. you need that too :)

Hope this helps

---

### Post by LostMagix on 2008-02-17
yep

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
I just thought about running compiz in the terminal. I got this...

```
chris@LostMagix:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

So i ran this...

```
chris@LostMagix:~$ cd /usr/local/bin/compiz
bash: cd: /usr/local/bin/compiz: No such file or directory

```

why wouldn't it make that file when i installed it compiz and its components via synaptic package manager?

---

### Post by Crafty Kisses on 2008-02-17
> **LostMagix said:**
> I was having problems with my video card but i seem to have it fixed. Here is the thread if you want to see what i was dealing with...

[http://ubuntuforums.org/showthread.php?t=697959]("http://ubuntuforums.org/showthread.php?t=697959")

the restricted driver manager says its enabled and in use.



Now when i go to enable my desktop effects i get this...

"The Composite extension is not available"

Im not sure if my card still isnt working or if there is a compiz problem so i just started a new thread.


I have tried a few simple things, but again I have reached the extent to my knowledge.
Post the following output: ```
glxinfo
```

---

### Post by LostMagix on 2008-02-17
```
root@LostMagix:~# glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
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
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
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
root@LostMagix:~# 


```

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
So what would "LIBGL_DEBUG=verbose" do?

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
*bump

---

### Post by LostMagix on 2008-02-17
I have to get this fixed TONIGHT!!!

Im running out of time here, I have exhausted all my resources, I dont know what else to do!!

---

### Post by DonDodge on 2008-02-17
What is so earthshakingly important about desktop effects? Jeez, give yourself a break from it.

---

### Post by LostMagix on 2008-02-17
If you dont have anything to say pertaining to the subject of the thread, dont post.

Im going away for 9-12 months, I will have no internet. I want everything working as it should.

---

### Post by LostMagix on 2008-02-18
bump

---

### Post by LostMagix on 2008-02-18
*bump

---

### Post by LostMagix on 2008-02-18
bump

---

### Post by LostMagix on 2008-02-18
Can someone at least tell me what this last line is?

```
chris@LostMagix:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

Why is the file not there??

---

### Post by jan quark on 2008-02-18
there are hints that this error occurs with the latest 7.12 ati drivers

but it works with the 7.11 ati drivers

what drivers do you use?

I use the restricted drivers xorg-driver-fglrx and have no issues whatsoever

---

### Post by LostMagix on 2008-02-18
I just figured it out, it was the latest Compiz.

I found the fix here...

[http://ubuntuforums.org/showthread.php?t=585252]("http://ubuntuforums.org/showthread.php?t=585252")


> **smcintyre said:**
> I had this message after upgrading to ATI fglrx 7.12.
This fixed it:

change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)

Before, these lines said:
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/"
...
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real)

Hope this helps.


It worked perfect.

---

### Post by jan quark on 2008-02-18
but i think you will have to change these lines after every update of compiz so beware :)

---

### Post by LostMagix on 2008-02-18
This should be my last update for a long time. Im not to worried about it.

---


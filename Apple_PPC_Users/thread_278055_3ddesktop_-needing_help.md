---
title: "3ddesktop -needing help"
date: 2006-10-15
forum: Apple PPC Users
---

### Post by macminiuser on 2006-10-15
I own a nonintel 1.4ghz mac mini 512 megs ram which is running ubuntu 6.06  
I am having trouble getting 3ddesktop to run.
I will run 3ddesk in a terminal and all I get is a gray screen?

anyone out there can help?

I think it comes with a ati radeon 9200 32meg ram

---

### Post by oswaldkelso on 2006-11-10
Hi I am running an emac 1 ghz G4 (oc to 1.33) with an ati 7500 graphics card. Its tri boot osx, ubuntu and debian both etch. I did the same install on ubuntu and debian but so far only debian is working (slowly!). I fixed the gray screen in debian with 

code 

3ddesk --acquired

i think!!!

anyway

code

3ddesk --help


will get you on your way 

 
and here is my 3ddesktop.conf file it goes in the hidden .3ddesktop directory in your home folder.

also see this link.

[http://ubuntuforums.org/showthread.php?t=22095&highlight=3ddesk](http://ubuntuforums.org/showthread.php?t=22095&highlight=3ddesk)


# 3ddesktop configuration
#
# Use this file to set various "views".
#
# Format:
#   view     <viewname1>
#   option1  <value1>
#   option2  <value2>
#   ...
#
#   view     <viewname2>
#   option1  <value1>
#   option2  <value2>
#   ... 
#   etc
#

#
# Global options (effect every view and program as whole)
# 
#   wm          - Specify which window manager you are using.  Options are:
#
#                    kde2, kde3, gnome1, gnome2, ewmh, fluxbox, windowmaker, 
#                    enlightenment, sawfishonly, workspaces
#
#                 The default should work for Gnome 1.x/2.x, Kde 3.x, Windowmaker, &
#                 Enlightenment but use wm for kde2, fluxbox or workspaces.
#
    texturesize 256
#   texturesize          - resolution of textures (power of 2, as in 128, 256, 512, 1024)
#                          default 1024
#   win                  - open in a window rather then fullscreen 
#                          (for debuggin: not really usable at this time)
#   early_desktop_switch - When desktop is switched (default true)
#   disable_keys_in_goto - Disable keys while in an automated "goto" (default true)
#   compression          - enables texture compression, not all cards support it
  autoacquire 0
#   autoacquire          - Set the number of seconds between screen captures by the server
#                          zero to disable
    fastest
#   fastest              - hog CPU for smooth movement
#   priority             - set the nice value of the server (default is 12)
#   default_background   - image to display in the background (512x512 BMP)
#   default_background_texturesize - res of bg texture (power of 2, as in 128, 256, 512, 1024)
#   screen_width         - Width of screen to affect
#   screen_height        - Height of screen to affect
#   keybinding_{left|right|up|down|select}   
#                        - Bind a keysym to left, right, up, down or select actions.
#   mousebinding_{left|right|up|down|select} 
#                        - Bind a mouse button to left, right, up, down or select actions.
#                        - (Specify bindings as X KeySyms e.g 'n' is 0x6e, 'tab' is 0xff09, 
#                           'f1' is 0xffbe, etc)
#
# Examples (uncomment to use)
#

#texturesize 512

wm          fluxbox


#
# Indicate which "view" to use on the command line with --view=<viewname>.
# Other options on the command line are ignored if a view is given.
#
# Options  (all must be lowercase)
#
    mode  carousel
#                 
#   mode        - set the "arrangement", one of carousel (default), linear,
#                 cylinder, viewmaster, carousel, priceisright, flip

#   show_digit  - show a digit indicating the current desktop/workspace
#   digit_size  - width of digit on screen
#   digit_color - color of digit (red, green, blue, lightblue, white, gray, 
#                 purple, yellow)
#   frame_color - color of un-cached desktops (the frame)
#   use_wireframe - if true draw a wireframe for uncached faces (default true)
#   randdelay   - delay before random movement (zero for no movement)
    
#   zoom        - set to one or zero to zoom out or not to zoom out 
#                 (default is zoom out).
#   nozoom      - set to zero or one to zoom out or not to zoom out 
#                 (default is zoom out).
#   depth       - how far to "zoom-out"
#   gotoright   - goto desktop to the right 
#   gotoleft    - goto desktop to the left 
#   gotoup      - goto desktop above 
#   gotodown    - goto desktop below 
#   gotocolumn  - goto desktop to the specified column
#   gotorow     - goto desktop to the specified row
#   dontexit    - don't exit after an automated goto operation
#   linear_spacing  - space between desktops in "linear" mode (default 2.0)
#   use_breathing   - turn on/off the ambient light dimming
#   animation_speed - number of milliseconds between animation steps
#   changespeed     - how fast the rotation or sliding of faces takes
#   zoomspeed       - how fast it zooms in and out from start
    reverse_mousewheel
#   reverse_mousewheel - mouse wheel up and down reversion
#   swap_mousebuttons  - swap left and right buttons on mouse
    alt_mousebuttons
#   alt_mousebuttons   - mouse button 1 activates, 2 goes back and exits,
#                        3 goes back, 6 goes left, 7 goes right.

#
# Example views (use by doing: '3ddesk --view=<viewname>')
#

view         default    ## this is the default if no --view specified
zoom         on
show_digit   on
digit_size   100
digit_color  green
use_breathing false


view         goright
zoom         on
mode         cylinder
gotoright    on


view         goleft
zoom         on
mode         cylinder
gotoleft     on


view         slide
zoom         on
mode         linear
digit_size   100
digit_color  gray
linear_spacing 0.0


view         nozoom
zoom         on
mode         viewmaster
digit_size   100
digit_color  gray


view         linear
mode         linear
digit_color  yellow
linear_spacing 0.0


view         linearzip
mode         linear
linear_spacing 19.0
depth        5
digit_size   200
digit_color  blue


view         bigmoney
mode         priceisright
depth        10
digit_color  purple
digit_size   150

#############################################

hope it helps.

If anyone is reading this thread and knows why 3ddesk work great on the "flip"  setting but laggs on others. **only** if all four desktops have been populated with a window.

3 windows and it flies.

ps set the wm bit to what ever wm you use, my config file is set to fluxbox but worked fine with gnome also.

---

### Post by oswaldkelso on 2006-11-11
My problem seems to have fixed its self. Its working fine even with eight workspaces in "carousel" the only thing I can think Ive done is when starting populate each workspace inturn. My procedure is:

login
populate each workspace as normal
start up 3ddesk. (With my setting this gives me a populated start workspace in the  "carousel" with the rest empty.)
visit each workspace in the "carousel"

What I have noticed is that switching wm can break it! untill a restart.

---

### Post by Torrance on 2006-11-11
I thought 3ddesktop requires 3D drivers... where'd you get 3D drivers for PPC??? 

I have an Nvidia card... and am waiting anxiously for the Nouveau project to deliver on a oss 3d driver. *fingers crossed*

---

### Post by APU on 2006-11-11
Well they are talking about ATI equipped Macs. You can find free and open ATI drivers, especially for these rather old cards.

I am also waiting for Nouveau to be able to use Ubuntu on my Powerbook. Right now I run it on a Mac mini which has a fully supported graphics card (ATI 9200SE). I did not yet try to use a 3D Desktop though!

---


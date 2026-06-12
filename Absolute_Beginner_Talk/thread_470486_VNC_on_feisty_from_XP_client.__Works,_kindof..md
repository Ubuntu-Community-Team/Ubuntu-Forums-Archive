---
title: "VNC on feisty from XP client.  Works, kindof."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ethos101 on 2007-06-11
I have set up VNC server in feisty on my home box.  I also installed tightVNC and realVNC on my laptop to remotely access.  I can successfully log in via my network.  My problem is this:  I can pull up a window, like firefox or home folder, and see it come up at the server but the client doesn't show it come up until I close the VNC app and reconnect.  Then I see firefox or whatever.  Then I close it and it closes on the server but the client doesn't change... until I restart the client.  I'm not sure what is going on here.

---

### Post by alanandhispc on 2007-06-11
one issue i have with vnc-ing to any machines from fiesty (well windows anyway), if the resolution is bigger than the one on my pc, i can scroll down or to the right to see the remainder of the screen, but i can't scroll back to the top or the left.

the only way to see the left/top is to close vnc down and re-open it



Alan

---

### Post by scottvan on 2007-06-11
> **ethos101 said:**
> I have set up VNC server in feisty on my home box.  I also installed tightVNC and realVNC on my laptop to remotely access.  I can successfully log in via my network.  My problem is this:  I can pull up a window, like firefox or home folder, and see it come up at the server but the client doesn't show it come up until I close the VNC app and reconnect.  Then I see firefox or whatever.  Then I close it and it closes on the server but the client doesn't change... until I restart the client.  I'm not sure what is going on here.
I think I kind of have the same problem you do.  I can start vnc from system B (Feisty) to control system A (also Feisty).  On system B, I can move the mouse around and see it moving around and interacting on system A.  On system B, the mouse moves around, but I only see a frozen snapshot of system A when I started vnc.  The viewer on system B does not show what is happening on system A, although I can control system A from system B.  Does that make sense?  It's like a static wallpaper that never changes.  Can anyone help?

---

### Post by lazyart on 2007-06-11
This is an issue with the included vino and Beryl/Compiz.

Install X11VNC from the repositories.

Go to System>Preferences>Sessions and remove vino as a startup program.
Add *x11vnc -forever* in it's place.
Restart X (Ctrl-Alt-Backsp) or reboot.
Log in, then try to access remotely.  This should fix it.

If you get the same thing, add :1 to the computer name when you vnc from another machine.

---

### Post by scottvan on 2007-06-11
> **lazyart said:**
> This is an issue with the included vino and Beryl/Compiz.

Install X11VNC from the repositories.

Go to System>Preferences>Sessions and remove vino as a startup program.
Add *x11vnc -forever* in it's place.
Restart X (Ctrl-Alt-Backsp) or reboot.
Log in, then try to access remotely.  This should fix it.

If you get the same thing, add :1 to the computer name when you vnc from another machine.
Thanks for the quick reply!  

It still does not work.  I installed X11VNC, and went to remove Vino from Session startup, but Vino wasn't there.  I added *X11vnc -forever* and logged out and logged back in.  No change, I get the same frozen picture of my desktop at home.  I changed :0 to :1, it shows the copyright info but just hangs, never asking for my password.  Do I need to install X11vnc on the server computer too?

---

### Post by lazyart on 2007-06-11
x11vnc goes on the machine you are trying to connect to.  Try running it from command line and see if you get any messages.

---

### Post by lazyart on 2007-06-11
I dropped the ball here:```
x11vnc -noxdamage -forever
```is the correct command in your sessions.  noxdamage lets you see the screen update w/beryl, forever tells it not to terminate after the connection closes.

---

### Post by krunge on 2007-06-11
This may be due to a bug in Xorg/XDAMAGE for eye-candy window managers like beryl that use openGL.  Is that your case?  [http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

No one seems to be fixing this bug... (record your case if you want to).

If you are using x11vnc as your VNC server, you can use the -noxdamage option as a workaround.  Otherwise, perhaps disabling XDAMAGE in your xorg.conf will also provide a workaround.

Apologies that this repeats some of the info in the previous posts.

---

### Post by ethos101 on 2007-06-11
Awsome!  Thanks for the reply guys.  I'll give it a shot when I get home.

---

### Post by scottvan on 2007-06-11
> **lazyart said:**
> x11vnc goes on the machine you are trying to connect to.  Try running it from command line and see if you get any messages.
Thanks again, I'll give that a try when I get home.

---

### Post by ethos101 on 2007-06-11
Okay, it's not working for me.

I didn't have any "vino" in my startup...

I installed x11vnc and add to sessions startup: "x11vnc -noxdamage -forever"

When I try "my-desktop" I'm getting the same window update problem.
When I try "my-desktop:1" it gives me "Status: No authentication needed."  And theres a HIDE button but nothing else.

I don't have xdamage in my xorg.conf.  How do I go about disabling it there?

---

### Post by lazyart on 2007-06-11
run x11vnc -noxdamage from your command line and post the output.

---

### Post by ethos101 on 2007-06-11
```
Settings:
 display:    null
 authfile:   null
 subwin:     0x0
 -sid mode:  0
 clip:       null
 flashcmap:  0
 shiftcmap:  0
 force_idx:  0
 cmap8to24:  0
 8to24_opts: null
 24to32:     0
 visual:     null
 overlay:    0
 ovl_cursor: 1
 scaling:    0 1.0000
 viewonly:   0
 shared:     0
 conn_once:  1
 timeout:    0
 inetd:      0
 filexfer:   1
 http:       0
 connect:    null
 connectfile null
 vnc_conn:   1
 allow:      null
 input:      null
 passfile:   null
 unixpw:     0
 unixpw_lst: null
 stunnel:    0
 accept:     null
 accept:     null
 gone:       null
 users:      null
 using_shm:  1
 flipbytes:  0
 onetile:    0
 solid:      null
 blackout:   null
 xinerama:   1
 xtrap:      0
 xrandr:     0
 xrandrmode: null
 padgeom:    null
 logfile:    null
 logappend:  0
 flag:       null
 rc_file:    ""
 norc:       0
 dbg:        0
 bg:         0
 mod_tweak:  1
 isolevel3:  0
 xkb:        0
 skipkeys:   null
 sloppykeys: 0
 skip_dups:  0
 addkeysyms: 1
 xkbcompat:  0
 clearmods:  0
 remap:      null
 norepeat:   1
 norepeatcnt:2
 nofb:       0
 watchbell:  1
 watchsel:   1
 watchprim:  1
 seldir:     null
 cursor:     1
 multicurs:  0
 curs_mode:  null
 arrow:      1
 xfixes:     1
 alphacut:   240
 alphafrac:  0.33
 alpharemove:0
 alphablend: 1
 cursorshape:1
 cursorpos:  1
 xwarpptr:   0
 buttonmap:  null
 dragging:   1
 wireframe:  0xff,3,0,32+8+8+8,all,0.15+0.30+5.0+0.125
 wirecopy:   always
 scrollcopy: always
  scr_area:  60000
  scr_skip:  ##Soffice.bin,##StarOffice
  scr_inc:   ##Nomatch
  scr_keys:  null
  scr_term:  null
  scr_keyrep: null
  scr_parms: 0+64+32+32,0.02+0.10+0.9,0.03+0.06+0.5+0.1+5.0
 fixscreen:  null
 noxrecord:  0
 grabbuster: 0
 ptr_mode:   2
 inputskip:  10
 speeds:     null
 wmdt:       null
 debug_ptr:  0
 debug_key:  0
 defer:      30
 waitms:     30
 wait_ui:    2.00
 nowait_bog: 0
 slow_fb:    0.00
 readtimeout: 20
 take_naps:  1
 sb:         60
 fbpm:       1
 xdamage:    0
  xd_area:   20000
  xd_mem:    1.000
 sigpipe:    null
 threads:    0
 fs_frac:    0.75
 gaps_fill:  4
 grow_fill:  3
 tile_fuzz:  2
 snapfb:     0
 rawfb:      null
 pipeinput:  null
 gui:        0
 gui_mode:   null
 noremote:   0
 unsafe:     0
 privremote: 0
 safer:      0
 nocmds:     0
 deny_all:   0
 pid:        5803

11/06/2007 20:06:43 x11vnc version: 0.8.2 lastmod: 2006-07-12
11/06/2007 20:06:43 Using X display :0.0
11/06/2007 20:06:43 
11/06/2007 20:06:43 ------------------ USEFUL INFORMATION ------------------
11/06/2007 20:06:43 Wireframing: -wireframe mode is in effect for window moves.
11/06/2007 20:06:43   If this yields undesired behavior (poor response, painting
11/06/2007 20:06:43   errors, etc) it may be disabled:
11/06/2007 20:06:43    - use '-nowf' to disable wireframing completely.
11/06/2007 20:06:43    - use '-nowcr' to disable the Copy Rectangle after the
11/06/2007 20:06:43      moved window is released in the new position.
11/06/2007 20:06:43   Also see the -help entry for tuning parameters.
11/06/2007 20:06:43   You can press 3 Alt_L's (Left "Alt" key) in a row to 
11/06/2007 20:06:43   repaint the screen, also see the -fixscreen option for
11/06/2007 20:06:43   periodic repaints.
11/06/2007 20:06:43 XFIXES available on display, resetting cursor mode
11/06/2007 20:06:43   to: '-cursor most'.
11/06/2007 20:06:43   to disable this behavior use: '-cursor arrow'
11/06/2007 20:06:43   or '-noxfixes'.
11/06/2007 20:06:43 using XFIXES for cursor drawing.
11/06/2007 20:06:43 GrabServer control via XTEST.
Xlib:  extension "RECORD" missing on display ":0.0".
11/06/2007 20:06:43 XKEYBOARD: all 28 "must have" keysyms accounted for.
11/06/2007 20:06:43   Not automatically switching to -xkb mode.
11/06/2007 20:06:43   If some keys still cannot be typed, try using -xkb.
11/06/2007 20:06:43   Also, remember "-remap DEAD" for accenting characters.
11/06/2007 20:06:43 X FBPM extension not supported.
11/06/2007 20:06:43 --------------------------------------------------------
11/06/2007 20:06:43 
11/06/2007 20:06:43 Default visual ID: 0x21
11/06/2007 20:06:43 Read initial data from X display into framebuffer.
11/06/2007 20:06:43 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5120
11/06/2007 20:06:43 
11/06/2007 20:06:43 X display :0.0 is 32bpp depth=24 true color

FrameBuffer Info:
 width:            1280
 height:           1024
 scaled_width:     1280
 scaled_height:    1024
 indexed_color:    0
 bits_per_pixel:   32
 depth:            24
 red_mask:   0x00ff0000  00000000111111110000000000000000
 green_mask: 0x0000ff00  00000000000000001111111100000000
 blue_mask:  0x000000ff  00000000000000000000000011111111
 red:   max: 255  shift: 16
 green: max: 255  shift:  8
 blue:  max: 255  shift:  0
 mainfb_bytes_per_line: 5120
 rfb_fb_bytes_per_line: 5120
 format:     ZPixmap
 byte_order: LSBFirst
 bitmap_pad:  32
 bitmap_unit: 32
 bitmap_bit_order: LSBFirst
 rfb_fb:      0xb77a9008
 main_fb:     0xb77a9008
 8to24_fb:    (nil)
 snap_fb:     (nil)
 raw_fb:      (nil)
 fake_fb:     (nil)

11/06/2007 20:06:44 setting up 32 cursors...
11/06/2007 20:06:44   done.
11/06/2007 20:06:44 
11/06/2007 20:06:44 Autoprobing TCP port 
11/06/2007 20:06:44 Autoprobing selected port 5902
11/06/2007 20:06:44 Xinerama: disabling: display does not support it.
11/06/2007 20:06:44 created 40 tile_row shm polling images.
11/06/2007 20:06:44 fb read rate: 309 MB/sec
11/06/2007 20:06:44 screen setup finished.
11/06/2007 20:06:44 
11/06/2007 20:06:44 WARNING: You are running x11vnc WITHOUT a password.  See
11/06/2007 20:06:44 WARNING: the warning message printed above for more info.
11/06/2007 20:06:44 
The VNC desktop is:      ethos-desktop:2
PORT=5902


```

---

### Post by lazyart on 2007-06-11
If you havent killed that terminal window, try connecting :2.  If you have killed it, run it again and connect on :2 (or whatever number it gives you at the end).  You are not trying with a password right now, are you?

---

### Post by ethos101 on 2007-06-12
Yeah, I'm using a password.  Shouldn't I?

I tried :2 before with the same result:  Hangs at:  No authentication needed.

Lemme try without.  Same thing.  I get the initial screen but if I open something it shows up on the server but not on the client.  I can watch the mouse move around but nothing changes on the client until I close and re-open it.

It works perfect if I disable beryl.  But thats no dang fun.  I wanted to show off beryl at work since my laptop doesn't support beryl but my desktop does.

---

### Post by scottvan on 2007-06-12
The -noxdamage solved the problem, thanks again for your help!

---

### Post by lazyart on 2007-06-12
> **ethos101 said:**
> Yeah, I'm using a password.  Shouldn't I?

I tried :2 before with the same result:  Hangs at:  No authentication needed.

Lemme try without.  Same thing.  I get the initial screen but if I open something it shows up on the server but not on the client.  I can watch the mouse move around but nothing changes on the client until I close and re-open it.

It works perfect if I disable beryl.  But thats no dang fun.  I wanted to show off beryl at work since my laptop doesn't support beryl but my desktop does.

For the moment we haven't set a password and that is why you're getting the authentication message... so we are almost there.```
x11vnc -noxdamage -forever -passwd *password*
``` is what you need in your Sessions >Startup Programs

Let's also make sure vino stops running by going to System>Preferences>Remote Desktop and killing off Sharing.

Now reboot (or just restart X with Ctrl-Alt Backsp) and log in.  You should be able to connect on :0 using the password you specified.

---

### Post by ethos101 on 2007-06-12
K, gotta go to work.  I'll try that when I get home.

Thanks again for the speedy reply.  You tha man!  lol

---

### Post by ethos101 on 2007-06-13
IT WORKS!  Cool man thanks for the help.

So just to be sure I know what happened:  I assume Vino is the built in remote desktop service in feisty.  Killing off sharing disabled it?  I didn't see it in sessions>startup but I'm guessing I wouldn't.  Will there be a GUI for x11vnc?

Forgive my noobness.  :D

Now to get this thing to work outside of my LAN...

---

### Post by lazyart on 2007-06-13
Havent seen a gui for it. :(

As for getting it to work outside of the lan, you'll need a dynamic dns provider, a dyndns client installed on your machine, the machine assigned to a static ip (internally) and the necessary port (5900) forwarded from your router to the target machine.

There has got to be a howto on this somewhere because it's a pretty common thing to do. If not I can make one.

---

### Post by ethos101 on 2007-06-13
Already done.  Just gotta try it out from work.  :)

Thanks again.
edit...

Works like a charm.

---


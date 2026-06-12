---
title: "Easy way to output to S-video and VGA in U7.10?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-10-17
I read somewhere that U7.10 has an 'easy' way to enable svideo out and VGA out on external TV/monitors. Is this rue? If so, which program is that?

---

### Post by Beggar on 2007-10-18
System->Administration->Screen and Graphics

---

### Post by the8thstar on 2007-10-18
That must be a joke... what a lousy non user friendly panel. I tried it and it fried my config. I had to reinstall Ubuntu. 

Both thumbs down on this piece of crap!!!:mad::mad::mad::mad:

---

### Post by disposition on 2007-10-18
> **Beggar said:**
> System->Administration->Screen and Graphics

This still doesn't allow me to output via S-Video.

---

### Post by the8thstar on 2007-10-18
Yep, another experimental science project...

---

### Post by adamorjames on 2007-10-18
I think, in the terminal type xrandr --auto
Make sure you are plugged in.

---

### Post by the8thstar on 2007-10-21
I've got a bad feeling about this... I don't see any options for S-video there:

> 
root@Ubuntu:/home/the8thstar# xrandr --help
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --off
      --crtc <crtc>
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

---

### Post by mLoke on 2007-10-22
I had little success in configuring S-Video TV-out from my Dell Vostro with GeForce 8400M GS.

System > Administration > Screen and Graphics
Enabled Screen 2 as extended desktop with different resolution than screen 1
Restarted X (logout/login)

Both screens were on but had a much lower resolution than the ones set. No amount of GUI changes and X restarts could get it to work or even restore back to my previous working single screen setup. At least X didn't break completely.

The interesting thing is that the "Screen and Graphics" screen detect did a worse job than the detection process used during installation. =\

In the end I had to restore an old version of xorg.conf via console. I suppose a recommendation would be to save the profile/location in "Screen and Graphics" before fiddling so you could restore your working settings.

---

### Post by adamorjames on 2007-10-22
> **the8thstar said:**
> I've got a bad feeling about this... I don't see any options for S-video there:

Just try xrandr --auto :guitar: It worked for me.

---

### Post by the8thstar on 2007-11-01
It does work... but it does nothing at all.

---

### Post by neekz on 2007-11-01
xrandr --auto didn't do anything for me do I have to reboot?? My problem was that with everything I tried I couldn't get my tv to display video.

---

### Post by Inxsible on 2007-11-01
you have to use the settings for your individual card.

if you are using Nvidia cards then type in ```
gksudo nvidia-settings
```

if you are using ATI, you have to use the ATI config to set it up.

---

### Post by adamorjames on 2007-11-01
> **the8thstar said:**
> It does work... but it does nothing at all.

Hmm, works for me. I connect and type xrandr --auto.

---

### Post by the8thstar on 2007-11-02
Well, good for you adamorjames.

Is there an equivalent of the nvidia settings for the Intel chipset?

---

### Post by adamorjames on 2007-11-02
Interesting I use Intel too.

---

### Post by mgmiller on 2007-11-02
I don't know about Intel video, but I have used ATI s-video out and unless the tv is connected to the video card and turned on prior to booting, the card won't detect the TV and will disable the port.

I guess what I'm saying is, shut down, turn on the TV with it conned to the s-video port and restart.

Also, make sure the TV is set to display video from the s-video in.  (Should be obvious, but, hey, you never know.)

---

### Post by the8thstar on 2007-11-11
Thanks **MgMiller** but it still doesn't work.

---

### Post by the8thstar on 2008-02-03
bump. 

Do I need to edit my xorg.conf file?

---


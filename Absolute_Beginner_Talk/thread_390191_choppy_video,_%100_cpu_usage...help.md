---
title: "choppy video, %100 cpu usage...help"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by farscape on 2007-03-21
Playing videos with any player is choppy. Very choppy. Unwatchable. Tried with Mplayer, real player, VLC and Movie player. I installed the Nvidia drivers through EASY UBUNTU. System monitor shows CPU usage at %100 percent when playing a video, opening any kind of window or program. Even streaming music from another machine seemed to hiccup every once in a awhile.
Where do I start on this problem. 

Machine:
CPU: 1.4Ghz Duron
RAM: 512Mb
Video: e-GeForce MX 4000 128Mb DDR (PCI card, not PCI express)
MB: PC Chips M810D series

---

### Post by raul_ on 2007-03-21
Using Beryl?

---

### Post by arochester on 2007-03-21
Have a look at "Fix jumpy/skipping/choppy/stuttering CD/DVD playback" on [http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma](http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma)

---

### Post by farscape on 2007-03-21
> **raul_ said:**
> Using Beryl?

Nope.

[QUOTE=arochester]Have a look at "Fix jumpy/skipping/choppy/stuttering CD/DVD playback" on [http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma](http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma)[/QUOTE]

I'll have a look see.

---

### Post by punx45 on 2007-03-21
have you installed the proprietary nvidia driver?   the system may be resorting to software decoding (big processor usage) rather than hardware decoding.   so replacing the 'nv' driver with the 'nvidia' driver may help.

search the forums for instructions, or the "envy" script which will do the dirty work for you.   do make sure your card is supported too.


streaming networked music is another issue entirely.   are the videos over the network too?  if they are then maybe it is just network issues.

---

### Post by farscape on 2007-03-21
The vidoes I'm trying to play are on the hard drive. AVI's. Yes, DMA is on for the hard drive. I also installed the codecs from easy ubuntu also. These mulitimedia codecs in easy ubuntu cover DivX/XviD Avi's..........right?
Well It's not just video, Most anything Runs CPU usage up to %100. 
Seems as if the video card is doing pretty much none of the work. CPU is doing it all.
How do I fix this?

---

### Post by punx45 on 2007-03-21
what else constitutes "most anything?"   and is this a constant 100%, or is it just quick spikes?

---

### Post by punx45 on 2007-03-21
this recent post

[http://ubuntuforums.org/showthread.php?t=390320](http://ubuntuforums.org/showthread.php?t=390320)

discusses updating the nvidia driver...

---

### Post by farscape on 2007-03-21
> **punx45 said:**
> have you installed the proprietary nvidia driver?   the system may be resorting to software decoding (big processor usage) rather than hardware decoding.   so replacing the 'nv' driver with the 'nvidia' driver may help.

search the forums for instructions, or the "envy" script which will do the dirty work for you.   do make sure your card is supported too.




And the villagers rejoice. :) 
Thanks punx45, envy did it. CPU runs at about %20 - %30 when playing videos now. Smooooooooth. 
I used the 0.8.2 version. Pressed one button and it was done. Very nice.

---

### Post by farscape on 2007-03-21
Not so fast.WHen I installed the driver with envy, I was thrown back to a command prompt. I logged in, started x. ok, everything thing is running good. smooth video. I go to restartreboot ubunto. the only choices I have are log out, switch user, lock screen or hibernate. No restart. I log out. I'm back at the command prompt. only way to shutdown is punch the power button once and it goes through the shutdown sequence. I restart. It starts normal. I log in and I'm back to choppy video. It doesn't stick. What am I doing wrong?

---

### Post by farscape on 2007-03-23
well now I've screwed myself. I'm posting from my windows box. I tried the "new legacy" driver and totally screwed myself. weeeeeeeeeeeeeeeeeeeeeeeeee...........
I'm trying to back myself out of this one.....

---

### Post by farscape on 2007-03-23
ok, I'm now getting an error on booting as I'm getting tossed to the command line.
" Couldn't open RGB_DB' /user/share/x11/rgb'

/user/share/x11/rgb   does not exist.

Plus now when I click the shutdown button in the corner. My mouse buttons quit functioning.  hummm. help please.

---

### Post by farscape on 2007-03-23
seems that I've completely hosed my system up beyond the point of recovery trying to install video drivers. Recon a complete reinstall of the system will get me back to square 1. 
Nuke and pave.

Thanks..

---

### Post by astrolabio on 2007-03-23
Ehy wait before the paving thing.
Don't you hav a backup of your xorg.conf file? You should have one. I think Envy does that.

You may have just to restore it with no paving.

---

### Post by farscape on 2007-03-23
> **astrolabio said:**
> Ehy wait before the paving thing.
Don't you hav a backup of your xorg.conf file? You should have one. I think Envy does that.

You may have just to restore it with no paving.

Not sure about the backup. Where should it be and how do I get it back. I'll look for it.

---

### Post by astrolabio on 2007-03-23
It should be inside the /etc/X11 directory

If it's not there to look for a file you can use command the
    locate xorg.conf

You may have to use the command 
    updatedb
before to update the index. Try locate xorg.conf, if nothing turns up or ask for an index use updatedb and try again.

warning: updatedb can take some time to create the index with updatedb.

---

### Post by farscape on 2007-03-23
Found the backups. How do I restore them? They are read only. I don't seem to have permission the alter them.

---

### Post by astrolabio on 2007-03-24
Simply you have to copy it over the xorg.conf and then restart.

   cp /etc/X11/xorg.conf.backupwhatver /etc/X11/xorg.conf

this will copy thr first file /etc/X11/xorg.conf.backupwhatveritsnameis over the /etc/X11/xorg.conf file which rules the configuration of X (the graphic window manager)

If this still doesn't work, google for Envy of alberto something, an italian guy, download the last deb version of it (i think is 9.something) and install it
  dpkg -i whateverisnamis0.9.deb
Then in a console type envy and follow the instructions to install your video driver.

---

### Post by raul_ on 2007-03-24
If you don't have a backup just run a ```
 dpkg reconfigure xserver-xorg
```

---

### Post by farscape on 2007-03-24
> **astrolabio said:**
> Simply you have to copy it over the xorg.conf and then restart.

   cp /etc/X11/xorg.conf.backupwhatver /etc/X11/xorg.conf

this will copy thr first file /etc/X11/xorg.conf.backupwhatveritsnameis over the /etc/X11/xorg.conf file which rules the configuration of X (the graphic window manager)

If this still doesn't work, google for Envy of alberto something, an italian guy, download the last deb version of it (i think is 9.something) and install it
  dpkg -i whateverisnamis0.9.deb
Then in a console type envy and follow the instructions to install your video driver.

Didn't work. Copied the backup. no go.
Reinstalled the driver via envy. didn't work.
"dpkg reconfigure xserver-xorg"   was the first thing I tried. Didn't help.
Now when I do eventually get to a GUI desktop, It freezes after about 10min. 
All seems to be lost. I'll keep screwing with it till Ubuntu 7 is released in a few weeks. That version should install the correct drivers automatically on install.........right? Hope so.

---

### Post by raul_ on 2007-03-24
Did you look here?
[http://ubuntuforums.org/showthread.php?t=132928]("http://ubuntuforums.org/showthread.php?t=132928")

---

### Post by farscape on 2007-03-24
This is what I get when I boot up.
**Failed to start the x server (your graphical interface). It is likley that it is not set up correctly. Would you like to view the X server output to diagnose the problem?   <yes>  <no>  **

I hit yes and I get this:
[B]dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object
file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen : /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object
file: No such file or directory

FatalError re-entered, aborting
No GLX modules loaded    

<ok>[/B]

I hit ok and get this:

[B]The x server is now disabled. Restart GDM when it is configured correctly.

<ok>    [/B]

I hit ok. Now I'm at a command line login prompt.
I log in. Type **startx** and I'm at my GUI desktop. I'm confused.
It runs very slow and when I open anything......it freezes and is unresponsive. Have to hold the power button to reboot.

It seems to be getting worse the more I screw with it.

---

### Post by farscape on 2007-03-25
Thanks for everyones help on this one. It's getting nuked.
I'm moving my linux install to a faster machine anyway. 
I'll start over from scratch. :)

---


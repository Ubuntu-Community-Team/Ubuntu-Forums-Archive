---
title: "Strobing Diagonal Line in video playback"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by nandotron on 2007-07-01
Hi,

just wondering if anyone noticed this problem with video playback in ubuntu.  When i play video files in vlc, totem and xine, there is a strobing diagonal line from the top right of the screen to the bottom left.  it is most prominent when there is movement or flashing in the frame.  the same problem does not appear when i play the files in vlc on in windows.  I have the same problem with dvd playback.

At first i thought it might be beryl-related, but even when i change the window manager to metacity, the problem  persists.  I should also mention that i am using an ati graphics card and fglrx drivers.  

Anyone else experiencing this problem?  any help would be greatly appreciated.

thanks!

---

### Post by afterburnerbg on 2007-07-26
I have the exact same problem with video playback. I am using Ubuntu 7.04, an Ati card and fglrx drivers. Used to have xgl and beryl, but now i am using standart gnome + metacity. Any ideas? Would a rollback to the original drivers help?

---

### Post by jjchico on 2007-10-20
I have the same problem after upgrading to Gutsy. It was not present in feisty. I had no compiz/beryl installed in feisty. It happens with either desktop effects on or off in Gutsy.
Any ideas?

Thanks.

---

### Post by exceptionfault_0E on 2007-10-20
Same problem here! Using an AMD Athlon 64 x2 Laptop with ATI Mobility Radeon X2300, fglrx driver working correctly (or so it seems) with --overlay-type=Xv, no desktop effects, MPlayer as video player. I confirm this was not present in Feisty. The video playback quality seems to have suffered quite a bit in general.

So far, commenting out various modules in xorg.conf have had no effect. Maybe a problem with the updated codec libraries? I'll try booting into another kernel, but I don't think that will be any help.

This constitutes a show-stopper for me, so I guess I'll be booting into Feisty again tomorrow. I can't think of any log files to attach right now, but if there's anything else I can do to track down the problem ...

**--- EDIT: POSSIBLE WORKAROUND? ---**

OK guys, I think I'm onto something. The ATI card basically seems to have two ways available to weave its magic (the hardware overlay): Xv and OpenGL. I'm not an expert, but I think the default is Xv, and this seems to cause problems.

So, let's change Xv to OpenGL by opening a terminal and typing:

sudo aticonfig --overlay-type=opengl

Now reboot. (It _should_ work with just restarting the X server, but let's make double sure). 

This may already improve things, but I suppose it is better to tell your media player to use the new hardware overlay, like this:

gmplayer -vo gl movie.avi

Commands for the media player of your choice may vary - or maybe you can't set it at all ...

If you're using MPlayer, you can make the new setting permanant by typing

sudo nano /etc/mplayer/mplayer.conf

and changing the line that reads

vo=xv

to

vo=gl

For me, this seems to work quite well, the annoying diagonal line is gone.

(Wait, am I seeing some horizontal choppiness that wasn' there before, or am I imagining things?)

Did that help?

---

### Post by szwety on 2008-01-11
i'm getting the same problem here.  i have nvidia card is there any way to fix it with if i use nvidia?

---

### Post by vahnx on 2008-02-01
The same problem is occuring here, and I'm on Gutsy. I used this persons guide to install my codecs and I have the same laptop as him:
[http://www.ubuntu1501.com/2007/11/easy-codec-install-for-gutsy.html]("http://www.ubuntu1501.com/2007/11/easy-codec-install-for-gutsy.html")

This is one of the reasons why I boot into Windows. It's the only way I can watch video without a stupid line from top right to bottom left. I tried VLC, Totem, and some other player.

---

### Post by redDEADresolve on 2008-02-01
its your video drivers and the eye candy, they are causing 90% of the video playback problems. If you use metacity or a non-xgl session it should clear right up.

---

### Post by vahnx on 2008-02-01
I'm a Linux noob. How do I exactly get into a non-xgl session? What's metacity? Will it require me to uninstall my current eye candy? I tried disabling all my eye candy (selected None under Desktop effects) but it still had the line. My drivers should be the best I can use because I followed the guys tutorial in the post. It's a Dell Inspiron 1501, 1.5GB RAM, ATI Radeon X1150 w/ 256MB Graphics. If I have to complete remove compiz just to watch a video without the line, it's not worth it for me. I'd rather reboot into Windows.

---

### Post by skullmunky on 2008-02-01
you can also try setting your video player to use a different mode; i have an nvidia card and this helps with occasional weirdness that varies between different driver versions, whether you have the Composite extension disabled, etc.

For example, in VLC, go to Settings->Preferences
in the Video section, choose "Output Modules"

try these different ones - XVideo extension, OpenGL, or X11, and see if it makes a difference.

in mplayer, r-click for the popup menu and choose preferences.  in the Video tab there's a bunch of drivers, see if any help.

---

### Post by vahnx on 2008-02-08
In VLC I didn't see an option to switch "output modules".
Couldn't find any option in Totem either.

---

### Post by skullmunky on 2008-02-14
In VLC (0.8.6, for me) try 

Settings->Preferences->Output Modules

in MPlayer, try R-Click->Preferences->Video Tab

---

### Post by vahnx on 2008-02-14
I switched from the Restriced Driver to using Envy to installthe latest ATI driver, and then when I disable Compiz it works fine.

---

### Post by miceagol on 2008-02-24
This is definitely caused by compiz fusion. Turned it off, and no horizontal lines in movies no more.

---

### Post by nandotron on 2008-02-24
yes, i tried turning off desktop effects but the playback still isnt perfect.  there's still a certain amount of strobing but it tends to be horizontal more than diagonal.  Its actually like a horizontal line that goes half way across, and is joined to another, lower horizontal line on the other side by a short diagonal line, so it looks sort of like a 'Z', if that makes any sense

---

### Post by exceptionfault_0E on 2008-02-26
When I upgraded to Gutsy (without Compiz Fusion; ATI Mobility Radeon X2300 with fglrx driver), I could "choose" between diagonal tearing and the Z-shaped tearing mentioned by nandotron by using the Xv or the OpenGL overlay, respectively. 

The solution was to downgrade to Feisty :-( The Feisty fglrx version ( 8.34.8 ) plays my videos without tearing. BTW, this diagonal tearing is also  listed as an unresolved bug in the release notes for the lastest fglrx: 
[https://a248.e.akamai.net/f/](https://a248.e.akamai.net/f/)
674/9206/0/www2.ati.com/drivers/
linux/catalyst_82_linux.html

(Sorry, the link wouldn't display any other way)

---

### Post by Neutrino on 2008-03-08
The problem of diagonal tearing was solved by the last ati drivers. I installed it and it worked.
I have a Ati HD Radeon 2300 card.

You can follow the installation guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually") 


Good luck!

---


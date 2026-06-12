---
title: "Pixilated Display problem."
date: 2009-04-22
forum: Apple Hardware Users
---

### Post by Vick on 2009-04-22
Hello,  I am a trying ubuntu for the first time.

I instaled it on my Mac g4, with a ATI radeon 8500 mac edition graphics card.

I got through the installation process and this is what my screen looks like:

[[IMG]http://img242.imageshack.us/img242/268/img0059k.th.jpg[/IMG]](http://img242.imageshack.us/my.php?image=img0059k.jpg)

[[IMG]http://img8.imageshack.us/img8/7193/img0058ucu.th.jpg[/IMG]](http://img8.imageshack.us/my.php?image=img0058ucu.jpg)

---

### Post by Vick on 2009-04-22
I tried changing the monitor resolution but I couldn't.  It says "unknown".

---

### Post by Vick on 2009-04-22
update:  I tried to change the monitor setting in preferences. It said monitor unknown and wouldn't let me change anything.

I tried the drivers thing under admin.  It searched for a little bit and said no proprietary drivers.

The monitor worked fine when I had os x installed.  It works fine plugged into my other computer as well.

Anyone have any clue what I should check next?

---

### Post by Vick on 2009-04-22
I'm not an expert but I am guessing maybe it is my video card drivers?

---

### Post by stream303 on 2009-04-23
It looks like you'll be joining the ranks of ppc users having to manually configure their /etc/X11/xorg.conf file with a text editor.

The most important thing right now is to determine what your monitor's vertical and horizontal sync values are from your documentation, or perhaps you can find it on the web.

I don't know what version of Ubuntu you have installed, so let us know.  There are a few things that need to be done, but in your xorg.conf file, you'll end up using something similar to this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-82
	VertRefresh	50-75
EndSection
```

Note that this is a VERY abbreviated snippet from my own xorg.conf, which has MY monitor's freqs in it.

If you can get to a virtual terminal, ie with CTRL-ALT-F2 and login, you'll be able to use the NANO editor to make this change.

There should be a few sample xorg.conf's here in the threads and ubuntu ppc wiki's (see the taglines at the first sticky threads for ppc at the top of the forum.

Be sure to let us know exactly what machine you have so we can pin down your setup better:

[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

I'm assuming a PowerMac in this instance...

Don't run your monitor in that funky mode any more than you have to - let's get those all important vertical and horizontal freqs fixed first.

---

### Post by Vick on 2009-04-28
Thanks for the advice.. I am new to linux but am having fun trying to figure this out.  I did figure out how change my xorg file but I only figured enough out to ruin everything so I had no monitor so I reinstalled from scratch.


I have a mac g4 "sawtooth".
My graphics card is a "ATI Radeon 8500 mac edition"
My monitor is a "DELL 2005FPW"

Cnet says this about my monitor:
#  Max Sync Rate (V x H)   75 Hz x 83 KHz  

[http://reviews.cnet.com/lcd-monitors/ultrasharp-2005fpw-20-1/4507-3174_7-31232082.html?tag=mncol;psum](http://reviews.cnet.com/lcd-monitors/ultrasharp-2005fpw-20-1/4507-3174_7-31232082.html?tag=mncol;psum)

I'll keep trying to read about xorg files.  Any further assistance would be appreciated as well!  I'm having fun, but I am like a bull in a china shop here.

---


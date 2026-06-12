---
title: "Xorg CPU usage 100%"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2006-12-11
Hi, I have posted this on the PPC section to no avail so I'm hoping for some assistance here.
I am using DAPPER on an iMac G3 400MHz PPC and have noticed that the CPU usage for **Xorg **can spike from 30% up to 100% at the time very little else is running (with regard to REAL work!)
Is this a correct usage or can I somehow reduce it?
As a total novice I'm probably talking complete nonsense  :( 
Any advice is most welcome.
Could this be a reason for overheating/switch off of the iMac ?
Cheers, RADIOLAD

---

### Post by zgornel on 2006-12-11
Are there only spikes or the system keeps on running at 100% load while do nothing that could stress it? G3 is a bit old and slow for ubuntu (using gnome) so occasional 100% cpu usage spikes don't sound too uncommon.

---

### Post by dwblas on 2006-12-11
I have read similiar things for other non-Mac systems.  The answer was that the 2.6 kernel will grab memory when it can in anticipation of what it might need.  Memory will appear to be 100% used, but it is not.  It started somewhere like 2.6.16, I'm not sure.  Also, I have seen posts that Mozilla browsers will slowly eat up memory if you leave the browser open for and extended time.

---

### Post by r4ik on 2006-12-11
Perfect machine to run Xubuntu,

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM, when using the Alternate Install CD you can do with 64 MB.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

Good luck !

---

### Post by Radiolad on 2006-12-11
> **zgornel said:**
> Are there only spikes or the system keeps on running at 100% load while do nothing that could stress it? G3 is a bit old and slow for ubuntu (using gnome) so occasional 100% cpu usage spikes don't sound too uncommon.

Hi, It is '**spikes**'. In fact on the GUI it looks like a heartbeat :rolleyes: 
I do have 512MB RAM in the iMac. The FIREFOX browser is pretty speedy so no problems there.
So... is the Xorg 'CPU usage' just something the system has to endure?
I have tried to reduce the 'priority' of the program to '8' but this makes no difference to the 100% spike.
      RADIOLAD

---

### Post by zgornel on 2006-12-12
You shouldn't worry about the spikes if there are no slowdowns associated with them.

---

### Post by Radiolad on 2006-12-12
Cheers, Thanks for the update.   RADIOLAD

---

### Post by yorick on 2006-12-16
Hi, I've just reinstalled Edgy and noticed also that xorg CPU usage was allways above 25%. 
I also noticed tearing with the avi movies (something with xv I think).

Anyway, I played a bit with xorg.conf and now I have normal xorg CPU usage (2-3%) and the movies are playing smoothly.

Here is the relevant part from my xorg.conf:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option "EnablePageFlip" "true"
        Option "RenderAccel" "true"
        Option "XAANoOffscreenPixmaps" "true"
        Option "AccelMethode" "EXA"
EndSection 
```

Hope this helps.

---

### Post by Radiolad on 2006-12-16
Hiya, Thanks for the info. I may need a 'newbie guide' in order to spell out how I go about it!
Cheers,   Radiolad

---

### Post by VoodooDali on 2007-02-03
This problem is driving me nuts. My computer is *this* close to inoperative, because my CPU is hovering at 100% continually.

So far I have tried the following, to no avail:

. Checked for the correct driver in Xorg.conf (i810 - correct).
. Disabling the "composite" option in Xorg.conf.
. Turning off the system tray, GUI effects and all eye candy (although none of these gave me any trouble before).
. Updating drivers and all other software.

I know this much is true (with apologies to Spandau Ballet):

. It's not a distro problem, as I'm seeing it echoed on Gentoo and SUSE forums.
. It's not a video processor or driver problem, as I've seen it happening to ATI, nVidia and other users as well as my Intel "Extreme" (yeah, right) graphics array.
. It's not a KDE thing, as it happens to GNOME users too.

I am convinced the problem is directly traceable to Xorg itself - unfortunately, X.org and the associated Wiki are no help at all.

Just writing this post has taken me a half hour. I'm *this* close to a reinstall, and avoiding all updates until I hear the problem is fixed.

My rig:
. Alienware Sentia series laptop
. Intel Pentium M series, 2GHz
. Intel Extreme Graphics 2 (P.O.S.) video
. 2GB RAM

Your advice would be greatly appreciated.

---

### Post by zgornel on 2007-02-03
What proceses exactly eat up the cpu ? The xorg server ? Using a composite window manager like beryl/compiz actually reduces cpu usage (cpu used for drawing windows and such) by using the video instead. Could you post a sequence of events that lead to a 100% abnormal cpu usage ?

---

### Post by VoodooDali on 2007-02-03
Both top and sysguard report xorg itself as being the main culprit - using 50-75% of CPU with no applications open.

Unfortunately, I have no 'sequence of events' to offer  :(  From the moment the X server starts up and I reach a desktop, the CPU is 100% taxed.

I've since regained a *little* functionality by reconfiguring the X server, manually specifying the amount of memory to be set aside for the (alleged) graphics processor.

I will now see if I can regain a little more performance, by installing a composite window manager. I'll probably try Beryl rather than Compiz, as I hear it runs better on i810 graphics.

Thanks very much for responding.

---

### Post by VoodooDali on 2007-02-03
Following up:

I have Beryl up and running now. Top shows that Xorg is still owning 50% of my CPU, but I'm somewhat more functional. Interesting, to see a performance increase after the implementation of *more* eye candy.  (heh)

N00b question: can I just kill Xorg, if my processes are all using AIGLX/Beryl?

---

### Post by zgornel on 2007-02-04
The only notable performance difference with compiz/beryl is when desktops are changed, windows are dragged (80-100% cpu vs. <5%), minimized/maximized (10% vs. <5%) and drawn for the first time (can't tell exactly). You also must have direct rendering enabled othewise X peformance is terrible.

---

### Post by mayfer on 2007-03-23
> **yorick said:**
> Hi, I've just reinstalled Edgy and noticed also that xorg CPU usage was allways above 25%. 
I also noticed tearing with the avi movies (something with xv I think).

Anyway, I played a bit with xorg.conf and now I have normal xorg CPU usage (2-3%) and the movies are playing smoothly.

Here is the relevant part from my xorg.conf:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option "EnablePageFlip" "true"
        Option "RenderAccel" "true"
        Option "XAANoOffscreenPixmaps" "true"
        Option "AccelMethode" "EXA"
EndSection 
```

Hope this helps.

this did it for me and my 9600xt. thanks.
(i also had my 9600xt overclocked, so i underclocked it to make it more stable.)

---


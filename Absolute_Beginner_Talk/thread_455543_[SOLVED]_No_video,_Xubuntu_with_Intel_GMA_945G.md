---
title: "[SOLVED] No video, Xubuntu with Intel GMA 945G"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-05-26
So after finally getting Xubuntu to recognize widescreen resolutions with my Intel GMA 945G, I went to open a video file with VLC to see how good it looked... 

And what do ya know? NO VIDEO!!!
Just sound

Tried xine, same deal.

Here is the Device part of my xorg.conf....

Section "Device"
        Identifier      "Intel GMA 945G"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection


What do I need to change to get this to play videos? I'm assuming the problem is in my xorg.conf file

thanks,
tom

---

### Post by overdrank on 2007-05-26
> **kernel tom said:**
> So after finally getting Xubuntu to recognize widescreen resolutions with my Intel GMA 945G, I went to open a video file with VLC to see how good it looked... 

And what do ya know? NO VIDEO!!!
Just sound

Tried xine, same deal.

Here is the Device part of my xorg.conf....

Section "Device"
        Identifier      "Intel GMA 945G"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection


What do I need to change to get this to play videos? I'm assuming the problem is in my xorg.conf file

thanks,
tom
Hi you need to install the codecs.:D
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by kernel tom on 2007-05-26
are you sure?

my videos all played before getting Xubuntu to recognize my widescreen

i installed xserver-xorg-video-intel

then reconfigured my xorg

and now it doesnt work, i have all codecs already... do i need to re-install?

---

### Post by kernel tom on 2007-05-26
re-installed all w32codecs, still nothing

help?

---

### Post by veloce on 2007-05-26
> **kernel tom said:**
> re-installed all w32codecs, still nothing

help?

To confirm that it's the "intel" driver, I suggest you switch back the i810 driver.  You'll need to install 915resolution to retain the wide screen:

sudo apt-get install 915resolution
sudo apt-get xserver-xorg-video-i810

then in your xorg.conf, change "intel" to "i810"

(Hopefully, 915resolution will recognise your widescreen automatically.  If not you need to specify the resolution in the /etc/default/915resolution file)

I've had issues with memory management and 3d acceleration in both i810 and intel drivers (and dual screen will not work with the intel driver)

This is a horrible backwards step, but will at least confirm that it's the intel driver.

---

### Post by kernel tom on 2007-05-27
I actually stumbled upon the answer.  Because I changed my graphics card set up, I needed to also change the "Video Output" on my media players

In VLC it had to be changed to X11
and for Xine the video driver had to be changed to xshm (this one was harder, just tried them all till i got picture)

Hopefully that helps anyone else with this problem

---

### Post by senab on 2007-05-29
Turn off Compiz and desktop effects, VLC will then work with all the output modules (including XV).

---

### Post by justleen on 2007-05-29
just a note, but VLC doenst need codecs.. thats the beauty of VLC...

---


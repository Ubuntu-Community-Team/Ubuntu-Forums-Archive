---
title: "Problems partioning on a Clamshell&amp;Display question"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by rachie on 2007-01-12
Hi i have not used Ubuntu before but today i downloaded a Live CD 6.10 and that went ok. I have Mac OS 10.3.9 on my Clamshell and Mac OS 9.2.2. I want to install Unbuntu also so that i can dual boot.
On the partioning set up page it gives me the option to use the largest continuous free space or to manually partition the partition  table. Seeing as i would like to reserve space for Mac OS i do not want to use up all the space for this install so i would need to manually edit.
I don't know how to manually edit though. I would appreciate any help on this.

Also i would like to know how do i go about changing the resolution in the settings. I don't know where they are right now.

Thanks

---

### Post by linear on 2007-01-12
There is a howto on resizing Mac partitions [here]("http://ubuntuforums.org/showthread.php?t=89960").

---

### Post by rachie on 2007-01-12
Thank you, i just need to work out how to change the resolution on this Clamshell in Ubuntu now.

---

### Post by brackishboy on 2007-01-12
What resolution are you running at? Bear in mind that the Clamshell iBook is limited to 800x600 pixels...

---

### Post by rachie on 2007-01-12
Brackish boy i own a 466mhz Clamshell with the 8mb video card and i have read around the net that this Clamshell can utilise a 1024x768 resolution in Ubuntu but that the slightly lower speced Clamshells cannot.

The resolution that it runs at the moment is 800x600 but i wanted to see if it could take 1024x768.

Thanks

Installing Ubuntu is harder than i thought what with having to resize partitons manually. Hopefully though i will get there in the end.

---

### Post by brackishboy on 2007-01-13
Ok, open up a terminal window and type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup.conf

sudo gedit /etc/X11/xorg.conf
```

In your xorg.conf, there will be a section that contains the allowed resolutions- it'll look something like this.

```
"800x600" "640x480"
```

At the beginning of each colour depth line, insert "1024x768".

Save the file, then restart X with Ctrl+Alt+Backspace (might be delete on the iBook).

If your panel supports XGA, it ought to boot into 1024x768. If not, you'll probably get some weird screen artifacts, so you can restore your file from the backup you made.

I'm sure someone could make this clearer than I just did... Hope I've got you a little closer to your goal!

---

### Post by bphinz on 2007-01-13
Hi rachie,

I just bought a 466mhz clamshell as well to replace my daughter's broken 366 and tried to get 1024x768 as well.  a google search turned up a post to a freebsd list from a few years back where the user claims to have it working, and even posted his xf86config file, but i could not replicate his success.  the modelines for 1024x768 are outside the default sync/refresh values and so far i haven't been able to find suitable values.

off topic, does your sound card work?  i had no trouble with the 366, but with the 466 no sound card is detected.  the hardware is fine, it works under osx...  would you mind posting the output of 'lspci -v' for me?  mine shows no sound dev:

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth FireWire (rev 01)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

Thanks,
-brian

---


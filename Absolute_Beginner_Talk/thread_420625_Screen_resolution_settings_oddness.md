---
title: "Screen resolution settings oddness"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-23
I am testing 7.04 in a vmware virtual machine, and some funny things are happening with screen resolution.

The screen resolutions offered by the preferences application are many and varied.  They are not those listed in xorg.conf (as far as I can tell by looking at the default colour depth modeline).  How can you tell which colour depth it is using, or for that matter change it. I am new to Ubuntu and haven't fount a preference tool to control colour depth anywhere.

Lastly, the preferences app also shows the refresh rate as 0 (that's zero!) Hz.

---

### Post by markl187ld on 2007-04-23
It's to do with the fact that VM machines are running in a window rather than a full monitor screen. The resolutions available are based on the windows dimensions. 

The colour depth is specified in the /etc/X11/xorg.conf file and should be set to 24bpp (full colour) by default. 

As for the refresh rate. It's not used in VM Machines it's set by the host machine.

---

### Post by ubnewbie2 on 2007-04-24
> **markl187ld said:**
> It's to do with the fact that VM machines are running in a window rather than a full monitor screen. The resolutions available are based on the windows dimensions. 

The colour depth is specified in the /etc/X11/xorg.conf file and should be set to 24bpp (full colour) by default. 

As for the refresh rate. It's not used in VM Machines it's set by the host machine.

Thanks.  I have to say, as a Mandriva user, that I like the approach Ubuntu is taking in general.  I may well install it properly and give it a real try for a while.

---


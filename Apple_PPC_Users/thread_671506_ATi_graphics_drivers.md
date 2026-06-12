---
title: "ATi graphics drivers?"
date: 2008-01-18
forum: Apple PPC Users
---

### Post by namtap on 2008-01-18
This could very well be something that I missed, but I did some searching and could not seem to find anything.

How can I get graphics drivers for my video card?  I have a Powerbook G4 with the ATi Mobility Radeon 9700.  ATi itself does not seem to support Linux on PPC, so I was wondering if there's some alternate way of getting compatible graphics drivers.

Thanks a lot.  Again, I'm sorry if this is somewhere else on these forums, but I couldn't find anything.

---

### Post by Auria on 2008-01-18
There's the open-source drivers, and they come with Ubuntu so probably they are already installed - you just need to make sure in your X.org config that the driver is set to "radeon" IIRC. This driver is average, it mostly works for 2D and some basic 3D though don't expect too much (I think ATI released specs thoguh? so maybe in the future there will be better ones)

---

### Post by stmiller on 2008-01-18
Yeah ATI has never made any PowerPC Linux drivers. The open source radeon driver has fairly good 3D. You can see videos on youtube of people doing compiz on their ibooks and such with this driver. Just do as Auria says and edit your /etc/X11/xorg.conf file to specify the radeon driver.

---

### Post by namtap on 2008-01-18
Alright, well I believe it is set to 'Radeon,' even though in the xorg.conf file, it doesn't say that it's a 9600, which I believe is incorrect.

I was just wondering, because I cannot get chess to work in 3D, despite installing the OpenGL and GtkGLExt Python Bindings.  Not to mention some other things that seem off.  Even in 2D, chess lags a lot, and when I drag around windows, it leaves a million 'trails' behind it.  Stuff like that.  It's pretty irritating, but I guess that's what I get for trying Ubuntu on a platform that's hardly supported.

---

### Post by stmiller on 2008-01-19
Editing the xorg.conf file is quite an exhaustive topic, so you might have to search around for more info to make any needed tweaks. Read through the links in the PowerPCFAQs for starters.

For powerpc the xorg.conf driver choices that work are:

nv
rage128
radeon
ati

The radeon driver supports your card in your powerbook for 3D. So specifying 'radeon' in the drivers section of the xorg.conf file will load the correct driver.

---

### Post by ssam on 2008-01-19
> **namtap said:**
> 
I was just wondering, because I cannot get chess to work in 3D, despite installing the OpenGL and GtkGLExt Python Bindings.

the chess issue is a bug, nothing to do with lacking graphics drivers.

try running the command

```

glxinfo | grep direct

```

that will tell you if direct rendering (3d acceleration) is enabled

also don't worry about the name of you card in xorg.conf, it is just a label. it could be 'graphics card 1' and it would work just the same.

i think a 9700 is a r300 (according to wikipedia, and assuming the mobility bit does not make any difference)

"All r3xx cards and all r4xx excluding the Xpress integrated chips should be supported by the new experimental r300 driver; as of June 2007, there is experimental support for the Xpress chips in the DRI and Mesa git repositories."

so it think it should work in gutsy, and maybe fiesty.

---


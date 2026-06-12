---
title: "Changing login screen resolution?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-10-20
So I got Gutsy Gibbon yesterday and did a fresh install. I'm VERY satisfied with it, but I just have a small pet peeve.

My monitor is 22" and can handle a 1680x1050 resolution. At the login screen, it's something like at 800x600 or something, But when I log into my account, it switches to the 1680x1050 resolution.

IIRC, the 'ubuntu' image at the splash screen is as though it was at a 800x600 resolution as well... perhaps I need to change it in GRUB or something like that?

I searched, and the only guides I found were for the vesa driver which doesn't support widescreen monitors (according to the posts I found). My graphics card is an Intel GMA 950 and I'm using the 'intel' driver on Gutsy.

---

### Post by dcstar on 2007-10-20
> **akiratheoni said:**
> So I got Gutsy Gibbon yesterday and did a fresh install. I'm VERY satisfied with it, but I just have a small pet peeve.

My monitor is 22" and can handle a 1680x1050 resolution. At the login screen, it's something like at 800x600 or something, But when I log into my account, it switches to the 1680x1050 resolution.

IIRC, the 'ubuntu' image at the splash screen is as though it was at a 800x600 resolution as well... perhaps I need to change it in GRUB or something like that?

I searched, and the only guides I found were for the vesa driver which doesn't support widescreen monitors (according to the posts I found). My graphics card is an Intel GMA 950 and I'm using the 'intel' driver on Gutsy.

Your login screen should be your "real" resolution - I use 1440x900 and that is what I get (except for the Splash screen).

You will probably need to edit you /etc/xorg.conf file and remove some of the unnecessary listed resolution settings - Ubuntu is probably detecting the wrong one on start up and picking it from the list.

There are numerous posts in the forum on how to make these changes.

---

### Post by akiratheoni on 2007-10-20
Dang, I knew I forgot to add one thing to my post.

I already deleted all resolutions except for 1680x1050 from my xorg.conf file, and it still is using a lower one than 1680x1050.

---

### Post by luckSpray on 2007-10-20
I have exactly the same problem after the upgrade to Gutsy... :(

The log in screen's stuck at a resolution of "640x480".

Here's the relevant xorg.conf snippet:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Monitor         "PHILIPS 107B"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection

```

Additionally: Everything worked fine before the upgrade. it's REALLY awkward, because I'm using another window manager (ion3) and it just stays at "640x480" when I use ion3.

When I log into a xfce session it changes the resolution to the desired "1024x768" though I don't know if this is due to the xorg.conf or because i changed it rough the display settings (GUI)...

:confused:

Thanks in advance!

---

### Post by rudeboyskunk on 2007-10-20
Ok, so I changed my xorg.conf file to just "1024x768" and it fixed the login screen...

But now my desktop screen is messed up!  And I stupidly did NOT make a backup of xorg.conf.  I cannot remember the one higher up resolution that was in there so I can change it back.

---

### Post by akiratheoni on 2007-10-20
Yeah, my section of the xorg.conf is:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"LCM-22w3"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
EndSection
```

---

### Post by Fabre on 2007-10-21
I have the same problem except my login screen is in 1920x800 instead of 1280x1024

Which also was the resolution ubuntu defaulted to after I installed the restricted drivers. 

No resolutions are specified in my xorg.org, is there another place where it could be stored?

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JP [Radeon X800XT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection
```

---

### Post by akiratheoni on 2007-10-22
Bump, I'm not the only person suffering from this problem :(

---

### Post by Lord_Dicranius on 2007-10-22
> **rudeboyskunk said:**
> Ok, so I changed my xorg.conf file to just "1024x768" and it fixed the login screen...

But now my desktop screen is messed up!  And I stupidly did NOT make a backup of xorg.conf.  I cannot remember the one higher up resolution that was in there so I can change it back.
Do you use gedit to edit your xorg.conf?  If so, if you haven't changed the default settings, there should be an xorg.conf file with a tilde in it's filename, that was created before your last saved.  Check that to see if it shows the old resolutions.

---

### Post by kyldere on 2007-10-23
I was wondering if you had edited your /boot/grub/menu.lst file. There is a line in the default options section for defoptions, and if you set the vga= to some integer value that isn't accepted, it will default to the lowest possible resolution. Check out  [this page]("https://help.ubuntu.com/community/ChangeTTYResolution") for more info.  Just a thought.

---

### Post by akiratheoni on 2007-10-24
> **kyldere said:**
> I was wondering if you had edited your /boot/grub/menu.lst file. There is a line in the default options section for defoptions, and if you set the vga= to some integer value that isn't accepted, it will default to the lowest possible resolution. Check out  [this page]("https://help.ubuntu.com/community/ChangeTTYResolution") for more info.  Just a thought.

Hm, well my normal resolution (1680x1050) isn't listed there; would you happen to know what value to enter, or any site that would help me find out what value to list? Thanks.

---

### Post by momentsbigadventure on 2007-10-25
Please people help find answer to this problem. I have tryed all these steps and i am having same problem too.
Im of moderate experience, i made a back up of xorg.conf and removed all the instances of other resolutions.
Has anyone considered the fact that for some reason there is a second instance of the "screen" section? I have a "Screen" and a "Screen" # , two different screen sections.

---

### Post by akiratheoni on 2007-10-27
Bumping, help please :(

---


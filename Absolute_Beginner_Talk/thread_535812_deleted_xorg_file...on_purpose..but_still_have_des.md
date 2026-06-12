---
title: "deleted xorg file...on purpose..but still have desktop environment...why?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-26
So after a huge battle with my xorg file not working i looked at it using vi everything looked fine! but it didn't work, i tried a few backups didn't work! so i deleted  it ON PURPOSE and did a reboot and wat do u know my desktop came up with 1440x900 resolution.  now just so i understand this what file is it using? i have 5 backups none of which are called xorg.conf, anyone care to elaborate on this and provide and explanation and perhaps some further steps to take to sort things out.

Thanks in advance, Alain!

---

### Post by aysiu on 2007-08-26
Can you post the output of these commands? ```
cd /etc/X11
ls
```

---

### Post by asmoore82 on 2007-08-26
as of like version 7.0 I think Xorg can automagically configure itself without a config file
but this automatic setup should be far from optimum performance if/when it actually works

if this autoconfiguration works at all it is a great starting point for an xorg.conf file so you can
capture the setup by running Xorg manually with the '-configure' option...
[QUOTE="Xorg manpage"]-configure
               When this option is specified, the Xorg server loads all  video
               driver  modules,  probes for available hardware, and writes out
               an initial xorg.conf(5) file based on what was detected.   This
               option  currently  has  some problems on some platforms, but in
               most cases it is a good way to bootstrap the configuration pro&#8208;
               cess.   This option is only available when the server is run as
               root (i.e, with real-uid 0).[/QUOTE]

---

### Post by S15_88 on 2007-08-27
app-defaults             xinit                     Xresources
cursors                  xkb                       xserver
default-display-manager  xorg.conf.20070803204934  Xsession
fonts                    xorg.conf.20070803214731  Xsession.d
gdm                      xorg.conf.20070803224708  Xsession.options
rgb.txt                  xorg.conf.20070803225033  XvMCConfig
X                        xorg.conf.20070826202912  Xwrapper.config


ps. all this chaos was spawned by me adding a few things to the xorg file to try to get S-Video out working.  now i'm scared to touch the xorg file, does anyone know of the correct way to fallback to the the previous xorg file?  would this work:
> 
cd /etc/X11
dir
mv xorg.conf.20070803204934 xorg
etc/init.d/gdm restart


Thanks again for all the help, Alain

---

### Post by KIAaze on 2007-08-27
It should work like this:

```
cd /etc/X11
**sudo** mv xorg.conf.20070803204934 xorg**.conf**
**sudo /**etc/init.d/gdm restart

```

I don't know why you mentioned the "dir" command. It does exist, but it seems to be more for programming than for actual comand-line usage.

---

### Post by mali2297 on 2007-08-27
> **KIAaze said:**
> I don't know why you mentioned the "dir" command. It does exist, but it seems to be more for programming than for actual comand-line usage.

Habit from DOS, I suspect. :)

---

### Post by forestpixie on 2007-08-27
> ps. all this chaos was spawned by me adding a few things to the xorg file to try to get S-Video out working

to get my s-video working on my old nvidia card I had to add these 2 lines to my xorg.conf, obviously the PAL-I would need changing to match where you're living. Vert refresh I believe to be from my ac frequency. Perhaps that'll help you 

```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     50.0
    Option         "DPMS"
    [COLOR="Red"]Option "TVStandard" "PAL-I"
    Option "TVOutFormat" "SVIDEO"[/COLOR]
```

---


---
title: "Blurry fonts are driving me nuts"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by mustang on 2005-09-03
Hey guys,

I'm quite frustrated on how to fix up the blurry fonts in Ubuntu. I went through guide after guide and still nothing. I tried [this](http://ubuntuforums.org/showthread.php?t=4456&page=1&pp=10&highlight=blurry+fonts)  and [this](http://ubuntuforums.org/showthread.php?t=20976&highlight=blurry+fonts). Could someone please point me to a simple guide please? I am running GNOME, AIW 8500dv, and using a 14inch CRT on 800x600 resolution.

Here is how ubuntuforums looks on my PC for reference:

[http://members.cox.net/vo154/Screenshot.png](http://members.cox.net/vo154/Screenshot.png)

Thank you,

Manish

---

### Post by poofyhairguy on 2005-09-03
[QUOTE=mustang]Hey guys,

I'm quite frustrated on how to fix up the blurry fonts in Ubuntu. I went through guide after guide and still nothing. I tried [this](http://ubuntuforums.org/showthread.php?t=4456&page=1&pp=10&highlight=blurry+fonts)  and [this](http://ubuntuforums.org/showthread.php?t=20976&highlight=blurry+fonts). Could someone please point me to a simple guide please? I am running GNOME, AIW 8500dv, and using a 14inch CRT on 800x600 resolution.

Here is how ubuntuforums looks on my PC for reference:

[http://members.cox.net/vo154/Screenshot.png](http://members.cox.net/vo154/Screenshot.png)

Thank you,

Manish[/QUOTE]


Whats your default font? (under preferences font)

---

### Post by mustang on 2005-09-03
[QUOTE=poofyhairguy]Whats your default font? (under preferences font)[/QUOTE]

Hi poofyhairguy,

it is sans/sans/verdana/sans all size 10. Whatever I change it to, it still looks blurry...

---

### Post by poofyhairguy on 2005-09-03
[QUOTE=mustang]Hi poofyhairguy,

it is sans/sans/verdana/sans all size 10. Whatever I change it to, it still looks blurry...[/QUOTE]

I think the problem is the sharpness setting of your monitor. For fonts, if it is set to too sharp (yes there is such a thing) or too little fonts will look real bad. Is there a way you can cahnge this? What graphics card to you have?

---

### Post by mustang on 2005-09-03
[QUOTE=poofyhairguy]I think the problem is the sharpness setting of your monitor. For fonts, if it is set to too sharp (yes there is such a thing) or too little fonts will look real bad. Is there a way you can cahnge this? What graphics card to you have?[/QUOTE]

There is no way to change the sharpness on my monitor, just the screen size, etc. I have an ATI all in wonder 8500dv graphics card. (I did not install any drivers for it)

---

### Post by WebbyBabe on 2005-09-03
I'm having the same problem with Blurry fonts on my comp.  [-X

---

### Post by Lux Perpetua on 2005-09-04
You can go to System->Preferences->Font and select Monochrome, but for me, this almost always makes the fonts look stunningly bad :( I know this isn't just a fact of Linux, since non-Gtk X-Windows applications like Emacs seem to use aliased fonts without looking horrible.

---

### Post by Cool Surfer on 2005-09-04
I am also having the same problem with fonts. Dunno if any one else also faced it,
but I had the same problem with mandrake, fedora fc3 also.

---

### Post by Knyven on 2005-09-04
How about trying to decreasing the refresh rate, my monitor blurs a little when you run at 85hz. The perfect refresh rate for my monitor is 75hz, it became sharp.

---

### Post by mustang on 2005-09-04
[QUOTE=Knyven]How about trying to decreasing the refresh rate, my monitor blurs a little when you run at 85hz. The perfect refresh rate for my monitor is 75hz, it became sharp.[/QUOTE]

I think the highest rate my monitor supports is 60hz :(

---

### Post by bin on 2005-09-04
No promises, but the following may help:-

1. Edit xorg.conf - in the monitor section put in an entry for the Display Size in mm as shown in bold.

sudo gedit /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"SDM-HS53"
	Option		"DPMS"
	**DisplaySize	305 228**
EndSection

This will help X get your DPI settings right.

If you haven't already done so - sudo apt-get install msttcorefonts

sudo dpkg-reconfigure fontconfig - step through with the relevant answers for you NOTE the CRT or LCD question.

Reboot and then do xdpyinfo. In there, near the top you'll find and entry....

screen #0:
  print screen:    no
  dimensions:    1024x768 pixels (306x229 millimeters)
  resolution:    85x85 dots per inch

This shows me at 85 dpi which is not quite right, should be 86 but just need to fiddle the size down a bit. 

System >Preferences>Font experiment with the settings - in Details use the above DPI figure

OR - replace your monitor - CRT's are so cheap, many folks are giving them away - and 60hz on an 800x600 will be doing your eyes a world of no good!

in light

bin

---

### Post by Irony on 2005-09-04
Note before you do;

*sudo gedit /etc/X11/xorg.conf*

Do;

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*

This creates a backup file, so that if you can't boot into GUI but end up in shell, type;

*sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*

Then *Ctrl+Alt+Del* to reboot.

This restores your original file. I say this because the first time I altered my file I ended up in shell and of course being new to linux didn't know what to do.

---

### Post by oracle2025 on 2005-09-04
If you want to have non anti-aliased Fonts edit
/etc/fonts/local.conf
And activate bitmapped fonts, then use the Font-Preferences in Gnome to change the default font to a bitmapped one.

---

### Post by mustang on 2005-09-04
[QUOTE=oracle2025]If you want to have non anti-aliased Fonts edit
/etc/fonts/local.conf
And activate bitmapped fonts, then use the Font-Preferences in Gnome to change the default font to a bitmapped one.[/QUOTE]

Hi oracle,

you're going to have to excuse my stupidity but how do I go about activating bitmap?]

Currently this is my /etc/fonts/local.conf

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
<!-- Uncomment below to enable the freetype autohinter module -->
<!--
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
</fontconfig>

```

Thanks!

---

### Post by Lux Perpetua on 2005-09-04
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--            [color=red]<<< delete this[/color]
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->             [color=red]<<< delete this[/color]
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->             [color=red]<<< ???[/color]
<!-- Uncomment below to enable the freetype autohinter module -->
<!--
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
</fontconfig>

```My [color=red]<<< ???[/color] is there because that line doesn't appear to be valid XML. Delete that line too.

---

### Post by mustang on 2005-09-05
[QUOTE=Lux Perpetua]```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--            [color=red]<<< delete this[/color]
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->             [color=red]<<< delete this[/color]
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->             [color=red]<<< ???[/color]
<!-- Uncomment below to enable the freetype autohinter module -->
<!--
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
-->
</fontconfig>

```My [color=red]<<< ???[/color] is there because that line doesn't appear to be valid XML. Delete that line too.[/QUOTE]

Done...still nothing :(

I've pretty much resigned to my fate...I need a new, bigger monitor.

---


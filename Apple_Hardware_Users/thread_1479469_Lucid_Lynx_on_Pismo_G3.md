---
title: "Lucid Lynx on Pismo G3"
date: 2010-05-10
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-05-10
Installation of Lucid Lynx (netboot) went excellent. I am posting it from within my new system. I had no problems getting my Broadcom PCMCIA wireless card to work. The [xorg.conf file from Karmic]("http://mac.linux.be/content/xorgconf-file-pismo-karmic-koalalucid-lynx") still works.

What I found was that the [Lenny xorg.conf]("http://mac.linux.be/content/g3-powerbook-pismo-modelines") file gave me low graphics mode. This is interesting as I saw other people having the same low graphics problem. I think I know the answer to this now. You need a modeline for your resolution.

[These modelines can be made with cvt]("http://mac.linux.be/content/setting-xorgconf-manually-xrandr"), a tool to create modelines. An idea for those of you running Karmic or Lucid in low graphics mode but in the right resolution is to add the modeline to the monitor section.

This is how my monitor section looks like in Lucid:

```
Section "Monitor"
	Identifier	"Standardbildschirm"
	HorizSync	28-51
	VertRefresh	43-60
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection
```

---

### Post by linuxopjemac on 2010-05-11
I have to admit that I am very impressed by the short boot and shutdown time. Sleep by closing the lid also works fine on my Pismo. The only thing that does not work well, is the Gnome desktop on my old machine, it's a little too bloated and therefore slow. I will try the lubuntu-desktop soon. Good work developers!

---

### Post by Cygni on 2010-07-06
Absolutely agreed. Lucid has to be one of the easiest installs of Ubuntu on a Pismo that I've encountered. Great functionality right out of the box.

---


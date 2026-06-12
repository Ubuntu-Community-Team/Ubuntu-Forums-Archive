---
title: "Can not change brightness and volume - but it shows them changing ..."
date: 2012-12-20
forum: Any Other OS
---

### Post by mind_exploit on 2012-12-20
Hey, Guys,

For two weeks I have CrunchBang and there is one thing that still can't figure out: if I use the key shortcuts for modifying the screen brightness or  the volume - (Fn + F2/F3 and Fn + F9/F10) - I see indication that it's  changing - but nothing changes actually.

(I can modify the volume  with the mouse from the "Volume control", but I'd prefer the keys  combinations. Also - the other combinations works fine - turn on/off the  touchpad or the wireless.)
I'm on Toshiba Satellite P855. Do you have any idea?

Thanks in advance [IMG]http://crunchbang.org/forums/plugins/ezbbc/style/smilies/wink.png[/IMG] ... 

PS:  I searched for this already, and from what I've found I tried some  things in the /etc/default/grub file, so now the line that starts with
```
GRUB_CMDLINE_LINUX_DEFAULT
```now looks like
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor noapic"
```But nothing helped so far [IMG]http://crunchbang.org/forums/plugins/ezbbc/style/smilies/sad.png[/IMG] ... can you help me please ... cause it's like watching the sun directly and my eyes are like burning ...

---

### Post by mind_exploit on 2012-12-21
1. Installed xbacklight, and when I try xbacklight -set XX or -dec XX or -inc XX - it gives me:
 
```
No outputs have backlight property 
```I tried with 

```
sudo setpci -s 01:00.0 F4.B=50
```("lspci -nn | grep VGA" returned "01:00.0 VGA ...")

But it did nothing. Restarted - and still the same. The screen brightness just burns my eyes.

---

### Post by mind_exploit on 2012-12-24
Hey there,

So, I decided to try different variants, and to see on what distro actually I'll be able to change brightness, no matter how - from command or some gui. So, I installed OpenSUSE 12.2 Gnome - very nice, but no way to change screen brightness, then installed Mint 14 Cinnamon - the same there. After that I installed Kubuntu 12.10. And then I found out that the KGamma has the ability to change the Gamma of the screen. And voila - now the screen doesn't burn my eyes when I watch it.

SO, now I'm with Kubuntu 12.10, and from the KGamma I'm able to make the screen OK. (Don't know if I'm changing the brightness actually, or maybe something else ... but the result is OK.)


PS: although there are some things that annoys me here too ... for example I don't have any autocomplete in the shell, and also - I have sound only from the headset, but not from the built-in speakers ...   ...

---


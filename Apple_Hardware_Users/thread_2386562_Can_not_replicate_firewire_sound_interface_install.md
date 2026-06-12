---
title: "Can not replicate firewire sound interface install on my fresh install on 16.04 LTS"
date: 2018-03-07
forum: Apple Hardware Users
---

### Post by rlajos on 2018-03-07
I would appreciate any help on following:

I read a post about installing firewire sound interface (ART Tubefire 8) on Ubuntu Jaunty (9.04) installation.
([http://ffado.org/?q=comment/311#comment-311](http://ffado.org/?q=comment/311#comment-311))

I installed Ubuntu (32bit)  on my old MacBook (late 2006), upgraded RAM to maximum 3GB, but unfortunately could not replicate the above mentioned sound interface install.

Maybe the file and directory system has been changed in between (9.04 and 16.04) but I can't find files, folders mentioned in this tutorial.

What I know:
[COLOR=#000000][FONT=Menlo]/etc$ lspci | grep -E -i "(1394|firewire)"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]03:03.0 [COLOR=#c33720]**FireWire**[/COLOR] (IEEE [COLOR=#c33720]**1394**[/COLOR]): LSI Corporation FW322/323 [TrueFire] [COLOR=#c33720]**1394**[/COLOR]a Controller (rev 61)

[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]For me it seems that the firewire interface is detected.

I am trying to use Ardour as DAW but the Jackaudio (QjackCtl) does not [/FONT][/COLOR][FONT=arial][COLOR=#000000]recognize the firewire interface. (In the Setup, Driver: Firewire, Interface: (default) only. So there is no known firewire interface.

So I am stocked...

Best,

Lajos[/COLOR][/FONT]

---


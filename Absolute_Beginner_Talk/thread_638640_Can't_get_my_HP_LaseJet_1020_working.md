---
title: "Can't get my HP LaseJet 1020 working"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-12
Hi, I've looked around the site and this seems
to be a problem with everyone that has this printer.
Do you think that the Ubuntu Team will fix it and add
the correct drivers?  Well, my question is this, I'm
kinda new to Ubuntu and need your help. I've read all
the post about the 1020 being an issue to get working
but a few people have reported that they got it working
by downloading some new drivers... When someone tells
me just to go somewhere and download things that
is not in the repository I worry.....  Could someone
tell me if this is a site that is ok to download and install
from.... thank you

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

---

### Post by mahiyar on 2007-12-12
Where support for such  things is so minimal I do not see any harm in trying it. The site looks reasonably detailed. I too had problems with my scanjet 2400, unsupported by sane, and I managed to download drivers from some obscure site, worked like a charm. In spite of informing the sane guy about existence of the drivers, in sane still shows as unsupported.

---

### Post by philinux on 2007-12-12
Looks like a well documented procedure too.

---

### Post by Malta paul on 2007-12-12
Hi, I have a HP laser jet and got it to work with a bit of research.
The important thing with these printers is that they require some firmware to be installed (once) as well as a driver,
Check out [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)
for your printer Firmware Terminal input commands, and the driver info.
Hope this helps, It will work when set up, 
Good luck  :)

---

### Post by Orbital75 on 2007-12-12
ah...... So if I do this firmware install will the printer still work in windows?
That's flashing the printers mem correct, kinda like a Bios upgrade?
Sounds dangerous?

---

### Post by HermanAB on 2007-12-12
No, the firmware is loaded at each power up of the printer.

H.

---

### Post by Malta paul on 2007-12-12
As HermanAB said the firmware will not effect Window operation, as it is only used with linux, When using Windows your HP windows drives will work the printer.
Don't worry you won't trash your computer :)

---

### Post by Orbital75 on 2007-12-12
Good deal..... I just didn't want to flash my Printers firmware.
I'll get to work on this when I get home and see if I can get
this working.... I really love Ubuntu but I have to have a Printer :)

---

### Post by stchman on 2007-12-12
> **Orbital75 said:**
> Hi, I've looked around the site and this seems
to be a problem with everyone that has this printer.
Do you think that the Ubuntu Team will fix it and add
the correct drivers?  Well, my question is this, I'm
kinda new to Ubuntu and need your help. I've read all
the post about the 1020 being an issue to get working
but a few people have reported that they got it working
by downloading some new drivers... When someone tells
me just to go somewhere and download things that
is not in the repository I worry.....  Could someone
tell me if this is a site that is ok to download and install
from.... thank you

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

I have procedure to get that printer working under Ubuntu Gutsy or Feisty.  I have a LaserJet 1000 working perfectly under Feisty.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Follow the instructions precisely for your distribution.  Gutsy and Feisty have different scripts to run.  Remember to use 1020 for your printer model.

---

### Post by Orbital75 on 2007-12-12
Thank you stchman, I will give that a try.
Looks nice and easy....... :)

---

### Post by Orbital75 on 2007-12-13
stchman, Sorry I didn't have time to try that yesterday but I will this evening.
I do have a quick question about your instructions. Below when you wrote.

If you have a Laserjet 1000 then substitute 1000 for <foo2zjs_identifier>.  A number other than one from the chart will cause the script to terminate.

do you mean <foo2zjs_1000>   or do you mean <1000>

Thank you for your help :KS

---

### Post by stchman on 2007-12-13
> **Orbital75 said:**
> stchman, Sorry I didn't have time to try that yesterday but I will this evening.
I do have a quick question about your instructions. Below when you wrote.

If you have a Laserjet 1000 then substitute 1000 for <foo2zjs_identifier>.  A number other than one from the chart will cause the script to terminate.

do you mean <foo2zjs_1000>   or do you mean <1000>

Thank you for your help :KS

Since you have Gutsy (according to your profile), and a 1020 printer use this CLI syntax assuming you have followed the instructions precisely.

```
sudo ~/ubuntu_foo2zjs_install_gutsy.sh 1020
```

I substituted 1020 for the <foo2zjs_identifier>, this tells the script your make/model of printer.  When you see command line terminology, items enclosed in <> are mandatory while items enclosed in [] are optional.  This is pretty universal.  You don't actually type the < or >.

Hope this helps.

---


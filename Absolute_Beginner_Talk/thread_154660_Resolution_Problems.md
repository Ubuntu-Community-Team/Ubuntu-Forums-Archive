---
title: "Resolution Problems"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by new2linux2009 on 2006-04-03
My graphics card has the ability to go up to 1024 X 768 (which is what I need), but for some reason it is only giving me the option of about half that....as a result there is this huge frame around the screen and my desktop (sry if that is not a term used in linux i just stop using windows) is very small and does not fill up my whole laptop screen.  Please tell me how to change this.  If there is a command needed, please tell me where I type it and how to get there as I am new to Linux.  Thank You.  I do not want to give up Ubuntu because of its AWESOME support.

---

### Post by Perfect Storm on 2006-04-03
First try with in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

Reboot.

---

### Post by new2linux2009 on 2006-04-03
that brought me to a complicated setup could you please tell me what to select my desired resolution is 1024 X 768

---

### Post by new2linux2009 on 2006-04-03
oh no now that i tried to go through the setup myself ubuntu would work.  It says there are errors with my graphics

---

### Post by new2linux2009 on 2006-04-03
guess i'll just have to install fedora](*,)

---

### Post by catlett on 2006-04-03
[http://support.dell.com/support/edocs/systems/ins5100/en/index.htm](http://support.dell.com/support/edocs/systems/ins5100/en/index.htm)
Follow that link and get a copy of the Inspiron manual. Go to the Specifications page. If you have your father's computer keep that next to you with the information on the screen. That set up will need to know about your specifications. Take your time. You don't have to rush through it. When it asks you a question about your computer look it up in the manual. Some of the set up you can go with the defaults. Like the type of keyboard, keyboard layout and mouse. When it comes to your monitor pick the advanced mode and enter the resolutions from the specs.

This is a walk through for Slackware but it is pretty much the same. Just choose Gnome at the end instead of their choice for window manager.  [http://www.slackware.com/config/x.php](http://www.slackware.com/config/x.php)

---

### Post by new2linux2009 on 2006-04-03
fedora wasn't all it was cut out to be so i'm reinstalling ubuntu (for the millionth time) lol...Thank You all for your help i'm going to try what you told me.

---

### Post by m.musashi on 2006-04-03
[QUOTE=new2linux2009]oh no now that i tried to go through the setup myself ubuntu would work.  It says there are errors with my graphics[/QUOTE]
If you haven't got this fixed yet, could you give a bit more info on the errors you are getting.

I just went through the sudo dpkg-reconfigure xserver-xorg again myself on a dell laptop (not the same) and I think you can pretty much use the defaults. Afterwards, do a ctrl-alt-backspace or just reboot. In theory that should get it working. Although, in theory you shouldn't even be having this problem. I've put ubuntu on several dell laptops and all of them configured correctly out of the box. Perhaps something in you system is different.

BTW, what version are you using? Dapper is certainly the better one but it isn't really ready yet for everyday use unless you like to fix/tweek things so you should be installing Breezy 5.10. With that version you can also use a nice tool called automatix (sorry don't have a link at the moment) to add a bunch of nice features.

Good luck. And catlett is right -- take it easy and don't flip out. Think of it as a nice adventure and with any adventure half the fun is just getting there. I'm still not there yet :).

Also good luck with FC5. I couldn't even get it to install.

---

### Post by new2linux2009 on 2006-04-03
how do i know which driver to select?:( 
my choices are i128, i740, i180, imstt, mga, neomagic, new port, nsc, nv, rendition, rival28, s3, s3virge, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, and vimware.  For system specs, please check the link above that has been graciously provided for me. Thanks for Any Help.](*,) :-D

---

### Post by new2linux2009 on 2006-04-03
sry few more choices i missed ;)....
apm
ark
ati
chips
cirrus
cirrus_alpine
cirrus_laguna
cyrix
fbdev
glide
glint

---

### Post by ndhskp on 2006-04-03
[quote=new2linux2009]how do i know which driver to select?:( 
my choices are i128, i740, i180, imstt, mga, neomagic, new port, nsc, nv, rendition, rival28, s3, s3virge, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, and vimware.  For system specs, please check the link above that has been graciously provided for me. Thanks for Any Help.](*,) :-D[/quote]What kind of video card do you have.  Nvidia, Ati or some other manufacture.  For example an Nvidia card would use "nv" while an Ati card would use a different driver.  Try this enter the driver name in google along with your specific type of video card.  If you don't know what specific card you have you need to find out.

---

### Post by m.musashi on 2006-04-03
[QUOTE=new2linux2009]how do i know which driver to select?:( 
my choices are i128, i740, i180, imstt, mga, neomagic, new port, nsc, nv, rendition, rival28, s3, s3virge, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, and vimware.  For system specs, please check the link above that has been graciously provided for me. Thanks for Any Help.](*,) :-D[/QUOTE]
When I run the  sudo dpkg-reconfigure xserver-xorg it gives the option to auto detect and then defalults to the ATI driver (I have ATI card). What does it default to for you? I don't know your computer but it's probably ATI or nvidia. Later in the reconfigure it asks about resolutions. You can scroll down and see if the ones you want are *ed and if not * them.

You might also post the contents of /etc/X11/xorg.conf so we can look it over and see if there is anything odd or easily changed.

---

### Post by new2linux2009 on 2006-04-03
Still need help here....](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by new2linux2009 on 2006-04-03
never mind ^^^^^^lol

---

### Post by new2linux2009 on 2006-04-03
I have a AGP video card to see futher info see the link that one of you provided me as i mentioned before. Thanks :)

---

### Post by m.musashi on 2006-04-04
[QUOTE=new2linux2009]I have a AGP video card to see futher info see the link that one of you provided me as i mentioned before. Thanks :)[/QUOTE]
Dude, don't mean to burst your bubble but AGP is not a video card but a video interface (is that the right description?). The two main ones are AGP and PCI-E. I don't believe this is really all that important for your issue. Knowing the chipset or controler is - ATI, nvidia, etc. I skimmed through the specs for your computer but I can't figure out your video. It is integrated into the board and looks like Intel but that is not an option in the xorg.conf.

If you are still having trouble then I suggest using the 'vesa' driver as it seems to work with just about system.

> Still need help here....
One more thing, this type of post isn't very useful. Give a clear and concise explanation of the problem and then patiently wait for a response. In the meantime, do some reading up on your system. At the very least you should be familiar with the hardware.

---


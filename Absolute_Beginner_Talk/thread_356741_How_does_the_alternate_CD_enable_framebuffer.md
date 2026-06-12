---
title: "How does the alternate CD enable framebuffer?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by DARKGuy on 2007-02-08
Greetings. I'm posting under links so sorry for any errors or formatting problems that might happen (but I dunno, this is my first time -posting- in Links so... (it's cool! xD)

I've been wondering, how does the alternate CD enable the framebuffer? I've been having some problems in the past trying to enable it in this config (b/w monitor + trident 9660) but somehow the alternate CD does it "right" (or at least, I can notice it's "graphic mode" because this card has a peculiarity (spelling?) to sometimes place weird small garbage on the screen when a vesa-like mode is set (I come from an MS-DOS world, so excuse me if it isn't really the vesa under linux, I don't know) so that's why) and I would like to know how it does it.

I have no idea where to start searching, as I barely know some of the "system commands" to get internal info, to say it that way. My guess would be that there are some options passed to the kernel, but pressing F6 at the boot splash screen shows nothing relevant. I'd like to know what does the CD do when it says "Trying to enable the framebuffer". I've typed dmesg and I see it starts some kind of VGA16 fullscreen color mode (?) but I don't know how to apply that to my current config.

Any help would be greatly appreciated :D

---

### Post by teaker1s on 2007-02-08
to configure graphics features you need to at grub select boot recovery then at a comandline
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
will bring up graphical config tool,when finished
[COLOR="Red"]sudo reboot[/COLOR]

---

### Post by DARKGuy on 2007-02-08
> **teaker1s said:**
> to configure graphics features you need to at grub select boot recovery then at a comandline
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
will bring up graphical config tool,when finished
[COLOR="Red"]sudo reboot[/COLOR]

Thanks for the answer, but would that really get the parameters and stuff needed for getting the framebuffer that's applied on the alternate CD? with framebuffer I actually mean console framebuffer. If you replied that because of the screen garbage comment, don't worry about it 'cause that's the card which has a small error in it, no biggie :P everything looks correctly though :) I just need to know how to get the VGA16 or whatever mode the alternate CD uses when "enabling the framebuffer" before showing the install screen :)

---

### Post by DARKGuy on 2007-02-09
Sorry for bumping but... nobody? :confused: :(

---

### Post by confused57 on 2007-02-09
I don't know how to get the framebuffer info from the alternate cd, but I found this discussion about fb with Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=23268&highlight=vga%3D792](http://www.ubuntuforums.org/showthread.php?t=23268&highlight=vga%3D792)

After installing Gentoo, I found that framebuffer didn't work for me when switching from X to console, I had added vga=792  to the kernel line in boot/grub/menu.lst file to enable framebuffer.

I think you add parameters to the kernel line for framebuffer, e.g. "vga=normal" would disable framebuffer, I don't have the list of resolutions specified for vga=xxx for enabling framebuffer.

This probably doesn't help you, least I bumped your thread again.  In all honesty, I'm not exactly sure how framebuffer is utilized...with framebuffer on, fonts in console were much smaller(higher resolution?), without framebuffer, fonts were larger(lower resolution=800x600?) in console.

Added:  I don't know if it'll work or not, but in the grub menu at bootup, highlight your entry to boot Ubuntu, press "e", to edit, then try adding a vga=xxx to your kernel line & try to boot(I think you press "b" to boot)...this change is only temporary, so it shouldn't harm your current setup.  There are probably framebuffer configuration files that can be edited, but that's completely out of my league.

---

### Post by DARKGuy on 2007-02-11
Actually, I've tried stuff like that, and vga=792 (or 791) don't seem to have any effect, nor any others I've tried. In fact they say "invalid video mode" and roll back to the vga=scan parameter, which then asks me which video mode I want. All it changes are the row&cols of the screen, but there's no real framebuffer at all, that I can see.

Framebuffer in console just adds the ability to have graphics in it (like the Knoppix boot screen, which has a pengüin on the top-left corner of the screen, along with text) and higher text resolution, more colors too!. Without framebuffer, you can only change the row&col size, you'll get smaller text too if you wish, but it won't archieve the same effect - it's still text-only, no graphics involved.

I'm just curious on the boot process of the alternate CD. I guess I'm gonna try some of the commands found in the thread you just linked to me, but I'm sure someone has tinkered with the alternate CD and maybe knows what strange stuff it does for enabling framebuffer that way.

Thanks for answering though! :)

---

### Post by DARKGuy on 2007-02-14
:bump: :( ?

---

### Post by DARKGuy on 2007-02-15
Man, I hate bumping and looking like a total n00baz0r and annoying guy, but I really want to know a solution for this... :(

---

### Post by mcduck on 2007-02-15
As far as I know the alternate cd doesn't have framebuffer enabled. The installer uses ncurses which doesn't need any graphics support.

Of course I may be wrong, but I've never seen anything that would require framebuffer used in Ubuntu by default.

---

### Post by owenm on 2007-02-27
> **mcduck said:**
> As far as I know the alternate cd doesn't have framebuffer enabled. The installer uses ncurses which doesn't need any graphics support.

Of course I may be wrong, but I've never seen anything that would require framebuffer used in Ubuntu by default.

It does use a framebuffer mode - if it causes problems you can turn it off and use VGA text mode as per the instructions here:

[https://answers.launchpad.net/ubuntu/+ticket/3657](https://answers.launchpad.net/ubuntu/+ticket/3657)

(short answer at boot of the alternate CD, pass options to the kernel as follows: linux fb=false video=vga16:off)

Very useful if trying to install the netboot mini.iso under Virtual PC 2004!

---


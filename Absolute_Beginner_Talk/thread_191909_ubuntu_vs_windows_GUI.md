---
title: "ubuntu vs windows GUI"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-06-08
i just installed ubuntu and starting to learn about it.

i notice the gui is slower compared to windows, is this true or am i imagining things?

---

### Post by Azr3n on 2006-06-08
[FONT="Verdana"][SIZE="2"]Were you refeering to the "drawing" of the windows? Cos I'd assume thats from using the default video Drivers - Try updating. Or was it somethiung else[/SIZE][/FONT]

---

### Post by verbatim210 on 2006-06-08
well at the moment im just playing around with my new ubuntu, quite exciting actually.

clicking around, browsing, surfing, testing out all the new stuff i've never seen before.  basically it seems like its ubuntu is lagging.

doesn't happen to ne1 else?

---

### Post by bruce89 on 2006-06-08
Firefox is slow on Ubuntu, as it doesn't use GTK+.  Also the proper graphics drivers speed things up lots.

---

### Post by verbatim210 on 2006-06-08
agreed.  i notice my computer slowing down as i opened more firefox windows.

"proper graphics drivers" how do i go about upgrading/updating to make sure my system runs at its bests?

thanks

---

### Post by bruce89 on 2006-06-08
Are you using an ATI card or a nVidia one?

---

### Post by verbatim210 on 2006-06-08
Ati

---

### Post by bruce89 on 2006-06-08
Follow these instructions - [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by verbatim210 on 2006-06-08
cheers i'll have a look now see how it goes, with lucky it might speed things up a bit.

also im starting to think maybe its not the gui thats slow.

cpu and memory?

---

### Post by MeneK on 2006-06-08
I noticed a great improvement after moving to a specific kernel package. If you are using the default 386 image, try installing the 686 or k7 one (with or without SMP).

---

### Post by bruce89 on 2006-06-08
686 for an Intel processor and k7 for AMD ones.

---

### Post by verbatim210 on 2006-06-08
the only types i see that are available for download is: 

i386
AMD64

---

### Post by MeneK on 2006-06-08
[QUOTE=verbatim210]the only types i see that are available for download is: 

i386
AMD64[/QUOTE]

Try searching for "linux-image" in the package manager.

---

### Post by u.b.u.n.t.u on 2006-06-08
[QUOTE=verbatim210]i just installed ubuntu and starting to learn about it.

i notice the gui is slower compared to windows, is this true or am i imagining things?[/QUOTE]

Which windows are you refering to?

ubuntu is faster than XP Pro.

---

### Post by bruce89 on 2006-06-08
"fast" is a subjective term, so it's quite difficult to compare.

---

### Post by verbatim210 on 2006-06-08
its not a matter of fast or slow, i think my unbuntu is NOT running properly.

...which is the reason its running slow, so yeh.

im reinstalling it now, i cant find the 686 image so i'll just try the ati driver thing after its finished.

i suspect hardware compatibility or my drivers need to be updated.

---

### Post by bruce89 on 2006-06-08
[QUOTE=verbatim210]I'm reinstalling it now, i cant find the 686 image so i'll just try the ati driver thing after its finished.[/QUOTE]
```
sudo apt-get install linux-686
``` will install it. (AFAIK)

---

### Post by verbatim210 on 2006-06-08
instead of installing 386 and then putting 686 over it, is there a way to do a fresh straight up installation of 686?

---

### Post by bruce89 on 2006-06-08
[QUOTE=verbatim210]instead of installing 386 and then putting 686 over it, is there a way to do a fresh straight up installation of 686?[/QUOTE]
This will install the 686 kernel beside the 386.  You will then have to search for "386" in synaptic and remove everything that starts with linux, which has 386 in it.

---

### Post by verbatim210 on 2006-06-08
thanks for that bruce, you have been a great help.

---

### Post by bruce89 on 2006-06-08
[QUOTE=verbatim210]thanks for that bruce, you have been a great help.[/QUOTE]
No problem.

---

### Post by verbatim210 on 2006-06-08
i've just finished updating my ATI drivers and i also installed the 686-linux.

the system still lags.

i think i need to update some hardware drivers or something...

---

### Post by bruce89 on 2006-06-08
Have you rebooted?

---

### Post by sherlock-holmes on 2006-06-08
[QUOTE=verbatim210]the only types i see that are available for download is: 

i386
AMD64[/QUOTE]

---delete please---

---

### Post by az on 2006-06-08
How old is your box?

I find that something like a pII will run slower than windows, in terms of snappyness and response-to-clicks at the desktop, but you will never suffer from the annoying lag that seems to happen randomly in windows.  So while the desktop is sluggish, you are more productive with Ubuntu.


Anything better than a Pentum 700 MHz will run just as fast as windows and although subjective, Ubuntu tends to be faster than windows XP on more modern hardware.

---

### Post by IYY on 2006-06-08
No GUI is as slow as Windows XP before you install the video card drivers. That's just pure pain. But of course, Linux without the proper drivers is also no dream, so you need to install them as soon as possible (and if you have a decent machine, also give XGL a try. it makes things -much- smoother)

---

### Post by lapsey on 2006-06-08
should i recompile previous software i have built under a different kernel, for example will vmware (compiled under a 386 kernel) operate any differently under a k7 kernel?

---

### Post by verbatim210 on 2006-06-08
Pentium ii 350MHz
224mb sdram
2x80gig hd

reboot still no improvement.  if windows can make the most of these limited resources, im sure ubuntu can too =)

---

### Post by BoyOfDestiny on 2006-06-08
[QUOTE=verbatim210]Pentium ii 350MHz
224mb sdram
2x80gig hd

reboot still no improvement.  if windows can make the most of these limited resources, im sure ubuntu can too =)[/QUOTE]

I'm guessing you are using 6.06... I guess you could try xubuntu. It has lower system requirements... 

There are probably better ways, but I imagine you could just install the xubuntu-desktop package. Then change the session at the login windows... Correct me if I'm wrong here people.

---

### Post by verbatim210 on 2006-06-08
i've installed 5.10 and 6.06.
im using 6.06 at the momen.
i'll try xubuntu tommorow after i download it tonight.  see how it goes.  anything else i should download/try while im at it?

---

### Post by 23meg on 2006-06-08
In terms of 2D graphics performance (window redraws, resizing, etc.) yes, Ubuntu is slower, because X is slower. In rough terms the reason is that Windows can actually utilize use your GPU to do all the dirty work, whereas in most areas X cannot do so, because fully open specs and capable drivers haven't arrived yet.

Once OpenGL-based accelerated X methods have matured this will all be history. 

What you can do to speed things up:

- Make sure your CPU is utilized properly, that its speed isn't decreased against your will by powernowd or a similar frequency scaling daemon.

- Make sure you're using the correct driver and your xorg.conf options are optimal for your hardware.

- Use a non-pixmap, light GTK theme and a fast GTK theme engine.

- Try turning off font anti-aliasing / subpixel smooting (System / Preferences / Font).

- Long term: help with XGL / AIGLX / Compiz development and testing, put pressure on ATI and NVidia for open specs and better drivers.

---


---
title: "X is messing up the console (tty's)"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by forighnewbe on 2006-11-15
Hi you all. (please excuse my misspelling, i'm not an eglish speaker)
just installed dapper and everything works fine exept :
when i press Ctrl+Alt+F.. the console is blured end dubbled
i can switch back to the X without any problem (Alt 7)
before the X is loaded the splash screen is normal
when it turned of the masages again are blured and dubled. 

couldn't google about it (what are the keywords for such problems?)
thanks from advanced .

```
lspci | grep VGA
0000:01:00.0 VGA compatible controller: Cirrus Logic GD 5465 [Laguna] (rev 03)

```

---

### Post by joshsherman on 2006-11-15
This is just a stab, but are you using an LCD?  I've found with my LCD when I was using the stock driver (prior to upgrading to the nvidia modules) the console would be blurry until I hit the button to resync the screen.  I have the same issue between Windows and Linux where I need to reset it to get everything crisp again.

-j

---

### Post by Mr Fat Bat on 2006-11-19
I'm having the same problem, whenever I switch over to any of TTY all I get is random coloured lines.  As above I also have no problems switching back to TTY 7.

---

### Post by eriefisher on 2006-11-19
tty crystal clear hear. I have an old NEC Multisync lcd and the only problem I've ever had with it is when I used it with a KVM switch. All would be good until I switched over and everything would be shifted to one side. No longer a problem because I don't use the switch any longer.

I know this not much help but it might help rule out an LCD question.

eriefisher

---

### Post by kopa on 2006-11-20
I have the same problem. On every tty console is see random colored lines. switching back to the console with the x-server running is fine.
```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```

I couldn't find a solution by now.

---

### Post by Mr Fat Bat on 2006-11-21
Anybody out there have any idea?  It's really annoying having to do everything from inside X!

---

### Post by Awale on 2006-12-09
[LEFT]Hello. I'm having the same problem as all of you, on my laptop. Not only the tty's are filled with green-pink silly lines, but also when I switch on/off the computer, there's an instant of time when you can see that strange screen too. I guess it has to do with the graphics card (im using ati radeon x1400.

I hope someone can help us with this issue!! thank her/him in advance..
[/LEFT]

---

### Post by riven0 on 2006-12-09
I don't know about you guys, but I noticed this problem after I installed the xserver updates from canonical. In my case, trying to switch to a different console does nothing. It just stays on F7. I'm still trying to figure out what could have went wrong. I need my consoles!


BTW, my card is ATI.

---

### Post by Destruct on 2006-12-09
This is my first linux distributive, i'm trying it under vmware workstation 5.5.3 build-34685. Normal ubuntu 6.10 ubuntu-6.10-desktop-i386, not kubuntu, xubuntu etc.
Host OS - WinXP Pro up-to-date.
And strangely enough exactly that thing is happening with Ubuntu consoles which are supposed to appear through ctrl+alt+fn. 
Doesn't seem to matter whether it's run in livecd mode or installed under vmware, "safe graphics mode" doesn't seem to make any difference also.
Vmware .vmx options
mks.enable3d = "TRUE"
svga.vramSize = "134217728"
don't seem to make any difference also, just like presence/absence of vmware tools installed in guest environment.
Whether vmware is in fullscreen also doesn't make any difference. It goes garbled etc and goes back to gnome desktop normally by ctrl+alt+f7.

Host environment graphic card is nvidia Geforce FX5600, forceware 93.71 drivers. Though i thought that shouldn't matter. Hardly imaginable that could be anything monitor-related also.

---

### Post by ischg on 2006-12-13
I got the same problem here. My machine has an ATI X1400 chipset and I installed the fglrx drivers (method one on [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") ).

---

### Post by mcduck on 2006-12-13
I had the same problem, but adding 'vga=792" to the end ot the kernel line in /boot/grub/menu.lst to make the boot spladh and TTY's run in 1024x768 solved the problem, now everything is working fine.

I'm running Mobility Radeon X1600 on a laptop with native resolution of 1280x800.

---

### Post by Mr Fat Bat on 2006-12-18
Thanks mcduck that worked!

Can you please just give a brief description on how that works?  Also I'm not sure if this existed before hand but now when I run fgl_glxgears I get:

> jim@Jimbuntu:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig


As I said, I'm not %100 sure if this was pre-existing ;)

---

### Post by ischg on 2006-12-20
I just stumbled across the solution: see this [howto]("http://thinkwiki.org/wiki/Installing_Ubuntu_6.10_%28Edgy_Eft%29_on_a_ThinkPad_T60#Problem:_Virtual_terminals_not_working")
Obviously there's already a bug report for the garbled virtual console out (here's the [link]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/63558"))

---


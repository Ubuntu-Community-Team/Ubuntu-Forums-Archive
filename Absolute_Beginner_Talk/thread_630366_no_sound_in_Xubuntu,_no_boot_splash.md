---
title: "no sound in Xubuntu, no boot splash"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-03
hey,

I have an Intel 82801DB-ICH4. In Ubuntu I had to enable the external amplifier, then uncheck it, then apply all the control settings to control the PCM, then I had to turn up everything full blast then turn down PCM: also, my hot-keys for turning up and down the volume aren't working, the did work in ubuntu (or should I say gnome, not xfce?)

ok

also, my boot is really slow and there is know splash screen. I solved this in ubuntu, but it involved recompiling my grub and installing it again (adding "splash" to it) where is the thread where I saw this?? I can't find it.

so, more plainly:

[B]- no sound
-no sound controlers
-no boot splash

sony vaio pcg-tr3a, intel chipset for graphics and video.[/B]

thanks a ton!

hoping to use xubuntu,
static V

---

### Post by jaybombalous on 2007-12-03
I thought the boot splash problem was a kernel frame buffer issue, grub doesn't have anything to do with that.

If u want to have text instead of a boot splash screen(which I presume is now black) edit /boot/grub/menu.lst and remove splash from lines #defoptions and #altoptions.

then issue this command

```
sudo update-grub
```

---

### Post by Teknyk on 2007-12-03
I am not sure if this applies to Xubuntu but I know it was an issue for me on Ubuntu 7.10

Check these for the splash issue.

[http://ubuntuforums.org/showthread.php?t=579568](http://ubuntuforums.org/showthread.php?t=579568)
(The steps here fixed mine)
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

As for the sound, sorry but I haven't had any issues with sound.

*EDIT*
I just realized the URL on my second link was truncated. Should work now.

---

### Post by staticvoid on 2007-12-03
I went to your first link and clicked around, finally I found the original fix that I used with Ubuntu :) Super simple fix from this thread: [http://ubuntuforums.org/showthread.php?p=3569987#post3569987](http://ubuntuforums.org/showthread.php?p=3569987#post3569987)

To fix the no boot splash I did the following,

> 1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

in the menu.lst  :: **before**

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8914b1be-a534-4519-99d7-1c982cbdfa0f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
**after**
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8914b1be-a534-4519-99d7-1c982cbdfa0f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
splash		vga=791
```

and in my /etc/usplash.conf I change it to 1280 by 768.

boot splash shows and boots faster. and don't forget step three!!  :)
copy and paste this:
sudo update-initramfs -u -k `uname -r`

those are back quotes.

***_now I need my sound fixed :(_***

thanks! I'll have it up and running in now time :) and hopefully this helps other people.
sv

---

### Post by Teknyk on 2007-12-03
lol...Yep that is the fix that is in the second link. ;)

---

### Post by staticvoid on 2007-12-03
but the second link just took me to the home page ubuntuforums.org.... wierd...

sv

---

### Post by staticvoid on 2007-12-04
> **staticvoid said:**
> but the second link just took me to the home page ubuntuforums.org.... wierd...

sv
bump. and the sound? anybody know a fix?

sv

---

### Post by mali2297 on 2007-12-04
First, check your sound with
```

aplay -vv /usr/share/firefox/res/samples/test.wav

```
Do you hear anything at all?

Post the output of
```

aplay -l
lspci -v | grep -A 5 [Aa]udio

```

As for the hotkeys, you can define them yourself. Suitable commands are
```

amixer set PCM 5%-
amixer set PCM 5%+
amixer set PCM toggle

```
(Respectively: decrease volume, increase volume and mute/unmute.)

---

### Post by staticvoid on 2007-12-04
No sound when I issued the command.
the output for** aplay -l**:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


and for** lspci -v | grep -A 5 [Aa]udio**
> 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 8144
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]


Okay. And thanks for the hotkeys settings :) Hopefully I'll have use for them soon ;)

sv

---

### Post by mali2297 on 2007-12-04
Everything in the output seems fine.. :-k

> 
In Ubuntu I had to enable the external amplifier, then uncheck it, then apply all the control settings to control the PCM, then I had to turn up everything full blast then turn down PCM


Try the corresponding thing from the terminal, see this post:
[http://ubuntuforums.org/showthread.php?t=75045?post=#10](http://ubuntuforums.org/showthread.php?t=75045?post=#10)

That is, run
```

alsamixer

```
and mess around with the options. :-)

---

### Post by staticvoid on 2007-12-04
I had to sudo apt-get install alsamixer first. Its good to know you can do it in the terminal :D Thanks for the link to that other guys findings. I'll try it out.

sv

---


---
title: "Configuring FluxBox"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-22
I really like FluxBox, it's breathed new life into my old 400 mhz 192 Ram laptop.
I had Xubuntu with Xfce which is nice, it was just a little to much for it to handle.
What I'd like is be able to rearrange some of the programs in the menu and
add some wallpaper to the Desktop.  

For example, I'd like to put the OpenOffice suite together instead of breaking
it up in groups. I'd like Firefox and Thunderbird to be together in their own
folder as well.  Also, is there a way to add programs to the Bar at the bottom.
it would be nice to have 2 or 3 programs that I use constantly sitting there.
such as Firefox, ThunderBird, and XMMS.

---

### Post by alzaf on 2007-10-22
I used fluxbox a wee while back. 

IIRC, there is a folder in your $HOME directory called .fluxbox

In there you can put the menu file which IIRC is in /usr/share/menu. All you need to do is move the entrys via any editor to get the menu to your liking.

Good luck.

---

### Post by Seisen on 2007-10-22
Check this out

[https://help.ubuntu.com/community/Fluxbox?highlight=%28fluxbox%29]("https://help.ubuntu.com/community/Fluxbox?highlight=%28fluxbox%29")

---

### Post by cknight on 2007-10-22
There's also the somewhat useful [Fluxbox wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki") where I learned how to set my background.  It also has help on all the additional configuration files.

Be sure to check out [RedSquirrel's Fluxbox menu how-to]("http://www.ubuntuforums.org/showthread.php?t=371144") as well.

As for programs you constantly use, consider thinking outside the box (as it were!) and try a different way of working with these programs which is the beauty of Fluxbox for me.  Put those constantly used programs at the top of your menu list.  Then right-click on the desktop to have immediate access to them.  

Or, and this is where it gets real fun, set up keyboard shortcuts (~/.fluxbox/keys) to these items.  I've got my Windows key + F key bound to Firefox, and Windows-T bound to Thunderbird.  Super quick to launch and with the apps configuration file (~/.fluxbox/apps) you can even specify pre-defined dimensions, location, workspace and other variables as to where and how to launch these.

Or even launch them at startup by putting them in the startup file (~/.fluxbox/startup).  Keys, apps, menu and startup configuration files are all covered in the wiki link above.  Have fun!

---

### Post by Orbital75 on 2007-10-22
Ah, I see now......  Great Link by the way.
I added Flux to my already XFCE so that's why
I have just this in my .fluxbox menu file.

```
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]
```

I guess that was created when RedSquirrel told me
to use this command to get a menu.

```
sudo update-menus
```

Now All That I have to do is Add my own code above the
[included] tag.  By doing something similar to this.

```
[begin] (fluxbox)
        [exec] (Evolution) {/usr/bin/evolution}
        [exec] (GAIM) {/usr/bin/gaim}
        [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login}
        [exec] (Epiphany) {/usr/bin/epiphany}
        [exec] (BMP) {/usr/bin/beep-media-player}
        [exec] (Xine) {/usr/bin/xine}
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]
```

Thank you for the help guys.......

---


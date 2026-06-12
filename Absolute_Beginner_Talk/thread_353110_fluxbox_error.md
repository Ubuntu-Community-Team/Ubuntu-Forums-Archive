---
title: "fluxbox error"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by g1gabyt3 on 2007-02-04
Hi all, I decided to install fluxbox today so that I had a lighter desktop other than gnome.  So i went into synaptic manager, typed in fluxbox, click on fluxbox and installed it.  All went well and I had fluxbox in my session manager.  I boot to fluxbox and all I have is a grey screen with a smal ltoolbar at the bottom the the time.  I right click the desktop and a tiny box appears that says fluxbox and nothing else.  No apps, no menus, nothing, just the screen described above.  what am i missing here?  did i have a bad install and just not notice it?  I really could use some direction on this.

Thanks

P.S. in case you need to know, I'm on an OLD laptop.  400Mhz PII, 384Mb of RAM and 8Megs of video.

---

### Post by arthurD on 2007-02-05
what release are you using?
I'm using dapper, and just installed fluxbux with aptitude - everything works fine.
So you might want to try
```

sudo aptitude reinstall fluxbox

```

---

### Post by kerry_s on 2007-02-05
You didn't do> sudo update-menus <so it can create the menu, make sure "menu" is installed.

Don't forget if you use nautilus it has to be launched> nautilus --nodesktop
I recommend thunar or rox instead, you might also want to grab eterm to set the background.
Here's my old menu, if you want to change it to your needs->

```
[begin] (Fluxbox)

[exec] (Thunar) {Thunar} 

[exec] (Terminal) {xfce4-terminal} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Gxine) {gxine}
 [exec] (VLC) {wxvlc}
 [exec] (Mplayer) {gmplayer}
 [exec] (Wmix) {wmix}
 [exec] (Kill-Wmix) {killall wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Thunar) {gksu Thunar /}
 [exec] (Terminal-Root) {gksu xterm}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {xfrun4}

[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exec] (Screen Off) {/home/user/.screen-off}
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---


---
title: "Fluxbox Question"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Dylock on 2006-12-16
So I just installed FluxBox a few minutes ago and went to go check it out. I log and change my session to FluxBox and log in. I have a pretty simple layout which is what I expected. However my problem lies with the menu. I have a feeling it isn't working right. I right click and it shows a menu but the only item on the menu it just some text that says FluxBox. I have checked my ~/.fluxbox/menu and here is what is in it

[begin] (fluxbox) {} <>
    [Programs] () {} 
        [Terminal] (aterm) {aterm -ls -tr -trsb -fg gray -fade 60} <>
    [end]
    [include] (/etc/X11/fluxbox/fluxbox-menu) {} <>
[end]

Any ideas?

---

### Post by tbroderick on 2006-12-16
Try installing fluxconf. It includes a simple menu editor called fluxmenu.

---

### Post by Dylock on 2006-12-16
yes i have installed it and tried the menu editor, however the menu still seems to only have that fluxbox text

apparently there is supposed to be a tool called fluxbox-generate_toolbar but it doesn't seem to exist in my /usr/bin

---

### Post by tbroderick on 2006-12-16
It's fluxbox-generate-menu you want.

---

### Post by Dylock on 2006-12-16
aye i tried fluxbox-generate_menu and command was not found. I'm wondering if something is missing from the install from Synaptic

After i installed the flux tools i have the following command available:
fluxbare  fluxbox   fluxconf  fluxkeys  fluxmenu

---

### Post by tbroderick on 2006-12-16
I don't have fluxbox installed right now, but check in /usr/share/doc/fluxbox.

---

### Post by kerry_s on 2006-12-16
run> sudo update-menus <in terminal
or change /.fluxbox/menu
[include] (/etc/X11/fluxbox/fluxbox-menu)
to
[include] (~/.fluxbox/fluxbox-menu)

then you can just > update-menus <as normal

here's my menu in case you want to snag some ideas->

```
[begin] (Fluxbox)

[exec] (Files) {emelfm} 

[exec] (Terminal) {xterm} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Gaim) {gaim}
 [exec] (Downloads) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Other)
 [exec] (Mplayer) {gmplayer}
 [exec] (Burner) {xfburn}
 [exec] (Wmix) {wmix}
 [exec] (Kill-Wmix) {killall wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Files) {gksu emelfm}
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
[exec] (Run Program) {fbrun}
[exec] (Keyboard) {xvkbd -no-keypad}

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

### Post by Dylock on 2006-12-16
hey thanks i got it working

i can finally start messin around with it

---


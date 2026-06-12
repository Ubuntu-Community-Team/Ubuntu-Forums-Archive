---
title: "no menu problem in fluxbox"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by rackne on 2006-09-23
i got a problem with using fluxbox. i cant get to the menu. i right-click anywhere on the desktop but all i get is a menu that says fluxbox and that's it. no submenus, no nothing. what's more none of the keyboard shortcuts work so i cant log out. is there a file i should've configured before using fluxbox?

---

### Post by lonce on 2006-09-23
The only time I have used FluxBox is when I installed Fluxbuntu.  The forums at the fluxbox site are really good.  If you just type fluxbox into google it will take you to their forums.

---

### Post by christhemonkey on 2006-09-23
The default fluxbox install does not have a menu file included.
You need to edit the .fluxbox/menu file:
```
gedit .fluxbox.menu 
```
and then paste this into it:
> [begin] (Fluxbox) {}
   [exec] (Gaim) {/usr/bin/gaim}
   [exec] (Firefox) {/usr/bin/firefox}
   [exec] (Irssi) { x-terminal-emulator -T "irssi-text" -e /usr/bin/irssi-text}
   [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login}
   [exec] (BMP) {/usr/bin/beep-media-player}
   [exec] (VLC) {/usr/bin/vlc}
   [exec] (F-Spot) {/usr/bin/f-spot}
   [exec] (Acrobat Reader) {/usr/bin/acroread}
   [submenu] (Apps) {}
        [submenu] (Editors) {}
            [exec] (Emacs) {/usr/bin/emacs21}
            [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano}
        [end]
        [submenu] (Net) {}

            [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet}
            [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html}
        [end]
        [submenu] (Programming) {}
            [exec] (Python) { x-terminal-emulator -T "Python (v2.4)" -e /usr/bin/python2.4}
        [end]
        [submenu] (Shells) {}

            [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i}
            [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login}
        [end]
        [submenu] (System) {}
            [exec] (gkrellm) { /usr/bin/gkrellm }
            [submenu] (Admin) {}
                [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e /usr/sbin/su-to-root -p root -c /usr/sbin/alsaconf}
                [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e /usr/sbin/su-to-root -p root -c /usr/sbin/pppconfig}
            [end]
            [exec] (aptitude) { x-terminal-emulator -T "aptitude" -e /usr/bin/aptitude}
            [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf}
            [exec] (GDM flexiserver) {gdmflexiserver}
            [exec] (GDM flexiserver in Xnest) {gdmflexiserver -n}
            [exec] (GDM Photo Setup) {gdmphotosetup}
            [exec] (GDM Setup) {gksu gdmsetup}
            [exec] (pstree) { x-terminal-emulator -T "pstree" -e /usr/bin/pstree.x11}
            [exec] (reportbug) { x-terminal-emulator -T "reportbug" -e /usr/bin/reportbug --exit-prompt}
            [exec] (Run as different user) {/usr/bin/gksuexec}
            [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top}
            [exec] (X-Terminal as root) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator}
        [end]
    [end]
    [submenu] (Help) {}
        [exec] (Info) { x-terminal-emulator -T "Info" -e info}
    [end]
    [submenu] (WindowManagers) {}
        [restart] (FluxBox) {/usr/bin/fluxbox}
    [end]
    [config] (Configuration) {}
    [submenu] (Styles) {}
        [stylesdir] (/usr/share/fluxbox/styles) {}
        [stylesdir] (~/.fluxbox/styles) {}
    [end]
    [workspaces] (Workspaces) {}
    [reconfig] (Reconfigure) {}
    [restart] (Restart) {}
    [exit] (Exit) {}
[end]



See this guide:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

### Post by kerry_s on 2006-09-23
Run> sudo update-menus <or> update-menus

---

### Post by rackne on 2006-09-23
thank you guys. that helped a lot. everything's fine now.

---

### Post by Drone4four on 2007-11-30
this is a useful thread because it solves my problem

---


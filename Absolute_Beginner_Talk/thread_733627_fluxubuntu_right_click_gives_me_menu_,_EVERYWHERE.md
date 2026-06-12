---
title: "fluxubuntu right click gives me menu , EVERYWHERE"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-03-24
So I fiiddled around with the settings in fluxconf or something .But the reult is that now I get a menu when I Right Click ANYWHERE this includes on an open window . It also causes the workspace to change when I move the mouse wheel up or down to in fact scroll down in an poen window . Its like the desktop is in front of every window . Any idea on how to change it . It was working fine till I changed things .

---

### Post by herbster on 2008-03-24
Paste your ~/.fluxbox/menu and your ~/.fluxbox/keys.

---

### Post by arjayes on 2008-03-24
~/.fluxbox/keys
> 
[begin] (Fluxbuntu) {} <>
    [exec] (Run...) {fbrun -title "Run..." -h 35} <>
    [separator] () {} <>
    [exec] (Editor) {leafpad} <>
    [exec] (File Browser) {rox-filer} <>
    [exec] (Web Browser) {firefox} <>
    [exec] (Terminal) {uxterm} <>
    [separator] () {} <>
    [include] (/etc/X11/fluxbox/fluxbox-menu) {} <>
[end]

/etc/X11/fluxbox/fluxbox-menu   :
> 
# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)
# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [submenu] (Applications) {}
      [submenu] (Network) {}
         [submenu] (Communication) {}
            [exec] (Pidgin) {/usr/bin/pidgin} </usr/share/pixmaps/pidgin-menu.xpm>
         [end]
      [end]
      [submenu] (Terminal Emulators) {}
         [exec] (XTerm) {xterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
         [exec] (XTerm (Unicode\)) {uxterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
      [end]
   [end]
   [submenu] (Apps) {}
      [submenu] (Editors) {}
         [exec] (AbiWord Word Processor) {/usr/bin/abiword} </usr/share/AbiSuite-2.4/icons/menu.xpm>
         [exec] (LeafPad) {/usr/bin/leafpad} </usr/share/pixmaps/leafpad.xpm>
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} </usr/share/nano/nano-menu.xpm>
      [end]
      [submenu] (Graphics) {}
         [exec] (Dia) {/usr/bin/dia-normal} </usr/share/pixmaps/dia_menu.xpm>
      [end]
      [submenu] (Net) {}
         [exec] (Claws Mail) {/usr/bin/claws-mail} </usr/share/pixmaps/claws-mail-32x32.xpm>
         [exec] (kazehakase) {/usr/bin/kazehakase} </usr/share/pixmaps/kaze_icon.xpm>
         [exec] (network-config) {/usr/bin/network-config} <>
         [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet} <>
         [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html} <>
      [end]
      [submenu] (Programming) {}
         [exec] (Python (v2.5\)) { x-terminal-emulator -T "Python (v2.5)" -e /usr/bin/python2.5} </usr/share/pixmaps/python2.5.xpm>
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (Sound) {}
         [exec] (Alsamixergui) {/usr/bin/alsamixergui} </usr/share/pixmaps/alsamixergui.xpm>
         [exec] (wmXMMS) {/usr/bin/wmxmms} </usr/share/pixmaps/wmxmms.xpm>
         [exec] (XMMS) {/usr/bin/xmms} </usr/share/pixmaps/xmms.xpm>
      [end]
      [submenu] (System) {}
         [submenu] (Admin) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
            [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e su-to-root -p root -c /usr/sbin/pppconfig} <>
         [end]
         [exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
         [exec] (Change X11 resolution (gvidm\)) {/usr/bin/gvidm} <>
         [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf} </usr/share/pixmaps/pppoeconf.xpm>
         [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} </usr/share/pixmaps/pstree16.xpm>
         [exec] (ROX Filer) {/usr/bin/rox} <>
         [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} </usr/share/synaptic/pixmaps/synaptic_32x32.xpm>
         [exec] (Task selector) { x-terminal-emulator -T "Task selector" -e su-to-root -c tasksel} <>
         [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} </usr/share/pixmaps/gksu-debian.xpm>
      [end]
      [submenu] (Tools) {}
         [exec] (fbpager) {/usr/bin/fbpager} <>
         [exec] (fluxconf) {/usr/bin/fluxconf} <>
         [exec] (fluxkeys) {/usr/bin/fluxkeys} <>
         [exec] (fluxmenu) {/usr/bin/fluxmenu} <>
         [exec] (Xarchiver) {/usr/bin/xarchiver} </usr/share/pixmaps/xarchiver.xpm>
      [end]
      [submenu] (Viewers) {}
         [exec] (ImageMagick) {/usr/bin/display} <>
         [exec] (VLC media player) {/usr/bin/wxvlc} </usr/share/vlc/vlc.xpm>
         [exec] (Xpdf) {/usr/bin/xpdf} </usr/share/pixmaps/xpdf.xpm>
         [exec] (xzgv Image Viewer) {/usr/bin/xzgv} </usr/share/pixmaps/xzgv.xpm>
      [end]
   [end]
   [submenu] (Help) {}
      [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
   [end]
   [submenu] (Screen) {}
      [submenu] (Lock) {}
         [submenu] (Assorted) {}
            [exec] (Anemone) {/usr/bin/xlock -remote -nice 19 -mode anemone} <>
            [exec] (Ball) {/usr/bin/xlock -remote -nice 19 -mode ball} <>
            [exec] (Blot) {/usr/bin/xlock -remote -nice 19 -mode blot} <>
            [exec] (Bounce) {/usr/bin/xlock -remote -nice 19 -mode bounce} <>
            [exec] (Bubble) {/usr/bin/xlock -remote -nice 19 -mode bubble} <>
            [exec] (Clock) {/usr/bin/xlock -remote -nice 19 -mode clock} <>
            [exec] (Crystal) {/usr/bin/xlock -remote -nice 19 -mode crystal} <>
            [exec] (Daisy) {/usr/bin/xlock -remote -nice 19 -mode daisy} <>
            [exec] (Dclock) {/usr/bin/xlock -remote -nice 19 -mode dclock} <>
            [exec] (Decay) {/usr/bin/xlock -remote -nice 19 -mode decay} <>
            [exec] (Deco) {/usr/bin/xlock -remote -nice 19 -mode deco} <>
            [exec] (Deluxe) {/usr/bin/xlock -remote -nice 19 -mode deluxe} <>
            [exec] (Eyes) {/usr/bin/xlock -remote -nice 19 -mode eyes +trackmouse} <>
            [exec] (Eyesptr) {/usr/bin/xlock -remote -nice 19 -mode eyes -trackmouse} <>
            [exec] (Fiberlamp) {/usr/bin/xlock -remote -nice 19 -mode fiberlamp} <>
            [exec] (Fzort) {/usr/bin/xlock -remote -nice 19 -mode fzort} <>
            [exec] (Goop) {/usr/bin/xlock -remote -nice 19 -mode goop} <>
            [exec] (Juggle) {/usr/bin/xlock -remote -nice 19 -mode juggle} <>
            [exec] (Marquee) {/usr/bin/xlock -remote -nice 19 -mode marquee} <>
            [exec] (Matrix) {/usr/bin/xlock -remote -nice 19 -mode matrix} <>
            [exec] (Munch) {/usr/bin/xlock -remote -nice 19 -mode munch} <>
            [exec] (Nose) {/usr/bin/xlock -remote -nice 19 -mode nose} <>
            [exec] (Pacman) {/usr/bin/xlock -remote -nice 19 -mode pacman} <>
            [exec] (Pyro) {/usr/bin/xlock -remote -nice 19 -mode pyro +use3d} <>
            [exec] (Pyro3d) {/usr/bin/xlock -remote -nice 19 -mode pyro -use3d} <>
            [exec] (Roll) {/usr/bin/xlock -remote -nice 19 -mode roll} <>
            [exec] (Slip) {/usr/bin/xlock -remote -nice 19 -mode slip} <>
            [exec] (Solitare) {/usr/bin/xlock -remote -nice 19 -mode solitare +trackmouse} <>
            [exec] (Solitareptr) {/usr/bin/xlock -remote -nice 19 -mode solitare -trackmouse} <>
            [exec] (Starfish) {/usr/bin/xlock -remote -nice 19 -mode starfish -install} <>
            [exec] (Swarm) {/usr/bin/xlock -remote -nice 19 -mode swarm +trackmouse} <>
            [exec] (Swarmptr) {/usr/bin/xlock -remote -nice 19 -mode swarm -trackmouse} <>
            [exec] (Swirl) {/usr/bin/xlock -remote -nice 19 -mode swirl -install} <>
            [exec] (T3d) {/usr/bin/xlock -remote -nice 19 -mode t3d} <>
            [exec] (Tetris) {/usr/bin/xlock -remote -nice 19 -mode tetris} <>
            [exec] (Tube) {/usr/bin/xlock -remote -nice 19 -mode tube -install} <>
            [exec] (Worm) {/usr/bin/xlock -remote -nice 19 -mode worm +use3d} <>
            [exec] (Worm3d) {/usr/bin/xlock -remote -nice 19 -mode worm -use3d} <>
            [exec] (Xcl) {/usr/bin/xlock -remote -nice 19 -mode xcl} <>
            [exec] (Xjack) {/usr/bin/xlock -remote -nice 19 -mode xjack} <>
         [end]
         [submenu] (Automata) {}
            [exec] (Ant) {/usr/bin/xlock -remote -nice 19 -mode ant -neighbors 4 +truchet} <>
            [exec] (Ant Truchet) {/usr/bin/xlock -remote -nice 19 -mode ant -neighbors 4 -truchet} <>
            [exec] (Ant3d) {/usr/bin/xlock -remote -nice 19 -mode ant3d} <>
            [exec] (Bee) {/usr/bin/xlock -remote -nice 19 -mode ant -neighbors 6 +truchet} <>
            [exec] (Bee Truchet) {/usr/bin/xlock -remote -nice 19 -mode ant -neighbors 6 -truchet} <>
            [exec] (Bug) {/usr/bin/xlock -remote -nice 19 -mode bug} <>
            [exec] (Demon) {/usr/bin/xlock -remote -nice 19 -mode demon} <>
            [exec] (Dilemma) {/usr/bin/xlock -remote -nice 19 -mode dilemma} <>
            [exec] (Life) {/usr/bin/xlock -remote -nice 19 -mode life} <>
            [exec] (Life Callahan) {/usr/bin/xlock -remote -nice 19 -mode life -callahan -size 7} <>
            [exec] (Life1d) {/usr/bin/xlock -remote -nice 19 -mode life1d} <>
            [exec] (Life3d) {/usr/bin/xlock -remote -nice 19 -mode life3d} <>
            [exec] (Loop) {/usr/bin/xlock -remote -nice 19 -mode loop} <>
            [exec] (Petri) {/usr/bin/xlock -remote -nice 19 -mode petri} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allautomata -fullrandom -neighbors 0} <>
            [exec] (Voters) {/usr/bin/xlock -remote -nice 19 -mode voters} <>
            [exec] (Wator) {/usr/bin/xlock -remote -nice 19 -mode wator} <>
            [exec] (Wire) {/usr/bin/xlock -remote -nice 19 -mode wire} <>
         [end]
         [submenu] (Fractal) {}
            [exec] (Coral) {/usr/bin/xlock -remote -nice 19 -mode coral} <>
            [exec] (Discrete) {/usr/bin/xlock -remote -nice 19 -mode discrete} <>
            [exec] (Dragon) {/usr/bin/xlock -remote -nice 19 -mode dragon} <>
            [exec] (Drift) {/usr/bin/xlock -remote -nice 19 -mode drift -fullrandom} <>
            [exec] (Euler2d) {/usr/bin/xlock -remote -nice 19 -mode euler2d} <>
            [exec] (Flame) {/usr/bin/xlock -remote -nice 19 -mode flame} <>
            [exec] (Flow) {/usr/bin/xlock -remote -nice 19 -mode flow} <>
            [exec] (Forest) {/usr/bin/xlock -remote -nice 19 -mode forest} <>
            [exec] (Hop) {/usr/bin/xlock -remote -nice 19 -mode hop -fullrandom} <>
            [exec] (IFS) {/usr/bin/xlock -remote -nice 19 -mode ifs} <>
            [exec] (Julia) {/usr/bin/xlock -remote -nice 19 -mode julia +trackmouse} <>
            [exec] (Juliaptr) {/usr/bin/xlock -remote -nice 19 -mode julia -trackmouse} <>
            [exec] (Kumppa) {/usr/bin/xlock -remote -nice 19 -mode kumppa} <>
            [exec] (Lightning) {/usr/bin/xlock -remote -nice 19 -mode lightning} <>
            [exec] (Lyapunov) {/usr/bin/xlock -remote -nice 19 -mode lyapunov -install} <>
            [exec] (Mandelbrot) {/usr/bin/xlock -remote -nice 19 -mode mandelbrot -install} <>
            [exec] (Mountain) {/usr/bin/xlock -remote -nice 19 -mode mountain} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allfractal -fullrandom} <>
            [exec] (Sierpinski) {/usr/bin/xlock -remote -nice 19 -mode sierpinski} <>
            [exec] (Strange) {/usr/bin/xlock -remote -nice 19 -mode strange} <>
            [exec] (Thornbird) {/usr/bin/xlock -remote -nice 19 -mode thornbird} <>
            [exec] (Triangle) {/usr/bin/xlock -remote -nice 19 -mode triangle} <>
            [exec] (Turtle) {/usr/bin/xlock -remote -nice 19 -mode turtle} <>
            [exec] (Vines) {/usr/bin/xlock -remote -nice 19 -mode vines} <>
         [end]
         [submenu] (Geometry) {}
            [exec] (Apollonian) {/usr/bin/xlock -remote -nice 19 -mode apollonian} <>
            [exec] (Braid) {/usr/bin/xlock -remote -nice 19 -mode braid} <>
            [exec] (Fadeplot) {/usr/bin/xlock -remote -nice 19 -mode fadeplot} <>
            [exec] (Helix) {/usr/bin/xlock -remote -nice 19 -mode helix -fullrandom} <>
            [exec] (Hyper) {/usr/bin/xlock -remote -nice 19 -mode hyper} <>
            [exec] (Ico) {/usr/bin/xlock -remote -nice 19 -mode ico} <>
            [exec] (Kaleid) {/usr/bin/xlock -remote -nice 19 -mode kaleid} <>
            [exec] (Laser) {/usr/bin/xlock -remote -nice 19 -mode laser} <>
            [exec] (Lisa) {/usr/bin/xlock -remote -nice 19 -mode lisa} <>
            [exec] (Lissie) {/usr/bin/xlock -remote -nice 19 -mode lissie} <>
            [exec] (Penrose) {/usr/bin/xlock -remote -nice 19 -mode penrose +ammann} <>
            [exec] (Penrose Ammann) {/usr/bin/xlock -remote -nice 19 -mode penrose -ammann} <>
            [exec] (Petal) {/usr/bin/xlock -remote -nice 19 -mode petal} <>
            [exec] (Polyominoes) {/usr/bin/xlock -remote -nice 19 -mode polyominoes} <>
            [exec] (Qix) {/usr/bin/xlock -remote -nice 19 -mode qix +complete} <>
            [exec] (Qix complete) {/usr/bin/xlock -remote -nice 19 -mode qix -complete} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allgeometry -fullrandom} <>
            [exec] (Rotor) {/usr/bin/xlock -remote -nice 19 -mode rotor} <>
            [exec] (Shape) {/usr/bin/xlock -remote -nice 19 -mode shape} <>
            [exec] (Sphere) {/usr/bin/xlock -remote -nice 19 -mode sphere} <>
            [exec] (Spiral) {/usr/bin/xlock -remote -nice 19 -mode spiral} <>
            [exec] (Spline) {/usr/bin/xlock -remote -nice 19 -mode spline} <>
            [exec] (Tik_Tak) {/usr/bin/xlock -remote -nice 19 -mode tik_tak} <>
            [exec] (Toneclock) {/usr/bin/xlock -remote -nice 19 -mode toneclock} <>
         [end]
         [submenu] (MarqueeMessage) {}
            [exec] (Back Soon) {/usr/bin/xlock -remote -nice 19 -mode marquee -message "$LOGNAME will be back soon."} <>
            [exec] (Overnight) {/usr/bin/xlock -remote -nice 19 -mode marquee -message "$LOGNAME will be back in the morning."} <>
            [exec] (Rude) {/usr/bin/xlock -remote -nice 19 -mode marquee -message "$LOGNAME not here, please go away!"} <>
         [end]
         [submenu] (NoseMessage) {}
            [exec] (Back Soon) {/usr/bin/xlock -remote -nice 19 -mode nose -message "$LOGNAME will be back soon."} <>
            [exec] (Overnight) {/usr/bin/xlock -remote -nice 19 -mode nose -message "$LOGNAME will be back in the morning."} <>
            [exec] (Rude) {/usr/bin/xlock -remote -nice 19 -mode nose -message "$LOGNAME not here, please go away!"} <>
         [end]
         [submenu] (Space) {}
            [exec] (Bouboule) {/usr/bin/xlock -remote -nice 19 -mode bouboule +use3d} <>
            [exec] (Bouboule3d) {/usr/bin/xlock -remote -nice 19 -mode bouboule -use3d} <>
            [exec] (Galaxy) {/usr/bin/xlock -remote -nice 19 -mode galaxy} <>
            [exec] (Grav) {/usr/bin/xlock -remote -nice 19 -mode grav +trail +decay} <>
            [exec] (Grav Decay) {/usr/bin/xlock -remote -nice 19 -mode grav -decay} <>
            [exec] (Grav Trail) {/usr/bin/xlock -remote -nice 19 -mode grav -trail} <>
            [exec] (Random Space) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allspace} <>
            [exec] (Rock) {/usr/bin/xlock -remote -nice 19 -mode star -rock} <>
            [exec] (Space) {/usr/bin/xlock -remote -nice 19 -mode space} <>
            [exec] (Star) {/usr/bin/xlock -remote -nice 19 -mode star +rock +use3d +trek 0} <>
            [exec] (Star Trek) {/usr/bin/xlock -remote -nice 19 -mode star -trek 100} <>
            [exec] (Star3d) {/usr/bin/xlock -remote -nice 19 -mode star -use3d} <>
            [exec] (World) {/usr/bin/xlock -remote -nice 19 -mode world} <>
         [end]
         [submenu] (Special) {}
            [exec] (Blank) {/usr/bin/xlock -remote -nice 19 -mode blank} <>
            [exec] (Bomb) {/usr/bin/xlock -remote -nice 19 -mode bomb} <>
            [exec] (Random 3d) {/usr/bin/xlock -remote -nice 19 -mode random -modelist all3d -use3d -fullrandom} <>
            [exec] (Random all) {/usr/bin/xlock -remote -nice 19 -mode random -modelist all -fullrandom -neighbors 0} <>
            [exec] (Random nice) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allnice -fullrandom -neighbors 0} <>
            [exec] (Random ptr) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allmouse -trackmouse -fullrandom} <>
            [exec] (Random standard) {/usr/bin/xlock -remote -nice 19 -mode random -modelist all-allgl -fullrandom -neighbors 0} <>
            [exec] (Random write) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allwrite -install -fullrandom} <>
            [exec] (Transparent) {/usr/bin/xlock -remote -nice 19 -mode blank -geometry 1x1 -enablesaver} <>
         [end]
         [submenu] (XjackMessage) {}
            [exec] (Crazy Boy) {/usr/bin/xlock -remote -nice 19 -mode xjack -message "All work and no play makes $LOGNAME a dull boy."} <>
            [exec] (Crazy Girl) {/usr/bin/xlock -remote -nice 19 -mode xjack -message "All work and no play makes $LOGNAME a dull girl."} <>
         [end]
         [submenu] (XPM) {}
            [exec] (Bat) {/usr/bin/xlock -remote -nice 19 -mode bat} <>
            [exec] (Flag) {/usr/bin/xlock -remote -nice 19 -mode flag} <>
            [exec] (Image) {/usr/bin/xlock -remote -nice 19 -mode image} <>
            [exec] (Life) {/usr/bin/xlock -remote -nice 19 -mode life} <>
            [exec] (Life1d) {/usr/bin/xlock -remote -nice 19 -mode life1d} <>
            [exec] (Maze) {/usr/bin/xlock -remote -nice 19 -mode maze} <>
            [exec] (Puzzle) {/usr/bin/xlock -remote -nice 19 -mode puzzle} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -mode random -modelist allxpm -fullrandom} <>
         [end]
      [end]
      [submenu] (Save) {}
         [submenu] (Assorted) {}
            [exec] (Anemone) {/usr/bin/xlock -remote -nice 19 -nolock -mode anemone} <>
            [exec] (Ball) {/usr/bin/xlock -remote -nice 19 -nolock -mode ball} <>
            [exec] (Blot) {/usr/bin/xlock -remote -nice 19 -nolock -mode blot} <>
            [exec] (Bounce) {/usr/bin/xlock -remote -nice 19 -nolock -mode bounce} <>
            [exec] (Bubble) {/usr/bin/xlock -remote -nice 19 -nolock -mode bubble} <>
            [exec] (Clock) {/usr/bin/xlock -remote -nice 19 -nolock -mode clock} <>
            [exec] (Crystal) {/usr/bin/xlock -remote -nice 19 -nolock -mode crystal} <>
            [exec] (Daisy) {/usr/bin/xlock -remote -nice 19 -nolock -mode daisy} <>
            [exec] (Dclock) {/usr/bin/xlock -remote -nice 19 -nolock -mode dclock} <>
            [exec] (Decay) {/usr/bin/xlock -remote -nice 19 -nolock -mode decay} <>
            [exec] (Deco) {/usr/bin/xlock -remote -nice 19 -nolock -mode deco} <>
            [exec] (Deluxe) {/usr/bin/xlock -remote -nice 19 -nolock -mode deluxe} <>
            [exec] (Eyes) {/usr/bin/xlock -remote -nice 19 -nolock -mode eyes +trackmouse} <>
            [exec] (Eyesptr) {/usr/bin/xlock -remote -nice 19 -nolock -mode eyes -trackmouse} <>
            [exec] (Fiberlamp) {/usr/bin/xlock -remote -nice 19 -nolock -mode fiberlamp} <>
            [exec] (Fzort) {/usr/bin/xlock -remote -nice 19 -nolock -mode fzort} <>
            [exec] (Goop) {/usr/bin/xlock -remote -nice 19 -nolock -mode goop} <>
            [exec] (Juggle) {/usr/bin/xlock -remote -nice 19 -nolock -mode juggle} <>
            [exec] (Marquee) {/usr/bin/xlock -remote -nice 19 -nolock -mode marquee} <>
            [exec] (Matrix) {/usr/bin/xlock -remote -nice 19 -nolock -mode matrix} <>
            [exec] (Munch) {/usr/bin/xlock -remote -nice 19 -nolock -mode munch} <>
            [exec] (Nose) {/usr/bin/xlock -remote -nice 19 -nolock -mode nose} <>
            [exec] (Pacman) {/usr/bin/xlock -remote -nice 19 -nolock -mode pacman} <>
            [exec] (Pyro) {/usr/bin/xlock -remote -nice 19 -nolock -mode pyro +use3d} <>
            [exec] (Pyro3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode pyro -use3d} <>
            [exec] (Roll) {/usr/bin/xlock -remote -nice 19 -nolock -mode roll} <>
            [exec] (Slip) {/usr/bin/xlock -remote -nice 19 -nolock -mode slip} <>
            [exec] (Solitare) {/usr/bin/xlock -remote -nice 19 -nolock -mode solitare +trackmouse} <>
            [exec] (Solitareptr) {/usr/bin/xlock -remote -nice 19 -nolock -mode solitare -trackmouse} <>
            [exec] (Starfish) {/usr/bin/xlock -remote -nice 19 -nolock -mode starfish -install} <>
            [exec] (Swarm) {/usr/bin/xlock -remote -nice 19 -nolock -mode swarm +trackmouse} <>
            [exec] (Swarmptr) {/usr/bin/xlock -remote -nice 19 -nolock -mode swarm -trackmouse} <>
            [exec] (Swirl) {/usr/bin/xlock -remote -nice 19 -nolock -mode swirl -install} <>
            [exec] (T3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode t3d} <>
            [exec] (Tetris) {/usr/bin/xlock -remote -nice 19 -nolock -mode tetris} <>
            [exec] (Tube) {/usr/bin/xlock -remote -nice 19 -nolock -mode tube -install} <>
            [exec] (Worm) {/usr/bin/xlock -remote -nice 19 -nolock -mode worm +use3d} <>
            [exec] (Worm3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode worm -use3d} <>
            [exec] (Xcl) {/usr/bin/xlock -remote -nice 19 -nolock -mode xcl} <>
            [exec] (Xjack) {/usr/bin/xlock -remote -nice 19 -nolock -mode xjack} <>
         [end]
         [submenu] (Automata) {}
            [exec] (Ant) {/usr/bin/xlock -remote -nice 19 -nolock -mode ant -neighbors 4 +truchet} <>
            [exec] (Ant Truchet) {/usr/bin/xlock -remote -nice 19 -nolock -mode ant -neighbors 4 -truchet} <>
            [exec] (Ant3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode ant3d} <>
            [exec] (Bee) {/usr/bin/xlock -remote -nice 19 -nolock -mode ant -neighbors 6 +truchet} <>
            [exec] (Bee Truchet) {/usr/bin/xlock -remote -nice 19 -nolock -mode ant -neighbors 6 -truchet} <>
            [exec] (Bug) {/usr/bin/xlock -remote -nice 19 -nolock -mode bug} <>
            [exec] (Demon) {/usr/bin/xlock -remote -nice 19 -nolock -mode demon} <>
            [exec] (Dilemma) {/usr/bin/xlock -remote -nice 19 -nolock -mode dilemma} <>
            [exec] (Life) {/usr/bin/xlock -remote -nice 19 -nolock -mode life} <>
            [exec] (Life Callahan) {/usr/bin/xlock -remote -nice 19 -nolock -mode life -callahan -size 7} <>
            [exec] (Life1d) {/usr/bin/xlock -remote -nice 19 -nolock -mode life1d} <>
            [exec] (Life3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode life3d} <>
            [exec] (Loop) {/usr/bin/xlock -remote -nice 19 -nolock -mode loop} <>
            [exec] (Petri) {/usr/bin/xlock -remote -nice 19 -nolock -mode petri} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allautomata -fullrandom -neighbors 0} <>
            [exec] (Voters) {/usr/bin/xlock -remote -nice 19 -nolock -mode voters} <>
            [exec] (Wator) {/usr/bin/xlock -remote -nice 19 -nolock -mode wator} <>
            [exec] (Wire) {/usr/bin/xlock -remote -nice 19 -nolock -mode wire} <>
         [end]
         [submenu] (Fractal) {}
            [exec] (Coral) {/usr/bin/xlock -remote -nice 19 -nolock -mode coral} <>
            [exec] (Discrete) {/usr/bin/xlock -remote -nice 19 -nolock -mode discrete} <>
            [exec] (Dragon) {/usr/bin/xlock -remote -nice 19 -nolock -mode dragon} <>
            [exec] (Drift) {/usr/bin/xlock -remote -nice 19 -nolock -mode drift -fullrandom} <>
            [exec] (Euler2d) {/usr/bin/xlock -remote -nice 19 -nolock -mode euler2d} <>
            [exec] (Flame) {/usr/bin/xlock -remote -nice 19 -nolock -mode flame} <>
            [exec] (Flow) {/usr/bin/xlock -remote -nice 19 -nolock -mode flow} <>
            [exec] (Forest) {/usr/bin/xlock -remote -nice 19 -nolock -mode forest} <>
            [exec] (Hop) {/usr/bin/xlock -remote -nice 19 -nolock -mode hop -fullrandom} <>
            [exec] (IFS) {/usr/bin/xlock -remote -nice 19 -nolock -mode ifs} <>
            [exec] (Julia) {/usr/bin/xlock -remote -nice 19 -nolock -mode julia +trackmouse} <>
            [exec] (Juliaptr) {/usr/bin/xlock -remote -nice 19 -nolock -mode julia -trackmouse} <>
            [exec] (Kumppa) {/usr/bin/xlock -remote -nice 19 -nolock -mode kumppa} <>
            [exec] (Lightning) {/usr/bin/xlock -remote -nice 19 -nolock -mode lightning} <>
            [exec] (Lyapunov) {/usr/bin/xlock -remote -nice 19 -nolock -mode lyapunov -install} <>
            [exec] (Mandelbrot) {/usr/bin/xlock -remote -nice 19 -nolock -mode mandelbrot -install} <>
            [exec] (Mountain) {/usr/bin/xlock -remote -nice 19 -nolock -mode mountain} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allfractal -fullrandom} <>
            [exec] (Sierpinski) {/usr/bin/xlock -remote -nice 19 -nolock -mode sierpinski} <>
            [exec] (Strange) {/usr/bin/xlock -remote -nice 19 -nolock -mode strange} <>
            [exec] (Thornbird) {/usr/bin/xlock -remote -nice 19 -nolock -mode thornbird} <>
            [exec] (Triangle) {/usr/bin/xlock -remote -nice 19 -nolock -mode triangle} <>
            [exec] (Turtle) {/usr/bin/xlock -remote -nice 19 -nolock -mode turtle} <>
            [exec] (Vines) {/usr/bin/xlock -remote -nice 19 -nolock -mode vines} <>
         [end]
         [submenu] (Geometry) {}
            [exec] (Apollonian) {/usr/bin/xlock -remote -nice 19 -nolock -mode apollonian} <>
            [exec] (Braid) {/usr/bin/xlock -remote -nice 19 -nolock -mode braid} <>
            [exec] (Fadeplot) {/usr/bin/xlock -remote -nice 19 -nolock -mode fadeplot} <>
            [exec] (Helix) {/usr/bin/xlock -remote -nice 19 -nolock -mode helix -fullrandom} <>
            [exec] (Hyper) {/usr/bin/xlock -remote -nice 19 -nolock -mode hyper} <>
            [exec] (Ico) {/usr/bin/xlock -remote -nice 19 -nolock -mode ico} <>
            [exec] (Kaleid) {/usr/bin/xlock -remote -nice 19 -nolock -mode kaleid} <>
            [exec] (Laser) {/usr/bin/xlock -remote -nice 19 -nolock -mode laser} <>
            [exec] (Lisa) {/usr/bin/xlock -remote -nice 19 -nolock -mode lisa} <>
            [exec] (Lissie) {/usr/bin/xlock -remote -nice 19 -nolock -mode lissie} <>
            [exec] (Penrose) {/usr/bin/xlock -remote -nice 19 -nolock -mode penrose +ammann} <>
            [exec] (Penrose Ammann) {/usr/bin/xlock -remote -nice 19 -nolock -mode penrose -ammann} <>
            [exec] (Petal) {/usr/bin/xlock -remote -nice 19 -nolock -mode petal} <>
            [exec] (Polyominoes) {/usr/bin/xlock -remote -nice 19 -nolock -mode polyominoes} <>
            [exec] (Qix) {/usr/bin/xlock -remote -nice 19 -nolock -mode qix +complete} <>
            [exec] (Qix complete) {/usr/bin/xlock -remote -nice 19 -nolock -mode qix -complete} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allgeometry} <>
            [exec] (Rotor) {/usr/bin/xlock -remote -nice 19 -nolock -mode rotor} <>
            [exec] (Shape) {/usr/bin/xlock -remote -nice 19 -nolock -mode shape} <>
            [exec] (Sphere) {/usr/bin/xlock -remote -nice 19 -nolock -mode sphere} <>
            [exec] (Spiral) {/usr/bin/xlock -remote -nice 19 -nolock -mode spiral} <>
            [exec] (Spline) {/usr/bin/xlock -remote -nice 19 -nolock -mode spline} <>
            [exec] (Tik_Tak) {/usr/bin/xlock -remote -nice 19 -nolock -mode tik_tak} <>
            [exec] (Toneclock) {/usr/bin/xlock -remote -nice 19 -nolock -mode toneclock} <>
         [end]
         [submenu] (MarqueeMessage) {}
            [exec] (Available) {/usr/bin/xlock -remote -nice 19 -nolock -mode marquee -message "Hey, I'm available now!"} <>
            [exec] (Brilliant!) {/usr/bin/xlock -remote -nice 19 -nolock -mode marquee -message "WOW! $LOGNAME, You're Brilliant!"} <>
            [exec] (Love You) {/usr/bin/xlock -remote -nice 19 -nolock -mode marquee -message "You know, I Love You $LOGNAME."} <>
         [end]
         [submenu] (NoseMessage) {}
            [exec] (Available) {/usr/bin/xlock -remote -nice 19 -nolock -mode nose -message "Hey, I'm available now!"} <>
            [exec] (Brilliant!) {/usr/bin/xlock -remote -nice 19 -nolock -mode nose -message "WOW! $LOGNAME, You're Brilliant!"} <>
            [exec] (Love You) {/usr/bin/xlock -remote -nice 19 -nolock -mode nose -message "You know, I Love You $LOGNAME."} <>
         [end]
         [submenu] (Space) {}
            [exec] (Bouboule) {/usr/bin/xlock -remote -nice 19 -nolock -mode bouboule +use3d} <>
            [exec] (Bouboule3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode bouboule -use3d} <>
            [exec] (Galaxy) {/usr/bin/xlock -remote -nice 19 -nolock -mode galaxy} <>
            [exec] (Grav) {/usr/bin/xlock -remote -nice 19 -nolock -mode grav +trail +decay} <>
            [exec] (Grav Decay) {/usr/bin/xlock -remote -nice 19 -nolock -mode grav -decay} <>
            [exec] (Grav Trail) {/usr/bin/xlock -remote -nice 19 -nolock -mode grav -trail} <>
            [exec] (Random Space) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allspace} <>
            [exec] (Rock) {/usr/bin/xlock -remote -nice 19 -nolock -mode star -rock} <>
            [exec] (Scooter) {/usr/bin/xlock -remote -nice 19 -nolock -mode scooter} <>
            [exec] (Space) {/usr/bin/xlock -remote -nice 19 -nolock -mode space} <>
            [exec] (Star) {/usr/bin/xlock -remote -nice 19 -nolock -mode star +rock +use3d +trek 0} <>
            [exec] (Star Trek) {/usr/bin/xlock -remote -nice 19 -nolock -mode star -trek 100} <>
            [exec] (Star3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode star -use3d} <>
            [exec] (World) {/usr/bin/xlock -remote -nice 19 -nolock -mode world} <>
         [end]
         [submenu] (Special) {}
            [exec] (Blank) {/usr/bin/xlock -remote -nice 19 -nolock -mode blank} <>
            [exec] (Bomb) {/usr/bin/xlock -remote -nice 19 -nolock -mode bomb} <>
            [exec] (Random 3d) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist all3d -use3d -fullrandom} <>
            [exec] (Random all) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist all -fullrandom -neighbors 0} <>
            [exec] (Random nice) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allnice -fullrandom -neighbors 0} <>
            [exec] (Random ptr) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allmouse -trackmouse -fullrandom} <>
            [exec] (Random standard) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist all-allgl -fullrandom -neighbors 0} <>
            [exec] (Random write) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allwrite -fullrandom} <>
         [end]
         [submenu] (XPM) {}
            [exec] (Bat) {/usr/bin/xlock -remote -nice 19 -nolock -mode bat} <>
            [exec] (Flag) {/usr/bin/xlock -remote -nice 19 -nolock -mode flag} <>
            [exec] (Image) {/usr/bin/xlock -remote -nice 19 -nolock -mode image} <>
            [exec] (Life) {/usr/bin/xlock -remote -nice 19 -nolock -mode life} <>
            [exec] (Life1d) {/usr/bin/xlock -remote -nice 19 -nolock -mode life1d} <>
            [exec] (Maze) {/usr/bin/xlock -remote -nice 19 -nolock -mode maze} <>
            [exec] (Puzzle) {/usr/bin/xlock -remote -nice 19 -nolock -mode puzzle} <>
            [exec] (Random) {/usr/bin/xlock -remote -nice 19 -nolock -mode random -modelist allxpm -fullrandom} <>
         [end]
      [end]
   [end]
   [submenu] (WindowManagers) {}
      [restart] (FluxBox)  {/usr/bin/startfluxbox}
   [end]
   [separator]
   [submenu] (Fluxbox) {}
      [config] (Configuration)
      [submenu] (Styles) {}
         [stylesdir] (/usr/share/fluxbox/styles)
         [stylesdir] (~/.fluxbox/styles)
      [end]
      [reconfig] (Reconfigure)
      [restart] (Restart Fluxbox)
   [end]
   [submenu] (System) {}
      [exec] (Networking) {gksudo -a -m "Enter Password to Access Network Configuration" "network-config"}
      [exec] (Screen Resolution) {gvidm}
   [end]
   [separator]
   [submenu] (Quit...) {}
      [exec] (Lock PC) {/usr/bin/xlock -remote -nice 19}
      [exit] (Log Off)
      [separator]
      [exec] (Reboot) {gksudo -a -m "Enter Password To Reboot Computer" "shutdown -r now"}
      [exec] (Standby) {gksudo -a -m "Enter Password To Standby Computer" "/etc/acpi/sleep.sh"}
      [exec] (Hibernate) {gksudo -a -m "Enter Password To Sleep Computer" "/etc/acpi/hibernate.sh"}
      [exec] (Shutdown) {gksudo -a -m "Enter Password To Shutdwon Computer" "shutdown -h now"}
   [end]
[end]

/etc/X11/fluxbox/fluxbox-keys
> 
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu
OnDesktop Mouse4 :nextWorkspace
OnDesktop Mouse5 :prevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Control F2 :execCommand fbrun -title "Fluxbuntu Run" -nearmouse -h 35
Control F3 :execCommand x-terminal-emulator
Control F5 :showdesktop
Control F11 :execCommand rox-filer
Control F12 :RootMenu
Control Mod1 L :execCommand /usr/bin/xlock -remote -nice 19
Mod1 Control Left :PrevWorkspace
Mod1 Control Right :NextWorkspace
Mod1 Control Shift Left :TakeToPrevWorkspace
Mod1 Control Shift Right :TakeToNextWorkspace
Mod4 :RootMenu


~/.fluxbox/keys
> 
# File generated by FluxConf
None Mouse1toppdate_configs	 :hideMenus
None Mouse1top :hideMenu
None Mouse2top :WorkspaceMenu
None Mouse3top :RootMenu
None Mouse4top :NextWorkspace
None Mouse5top :PrevWorkspace
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Control F2 :ExecCommand fbrun -title "Fluxbuntu Run" -nearmouse -h 35
Mod4 F3 :ExecCommand x-terminal-emulator
Control F5 :ShowDesktop
Control F11 :ExecCommand rox-filer
Control F12 :RootMenu
Control Mod1 L :ExecCommand /usr/bin/xlock -remote -nice 19
Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Control Mod1 Shift Left :TakeToPrevWorkspace
Control Mod1 Shift Right :TakeToNextWorkspace




---

### Post by herbster on 2008-03-24
You pasted two ~/.fluxbox/keys, I'm going to assume the bottom one is correct?

See the first 6 lines? Replace "None" with "OnDesktop" then hit Reconfigure on the menu and give it a whirl.

---

### Post by arjayes on 2008-03-24
Yeah that fixed most of it as in i can right click on windows now and scroll . BUt I still can't close the menu by clicking on the desktop . and yeah the first keys file was 
/etc/X11/fluxbox/keys
the second one - 
~/.fluxbox/keys,

---

### Post by herbster on 2008-03-24
```
None Mouse1top :hideMenu
```

Add an "s" to the end, so it's "hideMenus"

---

### Post by arjayes on 2008-03-24
Thanks, that solved it .

---

### Post by arjayes on 2008-03-24
Further problems : Now I can't click on a window or select anything . 
ie. I can't left-click anything on any window. not even the taskbar .
I can't select anything on any window or right click on any window . 
The ~/.fkuxbox/keys file is now
> 
# File generated by FluxConf
OnDesktop Mouse1top :hideMenus
OnDesktop Mouse2top :WorkspaceMenu
OnDesktop Mouse3top :RootMenu
OnDesktop Mouse4top :NextWorkspace
OnDesktop Mouse5top :PrevWorkspace
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Control F2 :ExecCommand fbrun -title "Fluxbuntu Run" -nearmouse -h 35
Mod4 t :ExecCommand x-terminal-emulator
Control F5 :ShowDesktop
Control F11 :ExecCommand rox-filer
Control F12 :RootMenu
Control Mod1 L :ExecCommand /usr/bin/xlock -remote -nice 19
Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Control Mod1 Shift Left :TakeToPrevWorkspace
Control Mod1 Shift Right :TakeToNextWorkspace


~/.fluxbox/menu
> 
[begin] (Fluxbuntu) {} <>
    [exec] (Run...) {fbrun -title "Run..." -h 35} <>
    [separator] () {} <>
    [exec] (Editor) {leafpad} <>
    [exec] (File Browser) {rox-filer} <>
    [exec] (Web Browser) {firefox} <>
    [exec] (Terminal) {uxterm} <>
    [separator] () {} <>
    [include] (/etc/X11/fluxbox/fluxbox-menu) {} <>
[end]

I've been unable to find a solution to this problem by Googling .
I really want to learn fluxbox but I've been unable to solve this on my own so please hel p

---

### Post by arjayes on 2008-03-24
Forget It problem solved on reboot .
Weird the way things sometimes work out :)

---

### Post by herbster on 2008-03-24
Mark the thread as solved for others :) Thread tool > Mark as solved.

---

### Post by kaiju on 2008-03-25
...and doing a quick "cp /wherever/whatever /wherever/whatever.backup" before fiddling with any settings files will save you a lot of such trouble in the future ;)

---


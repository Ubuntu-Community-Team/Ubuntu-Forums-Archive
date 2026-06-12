---
title: "Fluxbox configuration"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-04
Just installed breezy, and I must say, I like it. Hardware detection was great etc. Anyway, I want to run fluxbox as my WM, so I downloaded / installed with synaptec and started a new session with it. It's completly unconfigured, and the only thing on the menu other than the standard Restart / Exit was xterm.

How can I easily configure Fluxbox with menus like in gnome? Can I copy / paste some config files or is it more difficult?

---

### Post by funkydan2 on 2005-12-04
I think installing [menu](http://packages.ubuntu.com/breezy/admin/menu) should give you the debian menu in Fluxbox.

---

### Post by mcmillan on 2005-12-05
I don't know if it will solve the other person's problem, but I had the same thing happen when I installed fluxbox and I have menu installed. 

If what I interpret what I've read the file to edit the standard menu is in /etc/X11/fluxbox/system.fluxbox.menu and the user menu is in ~/.fluxbox/menu

For me the first of these contains

```
# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (fluxbox)

include-menu-defs

   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [restart] (Restart)
   [exit] (Exit)

[end]
```

The second is empty. I figure I need to tell it to include the menu, which when I run xfce it did by default, but I don't know where this menu is.

---

### Post by wr0x2 on 2005-12-06
All right, thanks for the help guys. I read up some more on fluxbox and I understand how menu config works.

I want to install flux from source though, so I deleted the binary I installed earlier. Unfortunatly when I compile I get some errors:

..... more stuff above here...
checking for iconv_open in -liconv... no
checking for libiconv_open in -liconv... no
checking for iconv declaration... no
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.
wr0x2@USSENTERPRISE:~/Docs/fluxbox-0.9.14$

I looked around in synaptec under X11, and I installed the libx11-dev package, hoping it would solve my problems. It didn't and I get the exact same error.

Oh by the way, earlier I tried the command apt-get build-deps fluxbox to satisfy the deps for fluxbox but it doesn't find anything. Do I need to update my repository source file?

---

### Post by timsch75 on 2005-12-09
have you done this?

 sudo apt-get install build-essential

This installs essential files to be able to install from source.

---

### Post by zenkoanlife on 2006-05-16
I'm getting the same messagechecking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

anybody know what else i need to install?
I installed breezy with :server, and then installed the following with apt: x-window-system-core, kdm, build-essential, and i'm trying to manually install fluxbox.

---

### Post by w1z4rd on 2006-06-21
Type this command, worked for me:

```
sudo apt-get install xlibs-dev    
```

---

### Post by Brunellus on 2006-06-21
please see the ubuntu fluxbox howto on the wiki.  There's a link in my .sig

You'll find everything you need to know in there.

---

### Post by sdrsmart on 2008-05-11
This is my fluxbox menu file. I think it will help
```
[begin] (fluxbox)

include-menu-defs

   [submenu] (programs) {}
      [exec] (terminal) {gnome-terminal} <~/.fluxbox/pixmaps/gloss/scalable/apps/gnome-terminal.png>
      [exec] (xterm) {xterm} <~/.fluxbox/pixmaps/gloss/scalable/apps/terminal.png>
      [exec] (urxvt) {urxvt}  <~/.fluxbox/pixmaps/gloss/scalable/apps/terminal.png>
      [exec] (Thunar) {thunar}  <~/.fluxbox/pixmaps/gloss/scalable/apps/file-manager.png>
      [exec] (Mozilla Firefox) {firefox}  <~/.fluxbox/pixmaps/gloss/scalable/apps/256/mozilla-firefox.png>
      [exec] (Gimp) {gimp}  <~/.fluxbox/pixmaps/gloss/scalable/apps/256/gimp.png>
      [exec] (Gqview) {gqview} <~/.fluxbox/pixmaps/gloss/scalable/apps/expose.png>
      [exec] (Audacious) {audacious} <~/.fluxbox/pixmaps/gloss/scalable/apps/audacious.png>
      [exec] (VLC Media Player) {vlc} <~/.fluxbox/pixmaps/gloss/scalable/apps/256/vlc.png>
      [exec] (Banshee Media Player) {banshee} <~/.fluxbox/pixmaps/gloss/scalable/apps/banshee.png>
      [exec] (Deluge Torrent Client) {deluge} <~/.fluxbox/pixmaps/gloss/scalable/apps/deluge-torrent.png>
      [exec] (Pidgin Messenger) {pidgin} <~/.fluxbox/pixmaps/gloss/scalable/apps/256/pidgin.png>
      [exec] (Open Office suit) {openoffice} <~/.fluxbox/pixmaps/gloss/scalable/apps/ooo-base.png>
      [exec] (Inkscape) {inkscape} <~/.fluxbox/pixmaps/gloss/scalable/apps/inkscape.png>
      [exec] (gftp) {gftp} <~/.fluxbox/pixmaps/gloss/scalable/apps/ghostview.png>
   [end]
   [separator]
   [submenu] (Backgrounds) {}
      [wallpapermenu] (~/.fluxbox/backgrounds/)
   [end]
   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [exec] (Reconfigure) {fluxconf}
   [urxvt &]
   [separator]
   [restart] (Restart)
   [exit] (Logout)
#[include] (/etc/X11/fluxbox/system.fluxbox-menu)
[end]
```

you can check out the manpage of fluxbox and edit the init file and startup file as you need.

---


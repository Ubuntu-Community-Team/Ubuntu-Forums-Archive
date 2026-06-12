---
title: "fluxbox help"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by aznboi on 2005-11-28
I installed fluxbox and some suggested packages for it via the apt-get command in the terminal. I run fluxbox in the terminal and get the following:
```
root@UbuntuLaptop:/home/hpham# fluxbox
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US/fluxbox.cat)
for translation, using default messages.
Failed to load database:/root/.fluxbox/init
Retrying with: /etc/X11/fluxbox/init
Failed to read: session.tabs
Setting default value
Failed to read: session.ignoreBorder
Setting default value
Failed to read: session.forcePseudoTransparency
Setting default value
Failed to read: session.numLayers
Setting default value
Failed to read: session.updateDelayTime
Setting default value
Failed to read: session.tabPadding
Setting default value
Failed to read: session.focusTabMinWidth
Setting default value
Failed to read: session.slitlistFile
Setting default value
Failed to read: session.groupFile
Setting default value
Failed to read: session.appsFile
Setting default value
Failed to read: session.tabsAttachArea
Setting default value
Failed to read: session.useMod1
Setting default value
apps file failure
ThemeItem<Font>: Warning! Failed to load default value 'fixed'
ThemeItem<Font>: Warning! Failed to load default value 'fixed'
ThemeItem<Font>: Warning! Failed to load default value 'fixed'
Failed to read: session.screen0.imageDither
Setting default value
Failed to read: session.screen0.opaqueMove
Setting default value
Failed to read: session.screen0.sloppywindowgrouping
Setting default value
Failed to read: session.screen0.workspacewarping
Setting default value
Failed to read: session.screen0.desktopwheeling
Setting default value
Failed to read: session.screen0.autoRaise
Setting default value
Failed to read: session.screen0.clickRaises
Setting default value
Failed to read: session.screen0.decorateTransient
Setting default value
Failed to read: session.screen0.rootCommand
Setting default value
Failed to read: session.screen0.resizeMode
Setting default value
Failed to read: session.screen0.windowMenu
Setting default value
Failed to read: session.screen0.followModel
Setting default value
Failed to read: session.screen0.window.focus.alpha
Setting default value
Failed to read: session.screen0.window.unfocus.alpha
Setting default value
Failed to read: session.screen0.menu.alpha
Setting default value
Failed to read: session.screen0.menuDelay
Setting default value
Failed to read: session.screen0.menuDelayClose
Setting default value
Failed to read: session.screen0.menuMode
Setting default value
Failed to read: session.screen0.overlay.lineWidth
Setting default value
Failed to read: session.screen0.overlay.lineStyle
Setting default value
Failed to read: session.screen0.overlay.joinStyle
Setting default value
Failed to read: session.screen0.overlay.capStyle
Setting default value
BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running.

```

anyone have any ideas?Thnx.

---

### Post by super on 2005-11-28
the last few lines explain what the problem is:
> [FONT="Courier New"]BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running.[/FONT]

you need to log out first. then select fluxbox from the login manager's 'sessions' menu.

---

### Post by aznboi on 2005-11-28
[QUOTE=super]the last few lines explain what the problem is:


you need to log out first. then select fluxbox from the login manager's 'sessions' menu.[/QUOTE]

wowwwwwww i feel like a total n00b... which i am, but still..... thnx that worked. But how do i get gtkwifi working after? cuz when im in the fluxbox, my wifi doesnt seem to work... thnx

---

### Post by aznboi on 2005-11-28
actually my wifi is working! But how do i open up the gtkwifi utility? Cuz it works, but i cant choose my AP since i cant see gtkwifi....thnx

---

